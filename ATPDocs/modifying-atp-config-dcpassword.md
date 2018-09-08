---
title: Azure Gelişmiş tehdit koruması yapılandırmasını değiştirme - etki alanı bağlantı parolası | Microsoft Docs
description: Azure ATP tek başına algılayıcı şirket etki alanı bağlantı parolasını değiştirme işlemini açıklamaktadır.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: e7f065fa-1ad1-4e87-bd80-99cc695efbf5
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: e5b3fd544fb52cd2979ab95d34918ffba3f56541
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44166196"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="change-azure-atp-workspace-portal-configuration---domain-connectivity-password"></a>Azure ATP çalışma alanı portal yapılandırmasını değiştirme - etki alanı bağlantı parolası



## <a name="change-the-domain-connectivity-password"></a>Etki alanı bağlantı parolasını değiştirme
Etki alanı bağlantı parolasını değiştirmeniz gerekiyorsa, girdiğiniz parolanın doğru olduğundan emin olun. Yüklü değilse, Azure ATP algılayıcı hizmeti için dağıtılan tüm algılayıcılar durdurur.

Bu, Azure ATP tek başına algılayıcı üzerinde gerçekleştiğini şüpheleniyorsanız Microsoft.Tri.sensor-Errors.log dosyasında şu hatalar bakın: `The supplied credential is invalid.`

Azure ATP çalışma alanı portalında etki alanı bağlantı parolası'nı güncelleştirmek için aşağıdaki yordamı izleyin:

> [!NOTE]
> Kullanıcı adı ve parola Active Directory şirket içi dağıtımından ve değil Azure AD'den budur.

1.  Azure ATP çalışma alanı portalı açın erişerek bir çalışma alanı URL'si.

2.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![Azure ATP yapılandırma ayarları simgesi](media/atp-config-menu.png)

3.  **Dizin Hizmetleri**’ni seçin.

    ![Azure ATP tek başına algılayıcı parola görüntüsünü değiştirme](media/directory-services.png)

4.  **Parola** altında, parolayı değiştirin.

 > [!NOTE]
 > Bir Active Directory kullanıcı ve parola Burada, Azure Active Directory girin.

5.  **Kaydet**'e tıklayın.

6.  Parolayı değiştirdikten sonra el ile Azure ATP tek başına algılayıcı sunucularda Azure ATP tek başına algılayıcı hizmetinin çalışıp çalışmadığını denetleyin.

7. Çalışma alanı portalında altında **yapılandırma**Git **algılayıcı** sayfasında ve sensörlerden durumunu denetleyin.

## <a name="see-also"></a>Ayrıca Bkz.

- [Windows Defender ATP ile tümleştirme](integrate-wd-atp.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)