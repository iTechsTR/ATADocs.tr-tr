---
title: Advanced Threat Analytics için olağanüstü durum kurtarma| Microsoft Docs
description: Olağanüstü durum sonrası ATA işlevselliğini hızlıca nasıl kurtarabileceğinizi açıklar
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 9/05/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 7620e171-76d5-4e3f-8b03-871678217a3a
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: 072abaef05432184653d260c43470e86a38d29db
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133591"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="ata-disaster-recovery"></a>ATA olağanüstü durum kurtarma
Bu makalede, ATA Center işlevselliğinin kaybolduğu ancak ATA Ağ Geçitlerinin çalışmayı sürdürdüğü durumlarda ATA Center’ı hızlıca kurtarıp ATA işlevselliğini hızlıca geri yükleyeme işlemini nasıl yapacağınız açıklanır. 

>[!NOTE]
> Açıklanan işlemle, daha önce algılanan şüpheli etkinlikler kurtarılmaz ancak ATA Center tam olarak işlevsel hale getirilir. Ayrıca, bazı davranış algılamaları için gereken öğrenme dönemi yeniden başlatılır ancak ATA’nın sunduğu algılamaların çoğu, ATA Center geri yüklendikten sonra çalışır duruma gelir. 

## <a name="back-up-your-ata-center-configuration"></a>ATA Center yapılandırmanızı yedekleme

1. ATA Center yapılandırmasını 4 saatte bir dosyaya yedeklenir. ATA Center yapılandırmasının en son yedek kopyasını bulun ve ayrı bir bilgisayara kaydedin. Bu dosyaları nasıl bulacağınıza ilişkin tam açıklama için bkz. [ATA yapılandırmasını dışarı ve içeri aktarma](ata-configuration-file.md). 
2. ATA Center sertifikasını dışarı aktarın.
    1. Sertifika Yöneticisi'nde, **Sertifikalar (Yerel Bilgisayar)** -> **Kişisel** ->**Sertifikalar**’a gidip **ATA Center**’ı seçin.
    2. Sağ **ATA Center** seçip **tüm görevler** ardından **dışarı**. 
     ![ATA Center Sertifikası](media/ata-center-cert.png)
    3. Sertifikayı dışarı aktarma yönergelerini izleyin ve özel anahtarı da dışarı aktardığınızdan emin olun.
    4. Dışarı aktarılan sertifika dosyasını ayrı bir bilgisayarda yedekleyin.

  > [!NOTE] 
  > Özel anahtarı dışarı aktaramazsanız, yeni bir sertifika oluşturmanız ve bunu [ATA Center sertifikasını değiştirme](modifying-ata-center-configuration.md) bölümünde açıklandığı gibi ATA’ya dağıtmanız gerekir. 

## <a name="recover-your-ata-center"></a>ATA Center’ı kurtarma

1. Önceki ATA Center makinesi ile aynı IP adresini ve bilgisayar adını kullanarak yeni bir Windows Server makinesi oluşturun.
2. Daha önce yedeklediğiniz sertifikayı yeni sunucuya aktarın.
3. Yeni oluşturulan Windows Server'da [ATA Center dağıtma](install-ata-step1.md) yönergelerini izleyin. ATA Ağ Geçitlerini yeniden dağıtmaya gerek yoktur. Sertifika istendiğinde, ATA Center yapılandırmasını yedeklerken dışarı aktardığınız sertifikayı sağlayın. 
![ATA Center’ı geri yükleme](media/disaster-recovery-deploymentss.png)
4. ATA Center hizmeti durdurun.
5. Yedeklenen ATA Center yapılandırmasını içeri aktarın:
    1. Varsayılan ATA Center Sistem Profili belgesini MongoDB’den kaldırın: 
        1. **C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin** yoluna gidin. 
        2. `mongo.exe ATA` öğesini çalıştırın. 
        3. Varsayılan sistem profilini kaldırmak için şu komutu çalıştırın: `db.SystemProfile.remove({})`
    2. Adımdaki yedekleme dosyasını kullanarak şu komutu çalıştırın: `mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`</br>
    Yedekleme dosyalarını nasıl bulacağınıza ve içeri aktaracağınıza ilişkin tam açıklama için bkz. [ATA yapılandırmasını dışarı ve içeri aktarma](ata-configuration-file.md). 
    3. ATA Center hizmeti başlatın.
    4. ATA Konsolu’nu açın. Tüm ATA Ağ Geçitlerinin, Yapılandırma/Ağ Geçitleri sekmesi altında bağlı olduğunu görmeniz gerekir.
    5. Bir [**Dizin hizmetleri kullanıcısı**](install-ata-step2.md) tanımladığınızdan ve bir [**Etki alanı denetleyicisi eşitleyicisi**](install-ata-step5.md) seçtiğinizden emin olun. 






## <a name="see-also"></a>Ayrıca Bkz.
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](install-ata-step6.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
