---
title: "Advanced Threat Analytics’i Yükleme - 6. Adım | Microsoft Docs"
description: "ATA’yı yükleme işleminin son adımında Honeytoken kullanıcısını yapılandırırsınız."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 8980e724-06a6-40b0-8477-27d4cc29fd2b
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: da6e72ac5c2966f3e77ce3bef8fe23fcda6770a4
ms.sourcegitcommit: 9b128d6946e32b00f595e00902b9ff95f18141ff
translationtype: HT
---
*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*



# <a name="install-ata---step-6"></a>ATA’yı Yükleme - 6. Adım

>[!div class="step-by-step"]
[« 5. Adım](install-ata-step5.md)

## <a name="step-6-configure--ip-address-exclusions-and-honeytoken-user"></a>6. Adım. IP adresi dışlamalarını ve Honeytoken kullanıcısını yapılandırma
ATA, belirli IP adreslerinin iki tür algılamadan dışlanmasını sağlar: **DNS Keşfi** ve **Anahtar Geçişi**. 

Örneğin, bir **DNS Keşfi dışlaması** DNS’i tarama mekanizması olarak kullanan bir güvenlik tarayıcısı olabilir. Bu dışlama işlemi ATA’nın böyle tarayıcıları yoksaymasına yardımcı olur. *Anahtar Geçişi* dışlama işlemine örnek olarak bir NAT aygıtı gösterilebilir.    

ATA ayrıca, kötü amaçlı aktörler için tuzak olarak kullanılan bir Honeytoken kullanıcısının yapılandırılmasına olanak tanır. Bu hesapla (normalde etkinliği yoktur) ilişkilendirilen herhangi bir kimlik doğrulaması bir uyarının tetiklenmesine neden olur.

Yukarıdakileri yapılandırmak için şu adımları izleyin:

1.  ATA Konsolu’ndan, ayarlar simgesine tıklayın ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları](media/ATA-config-icon.JPG)

2.  **Algılama dışlamaları** altında, *DNS keşfi* veya *Anahtar Geçişi* için bir IP adresi girin ve *artı* işaretine tıklayın.

    ![Değişiklikleri kaydedin.](media/ATA-exclusions.png)

3.  **Algılama ayarları** altında Honeytoken hesap SID’lerini girin ve artı işaretine tıklayın. Örneğin: `S-1-5-21-72081277-1610778489-2625714895-10511`.

    ![ATA yapılandırma ayarları](media/ATA-honeytoken.png)

    > [!NOTE]
    > Bir kullanıcının SID’ini bulmak için, ATA Konsolu’nda kullanıcıyı arayın ve **Hesap Bilgileri** sekmesine tıklayın. 

4.  **Kaydet**'e tıklayın.


Tebrikler, Microsoft Advanced Threat Analytics dağıtımını başarıyla tamamladınız!

Algılanan kuşkulu etkinlikleri görüntülemek için saldırı zaman çizelgesini gözden geçirin ve kullanıcıları veya bilgisayarları arayın ve profillerini görüntüleyin.

ATA hemen şüpheli etkinlikler için tarama yapmaya başlar. ATA, davranış profilleri (en az üç haftalık) oluşturmak için zaman bulana kadar, bazı şüpheli davranış etkinlikleri gibi bazı etkinlikler kullanılamaz.

ATA’nın çalışır durumda olduğunu ve ağınızdaki ihlalleri yakalayıp yakalamadığını denetlemek için [ATA saldırı simülasyonu senaryo kitabına](https://docs.microsoft.com/enterprise-mobility-security/solutions/ata-attack-simulation-playbook) bakabilirsiniz.


>[!div class="step-by-step"]
[« 5. Adım](install-ata-step5.md)


## <a name="see-also"></a>Ayrıca bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)

