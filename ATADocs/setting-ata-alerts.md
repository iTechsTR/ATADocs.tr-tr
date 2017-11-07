---
title: Advanced Threat Analytics bildirimlerini ayarlama | Microsoft Docs
description: "Şüpheli etkinlikler algılandığında bildirim almak için ATA uyarıları oluşturma adımları açıklanmaktadır."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 14cb7513-5dc8-49cb-b3e0-94f469c443dd
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 11692b6c61c2a06b338615fbf1ad83ace2fae419
ms.sourcegitcommit: e2cb3af9c1dbb0b75946dc70cc439b19d654541c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="set-ata-notifications"></a>ATA Bildirimlerini Ayarlama
ATA şüpheli bir etkinlik algıladığında, e-postayla veya ATA olay iletme özelliğini kullanıp olayı SIEM/syslog sunucunuza ileterek size bildirebilir. Hangi bildirimleri almak istediğinizi seçmeden önce, [e-posta sunucunuzu ve Syslog sunucunuzu ayarlamanız](setting-syslog-email-server-settings.md) gerekir.

> [!NOTE]
> -   E-posta bildirimleri kullanıcıyı doğrudan algılanan kuşkulu etkinliğe götüren bir bağlantı içerir. Bağlantının ana bilgisayar adı bölümü ATA Center sayfasındaki ATA Konsolu URL’si ayarından alınır. Varsayılan olarak, ATA Konsolu URL’si ATA Center’ın yüklemesi sırasında seçilen IP adresidir.  E-posta bildirimlerini yapılandıracaksanız, ATA Konsolu URL’si olarak FQDN kullanmanız önerilir.
> -   Bildirimler, ATA Center’dan SMTP sunucusuna veya Syslog sunucusuna gönderilir.


Bildirim almak için aşağıdakileri uygulayın:


1. ATA Konsolu’nda, araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.png)

2. **Bildirimler ve Raporlar** bölümü altında **Bildirimler**’i seçin.
3. **Posta bildirimleri** altında hangi bildirimlerin (yeni şüpheli etkinlikler ve yeni sistem durumu sorunları) e-posta yoluyla gönderileceğini belirtin. Şüpheli etkinlikler ve sistem durumu uyarıları için ayrı e-posta adresleri belirleyebilirsiniz, böylece örneğin, şüpheli etkinlik bildirimleri güvenlik analistinize gönderilirken sistem durumu uyarı bildirimleri BT yöneticinize gönderilebilir.
>   [!NOTE]
>   Kuşkulu etkinlikler için e-posta uyarıları, yalnızca kuşkulu etkinlik oluşturulduğunda gönderilir.
3. **Syslog bildirimleri** altında hangi bildirimlerin (yeni şüpheli etkinlikler, güncelleştirilmiş şüpheli etkinlikler ve yeni sistem durumu sorunları) Syslog sunucunuza gönderileceğini belirtin.
5. **Kaydet**'e tıklayın.

![ATA posta bildirimi ayarları resmi](media/ata-mail-notification-settings.png)




## <a name="see-also"></a>Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
