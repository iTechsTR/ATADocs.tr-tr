---
title: Advanced Threat Analytics’te e-posta bildirim ayarlarını yapma | Microsoft Docs
description: ATA’nın kuşkulu etkinlikler algıladığında size nasıl bildireceği (e-postayla veya ATA olay iletme yoluyla) açıklanır
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: bff20bf7-8b53-49da-81e5-b818a1c3b24e
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: b702574a3b46c91d779236a4ab45fe5faf56210a
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133761"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="provide-ata-with-your-email-server-settings"></a>ATA’ya e-posta sunucusu ayarlarınızı belirtin
ATA, kuşkulu bir etkinlik algıladığında size bildirebilir. ATA’nın e-posta bildirimleri gönderebilmesi için öncelikle **E-posta sunucusu ayarları**’nı yapılandırmanız gerekir.

1.  ATA Center sunucusunda, masaüstündeki **Microsoft Advanced Threat Analytics Yönetimi** simgesine tıklayın.

2.  Kullanıcı adınızla parolanızı girin ve **Oturum aç**’a tıklayın.

3.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.png)

4.  **Bildirimler** bölümündeki **Posta sunucusu** altında aşağıdaki bilgileri girin:

    |Alan|Description|Değer|
    |---------|---------------|---------|
    |SMTP sunucusu uç noktası (gerekli)|SMTP sunucunuzun FQDN’sini girin ve isteğe bağlı olarak bağlantı noktası numarasını (varsayılan 25) değiştirin.|Örneğin:<br />smtp.contoso.com|
    |SSL|SMTP sunucusu SSL gerektiriyorsa, SSL’ye geçin. **Not:** SSL'yi etkinleştirirseniz, ayrıca bağlantı noktası numarasını değiştirmeniz gerekir.|Varsayılan devre dışı olmasıdır|
    |Kimlik doğrulama|SMTP sunucunuz kimlik doğrulaması gerektiriyorsa etkinleştirin. **Not:** kimlik doğrulamasını etkinleştirirseniz, bir kullanıcı adı ve SMTP sunucusuna bağlanma izni olan bir e-posta hesabının parolasını sağlamanız gerekir.|Varsayılan devre dışı olmasıdır|
    |Gönderen (gerekli)|E-postayı gönderecek olan e-posta adresini girin.|Örneğin:<br />ATA@contoso.com|
    
    ![ATA e-posta sunucu ayarları resmi](media/ata-email-server.png)

## <a name="provide-ata-with-your-syslog-server-settings"></a>ATA’ya Syslog sunucusu ayarlarınızı belirtin
ATA kuşkulu bir etkinlik algıladığında Syslog sunucunuza bildirim göndererek size bildirebilir. Syslog bildirimlerini etkinleştirirseniz, bu uyarılar için aşağıdakileri ayarlayabilirsiniz.

1.  Syslog bildirimlerini yapılandırmadan önce, SIEM yöneticinizle birlikte çalışarak aşağıdaki bilgileri bulun:

    -   SIEM sunucusunun FQDN değeri veya IP adresi

    -   SIEM sunucusunun dinlediği bağlantı noktası

    -   Hangi aktarım kullanılacak: UDP, TCP veya TLS (güvenli Syslog)

    -   Veriler gönderilirken kullanılacak biçim, RFC 3164 veya 5424

2.  ATA Center sunucusunda, masaüstündeki **Microsoft Advanced Threat Analytics Yönetimi** simgesine tıklayın.

3.  Kullanıcı adınızla parolanızı girin ve **Oturum aç**’a tıklayın.

4.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.png)

5.  Bildirimler bölümü altında **Syslog sunucusu**’nu seçin ve aşağıdaki bilgileri girin:

    |Alan|Description|
    |---------|---------------|
    |Syslog sunucusu uç noktası|Syslog sunucunuzun FQDN’sini girin ve isteğe bağlı olarak bağlantı noktası numarasını (varsayılan 514) değiştirin|
    |Aktarım|UDP, TCP veya TLS (güvenli Syslog) olabilir|
    |Biçim|Bu, ATA’nın olayları SIEM sunucusuna gönderirken kullandığı biçimdir; RFC 5424 veya RFC 3164.|

 ![ATA Syslog sunucusu ayarları resmi](media/ata-syslog-server-settings.png)



## <a name="see-also"></a>Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
