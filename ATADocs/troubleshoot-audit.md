---
title: "ATA denetim günlükleriyle çalışma | Microsoft Docs"
description: "Bu makalede, Windows Olay Günlüğü'ndeki ATA denetim günlükleri ile nasıl çalışılacağını açıklanmaktadır."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1d186a96-ef70-4787-aa64-c03d1db94ce0
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 2b7489e9057828ea452d55ddb01b37e0a1c16e2f
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*

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

* Yapılandırma değişikliği denetim günlüğü, önceki yapılandırmayı ve yeni yapılandırmayı içerir.


## <a name="see-also"></a>Ayrıca bkz:
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
