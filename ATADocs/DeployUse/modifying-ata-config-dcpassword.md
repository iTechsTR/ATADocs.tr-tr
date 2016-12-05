---
title: "ATA yapılandırmasını değiştirme: etki alanı bağlantısı parolası | Microsoft Docs"
description: "ATA Gateway’de Etki Alanı Bağlantı Parolası’nın nasıl değiştirileceği açıklanır."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 4a25561b-a5ed-44aa-9b72-366976b3c72a
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bc7af91a925928183d179391f15d3a24cda2b576
ms.openlocfilehash: a6dbdb0d53a0a7f6903ec858bb44054c624ae226


---

*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*



# <a name="change-ata-configuration---domain-connectivity-password"></a>ATA yapılandırmasını değiştirme - etki alanı bağlantısı parolası

>[!div class="step-by-step"]
[« ATA Konsolu URL’si](modifying-ata-config-consoleurl.md)


## <a name="change-the-domain-connectivity-password"></a>Etki alanı bağlantı parolasını değiştirme
Etki Alanı Bağlantısı Parolası’nı değiştirirseniz, girdiğiniz parolanın doğru olduğundan emin olun. Doğru olmazsa, ATA Gateway hizmeti ATA Gateway bileşenleri üzerinde çalışmayı durdurur.

Böyle bir durum oluştuğundan kuşkulanırsanız, Microsoft.Tri.Gateway-Errors.log dosyasında şunu arayın: `The supplied credential is invalid.`

Bunu düzeltmek için, bu yordamı izleyerek ATA Center’da Etki Alanı Bağlantısı parolasını güncelleştirin:

1.  ATA Center’da ATA Konsolu’nu açın.

2.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

3.  **Dizin Hizmetleri**’ni seçin.

    ![ATA Gateway parola değiştirme resmi](media/ATA-GW-change-DC-password.png)

4.  **Parola** altında, parolayı değiştirin.

    ATA Center’ın etki alanına bağlantısı varsa, kimlik bilgilerini doğrulamak için **Bağlantıyı Sına** düğmesine tıklayın

5.  **Kaydet**'e tıklayın.

6.  Parolayı değiştirdikten sonra, ATA Gateway sunucularında ATA Gateway hizmetinin çalıştığını el ile denetleyin.

>[!div class="step-by-step"]
[« ATA Konsolu URL’si](modifying-ata-config-consoleurl.md)

## <a name="see-also"></a>Ayrıca bkz.
- [ATA Konsolu ile çalışma](working-with-ata-console.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Nov16_HO5-->


