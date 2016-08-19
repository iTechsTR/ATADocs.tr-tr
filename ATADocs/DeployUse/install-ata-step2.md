---
title: "ATA’yı Yükleme - 2. Adım | Microsoft ATA"
description: "ATA’yı yükleme işleminin ikinci adımı, ATA Center sunucunuzda etki alanı bağlantı ayarlarını yapılandırmanıza yardımcı olur."
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: e1c5ff41-d989-46cb-aa38-5a3938f03c0f
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f13750f9cdff98aadcd59346bfbbb73c2f3a26f0
ms.openlocfilehash: 65ec5c86478e9ded096b899d64eb257257095eaf


---

# ATA’yı Yükleme - 2. Adım

>[!div class="step-by-step"]
[« 1. Adım](install-ata-step1.md)
[3. Adım »](install-ata-step3.md)

## 2. Adım ATA Gateway genel ayarlarını yapılandırma
**Genel** ayarlar sekmesindeki ayarlar, ATA Center tarafından yönetilen tüm ATA Gateway bileşenlerine uygulanır.

Genel ATA Gateway ayarlarını yapılandırmak için aşağıdakileri gerçekleştirin:

1.  ATA Konsolu’nu açın ve oturum açın. Yönergeler için bkz. [ATA Konsolu’yla çalışma](working-with-ata-console.md)

2.  Ayarlar simgesine tıklayın ve **Yapılandırma**’yı seçin.

    ![ATA Gateway yapılandırma ayarları](media/ATA-config-icon.JPG)

3.  **Genel** sekmesinde, **ATA Gateway Bileşenleri** altında, aşağıdaki bilgileri girip **kaydet**’e tıklayın.

    |Alan|Açıklamalar|
    |---------|------------|
    |**Kullanıcı adı** (gerekli)|Salt okunur kullanıcı adını girin, örneğin: **kullanıcı1**|
    |**Parola** (gerekli)|Salt okunur kullanıcının parolasını girin, örneğin: **Kalem1**. **Not:** Bu parolanın doğru olduğundan emin olun. Yanlış parola kaydederseniz, ATA Gateway sunucularında ATA Hizmeti çalışmayı durdurur.|
    |**Etki alanı** (gerekli)|Salt okunur kullanıcının etki alanını girin, örneğin, **contoso.com**. **Not:** Kullanıcının bulunduğu etki alanının tam FQDN’sini girmek önemlidir. Örneğin, kullanıcının hesabı corp.contoso.com etki alanındaysa, contoso.com değil `corp.contoso.com` girmeniz gerekir.|
    |Tüm ATA Gateway bileşenlerini otomatik olarak güncelleştir |Bu ayarı etkinleştirirseniz, gelecek sürümlerde ATA Center’ı güncelleştirdiğinizde tüm ATA Gateway bileşenleri otomatik olarak güncelleştirilir.|

    ![ATA Etki Alanı bağlantı ayarlarının resmi](media/ata-domain-connectivity-user.jpg)



>[!div class="step-by-step"]
[« 1. Adım](install-ata-step1.md)
[3. Adım »](install-ata-step3.md)


## Ayrıca Bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)



<!--HONumber=Jul16_HO4-->


