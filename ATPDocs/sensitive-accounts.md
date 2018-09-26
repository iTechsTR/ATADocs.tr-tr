---
title: Etiket hassas hesapları Azure ATP ile | Microsoft Docs
description: Azure Gelişmiş tehdit Koruması (ATP) kullanarak hassas hesapları etiketi açıklar
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/12/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 43e57f87-ca85-4922-8ed0-9830139fe7cb
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: ccb87ab6b3fabed5edaf7c32324701c74259f098
ms.sourcegitcommit: 5ff50807f855db1051b977a64eb6e90487ea196c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45750446"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="working-with-sensitive-accounts"></a>Hassas hesaplar ile çalışma

## <a name="sensitive-groups"></a>Gizli gruplar

Aşağıdaki listede yer alan grupları, önemli Azure ATP tarafından değerlendirilir. Şu grupların üyesi olan herhangi bir varlık, gizli olarak kabul edilir:

-   Yöneticiler
-   İleri Kullanıcılar
-   Account Operators
-   Server Operators
-   Print Operators
-   Backup Operators
-   Replicators
-   Ağ Yapılandırması İşleçleri 
-   Incoming Forest Trust Builders
-   Etki Alanı Yöneticileri
-   Domain Controllers
-   Group Policy Creator Owners 
-   salt okunur etki alanı denetleyicileri 
-   Kurumsal salt okunur etki alanı denetleyicileri 
-   Schema Admins 
-   Enterprise Admins

 > [!NOTE]
 > Eylül 2018'e kadar Uzak Masaüstü kullanıcıları da otomatik olarak duyarlı Azure ATP tarafından ele alındı. Uzak Masaüstü varlıklar veya bu tarihin artık otomatik olarak işaretlenmiş sonra Uzak Masaüstü varlıkları sırasında hassas olarak eklenen gruplar veya bu tarihten önce eklenen gruplar, hassas olarak işaretlenmiş kalabilir. Bu hassas ayar artık el ile değiştirilebilir.  

## <a name="tagging-sensitive-accounts"></a>Hassas hesapları etiketleme

Bu grupların yanı sıra, grupları veya hesapları hassas olarak algılamaları geliştirmek için el ile etiketleyebilirsiniz. Gizli Grup değişikliği algılama ve yanal hareket yolunun gibi bazı Azure ATP algılamalar hangi gruplar ve hesaplar hassas kabul edilir üzerinde dayandığından, bu önemlidir. Diğer kullanıcı veya grup Panosu üyeleri, şirket Yöneticiler, satış, vb. Direktörü, hassas olarak el ile etiketleyebilir ve Azure ATP bunları gizli olarak değerlendirdiği.

1.  Azure ATP çalışma alanı portalında **yapılandırma** menü çubuğundaki dişli.

2.  Altında **algılama** tıklayın **varlık etiketleri**.

    ![Azure ATP varlık etiketleri](media/entity-tags.png)

3.  İçinde **hassas** bölümünde, adını, **hassas hesapları** ve **gizli gruplarda** ve ardından **+** bunları eklemek oturum açın.

    ![Azure ATP hassas hesap örneği](media/sensitive-account-sample.png)

4. **Kaydet**'e tıklayın.

    
## <a name="see-also"></a>Ayrıca bkz.

- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)