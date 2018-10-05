---
title: Etiket hassas hesapları Azure ATP ile | Microsoft Docs
description: Azure Gelişmiş tehdit Koruması (ATP) kullanarak hassas hesapları etiketi açıklar
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 43e57f87-ca85-4922-8ed0-9830139fe7cb
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 31871a03795b1c08e4fd8954cac80a00538863db
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48783347"
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

1.  Azure ATP portalında **yapılandırma** menü çubuğundaki dişli.

2.  Altında **algılama** tıklayın **varlık etiketleri**.

    ![Azure ATP varlık etiketleri](media/entity-tags.png)

3.  İçinde **hassas** bölümünde, adını, **hassas hesapları** ve **gizli gruplarda** ve ardından **+** bunları eklemek oturum açın.

    ![Azure ATP hassas hesap örneği](media/sensitive-account-sample.png)

4. **Kaydet**'e tıklayın.

    
## <a name="see-also"></a>Ayrıca bkz.

- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)