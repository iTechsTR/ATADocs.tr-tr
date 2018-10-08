---
title: Erişim yönetimi için Azure Gelişmiş tehdit koruması rol grupları | Microsoft Docs
description: Azure ATP rol grupları ile çalışmada size yol gösterir.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/07/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: effca0f2-fcae-4fca-92c1-c37306decf84
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 7ae3f0adca3137664f0a89c15e8feee71d0cd915
ms.sourcegitcommit: c4978be196e0039c7a5d5887bec4cbc5c01d64f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48848622"
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

Azure ATP güvenlik gruplarını üç tür sağlar: Azure ATP *(çalışma alanı adı)* yöneticileri, Azure ATP *(çalışma alanı adı)* kullanıcılar ve Azure ATP *(çalışma alanı adı)* Görüntüleyiciler. Aşağıdaki tabloda, her rol için kullanılabilen Azure ATP portalında erişim türü açıklanır. Hangi rolü, atama, çeşitli ekranlar ve menü seçenekleri Azure ATP bağlı portalı gibidir, bu kullanıcılar için kullanılamaz:

|Etkinlik |Azure ATP *(çalışma alanı adı)* yöneticileri|Azure ATP *(çalışma alanı adı)* kullanıcılar|Azure ATP *(çalışma alanı adı)* görüntüleyiciler|
|----|----|----|----|
|Oturum aç|Kullanılabilir|Kullanılabilir|Kullanılabilir|
|(Yeniden açın, Kapat, dışlama gösterme) güvenlik uyarılarının durumunu değiştirme|Kullanılabilir|Kullanılabilir|Yok|
|Güvenlik Uyarıları paylaşımı/dışarı aktarma (e-posta aracılığıyla bağlantı alma, ayrıntılarını indir)|Kullanılabilir|Kullanılabilir|Kullanılabilir|
|Bir raporu indir|Kullanılabilir|Kullanılabilir|Kullanılabilir|
|İzleme Uyarılarının durumunu değiştirme|Kullanılabilir|Yok|Yok|
|Azure ATP yapılandırma - algılayıcı güncelleştirme (indirin, anahtarı yeniden oluşturmak, yapılandırmak, silme)|Kullanılabilir|Yok|Yok|
|Azure ATP yapılandırma - veri kaynakları (Dizin Hizmetleri, SIEM, VPN WD-ATP) güncelleştirme|Kullanılabilir|Yok|Yok|
|ATP yapılandırma - güncelleştirmeler güncelleştirme|Kullanılabilir|Yok|Yok|
|ATP yapılandırma güncelleştirmesi-Zamanlanan raporlar|Kullanılabilir|Kullanılabilir|Yok|
|ATP yapılandırma güncelleştirmesi-varlık etiketleri (duyarlı ve honeytoken)|Kullanılabilir|Kullanılabilir|Yok|
|ATP yapılandırma güncelleştirmesi-dışlamaları|Kullanılabilir|Kullanılabilir|Yok|
|ATP yapılandırma güncelleştirmesi-dil|Kullanılabilir|Kullanılabilir|Yok|
|ATP yapılandırma güncelleştirmesi-bildirimleri (e-posta ve syslog)|Kullanılabilir|Kullanılabilir|Yok|
|ATP yapılandırma güncelleştirmesi-Önizleme algılamalar|Kullanılabilir|Kullanılabilir|Yok|
|Varlık profilleri ve güvenlik uyarılarını görüntüleme|Kullanılabilir|Kullanılabilir|Kullanılabilir|


Kullanıcılar kendi rol grupları için kullanılabilir olmayan bir sayfaya erişmeye çalıştıklarında, bunlar Azure ATP yetkisiz sayfasına yönlendirilir. 

## <a name="add-and-remove-users"></a>Ekleme ve kullanıcıları kaldırma 


Azure ATP, rol grupları için temel olarak Azure AD güvenlik grupları kullanır. Rol grupları alanından yönetilebilir [ https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/All%20groups ](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/All%20groups). Yalnızca Azure AD kullanıcıları eklenebilir veya güvenlik grubundan kaldırıldı. 

## <a name="see-also"></a>Ayrıca Bkz.
- [ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [ATP mimarisi](atp-architecture.md)
- [Azure ATP yükleyin](install-atp-step1.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)

