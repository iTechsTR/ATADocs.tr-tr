---
title: Erişim yönetimi için Azure Gelişmiş tehdit koruması rol grupları | Microsoft Docs
description: Azure ATP rol grupları ile çalışmada size yol gösterir.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/15/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: effca0f2-fcae-4fca-92c1-c37306decf84
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 28a500aeeeef127425ac292b53dbdc34aa1aad45
ms.sourcegitcommit: 7f3ded32af35a433d4b407009f87cfa6099f8edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44125949"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*




# <a name="azure-atp-role-groups"></a>Azure ATP rol grupları

Azure ATP rol tabanlı güvenlik, bir kuruluşun belirli güvenlik ve uyumluluk gereksinimlerine göre verilerinizi korumak için sunar. Azure ATP destekleyen üç ayrı rol: Yöneticiler, kullanıcılar ve görüntüleyiciler. 

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

Rol grupları Azure ATP için erişim yönetimini etkinleştirin. Rol gruplarını kullanarak güvenlik ekibinizdeki görevleri ayırabilir ve kullanıcılara sadece işlerini yapması için gereken miktarda erişim izni verebilirsiniz. Bu makalede erişim yönetimi, Azure ATP rol yetkilendirmesi ve ATP rol grupları ile ayarlayıp çalıştırmaya başlamasına yardımcı açıklanmaktadır.

> [!NOTE]
> Herhangi bir genel yönetici veya Güvenlik Yöneticisi kiracının Azure Active Directory'ye otomatik olarak Azure ATP yönetici olur.

## <a name="accessing-the-management-portal"></a>Yönetim portalına erişim

Yönetim Portalı (portal.atp.azure.com) erişimi yalnızca dizin rolü genel yönetici veya güvenlik yöneticisi olan bir Azure AD kullanıcı tarafından gerçekleştirilebilir. Portal girdikten sonra çalışma alanı oluşturabilirsiniz. Azure ATP hizmeti, Azure Active Directory kiracınızda üç güvenlik grupları oluşturur: Yöneticiler, kullanıcılar, görüntüleyiciler. 

> [!NOTE]
> Azure ATP çalışma alanı portalına erişim, yalnızca söz konusu çalışma alanında, genel Yöneticiler ve güvenlik yöneticileri için Azure AD güvenlik gruplarına kapsamındaki kullanıcılara verilir.


## <a name="types-of-azure-atp-security-groups"></a>Azure ATP güvenlik gruplarının türleri 

Azure ATP güvenlik grubunun üç tür sunar: Azure ATP *çalışma alanı adı* yöneticileri, Azure ATP *çalışma alanı adı* kullanıcılar ve Azure ATP *çalışma alanı adı* görüntüleyiciler . Aşağıdaki tabloda Azure ATP çalışma alanı portalında her rol için kullanılabilen erişim türü açıklanır. Hangi rol, atama, çeşitli ekranlar ve menü seçenekleri Azure ATP bağlı çalışma portalı kullanılabilir değil, şu şekilde:

|Etkinlik |Azure ATP *çalışma alanı adı* yöneticileri|Azure ATP *çalışma alanı adı* kullanıcılar|Azure ATP *çalışma alanı adı* görüntüleyiciler|
|----|----|----|----|
|Oturum aç|Kullanılabilir|Kullanılabilir|Kullanılabilir|
|Kuşkulu Etkinliklerin durumunu değiştirme|Kullanılabilir|Kullanılabilir|Yok|
|E-posta/bağlantı alma üzerinden şüpheli etkinlikleri paylaşma/dışarı aktarma|Kullanılabilir|Kullanılabilir|Kullanılabilir|
|İzleme Uyarılarının durumunu değiştirme|Kullanılabilir|Yok|Yok|
|Azure ATP yapılandırmasını güncelleştirme|Kullanılabilir|Yok|Yok|
|Algılayıcı – Ekle|Kullanılabilir|Yok|Yok|
|Algılayıcı – silme |Kullanılabilir|Yok|Yok|
|İzlenen DC – Ekleme |Kullanılabilir|Yok|Yok|
|İzlenen DC – Silme|Kullanılabilir|Yok|Yok|
|Uyarıları ve şüpheli etkinlikleri görüntüleme|Kullanılabilir|Kullanılabilir|Kullanılabilir|


Kullanıcılar kendi rol grupları için kullanılabilir olmayan bir sayfaya erişmeye çalıştıklarında, bunlar Azure ATP yetkisiz sayfasına yönlendirilir. 

## <a name="add-and-remove-users"></a>Ekleme ve kullanıcıları kaldırma 


Azure ATP, rol grupları için temel olarak Azure AD güvenlik grupları kullanır. Rol grupları alanından yönetilebilir [ https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/All%20groups ](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/All%20groups). Yalnızca Azure AD kullanıcıları eklenebilir veya güvenlik grubundan kaldırıldı. 

## <a name="see-also"></a>Ayrıca Bkz.
- [ATA boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [ATA mimarisi](atp-architecture.md)
- [ATA’yı yükleme](install-atp-step1.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)

