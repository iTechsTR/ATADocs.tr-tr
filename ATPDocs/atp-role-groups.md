---
title: Erişim yönetimi için Azure Gelişmiş tehdit koruması rol grupları | Microsoft Docs
description: Azure ATP rol grupları ile çalışmada size yol gösterir.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/26/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: effca0f2-fcae-4fca-92c1-c37306decf84
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 39709e4749b7f897bffb914dd1e15c80277d6ed8
ms.sourcegitcommit: 7d025a2518ce63f38ce609dc21d8c3bacdd6a8e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948974"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*




# <a name="azure-atp-role-groups"></a>Azure ATP rol grupları

Azure ATP rol tabanlı güvenlik, bir kuruluşun belirli güvenlik ve uyumluluk gereksinimlerine göre verilerinizi korumak için sunar. Azure ATP destekleyen üç ayrı rol: Yöneticiler, kullanıcılar ve görüntüleyiciler. 

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

Rol grupları Azure ATP için erişim yönetimini etkinleştirin. Rol gruplarını kullanarak güvenlik ekibinizdeki görevleri ayırabilir ve kullanıcılara sadece işlerini yapması için gereken miktarda erişim izni verebilirsiniz. Bu makalede erişim yönetimi ve Azure ATP rol yetkilendirmesi ve ATP rol grupları ile ayarlayıp çalıştırmaya başlamasına yardımcı açıklanmaktadır.

> [!NOTE]
> Herhangi bir genel yönetici veya Güvenlik Yöneticisi kiracının Azure Active Directory'ye otomatik olarak Azure ATP yönetici olur.

## <a name="accessing-the-workspace-management-portal"></a>Çalışma alanı yönetim portalına erişim

Çalışma alanı Yönetim Portalı'nı (portal.atp.azure.com) erişimi yalnızca dizin rolü genel yönetici veya güvenlik yöneticisi olan bir Azure AD kullanıcı tarafından gerçekleştirilebilir. Portal girdikten sonra farklı çalışma alanları oluşturabilirsiniz. Her çalışma alanı için Azure ATP hizmeti üç güvenlik gruplarını Azure Active Directory kiracınızda oluşturur: Yöneticiler, kullanıcılar, görüntüleyiciler. 

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

Azure ATP, rol grupları için temel olarak Azure AD güvenlik grupları kullanır. Rol grupları alanından yönetilebilir [ https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UserManagementMenuBlade/All%20groups ](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UserManagementMenuBlade/All%20groups). AAD kullanıcıları eklenebilir veya güvenlik grubundan kaldırıldı. 


## <a name="see-also"></a>Ayrıca bkz:
- [ATA boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [ATA mimarisi](atp-architecture.md)
- [ATA’yı yükleme](install-atp-step1.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)

