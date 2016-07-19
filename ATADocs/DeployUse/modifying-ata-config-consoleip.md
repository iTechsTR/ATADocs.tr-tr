---
title: "ATA yapılandırmasını değiştirme - ATA Konsolu IP adresi | Microsoft Advanced Threat Analytics"
description: "ATA Gateway bileşenleri üzerindeki ATA Konsolu’nun kısayolunu oluşturmak için kullanılan ATA Konsolu IP adresinin nasıl değiştirileceği açıklanır."
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 50118465-df34-4e04-b0cc-48808b6a96b1
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8d1dedaf86031e8585cca23241aead58f7f3db4e
ms.openlocfilehash: ee775e66de1a56b5270b0d32c7d5ca33d4d7980c


---

# Ata yapılandırmasını değiştirme - ATA Konsolu IP adresi

>[!div class="step-by-step"]
[« ATA Center sertifikası](modifying-ata-config-centercert.md)
[IIS sertifikası »](modifying-ata-config-iiscert.md)

## ATA Konsolu IP adresini değiştirme
Varsayılan olarak, ATA Konsolu URL'si ATA Center’ı yüklerken seçilen ATA Konsolu IP adresidir.

URL aşağıdaki senaryolarda kullanılır:

-   ATA Gateway bileşenleri yüklemesi – ATA Gateway yüklenirken, kendini ATA Center’a kaydeder. Bu kayıt işlemi ATA Konsolu’na bağlantı kurularak gerçekleştirilir. ATA Konsolu URL’si için bir FQDN girerseniz, ATA Gateway’in FQDN’yi ATA Konsolu’nun bir IIS’ye bağlı olduğu IP adresine çözümleyebileceğinden emin olmalısınız. Buna ek olarak, URL ATA Gateway bileşenlerinde ATA Konsolu’nun kısayolunu oluşturmak için kullanılır.

-   Uyarılar – ATA bir SIEM veya e-posta uyarısı gönderdiğinde, kuşkulu etkinliğin bağlantısını içerir. Bağlantının ana bilgisayar bölümü, ATA Konsolu URL ayarıdır.

-   İç Sertifika Yetkilinizden (CA) bir sertifika yüklediyseniz, kullanıcıların ATA Konsolu’na bağlanırken uyarı iletisi almalarını önlemek için büyük olasılıkla URL’yi sertifikanın konu adıyla eşleştirmek istersiniz.

-   ATA Konsolu URL’si olarak bir FQDN kullanmak, geçmişte gönderilmiş olan uyarıları kesmeden veya ATA Gateway paketini yeniden indirmek zorunda kalmadan, IIS tarafından ATA Konsolu için kullanılan IP adresini değiştirebilmenizi sağlar. DNS’yi yeni IP adresiyle güncelleştirmeniz yeterli olur.

> [!NOTE]
> ATA Konsolu URL’sini değiştirdikten sonra, yeni ATA Gateway bileşenlerini yüklemeden ATA Gateway Kurulum paketini indirmelisiniz.

IIS tarafından ATA Konsolu için kullanılan IP adresini değiştirmeniz gerekirse, ATA Center sunucusunda şu adımları izleyin.

1.  ATA Center sunucusunda IP adresini yükleyin.

2.  Internet Information Services (IIS) Yöneticisi’ni açın.

3.  Sunucunun adını genişletin ve **Siteler**’i genişletin.

4.  Microsoft ATA Konsolu sitesini seçin ve **Eylemler** bölmesinde **Bağlamalar**’a tıklayın.

    ![ATA Konsolu bağlamalar eyleminin resmi](media/ATA-console-change-IP-bindings.jpg)

5.  Yeni IP adresini seçmek için, **HTTP**’yi seçin ve **Düzenle**’ye tıklayın. **HTTPS** için de aynı işlemi yapın ve aynı IP adresini seçin.

    ![Site bağlamasını düzenleme resmi](media/ATA-change-console-IP.jpg)

6.  **Eylem** bölmesinde, **Web Sitesini Yönet**’in altında **Yeniden Başlat**’a tıklayın.

7.  Yönetici komut istemini açın ve HTTP.SYS sürücüsünü güncelleştirmek için aşağıdaki komutları yazın:

    -   Yeni IP adresi eklemek için - `netsh http add iplisten ipaddress=newipaddress`

    -   Yeni adresin kullanılmakta olduğunu görmek için - `netsh http show iplisten`

    -   Eski IP adresini silmek için – `netsh http delete iplisten ipaddress=oldipaddress`

8.  ATA Konsolu URL’si hala bir IP adresi kullanıyorsa, ATA Konsolu URL’sini yeni IP adresini kullanacak şekilde güncelleştirin ve yeni ATA Gateway bileşenlerini dağıtmadan önce ATA Gateway Kurulum paketini indirin.

9. ATA Konsolu URL’si bir FQDN ise, FQDN için DNS’yi yeni IP adresiyle güncelleştirin.

>[!div class="step-by-step"]
[« ATA Center sertifikası](modifying-ata-config-centercert.md)
[IIS sertifikası »](modifying-ata-config-iiscert.md)


## Ayrıca Bkz.
- [ATA Konsolu’yla çalışma](working-with-ata-console.md)
- [ATA’yı yükleme](install-ata.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jun16_HO4-->


