---
title: "ATA denetim günlükleriyle çalışma | Microsoft Docs"
description: "Bu makalede, Windows Olay Günlüğü'ndeki ATA denetim günlükleri ile nasıl çalışılacağını açıklanmaktadır."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1d186a96-ef70-4787-aa64-c03d1db94ce0
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: f193e7a173223b6b6aca8f4e31abf471d4b70ba9
ms.sourcegitcommit: e2cb3af9c1dbb0b75946dc70cc439b19d654541c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2017
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
