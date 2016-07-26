---
title: "ATA yapılandırmasını değiştirme - etki alanı bağlantısı parolası | Microsoft ATA"
description: "ATA Gateway’de Etki Alanı Bağlantı Parolası’nın nasıl değiştirileceği açıklanır."
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 4a25561b-a5ed-44aa-9b72-366976b3c72a
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5c7163bc7b1989672e587bfb4fa6a65cd4e3751
ms.openlocfilehash: 860a83aa4e6656480217a457bb2492431d73637a


---

# ATA yapılandırmasını değiştirme - etki alanı bağlantısı parolası

>[!div class="step-by-step"]
[« IIS sertifikası](modifying-ata-config-iiscert.md)


## Etki alanı bağlantı parolasını değiştirme
Etki Alanı Bağlantısı Parolası’nı değiştirirseniz, girdiğiniz parolanın doğru olduğundan emin olun. Doğru olmazsa, ATA Gateway hizmeti ATA Gateway bileşenleri üzerinde çalışmayı durdurur.

Böyle bir durum oluştuğundan kuşkulanırsanız, Microsoft.Tri.Gateway-Errors.log dosyasında şunu arayın:
`The supplied credential is invalid.`

Bunu düzeltmek için, bu yordamı izleyerek ATA Gateway’de Etki Alanı Bağlantı Parolası’nı güncelleştirin:

1.  ATA Gateway’de ATA Konsolu’nu açın.

2.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

3.  **Genel**’i seçin.

    ![ATA Gateway parola değiştirme resmi](media/ATA-GW-change-DC-password.JPG)

4.  **Genel** altında, parolayı değiştirin.

5.  **Kaydet**'e tıklayın.

6.  Parolayı değiştirdikten sonra, ATA Gateway sunucularında ATA Gateway hizmetinin çalıştığını el ile denetleyin.

>[!div class="step-by-step"]
[« IIS sertifikası](modifying-ata-config-iiscert.md)

## Ayrıca Bkz.
- [ATA Konsolu’yla çalışma](working-with-ata-console.md)
- [ATA’yı yükleme](install-ata.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jul16_HO3-->


