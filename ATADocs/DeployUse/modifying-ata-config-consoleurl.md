---
title: "ATA yapılandırmasını değiştirme - ATA Konsolu IP adresi | Microsoft Advanced Threat Analytics"
description: "ATA Gateway bileşenleri üzerindeki ATA Konsolu’nun kısayolunu oluşturmak için kullanılan ATA Konsolu IP adresinin nasıl değiştirileceği açıklanır."
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 08/24/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 50118465-df34-4e04-b0cc-48808b6a96b1
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 050f1ef0b39d69b64ede53243a7fa2d33d0e4813
ms.openlocfilehash: b3d11a87f1909c1fd964fa990e5d36a91691a844


---

*Uygulama hedefi: Advanced Threat Analytics sürüm 1.7*



# ATA yapılandırmasını değiştirme - ATA Konsolu URL’si

>[!div class="step-by-step"]
[« ATA Center sertifikası](modifying-ata-config-centercert.md)
[Etki alanı bağlantı parolası »](modifying-ata-config-dcpassword.md)

## ATA Konsolu URL’sini değiştirme
Varsayılan olarak, ATA Konsolu URL'si ATA Center’ı yüklerken seçilen ATA Konsolu IP adresidir.

URL aşağıdaki senaryolarda kullanılır:

-   ATA Gateway bileşenleri yüklemesi – ATA Gateway yüklenirken, kendini ATA Center’a kaydeder. Bu kayıt işlemi ATA Konsolu’na bağlantı kurularak gerçekleştirilir. ATA Konsolu URL’si için bir FQDN girerseniz, ATA Gateway’in FQDN’yi ATA Konsolu’nun bağlı olduğu IP adresine çözümleyebileceğinden emin olmanız gerekir.

-   Uyarılar – ATA bir SIEM veya e-posta uyarısı gönderdiğinde, kuşkulu etkinliğin bağlantısını içerir. Bağlantının ana bilgisayar bölümü, ATA Konsolu URL ayarıdır.

-   İç Sertifika Yetkilinizden (CA) bir sertifika yüklediyseniz, kullanıcıların ATA Konsolu’na bağlanırken uyarı iletisi almalarını önlemek için büyük olasılıkla URL’yi sertifikanın konu adıyla eşleştirmek istersiniz.

-   ATA Konsolu URL’si olarak bir FQDN kullanmak, geçmişte gönderilmiş olan uyarıları kesmeden veya ATA Gateway paketini yeniden indirmek zorunda kalmadan, ATA Konsolu için kullanılan IP adresini değiştirebilmenizi sağlar. DNS’yi yeni IP adresiyle güncelleştirmeniz yeterli olur.

> [!NOTE]
> ATA Konsolu URL’sini değiştirdikten sonra, yeni ATA Gateway bileşenlerini yüklemeden ATA Gateway Kurulum paketini indirmelisiniz.

ATA Konsolu URL’sini değiştirmeniz gerekirse, ATA Center sunucusunda şu adımları izleyin.

1.  ATA Konsolu’nu açın.

2.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

3.  **Center**’ı seçin.

4.  **Konsol IP Adresi** altında, mevcut IP adreslerinden birini seçin

5.  **Konsol URL’si** altında, URL’yi gerektiği gibi değiştirin:

    ![ATA Konsolu URL’si](media/ATA-chge-center-URL.png)
6.  **Kaydet**'e tıklayın.

>[!div class="step-by-step"]
[« ATA Center sertifikası](modifying-ata-config-centercert.md)
[Etki alanı bağlantı parolası »](modifying-ata-config-dcpassword.md)


## Ayrıca bkz.
- [ATA Konsolu’yla çalışma](working-with-ata-console.md)
- [ATA’yı yükleme](install-ata.md)
- [ATA forumuna bakın!](https://aka.ms/ata-forum)



<!--HONumber=Aug16_HO5-->


