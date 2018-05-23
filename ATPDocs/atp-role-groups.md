---
title: Erişim yönetimi için Azure Advanced Threat Protection rol grupları | Microsoft Docs
description: Azure ATP rol gruplarıyla çalışmada size yol gösterir.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: effca0f2-fcae-4fca-92c1-c37306decf84
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 77a2464634b4286d2f6d35504e9ab7512cf7b612
ms.sourcegitcommit: 324dc941282f2948366afa5a919bda0b029bd59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*




# <a name="azure-atp-role-groups"></a>Azure ATP rol grupları

Azure ATP bir kuruluşun belirli güvenlik ve uyumluluk gereksinimlerine göre verilerinizi korumak için rol tabanlı güvenlik sunar. Azure ATP destekleyen üç ayrı roller: Yöneticiler ve kullanıcılar görüntüleyiciler. 

> [!NOTE]
> Görüntüleme veya kişisel verileri silme düşünüyorsanız, lütfen Microsoft'un Kılavuzu gözden [Microsoft Uyumluluk Yöneticisi](https://servicetrust.microsoft.com/ComplianceManager) ve [Microsoft 365 Kurumsal uyumluluk sitesininGDPRbölümünü](https://docs.microsoft.com/en-us/microsoft-365/compliance/gdpr). GDPR hakkında genel bilgi arıyorsanız bkz [Hizmeti'ne güvenen portal GDPR bölümünü](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

Rol grupları Azure ATP için erişim yönetimini etkinleştirin. Rol gruplarını kullanarak güvenlik ekibinizdeki görevleri ayırabilir ve kullanıcılara sadece işlerini yapması için gereken miktarda erişim izni verebilirsiniz. Bu makalede, erişim yönetimi ve Azure ATP rol yetkilendirme ve ATP rol gruplarla çalışır alma yardımcı açıklanmaktadır.

> [!NOTE]
> Herhangi bir genel yönetici veya Güvenlik Yöneticisi kiracının Azure Active Directory'ye otomatik olarak bir Azure ATP yöneticidir.

## <a name="accessing-the-workspace-management-portal"></a>Çalışma alanı yönetim portalına erişim

Çalışma alanı Yönetim Portalı'nı (portal.atp.azure.com) erişimi yalnızca genel yönetici veya Güvenlik Yöneticisi dizin rolüne sahip bir Azure AD kullanıcı tarafından gerçekleştirilebilir. Portal girdikten sonra farklı çalışma alanları oluşturabilirsiniz. Her çalışma alanı için Azure ATP hizmeti üç güvenlik grupları, Azure Active Directory kiracınızda oluşturur: Yöneticiler, kullanıcılar, görüntüleyiciler. 

> [!NOTE]
> Azure ATP çalışma portalına erişim, yalnızca bu çalışma alanında ve genel yönetici ve güvenlik Yöneticiler için Azure AD güvenlik gruplarının içinde kullanıcılara verilir.


## <a name="types-of-azure-atp-security-groups"></a>Azure ATP güvenlik grupları türleri 

Azure ATP güvenlik grubu üç tür sunar: Azure ATP *çalışma alanı adı* Yöneticiler, Azure ATP *çalışma alanı adı* kullanıcılar ve Azure ATP *çalışma alanı adı* görüntüleyiciler . Aşağıdaki tabloda Azure ATP çalışma portalında rol kullanılabilir bir erişim türü açıklanmaktadır. Hangi rolü atadığınız, çeşitli ekranları ve Azure ATP menüsü seçeneklerini bağlı olarak çalışma portal kullanılamaz, aşağıdaki gibi:

|Etkinlik |Azure ATP *çalışma alanı adı* yöneticileri|Azure ATP *çalışma alanı adı* kullanıcılar|Azure ATP *çalışma alanı adı* görüntüleyiciler|
|----|----|----|----|
|Oturum aç|Kullanılabilir|Kullanılabilir|Kullanılabilir|
|Kuşkulu Etkinliklerin durumunu değiştirme|Kullanılabilir|Kullanılabilir|Yok|
|E-posta/bağlantı alma üzerinden şüpheli etkinlikleri paylaşma/dışarı aktarma|Kullanılabilir|Kullanılabilir|Kullanılabilir|
|İzleme Uyarılarının durumunu değiştirme|Kullanılabilir|Yok|Yok|
|Azure ATP yapılandırmasını güncelleştir|Kullanılabilir|Yok|Yok|
|Algılayıcı – Ekle|Kullanılabilir|Yok|Yok|
|Algılayıcı – Sil |Kullanılabilir|Yok|Yok|
|İzlenen DC – Ekleme |Kullanılabilir|Yok|Yok|
|İzlenen DC – Silme|Kullanılabilir|Yok|Yok|
|Uyarıları ve şüpheli etkinlikleri görüntüleme|Kullanılabilir|Kullanılabilir|Kullanılabilir|


Kullanıcılar kendi rol grubu için kullanılabilir olmayan bir sayfaya erişmeye çalıştığında, bunlar Azure ATP yetkisiz sayfasına yönlendirilirsiniz. 

## <a name="add-and-remove-users"></a>Ekleme ve kaldırma 

Azure ATP Azure AD güvenlik grupları için rol gruplarını temel olarak kullanır. Rol grupları sunucudan yönetilebilir [ https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UserManagementMenuBlade/All grupları](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UserManagementMenuBlade/All groups).  Yalnızca AAD kullanıcılarını eklenemez veya güvenlik grubundan kaldırıldı. 


## <a name="see-also"></a>Ayrıca bkz:
- [ATA boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [ATA mimarisi](atp-architecture.md)
- [ATA’yı yükleme](install-atp-step1.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)

