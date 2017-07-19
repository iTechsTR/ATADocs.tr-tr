---
title: "ATA denetim günlükleriyle çalışma | Microsoft Docs"
description: "Bu makalede, Windows Olay Günlüğü'ndeki ATA denetim günlükleri ile nasıl çalışılacağını açıklanmaktadır."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/5/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1d186a96-ef70-4787-aa64-c03d1db94ce0
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 54f17bc4775868e380586822456330dfc2d45c29
ms.sourcegitcommit: 53b56220fa761671442da273364bdb3d21269c9e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/05/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*

# <a name="working-with-ata-audit-logs"></a>ATA denetim günlükleriyle çalışma

ATA denetim günlükleri; ATA Center ve ATA Gateway makinelerindeki Windows Olay Günlükleri’nde **Uygulamalar ve Hizmetler** altında bulunan **Microsoft ATA**’da saklanır.

ATA Center denetim günlüğü şunları barındırır:
-   Şüpheli etkinlik bilgileri
-   İzleme uyarıları (sistem durumu sayfası)
-   ATA Konsolu’ndaki oturum açma işlemleri
-   Tüm yapılandırma değişiklikleri*

ATA Gateway denetim günlüğü şunları barındırır:
-   Ağ geçidi yapılandırma değişiklikleri* 

(Tüm ATA Gateway yapılandırma değişiklikleri ATA Center’da yapılandırılır ancak yine de Gateway makinesinde denetlenir.)

*Yapılandırma değişikliği denetim günlüğü, eski ve yeni yapılandırmaları birlikte barındırır.


## <a name="see-also"></a>Ayrıca Bkz.
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
