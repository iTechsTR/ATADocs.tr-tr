---
# required metadata

title: ATA Uyarılarını Ayarlama | Microsoft Advanced Threat Analytics
description: ATA’nın kuşkulu etkinlikler algıladığında sizi nasıl uyaracağı (e-postayla veya ATA olay iletme yoluyla) açıklanır 
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

# ATA Uyarılarını Ayarlama
ATA kuşkulu bir etkinlik algıladığında e-postayla veya ATA olay iletme özelliğini kullanıp olayı SIEM/syslog sunucunuza ileterek sizi uyarabilir. Bu uyarı türlerinden birini veya her ikisini etkinleştirirseniz, bu uyarılar için aşağıdakileri ayarlayabilirsiniz.

> [!NOTE]
> -   E-posta bildirimleri kullanıcıyı doğrudan algılanan kuşkulu etkinliğe götüren bir bağlantı içerir. Bağlantının ana bilgisayar adı bölümü ATA Center sayfasındaki ATA Konsolu URL’si ayarından alınır. Varsayılan olarak, ATA Konsolu URL’si ATA Center’ın yüklemesi sırasında seçilen IP adresidir.  E-posta uyarılarını yapılandıracaksanız, ATA Konsolu URL’si olarak FQDN kullanmanız önerilir.
> -   Sistem Durumu Uyarıları yalnızca e-postayla gönderilir.
> -   Uyarılar, ATA Center’dan SMTP sunucusuna veya Syslog sunucusuna gönderilir.
> -   Kuşkulu etkinlikler için e-posta uyarıları, yalnızca kuşkulu etkinlik oluşturulduğunda gönderilir.

## Dili ve sıklığı ayarlama
**Dil** ayarı e-postayla gönderilen bildirimlere ve Syslog sunucusuna gönderilen bildirimlere uygulanır.

**Sıklık** ayarı, yalnızca Syslog sunucusuna gönderilen bildirimlere uygulanır.

1.  ATA Konsolu’nu açın.

2.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin..

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

3.  **Uyarılar**’ı seçin..

4.  **Dil**’in altında istediğiniz dili seçin.

5.  **Sıklık**’ın altında, yalnızca yeni uyarı oluşturulduğunda kısa bir bildirim almak istiyorsanız **Düşük sıklıkta** ayarını seçin. Hem yeni uyarı oluşturulduğunda hem de var olan uyarılar değiştirildiğinde ayrıntılı bir bildirim almak istiyorsanız **Yüksek sıklıkta** ayarını seçin.

    ![Uyarı ayrıntı düzeyini yapılandırma resmi](media/ATA-alerts-verbosity-language.png)

6.  **Kaydet**'e tıklayın..

## E-posta uyarılarını ayarlama
ATA, kuşkulu bir etkinlik algıladığında sizi uyarabilir. E-posta uyarılarını etkinleştirirseniz, bu uyarılar için aşağıdakileri ayarlayabilirsiniz.

1.  ATA Center sunucusunda, masaüstündeki **Microsoft Advanced Threat Analytics Yönetimi** simgesine tıklayın.

2.  Kullanıcı adınızla parolanızı girin ve **Oturum aç**’a tıklayın..

3.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin..

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

4.  **Uyarılar**’ı seçin..

5.  E-posta uyarılarını etkinleştirmek için **Posta**’yı açın ve şu bilgileri girin:

    |Alan|Açıklama|Değer|
    |---------|---------------|---------|
    |SMTP sunucusu uç noktası (gerekli)|SMTP sunucunuzun FQDN değerini girin.|Örneğin:<br />smtp.contoso.com|
    |SSL|SMTP sunucusu SSL gerektiriyorsa, SSL’ye geçin. **Not:** SSL’yi etkinleştirirseniz Bağlantı noktası numarasını da değiştirmeniz gerekir.|Varsayılan devre dışı olmasıdır|
    |Kimlik doğrulaması|SMTP sunucunuz kimlik doğrulaması gerektiriyorsa etkinleştirin. **Not:** Kimlik doğrulamasını etkinleştirirseniz, SMTP sunucusuna bağlanma izni olan bir e-posta hesabının kullanıcı adını ve parolasını sağlamanız gerekir.|Varsayılan devre dışı olmasıdır|
    |Gönderen (gerekli)|E-postayı gönderecek olan e-posta adresini girin.|Örneğin:<br />ATA@contoso.com|
    |Alan (gerekli)|ATA kuşkulu bir etkinlik algıladığında e-postaları alması gereken kullanıcıların ve e-posta gruplarının e-posta adreslerini girin. **Not:** Bir kerede tek bir e-posta adresi girin ve eklemek için artı işaretine tıklayın.|Örneğin:<br />guvenlikekibi@contoso.com|

## SIEM’e ATA olay iletmeyi ayarlama
ATA kuşkulu bir etkinlik algıladığında Syslog sunucunuza uyarı göndererek sizi uyarabilir. Syslog uyarılarını etkinleştirirseniz, bu uyarılar için aşağıdakileri ayarlayabilirsiniz.

1.  Syslog uyarılarını yapılandırmadan önce, SIEM yöneticinizle birlikte çalışarak aşağıdaki bilgileri bulun:

    -   SIEM sunucusunun FQDN değeri veya IP adresi

    -   SIEM sunucusunun dinlediği bağlantı noktası

    -   Hangi aktarım (UDP, TCP veya Güvenli TCP) kullanılacak?

    -   Veriler gönderilirken kullanılacak biçim, RFC 3164 veya 5424

2.  ATA Center sunucusunda, masaüstündeki **Microsoft Advanced Threat Analytics Yönetimi** simgesine tıklayın.

3.  Kullanıcı adınızla parolanızı girin ve **Oturum aç**’a tıklayın..

4.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin..

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

5.  **Uyarılar**’ı seçin..

6.  Kuşkulu etkinlikler hakkındaki uyarıların Syslog sunucunuza gönderilebilmesini sağlamak için **Syslog**’u açın ve aşağıdaki bilgileri girin:

    |Alan|Açıklama|
    |---------|---------------|
    |Syslog sunucusu uç noktası|Syslog sunucusunun FQDN değeri|
    |Aktarım|UDC, TCP veya Güvenli TCP olabilir|
    |Biçim|Bu, ATA’nın olayları SIEM sunucusuna gönderirken kullandığı biçimdir; RFC 5424 veya RFC 3164.|

## Ayrıca Bkz.
[Destek için forumumuzu gözden geçirin!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=Apr16_HO4-->


