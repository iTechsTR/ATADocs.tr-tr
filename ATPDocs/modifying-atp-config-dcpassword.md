---
title: Azure Advanced Threat Protection yapılandırma - etki alanı bağlantı parolasını değiştirme | Microsoft Docs
description: Azure ATP tek başına algılayıcı etki alanı bağlantı parolasını değiştirme açıklar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/14/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: e7f065fa-1ad1-4e87-bd80-99cc695efbf5
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 369f00b1b33fe509850bc331b0d5b45ae161f91c
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
ms.locfileid: "29445969"
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="change-azure-atp-workspace-portal-configuration---domain-connectivity-password"></a>Azure ATP çalışma portal yapılandırmasını değiştirme - etki alanı bağlantı parolası



## <a name="change-the-domain-connectivity-password"></a>Etki alanı bağlantı parolasını değiştirme
Etki alanı bağlantı parolası değiştirmeniz gerekiyorsa, girdiğiniz parolanın doğru olduğundan emin olun. Değilse, tüm dağıtılan algılayıcılar için Azure ATP algılayıcı hizmetini durdurur.

Aşağıdaki hatalar Microsoft.Tri.sensor-Errors.log dosyasında, bu, Azure ATP tek başına algılayıcı kuşkulanırsanız bakın: `The supplied credential is invalid.`

Etki alanı bağlantı parolası Azure ATP çalışma portalındaki güncelleştirmek için aşağıdaki yordamı izleyin:

> [!NOTE]
> Kullanıcı adı ve parolası Active Directory şirket içi dağıtımından ve Azure AD'den değil budur.

1.  Azure ATP çalışma Portalı'nı açmak çalışma alanı URL'si erişerek.

2.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![Azure ATP yapılandırma ayarları simgesi](media/atp-config-menu.png)

3.  **Dizin Hizmetleri**’ni seçin.

    ![Azure ATP tek başına algılayıcı parola görüntüsünü değiştirme](media/directory-services.png)

4.  **Parola** altında, parolayı değiştirin.

 > [!NOTE]
 > Bir Active Directory kullanıcı ve parola Burada, Azure Active Directory girin.

5.  **Kaydet**'e tıklayın.

6.  Parolayı değiştirdikten sonra el ile Azure ATP bağımsız algılayıcı hizmeti Azure ATP tek başına algılayıcı sunucularda çalışıp çalışmadığını denetleyin.

7. Çalışma alanı portalında altında **yapılandırma**gidin **algılayıcı** sayfasında ve algılayıcılar durumunu kontrol edin.

## <a name="see-also"></a>Ayrıca bkz:

- [Windows Defender ATP ile tümleştirme](integrate-wd-atp.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)