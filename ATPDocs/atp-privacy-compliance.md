---
title: Azure Advanced Threat Protection kişisel veriler ilke | Microsoft Docs
description: Özel bilgi ve kişisel verilerinizi Azure ATP silme hakkında bilgilere bağlantılar sağlar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/29/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 224e629a-0e82-458c-bb03-b67070a9241d
ms.reviewer: ophirp
ms.suite: ems
ms.openlocfilehash: 1f9ed3dba82d032b0cd13bdc462ff6e58a4af6ad
ms.sourcegitcommit: 3eade64779002d2c8ae005565bc69e1b3f89fb7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34560233"
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*

# <a name="azure-atp-data-security-and-privacy"></a>Azure ATP veri güvenlik ve gizlilik

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

## <a name="search-for-and-identify-personal-data"></a>Arama ve kişisel veriler tanımlayın 

Azure Gelişmiş tehdit koruması kişisel olarak tanımlanabilen verileri görüntüleyebilirsiniz [çalışma portal](workspace-portal.md) kullanarak [arama çubuğunu](workspace-portal.md#search-bar). 

Belirli bir kullanıcı veya bilgisayar için arama yapabilirsiniz ve varlıkta tıklatarak getirecek, kullanıcı veya bilgisayar [profili sayfasını](entity-profiles.md). Profil, varlık hakkında kapsamlı ayrıntılarla varlık ve geçmişiyle ilgili ağ etkinliği de dahil olmak üzere Active Directory sağlar.

Azure ATP kişisel verileri Active Directory'den Azure ATP algılayıcı toplanan ve arka uç veritabanında depolanır.

## <a name="update-personal-data"></a>Kişisel veri güncelleştirme 

Kullanıcının nesnesi Active Directory kuruluşun Azure ATP kullanıcının kişisel verileri türetilir olduğundan, kullanıcı profili için AD içinde yapılan değişiklikler Azure ATP yansıtılır.


## <a name="delete-personal-data"></a>Kişisel verilerini sil 

Bir kullanıcı kuruluşun Active Directory'den silindikten sonra Azure ATP otomatik olarak kullanıcı profili ve ilgili ağ etkinliği bir yıl içinde siler. Ayrıca [silmek](working-with-suspicious-activities.md#review-suspicious-activities-on-the-attack-time-line) kişisel verileri içeren herhangi bir güvenlik uyarıları. 

## <a name="export-personal-data"></a>Kişisel verileri dışarı aktarma 

Azure ATP yeteneğine sahip [verme](working-with-suspicious-activities.md#review-suspicious-activities-on-the-attack-time-line) Excel güvenlik uyarı bilgileri. Bu, aynı zamanda kişisel veriler verecektir. 
 
## <a name="audit-personal-data"></a>Denetim kişisel veriler

Azure ATP kişisel veri değişiklikleri, Denetim ve kişisel veri kayıtlarını dışarı aktarma silme gibi uygular. Denetim izi saklama süresi 90 gündür. Azure ATP denetimi: bir arka uç özelliği ve müşteriler için erişilebilir değil.
 
## <a name="additional-resources"></a>Ek kaynaklar

- Azure ATP güven ve Uyumluluk hakkında daha fazla bilgi için bkz: [hizmet güven portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted) ve [Microsoft 365 Kurumsal GDPR uyumluluk site](https://docs.microsoft.com/microsoft-365/compliance/compliance-solutions-overview).