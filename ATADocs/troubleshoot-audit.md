---
title: ATA denetim günlükleriyle çalışma | Microsoft Docs
description: Bu makalede, Windows Olay Günlüğü'ndeki ATA denetim günlükleri ile nasıl çalışılacağını açıklanmaktadır.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 1d186a96-ef70-4787-aa64-c03d1db94ce0
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 55712dfcb74e8779c2e06137ac3ea08f132a4f0f
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133438"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*

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

* Yapılandırma değişikliği denetim günlüğü, hem eski ve yeni yapılandırmayı içerir.


## <a name="see-also"></a>Ayrıca Bkz.
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
