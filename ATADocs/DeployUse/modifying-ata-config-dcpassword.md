---
# required metadata

title: ATA yapılandırmasını değiştirme - etki alanı bağlantı parolası | Microsoft Advanced Threat Analytics
description: ATA Gateway’de Etki Alanı Bağlantı Parolası’nın nasıl değiştirileceği açıklanır.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 4a25561b-a5ed-44aa-9b72-366976b3c72a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ATA yapılandırmasını değiştirme - etki alanı bağlantısı parolası

>[!div class="step-by-step"]
[« IIS sertifikası](modifying-ata-config-iiscert.md)
[Yakalama ağ bağdaştırıcısının adı »](modifying-ata-config-nicname.md)

## Etki alanı bağlantı parolasını değiştirme
Etki Alanı Bağlantısı Parolası’nı değiştirirseniz, girdiğiniz parolanın doğru olduğundan emin olun. Doğru olmazsa, ATA Gateway bileşenleri üzerinde ATA Hizmeti çalışmayı durdurur.

Böyle bir durum oluştuğundan kuşkulanırsanız, Microsoft.Tri.Gateway-Errors.log dosyasında şunu arayın:
`The supplied credential is invalid.`

Bunu düzeltmek için, bu yordamı izleyerek ATA Gateway’de Etki Alanı Bağlantı Parolası’nı güncelleştirin:

1.  ATA Gateway’de ATA Konsolu’nu açın.

2.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin..

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

3.  **ATA Gateway**’i seçin..

    ![ATA Gateway parola değiştirme resmi](media/ATA-GW-change-DC-password.JPG)

4.  **Etki Alanı Bağlantı Ayarları**’nın altında parolayı değiştirin.

5.  **Kaydet**'e tıklayın..

6.  Parolayı değiştirdikten sonra, ATA Gateway sunucularında ATA Gateway hizmetinin çalıştığını el ile denetleyin.

>[!div class="step-by-step"]
[« IIS sertifikası](modifying-ata-config-iiscert.md)
[Yakalama ağ bağdaştırıcısının adı »](modifying-ata-config-nicname.md)

## Ayrıca Bkz.
- [ATA Konsolu’yla çalışma](/advanced-threat-analytics/understand-explore/working-with-ata-console)
- [ATA’yı yükleme](install-ata.md)
- [Destek için forumumuzu gözden geçirin!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=Apr16_HO4-->


