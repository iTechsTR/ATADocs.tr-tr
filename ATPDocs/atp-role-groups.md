---
title: Erişim yönetimi için Azure Gelişmiş tehdit koruması rol grupları | Microsoft Docs
description: Azure ATP rol grupları ile çalışmada size yol gösterir.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: effca0f2-fcae-4fca-92c1-c37306decf84
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 2a5bc4ca940eef36911480b821e99b46749e1379
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48783619"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*




# <a name="azure-atp-role-groups"></a>Azure ATP rol grupları

Azure ATP rol tabanlı güvenlik, bir kuruluşun belirli güvenlik ve uyumluluk gereksinimlerine göre verilerinizi korumak için sunar. Azure ATP destekleyen üç ayrı rol: Yöneticiler, kullanıcılar ve görüntüleyiciler. 

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

Rol grupları Azure ATP için erişim yönetimini etkinleştirin. Rol gruplarını kullanarak güvenlik ekibinizdeki görevleri ayırabilir ve kullanıcılara sadece işlerini yapması için gereken miktarda erişim izni verebilirsiniz. Bu makalede, Azure ATP rol grupları ile ayarlayıp çalıştırmaya başlamasına yardımcı erişim yönetimi ve Azure ATP rol yetkilendirmesi açıklanır.

> [!NOTE]
> Herhangi bir genel yönetici veya Güvenlik Yöneticisi kiracının Azure Active Directory'ye otomatik olarak Azure ATP yönetici olur.

## <a name="accessing-the-azure-atp-portal"></a>Azure ATP portalına erişim

Azure ATP portalına (portal.atp.azure.com) erişim, yalnızca dizin rolü genel yönetici veya güvenlik yöneticisi olan bir Azure AD kullanıcı tarafından gerçekleştirilebilir. Portal girdikten sonra çalışma alanı oluşturabilirsiniz. Azure ATP hizmeti, Azure Active Directory kiracınızda üç güvenlik grupları oluşturur: Yöneticiler, kullanıcılar, görüntüleyiciler. 

> [!NOTE]
> Azure ATP portalına erişim, yalnızca kullanıcılara Azure ATP güvenlik gruplarını Azure Active Directory ve genel Yöneticiler ve güvenlik yöneticileri Kiracı içinde verilir.


## <a name="types-of-azure-atp-security-groups"></a>Azure ATP güvenlik gruplarının türleri 

Azure ATP güvenlik grubunun üç tür sunar: Azure ATP *(çalışma alanı adı)* yöneticileri, Azure ATP *(çalışma alanı adı)* kullanıcılar ve Azure ATP *(çalışma alanı adı)* Görüntüleyiciler. Aşağıdaki tabloda Azure ATP portalında her rol için kullanılabilen erişim türü açıklanır. Ata, çeşitli ekranlar ve menü seçenekleri Azure ATP ata'daki role bağlı portalı kullanılamaz, şu şekilde:

|Etkinlik |Azure ATP *(çalışma alanı adı)* yöneticileri|Azure ATP *(çalışma alanı adı)* kullanıcılar|Azure ATP *(çalışma alanı adı)* görüntüleyiciler|
|----|----|----|----|
|Oturum aç|Kullanılabilir|Kullanılabilir|Kullanılabilir|
|Güvenlik uyarılarının durumunu değiştirme|Kullanılabilir|Kullanılabilir|Yok|
|Güvenlik Uyarıları e-posta/bağlantı alma üzerinden paylaşımı/dışarı aktarma|Kullanılabilir|Kullanılabilir|Kullanılabilir|
|İzleme Uyarılarının durumunu değiştirme|Kullanılabilir|Yok|Yok|
|Azure ATP yapılandırmasını güncelleştirme|Kullanılabilir|Yok|Yok|
|Algılayıcı – Ekle|Kullanılabilir|Yok|Yok|
|Algılayıcı – silme |Kullanılabilir|Yok|Yok|
|İzlenen DC – Ekleme |Kullanılabilir|Yok|Yok|
|İzlenen DC – Silme|Kullanılabilir|Yok|Yok|
|Uyarıları görüntüleme ve güvenlik uyarıları|Kullanılabilir|Kullanılabilir|Kullanılabilir|


Kullanıcılar kendi rol grupları için kullanılabilir olmayan bir sayfaya erişmeye çalıştıklarında, bunlar Azure ATP yetkisiz sayfasına yönlendirilir. 

## <a name="add-and-remove-users"></a>Ekleme ve kullanıcıları kaldırma 


Azure ATP, rol grupları için temel olarak Azure AD güvenlik grupları kullanır. Rol grupları alanından yönetilebilir [ https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/All%20groups ](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/All%20groups). Yalnızca Azure AD kullanıcıları eklenebilir veya güvenlik grubundan kaldırıldı. 

## <a name="see-also"></a>Ayrıca Bkz.
- [ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [ATP mimarisi](atp-architecture.md)
- [Azure ATP yükleyin](install-atp-step1.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)

