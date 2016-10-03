---
title: "ATA’yı Yükleme - 2. Adım | Microsoft ATA"
description: "ATA’yı yükleme işleminin ikinci adımı, ATA Center sunucunuzda etki alanı bağlantı ayarlarını yapılandırmanıza yardımcı olur."
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: e1c5ff41-d989-46cb-aa38-5a3938f03c0f
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 050f1ef0b39d69b64ede53243a7fa2d33d0e4813
ms.openlocfilehash: fc268bcb2e3d027b09fa3349427934f60783b971


---

*Uygulama hedefi: Advanced Threat Analytics sürüm 1.7*



# ATA’yı Yükleme - 2. Adım

>[!div class="step-by-step"]
[« 1. Adım](install-ata-step1.md)
[3. Adım »](install-ata-step3.md)

## 2. Adım Active Directory Ormanınıza bağlanmak için bir Kullanıcı Adı ve Parola sağlayın

ATA Konsolunu ilk açtığınızda aşağıdaki ekran görünür:

![ATA hoş geldiniz aşaması 1](media/ATA_1.7-welcome-provide-username.png)

1.  Aşağıdaki bilgileri girin ve **Kaydet**’e tıklayın:

    |Alan|Açıklamalar|
    |---------|------------|
    |**Kullanıcı adı** (gerekli)|Salt okunur kullanıcı adını girin, örneğin: **ATAkullanıcısı**.|
    |**Parola** (gerekli)|Salt okunur kullanıcının parolasını girin, örneğin: **Kalem1**.|
    |**Etki alanı** (gerekli)|Salt okunur kullanıcının etki alanını girin, örneğin, **contoso.com**. **Not:** Kullanıcının bulunduğu etki alanının tam FQDN’sini girmek önemlidir. Örneğin, kullanıcının hesabı corp.contoso.com etki alanındaysa, contoso.com değil `corp.contoso.com` girmeniz gerekir.|
    |Tüm ATA Gateway bileşenlerini otomatik olarak güncelleştir |Bu ayarı etkinleştirirseniz, gelecek sürümlerde ATA Center’ı güncelleştirdiğinizde tüm ATA Gateway bileşenleri otomatik olarak güncelleştirilir.|

    Kaydedildikten sonra, Konsoldaki hoş geldiniz iletisi şu şekilde değişir: ![ATA hoş geldiniz aşaması 1 tamamlandı](media/ATA_1.7-welcome-provide-username-finished.png)

2. Devam etmek için Konsolda **Ağ Geçidi kurulumunu indir ve ilk Ağ Geçidini yükle**’ye tıklayın.


>[!div class="step-by-step"]
[« 1. Adım](install-ata-step1.md)
[3. Adım »](install-ata-step3.md)


## Ayrıca Bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)



<!--HONumber=Aug16_HO5-->


