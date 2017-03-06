---
title: "Advanced Threat Analytics için olağanüstü durum kurtarma| Microsoft Docs"
description: "Olağanüstü durum sonrası ATA işlevselliğini hızlıca nasıl kurtarabileceğinizi açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 02/28/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 7620e171-76d5-4e3f-8b03-871678217a3a
ms.reviewer: arzinger
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1d483b4e37ccfdc0eadaf895edf425f8aebfddee
ms.openlocfilehash: f27099ed3935aa5b3ece18397144f39e8e87564c
ms.lasthandoff: 02/28/2017


---

*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*



# <a name="ata-disaster-recovery"></a>ATA olağanüstü durum kurtarma
Bu makalede, ATA Center işlevselliğinin kaybolduğu ancak ATA Ağ Geçitlerinin çalışmayı sürdürdüğü durumlarda ATA Center’ı hızlıca kurtarıp ATA işlevselliğini hızlıca geri yükleyeme işlemini nasıl yapacağınız açıklanır. 

>[!NOTE]
> Açıklanan işlemle, daha önce algılanan şüpheli etkinlikler kurtarılmaz ancak ATA Center tam olarak işlevsel hale getirilir. Ayrıca, bazı davranış algılamaları için gereken öğrenme dönemi yeniden başlatılır ancak ATA’nın sunduğu algılamaların çoğu, ATA Center geri yüklendikten sonra çalışır duruma gelir. 

## <a name="back-up-your-ata-center-configuration"></a>ATA Center yapılandırmanızı yedekleme

1. ATA Center yapılandırması, bir dosyaya saat başı yedeklenir. ATA Center yapılandırmasının en son yedek kopyasını bulun ve ayrı bir bilgisayara kaydedin. Bu dosyaları nasıl bulacağınıza ilişkin tam açıklama için bkz. [ATA yapılandırmasını dışarı ve içeri aktarma](/advanced-threat-analytics/deploy-use/ata-configuration-file). 
2. ATA Center sertifikasını dışarı aktarın.
    1. Sertifika Yöneticisi'nde, **Sertifikalar (Yerel Bilgisayar)** -> **Kişisel** ->**Sertifikalar**’a gidip **ATA Center**’ı seçin.
    2. **ATA Center**’a sağ tıklayıp **Tüm Görevler**’i ve ardından **Dışarı Aktar**’ı seçin. 
     ![ATA Center Sertifikası](media/ata-center-cert.png)
    3. Sertifikayı dışarı aktarma yönergelerini izleyin ve özel anahtarı da dışarı aktardığınızdan emin olun.
    4. Dışarı aktarılan sertifika dosyasını ayrı bir bilgisayarda yedekleyin.

  > [!NOTE] 
  > Özel anahtarı dışarı aktaramazsanız, yeni bir sertifika oluşturmanız ve bunu [ATA Center sertifikasını değiştirme](/advanced-threat-analytics/deploy-use/modifying-ata-config-centercert) bölümünde açıklandığı gibi ATA’ya dağıtmanız gerekir. 

## <a name="recover-your-ata-center"></a>ATA Center’ı kurtarma

1. Önceki ATA Center makinesi ile aynı IP adresini ve bilgisayar adını kullanarak yeni bir Windows Server makinesi oluşturun.
4. Yukarıdaki bölümde yedeklediğiniz sertifikayı yeni sunucuya aktarın.
5. Yeni oluşturulan Windows Server'da [ATA Center dağıtma](/advanced-threat-analytics/deploy-use/install-ata-step1) yönergelerini izleyin. ATA Ağ Geçitlerini yeniden dağıtmaya gerek yoktur. Sertifika istendiğinde, ATA Center yapılandırmasını yedeklerken dışarı aktardığınız sertifikayı sağlayın. 
![ATA Center’ı geri yükleme](media/ata-center-restore.png)
6. Yedeklenen ATA Center yapılandırmasını içeri aktarın:
    1. Varsayılan ATA Center Sistem Profili belgesini MongoDB’den kaldırın: 
        1. **C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin** yoluna gidin. 
        2. `mongo.exe` öğesini çalıştırın. 
        3. Varsayılan sistem profilini kaldırmak için şu komutu çalıştırın: `db.SystemProfile.remove({})`
    2. 1. adımdaki yedekleme dosyasını kullanarak şu komutu çalıştırın: `mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`</br>
    Yedekleme dosyalarını nasıl bulacağınıza ve içeri aktaracağınıza ilişkin tam açıklama için bkz. [ATA yapılandırmasını dışarı ve içeri aktarma](/advanced-threat-analytics/deploy-use/ata-configuration-file). 
    3. İçeri aktarma işleminden sonra, bazı varsayılan sistem profillerini kaldırmak için (bunları yeni ortam için sıfırlamak amacıyla) şu komutu çalıştırın: `db.SystemProfile.remove({$or:[{"_t":"DetectorProfile"}, "_t":"DirectoryServicesSystemProfile"}]}) `
    4. ATA Konsolu’nu açın. Tüm ATA Ağ Geçitlerinin, Yapılandırma/Ağ Geçitleri sekmesi altında bağlı olduğunu görmeniz gerekir. 
    5. Bir [**Dizin hizmetleri kullanıcısı**](/advanced-threat-analytics/deploy-use/install-ata-step2) tanımladığınızdan ve bir [**Etki alanı denetleyicisi eşitleyicisi**](/advanced-threat-analytics/deploy-use/install-ata-step5) seçtiğinizden emin olun. 






## <a name="see-also"></a>Ayrıca Bkz.
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [ATA kapasite planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [Olay koleksiyonunu yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [Windows olay iletme özelliğini yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

