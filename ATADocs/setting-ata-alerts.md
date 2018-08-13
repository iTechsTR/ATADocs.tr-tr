---
title: Advanced Threat Analytics bildirimlerini ayarlama | Microsoft Docs
description: Şüpheli etkinlikler algılandığında bildirim almak için ATA uyarıları oluşturma adımları açıklanmaktadır.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 14cb7513-5dc8-49cb-b3e0-94f469c443dd
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 0b4d783d55d38d2a50c651ba47c584fed8bcee50
ms.sourcegitcommit: 1de2b047c0e9f92a106169f7634c480f694baf10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2018
ms.locfileid: "30010151"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="set-ata-notifications"></a>ATA Bildirimlerini Ayarlama
ATA şüpheli bir etkinlik algıladığında, e-postayla veya ATA olay iletme özelliğini kullanıp olayı SIEM/syslog sunucunuza ileterek size bildirebilir. Hangi bildirimleri almak istediğinizi seçmeden önce, [e-posta sunucunuzu ve Syslog sunucunuzu ayarlamanız](setting-syslog-email-server-settings.md) gerekir.

> [!NOTE]
> -   E-posta bildirimleri kullanıcıyı doğrudan algılanan kuşkulu etkinliğe götüren bir bağlantı içerir. Bağlantının ana bilgisayar adı bölümü ATA Center sayfasındaki ATA Konsolu URL’si ayarından alınır. Varsayılan olarak, ATA Konsolu URL’si ATA Center’ın yüklemesi sırasında seçilen IP adresidir. E-posta bildirimlerini yapılandırmak için kullanacaksanız, ATA Konsolu URL'si olarak FQDN kullanmanız önerilir.
> -   Bildirimler, ATA Center’dan SMTP sunucusuna veya Syslog sunucusuna gönderilir.


Bildirimleri almak için şu parametreleri ayarlayın:


1. ATA Konsolu’nda, araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.png)

2. **Bildirimler ve Raporlar** bölümü altında **Bildirimler**’i seçin.
3. **Posta bildirimleri** altında hangi bildirimlerin (yeni şüpheli etkinlikler ve yeni sistem durumu sorunları) e-posta yoluyla gönderileceğini belirtin. Şüpheli etkinlikler ve sistem durumu uyarıları için ayrı e-posta adresleri belirleyebilirsiniz, böylece örneğin, şüpheli etkinlik bildirimleri güvenlik analistinize gönderilirken sistem durumu uyarı bildirimleri BT yöneticinize gönderilebilir.
>   [!NOTE]
>   Kuşkulu etkinlikler için e-posta uyarıları, yalnızca kuşkulu etkinlik oluşturulduğunda gönderilir.
3. Altında **Syslog bildirimlerini**, Syslog sunucunuza - yeni şüpheli etkinlikler, güncelleştirilmiş şüpheli etkinlikler ve yeni sistem durumu sorunları hangi bildirimlerin gönderilmesi gerektiğini belirtin.
5. **Kaydet**'e tıklayın.

![ATA posta bildirimi ayarları resmi](media/ata-mail-notification-settings.png)




## <a name="see-also"></a>Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
