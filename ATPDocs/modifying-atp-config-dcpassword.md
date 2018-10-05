---
title: Azure Gelişmiş tehdit koruması yapılandırmasını değiştirme - etki alanı bağlantı parolası | Microsoft Docs
description: Azure ATP tek başına algılayıcı şirket etki alanı bağlantı parolasını değiştirme işlemini açıklamaktadır.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: e7f065fa-1ad1-4e87-bd80-99cc695efbf5
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: a175a23a087b11d481dbcf055bff4fe5577b4f8e
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48783126"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="change-azure-atp-workspace-portal-configuration---domain-connectivity-password"></a>Azure ATP çalışma alanı portal yapılandırmasını değiştirme - etki alanı bağlantı parolası



## <a name="change-the-domain-connectivity-password"></a>Etki alanı bağlantı parolasını değiştirme
Etki alanı bağlantı parolasını değiştirmeniz gerekiyorsa, girdiğiniz parolanın doğru olduğundan emin olun. Yüklü değilse, Azure ATP algılayıcı hizmeti için dağıtılan tüm algılayıcılar durdurur.

Bu, Azure ATP tek başına algılayıcı üzerinde gerçekleştiğini şüpheleniyorsanız Microsoft.Tri.sensor-Errors.log dosyasında şu hatalar bakın: `The supplied credential is invalid.`

Azure ATP portalında etki alanı bağlantı parolası'nı güncelleştirmek için aşağıdaki yordamı izleyin:

> [!NOTE]
> Kullanıcı adı ve parola Active Directory şirket içi dağıtımından ve değil Azure AD'den budur.

1.  Azure ATP portalı açın erişerek bir çalışma alanı URL'si.

2.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![Azure ATP yapılandırma ayarları simgesi](media/atp-config-menu.png)

3.  **Dizin Hizmetleri**’ni seçin.

    ![Azure ATP tek başına algılayıcı parola görüntüsünü değiştirme](media/directory-services.png)

4.  **Parola** altında, parolayı değiştirin.

 > [!NOTE]
 > Bir Active Directory kullanıcı ve parola Burada, Azure Active Directory girin.

5.  **Kaydet**'e tıklayın.

6.  Parolayı değiştirdikten sonra el ile Azure ATP tek başına algılayıcı sunucularda Azure ATP tek başına algılayıcı hizmetinin çalışıp çalışmadığını denetleyin.

7. Azure ATP portalında altında **yapılandırma**Git **algılayıcı** sayfasında ve sensörlerden durumunu denetleyin.

## <a name="see-also"></a>Ayrıca Bkz.

- [Windows Defender ATP ile tümleştirme](integrate-wd-atp.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)