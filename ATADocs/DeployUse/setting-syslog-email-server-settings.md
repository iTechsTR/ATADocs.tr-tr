---
title: ATA Bildirimlerini Ayarlama | Microsoft Advanced Threat Analytics
description: "ATA’nın kuşkulu etkinlikler algıladığında size nasıl bildireceği (e-postayla veya ATA olay iletme yoluyla) açıklanır"
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
ms.openlocfilehash: 66194d89c3e937923e576004a3ab4b7177f179c4


---

## ATA’ya e-posta sunucusu ayarlarınızı belirtin
ATA, kuşkulu bir etkinlik algıladığında size bildirebilir. ATA’nın e-posta bildirimleri gönderebilmesi için öncelikle **E-posta sunucusu ayarları**’nı yapılandırmanız gerekir.

1.  ATA Center sunucusunda, masaüstündeki **Microsoft Advanced Threat Analytics Yönetimi** simgesine tıklayın.

2.  Kullanıcı adınızla parolanızı girin ve **Oturum aç**’a tıklayın.

3.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

4.  **Genel** sekmesinde, **E-posta sunucusu** altında, aşağıdaki bilgileri girin:

    |Alan|Açıklama|Değer|
    |---------|---------------|---------|
    |SMTP sunucusu uç noktası (gerekli)|SMTP sunucunuzun FQDN değerini girin.|Örneğin:<br />smtp.contoso.com|
    |SSL|SMTP sunucusu SSL gerektiriyorsa, SSL’ye geçin. **Not:** SSL’yi etkinleştirirseniz Bağlantı noktası numarasını da değiştirmeniz gerekir.|Varsayılan devre dışı olmasıdır|
    |Kimlik doğrulaması|SMTP sunucunuz kimlik doğrulaması gerektiriyorsa etkinleştirin. **Not:** Kimlik doğrulamasını etkinleştirirseniz, SMTP sunucusuna bağlanma izni olan bir e-posta hesabının kullanıcı adını ve parolasını sağlamanız gerekir.|Varsayılan devre dışı olmasıdır|
    |Gönderen (gerekli)|E-postayı gönderecek olan e-posta adresini girin.|Örneğin:<br />ATA@contoso.com|
    ![ATA e-posta sunucu ayarları resmi](media/ATA-email-server.png)

## ATA’ya Syslog sunucusu ayarlarınızı belirtin
ATA kuşkulu bir etkinlik algıladığında Syslog sunucunuza bildirim göndererek size bildirebilir. Syslog bildirimlerini etkinleştirirseniz, bu uyarılar için aşağıdakileri ayarlayabilirsiniz.

1.  Syslog bildirimlerini yapılandırmadan önce, SIEM yöneticinizle birlikte çalışarak aşağıdaki bilgileri bulun:

    -   SIEM sunucusunun FQDN değeri veya IP adresi

    -   SIEM sunucusunun dinlediği bağlantı noktası

    -   Hangi aktarım kullanılacak: UDP, TCP veya TLS (Güvenli Syslog)

    -   Veriler gönderilirken kullanılacak biçim, RFC 3164 veya 5424

2.  ATA Center sunucusunda, masaüstündeki **Microsoft Advanced Threat Analytics Yönetimi** simgesine tıklayın.

3.  Kullanıcı adınızla parolanızı girin ve **Oturum aç**’a tıklayın.

4.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

5.  **Syslog sunucusu**’nu seçin ve aşağıdaki bilgileri girin:

    |Alan|Açıklama|
    |---------|---------------|
    |Syslog sunucusu uç noktası|Syslog sunucusunun FQDN değeri|
    |Aktarım|UDC, TCP veya TLS (Güvenli Syslog) olabilir|
    |Biçim|Bu, ATA’nın olayları SIEM sunucusuna gönderirken kullandığı biçimdir; RFC 5424 veya RFC 3164.|





## Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jun16_HO4-->


