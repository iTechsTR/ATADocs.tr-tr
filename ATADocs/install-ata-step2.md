---
title: "Advanced Threat Analytics’i Yükleme - 2. Adım | Microsoft Docs"
description: "ATA’yı yükleme işleminin ikinci adımı, ATA Center sunucunuzda etki alanı bağlantı ayarlarını yapılandırmanıza yardımcı olur."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 07/2/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: e1c5ff41-d989-46cb-aa38-5a3938f03c0f
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: aa5e752fa10644165cb70d2cd8c08a1145261edb
ms.sourcegitcommit: fa50f37b134d7579d7c310852dff60e5f1996eaa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="install-ata---step-2"></a>ATA’yı Yükleme - 2. Adım

>[!div class="step-by-step"]
[« 1. Adım](install-ata-step1.md)
[3. Adım »](install-ata-step3.md)

## <a name="step-2-provide-a-username-and-password-to-connect-to-your-active-directory-forest"></a>2. Adım Active Directory Ormanınıza bağlanmak için bir Kullanıcı Adı ve Parola sağlayın

ATA Konsolunu ilk açtığınızda aşağıdaki ekran görünür:

![ATA hoş geldiniz aşaması 1](media/ATA_1.7-welcome-provide-username.png)

1.  Aşağıdaki bilgileri girin ve **Kaydet**’e tıklayın:

    |Alan|Açıklamalar|
    |---------|------------|
    |**Kullanıcı adı** (gerekli)|Salt okunur kullanıcı adını girin, örneğin: **ATAkullanıcısı**.|
    |**Parola** (gerekli)|Salt okunur kullanıcının parolasını girin, örneğin: **Kalem1**.|
    |**Etki alanı** (gerekli)|Salt okunur kullanıcının etki alanını girin, örneğin, **contoso.com**. **Not:** Kullanıcının bulunduğu etki alanının tam FQDN’sini girmek önemlidir. Örneğin, kullanıcının hesabı corp.contoso.com etki alanındaysa, contoso.com değil `corp.contoso.com` girmeniz gerekir.|

2. **Bağlantıyı sına**’ya tıklayarak etki alanı bağlantısını sınayabilir ve verilen kimlik bilgilerinin erişim sağlayıp sağlamadığını kontrol edebilirsiniz. Bu, yalnızca ATA Center’ın etki alanına bağlı olması durumunda çalışır.   

    Kaydedildikten sonra, Konsoldaki hoş geldiniz iletisi şu şekilde değişir: ![ATA hoş geldiniz aşama 1 tamamlandı](media/ATA_1.7-welcome-provide-username-finished.png)

3. Devam etmek için Konsolda **Ağ Geçidi kurulumunu indir ve ilk Ağ Geçidini yükle**’ye tıklayın.


>[!div class="step-by-step"]
[« 1. Adım](install-ata-step1.md)
[3. Adım »](install-ata-step3.md)


## <a name="see-also"></a>Ayrıca bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)
