---
title: ATA denetim günlükleriyle çalışma | Microsoft Docs
description: Bu makalede, Windows Olay Günlüğü'ndeki ATA denetim günlükleri ile nasıl çalışılacağını açıklanmaktadır.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 1d186a96-ef70-4787-aa64-c03d1db94ce0
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 5f4e7a51ca0a678b93d2b36bdafc885141dda1eb
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44165958"
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
