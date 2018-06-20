---
title: Yükleme Azure Gelişmiş tehdit koruması - 2. adım | Microsoft Docs
description: Azure ATP yükleme adım iki Azure ATP bulut hizmetinizde etki alanı bağlantı ayarlarını yapılandırmanıza yardımcı olur
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2017
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: ae8a95f0-278c-4a12-ae69-14282364fba1
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 11f9d5bf69ffda0843a94c7a2bb31869dc980dce
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
ms.locfileid: "29446494"
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="install-azure-atp---step-2"></a>Azure ATP - 2. adım yükleme

>[!div class="step-by-step"]
[« 1. Adım](install-atp-step1.md)
[3. Adım »](install-atp-step3.md)

## <a name="step-2-provide-a-username-and-password-to-connect-to-your-active-directory-forest"></a>2. Adım Active Directory ormanına Bağlan için bir kullanıcı adı ve parolayı belirtin

Azure ATP çalışma portal ilk açtığınızda, aşağıdaki ekran görüntülendiğinde:

![Azure ATP Hoş Geldiniz Aşama 1](media/directory-services.png)

> [!IMPORTANT]
> Buraya kullanıcı kimlik bilgileri, şirket içi Active Directory'de bir kullanıcı hesabı için olmalıdır. 


1.  Aşağıdaki bilgileri girin ve **Kaydet**’e tıklayın:

    |Alan|Açıklamalar|
    |---------|------------|
    |**Kullanıcı adı** (gerekli)|Örneğin salt okunur Active Directory kullanıcı adı girin: **ATPuser**.|
    |**Parola** (gerekli)|Salt okunur kullanıcının parolasını girin, örneğin: **Kalem1**.|
    |**Etki alanı** (gerekli)|Salt okunur kullanıcının etki alanını girin, örneğin, **contoso.com**. **Not:** Kullanıcının bulunduğu etki alanının tam FQDN’sini girmek önemlidir. Örneğin, kullanıcının hesabı corp.contoso.com etki alanındaysa, contoso.com değil `corp.contoso.com` girmeniz gerekir.|

3. Çalışma alanı Portalı'nda tıklatın **algılayıcı Kurulum yükleyip ilk algılayıcı** devam etmek için.


>[!div class="step-by-step"]
[« 1. Adım](install-atp-step1.md)
[3. Adım »](install-atp-step3.md)


## <a name="see-also"></a>Ayrıca bkz:
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)