---
title: Yükleme Azure Gelişmiş tehdit koruması - 2. adım | Microsoft Docs
description: Azure ATP yükleme adımı iki Azure ATP bulut hizmetinizde etki alanı bağlantı ayarlarını yapılandırmanıza yardımcı olur.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2017
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: ae8a95f0-278c-4a12-ae69-14282364fba1
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: b2f83da3192770ddde05b04bed46a558a4491290
ms.sourcegitcommit: 7f3ded32af35a433d4b407009f87cfa6099f8edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44125898"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="install-azure-atp---step-2"></a>Azure ATP - 2. Adım'ı yükleme

>[!div class="step-by-step"]
[« 1. Adım](install-atp-step1.md)
[3. Adım »](install-atp-step3.md)

## <a name="step-2-provide-a-username-and-password-to-connect-to-your-active-directory-forest"></a>2. Adım Bir kullanıcı adı ve Active Directory ormanınıza bağlanmak için parola sağlayın

Azure ATP çalışma alanı portalı ilk açtığınızda aşağıdaki ekran görünür:

![Azure ATP Hoş Geldiniz aşaması 1](media/directory-services.png)

> [!IMPORTANT]
> Buraya kullanıcı kimlik bilgileri, şirket içi Active Directory'de bir kullanıcı hesabı için olmalıdır. 


1.  Aşağıdaki bilgileri girin ve **Kaydet**’e tıklayın:

    |Alan|Açıklamalar|
    |---------|------------|
    |**Kullanıcı adı** (gerekli)|Salt okunur Active Directory kullanıcı adını girin, örneğin: **ATPuser**.|
    |**Parola** (gerekli)|Salt okunur kullanıcının parolasını girin, örneğin: **Kalem1**.|
    |**Etki alanı** (gerekli)|Salt okunur kullanıcının etki alanını girin, örneğin, **contoso.com**. **Not:** Kullanıcının bulunduğu etki alanının tam FQDN’sini girmek önemlidir. Örneğin, kullanıcının hesabı corp.contoso.com etki alanındaysa, contoso.com değil `corp.contoso.com` girmeniz gerekir.|

3. Çalışma alanı portalında **algılayıcı Kurulum indirin ve ilk algılayıcıyı yükleyin** devam etmek için.


>[!div class="step-by-step"]
[« 1. Adım](install-atp-step1.md)
[3. Adım »](install-atp-step3.md)


## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)