---
# required metadata

title: ATA’yı Yükleme - 2. Adım | Microsoft Advanced Threat Analytics
description: ATA’yı yükleme işleminin ikinci adımı, ATA Center sunucunuzda etki alanı bağlantı ayarlarını yapılandırmanıza yardımcı olur.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: e1c5ff41-d989-46cb-aa38-5a3938f03c0f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ATA’yı Yükleme - 2. Adım

>[!div class="step-by-step"]
[« 1. Adım](install-ata-step1.md)
[3. Adım »](install-ata-step3.md)

## 2. Adım ATA Gateway etki alanı bağlantı ayarlarını yapılandırma
Etki alanı bağlantı ayarları bölümündeki ayarlar, ATA Center tarafından yönetimen tüm ATA Gateway bileşenlerine uygulanır.

Etki alanı bağlantı ayarlarını yapılandırmak için, ATA Center sunucusunda aşağıdakileri gerçekleştirin.

1.  ATA Konsolu’nu açın ve oturum açın. Yönergeler için bkz. [ATA Konsolu’yla çalışma](/advanced-threat-analytics/understand-explore/working-with-ata-console).

2.  ATA Center yüklendikten sonra ATA Konsolu’nda ilk kez oturum açtığınızda, otomatik olarak ATA Gateway bileşenleri yapılandırma sayfasına gidersiniz. Bundan sonra ayarlardan herhangi birinde değişiklik yapmanız gerektiğinde, Ayarlar simgesine tıklayın ve **Yapılandırma**’yı seçin..

    ![ATA Gateway yapılandırma ayarları](media/ATA-config-icon.JPG)

3.  **Gateway Bileşenleri** sayfasında **Etki alanı bağlantı ayarları**’na tıklayın, aşağıdaki bilgileri girin ve **Kaydet**’e tıklayın..

    |Alan|Açıklamalar|
    |---------|------------|
    |**Kullanıcı adı** (gerekli)|Salt okunur kullanıcı adını girin, örneğin: **kullanıcı1**.|
    |**Parola** (gerekli)|Salt okunur kullanıcının parolasını girin, örneğin: **Kalem1**. **Not:** Bu parolanın doğru olduğundan emin olun. Yanlış parola kaydederseniz, ATA Gateway sunucularında ATA Hizmeti çalışmayı durdurur.|
    |**Etki alanı** (gerekli)|Salt okunur kullanıcının etki alanını girin, örneğin: **contoso.com**. **Not:** Kullanıcının bulunduğu etki alanının tam FQDN değerini girmeniz önemlidir. Örneğin, kullanıcının hesabı corp.contoso.com etki alanındaysa, contoso.com değil `corp.contoso.com` girmeniz gerekir.|
    ![ATA Etki Alanı bağlantı ayarlarının resmi](media/ATA-Domain-Connectivity-User.JPG)


>[!div class="step-by-step"]
[« 1. Adım](install-ata-step1.md)
[3. Adım »](install-ata-step3.md)


## Ayrıca Bkz.

- [Destek için forumumuzu gözden geçirin!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](/advanced-threat-analytics/plan-design/configure-event-collection)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)


<!--HONumber=Apr16_HO4-->


