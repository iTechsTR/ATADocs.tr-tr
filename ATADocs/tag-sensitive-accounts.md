---
title: Etiket hassas hesaplar ile ATA | Microsoft Docs
description: Advanced Threat Analytics (ATA) kullanarak hassas hesapları etiketi açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/14/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 40a1c5c4-b8d6-477c-8ae5-562b37661624
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: cea6d666d3d969070541fc8dcc4fd59726ac8c38
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46134101"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="tag-sensitive-accounts"></a>Etiket hassas hesapları

El ile grupları veya hesapları hassas olarak algılamaları geliştirmek için etiketleyebilirsiniz. Gizli Grup değişikliği algılama ve yanal hareket yolunun gibi bazı ATA algılamaları hangi gruplar ve hesaplar hassas kabul edilir üzerinde dayandığından güncelleştirildiğinden emin olmak önemlidir. Daha önce ATA varlığın otomatik olarak kabul *hassas* belirli bir liste gruplarının bir üyesi ise. Artık el ile diğer kullanıcılara veya gruplara Pano üyeleri, şirket Yöneticiler, satış, vb. Direktörü, hassas olarak etiketleyebilir ve ATA bunları hassas dikkate alacaktır.

1.  ATA Konsolu'nda **yapılandırma** menü çubuğundaki dişli.

2.  Altında **algılama** tıklayın **varlık etiketleri**.

    ![Varlık etiketleri ATA](media/entity-tags.png)

3.  İçinde **hassas** bölümünde, adını, **hassas hesapları** ve **gizli gruplarda** ve ardından **+** bunları eklemek oturum açın.

    ![ATA hassas hesap örnek](media/sensitive-account-sample.png)

4. **Kaydet**'e tıklayın.

5. Varlık adına tıklayarak varlık profili sayfasına gidin. Burada bir gruba üyelik nedeniyle veya manuel olarak hassas etiketleme nedeniyle olup neden varlık hassas - kabul edilen görmeye olacaktır.


## <a name="sensitive-groups"></a>Gizli gruplar

Aşağıdaki listede yer alan grupları, duyarlı ATA tarafından değerlendirilir. Şu grupların üyesi olan herhangi bir varlık, gizli olarak kabul edilir:

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
-   Kurumsal salt okunur etki alanı denetleyicileri 
-   Schema Admins 
-   Enterprise Admins
     
## <a name="see-also"></a>Ayrıca bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
