---
title: Azure Gelişmiş tehdit koruması kişisel veri ilkesi | Microsoft Docs
description: Azure ATP özel bilgileri ve kişisel verileri silme hakkında daha fazla bilgi için bağlantılar sağlar.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/15/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 224e629a-0e82-458c-bb03-b67070a9241d
ms.reviewer: ophirp
ms.suite: ems
ms.openlocfilehash: 274e016f7a870b8879fad0dec4628dcea60bc538
ms.sourcegitcommit: 7f3ded32af35a433d4b407009f87cfa6099f8edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44126153"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*

# <a name="azure-atp-data-security-and-privacy"></a>Azure ATP veri güvenlik ve gizlilik

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

## <a name="search-for-and-identify-personal-data"></a>Kişisel verileri tanımlamak ve arayın 

Azure Gelişmiş tehdit koruması kişisel olarak tanımlanabilen verileri görüntüleyebilirsiniz [çalışma portalı](workspace-portal.md) kullanarak [Arama çubuğuna](workspace-portal.md#search-bar). 

Belirli bir kullanıcı veya bilgisayar için arama yapın ve kullanıcıya veya bilgisayara getirmek için varlık tıklayın [profil sayfası](entity-profiles.md). Profil, varlık hakkında ayrıntılar kapsamlı, varlık ve buna ait geçmişi ilgili ağ etkinliği de dahil olmak üzere Active Directory sağlar.

Azure ATP kişisel verileri Active Directory'den Azure ATP algılayıcısını toplanan ve arka uç veritabanında depolanır.

## <a name="update-personal-data"></a>Kişisel verilerini güncelleştirin 

Azure ATP'nin kişisel kullanıcı verileri, kullanıcının nesnesi Active Directory kuruluş türetilir. Bu nedenle, AD kuruluş kullanıcı profiline yapılan değişiklikler, ATA'daki yansıtılır.


## <a name="delete-personal-data"></a>Kişisel verilerini silme 

Bir kullanıcı kuruluşun Active Directory'den silindikten sonra Azure ATP otomatik olarak kullanıcı profili ve tüm ilgili ağ etkinliği bir yıl içinde siler. Ayrıca [Sil](working-with-suspicious-activities.md#review-suspicious-activities-on-the-attack-time-line) kişisel verileri içeren herhangi bir güvenlik uyarıları. 

## <a name="export-personal-data"></a>Kişisel verileri dışarı aktarma 

ATA'daki yeteneğine sahip [dışarı](working-with-suspicious-activities.md#review-suspicious-activities-on-the-attack-time-line) Excel güvenlik uyarı bilgisi. Bu işlev, ayrıca kişisel verileri dışarı aktarır. 
 
## <a name="audit-personal-data"></a>Kişisel verileri denetleme

Azure ATP kişisel veri kayıtlarının dışarı aktarma ve silme de dahil olmak üzere kişisel verileri değişiklikler, Denetim uygular. Denetim izi elde tutma süresi 90 gündür. ATA'daki denetimi, bir arka uç özelliğidir ve müşteriler için erişilebilir değil.
 
## <a name="additional-resources"></a>Ek kaynaklar

- Azure ATP güven ve Uyumluluk hakkında daha fazla bilgi için bkz. [hizmet güveni portalı](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted) ve [Microsoft 365 Kurumsal GDPR uyumluluğu site](https://docs.microsoft.com/microsoft-365/compliance/compliance-solutions-overview).
