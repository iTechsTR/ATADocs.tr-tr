---
# required metadata

title: ATA Bildirimlerini Ayarlama | Microsoft Advanced Threat Analytics
description: ATA’nın kuşkulu etkinlikler algıladığında size nasıl bildireceği (e-postayla veya ATA olay iletme yoluyla) açıklanır 
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 14cb7513-5dc8-49cb-b3e0-94f469c443dd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ATA Bildirimlerini Ayarlama
ATA kuşkulu bir etkinlik algıladığında e-postayla veya ATA olay iletme özelliğini kullanıp olayı SIEM/syslog sunucunuza ileterek size bildirebilir. Hangi bildirimleri almak istediğinizi seçmeden önce, [e-posta sunucunuzu ve Syslog sunucunuzu ayarlamanız](setting-syslog-email-server-settings.md) gerekir.

> [!NOTE]
> -   E-posta bildirimleri kullanıcıyı doğrudan algılanan kuşkulu etkinliğe götüren bir bağlantı içerir. Bağlantının ana bilgisayar adı bölümü ATA Center sayfasındaki ATA Konsolu URL’si ayarından alınır. Varsayılan olarak, ATA Konsolu URL’si ATA Center’ın yüklemesi sırasında seçilen IP adresidir.  E-posta bildirimlerini yapılandıracaksanız, ATA Konsolu URL’si olarak FQDN kullanmanız önerilir.
> -   Bildirimler, ATA Center’dan SMTP sunucusuna veya Syslog sunucusuna gönderilir.

E-posta bildirimleri almak için aşağıdakileri ayarlayın:


1. ATA Konsolu’nda, araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.
![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

2. **Bildirimler**’i seçin.
3. **E-posta bildirimleri** altında, hangi bildirimlerin gönderilmesi gerektiğini seçmek için değiştirme düğmelerini kullanın:


    - Yeni şüpheli etkinlik algılandı
    - Yeni bir sistem durumu sorunu algılandı
    - Yeni yazılım güncelleştirmesi kullanıma hazır

4. E-posta yoluyla bildirimleri alacak alıcıları belirtin.

    [!Not:] Kuşkulu etkinlikler için e-posta uyarıları, yalnızca kuşkulu etkinlik oluşturulduğunda gönderilir.


5. **Kaydet**'e tıklayın.

Syslog bildirimleri almak için aşağıdakileri ayarlayın:


1. ATA Konsolu’nda, araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.
![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

2. **Bildirimler**’i seçin.
3. **Syslog bildirimleri** altında, hangi bildirimlerin gönderilmesi gerektiğini seçmek için değiştirme düğmelerini kullanın:


    - Yeni şüpheli etkinlik algılandı
    - Varolan şüpheli etkinlik güncelleştirildi
    - Yeni bir sistem durumu sorunu algılandı
5. **Kaydet**'e tıklayın.
![ATA bildirim ayarları görüntüsü](media/ATA-notification-settings.png)




## Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=May16_HO3-->


