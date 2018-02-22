---
title: "Etiket Azure ATP hassas hesaplarıyla | Microsoft Docs"
description: "Azure Gelişmiş tehdit Koruması (ATP) kullanarak hassas hesapları etiketi açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 43e57f87-ca85-4922-8ed0-9830139fe7cb
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 4270ebda76309e19518f9d49b72bbce7f9bb5f32
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
---
*Uygulandığı öğe: Azure Advanced Threat Protection sürüm 1.9*



# <a name="working-with-sensitive-accounts"></a>Hassas hesapları ile çalışma

## <a name="sensitive-groups"></a>Gizli gruplar

Aşağıdaki listede gruplarının, duyarlı Azure ATP tarafından değerlendirilir. Şu grupların üyesi olan herhangi bir varlık, gizli olarak kabul edilir:

-   Yöneticiler
-   İleri Kullanıcılar
-   Account Operators
-   Server Operators
-   Print Operators
-   Backup Operators
-   Replicators
-   Uzak Masaüstü Kullanıcıları 
-   Ağ Yapılandırması İşleçleri 
-   Incoming Forest Trust Builders
-   Etki Alanı Yöneticileri
-   Domain Controllers
-   Group Policy Creator Owners 
-   salt okunur etki alanı denetleyicileri 
-   Kuruluş salt okunur etki alanı denetleyicileri 
-   Schema Admins 
-   Enterprise Admins


## <a name="tagging-sensitive-accounts"></a>Hassas hesapları etiketleme

Bu gruplarına ek olarak, grupları veya hesapları hassas olarak algılamaların geliştirmek için el ile etiketleyebilirsiniz. Hassas grubu değişikliği algılama ve yanal hareket yolu gibi bazı Azure ATP algılamaların hangi gruplar ve hesaplar hassas kabul edilir üzerinde dayandığından, bu önemlidir. Diğer kullanıcılara veya gruplara Panosu üyeleri, şirket Yöneticiler, vb. Satış Müdürü gibi hassas olarak el ile etiketi ve Azure ATP bunları hassas göz önünde bulundurur.

1.  Azure ATP çalışma Portalı'nda tıklatın **yapılandırma** menü çubuğunda dişlisine.

2.  Altında **algılama** tıklatın **varlık etiketleri**.

    ![Azure ATP varlık etiketleri](media/entity-tags.png)

3.  İçinde **hassas** bölümünde, adı **hassas hesapları** ve **hassas gruplara** ve ardından  **+**  bunları eklemek oturum açın.

    ![Azure ATP hassas hesap örnek](media/sensitive-account-sample.png)

4. **Kaydet**'e tıklayın.

    
## <a name="see-also"></a>Ayrıca bkz.

- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)