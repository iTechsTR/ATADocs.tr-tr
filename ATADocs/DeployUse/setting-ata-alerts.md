---
title: ATA Bildirimlerini Ayarlama | Microsoft Advanced Threat Analytics
description: "Şüpheli etkinlikler algılandığında bildirim almak için ATA uyarıları oluşturma adımları açıklanmaktadır."
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 14cb7513-5dc8-49cb-b3e0-94f469c443dd
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8d1dedaf86031e8585cca23241aead58f7f3db4e
ms.openlocfilehash: a32799b68d9a8b2949033ab5d1fc5910cff71258


---

# ATA Bildirimlerini Ayarlama
ATA şüpheli bir etkinlik algıladığında, e-postayla veya ATA olay iletme özelliğini kullanıp olayı SIEM/syslog sunucunuza ileterek size bildirebilir. Hangi bildirimleri almak istediğinizi seçmeden önce, [e-posta sunucunuzu ve Syslog sunucunuzu ayarlamanız](setting-syslog-email-server-settings.md) gerekir.

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

    [!Not:] Şüpheli etkinlikler için e-posta uyarıları, yalnızca şüpheli etkinlik oluşturulduğunda gönderilir.


5. **Kaydet**'e tıklayın.

Syslog bildirimleri almak için aşağıdakileri ayarlayın:


1. ATA Konsolu’nda, araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.
![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

2. **Bildirimler**’i seçin.
3. **Syslog bildirimleri** altında, hangi bildirimlerin gönderilmesi gerektiğini seçmek için değiştirme düğmelerini kullanın:


    - Yeni şüpheli etkinlik algılandı
    - Mevcut şüpheli etkinlik güncelleştirildi
    - Yeni bir sistem durumu sorunu algılandı
5. **Kaydet**'e tıklayın.
![ATA bildirim ayarları görüntüsü](media/ATA-notification-settings.png)




## Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jun16_HO4-->


