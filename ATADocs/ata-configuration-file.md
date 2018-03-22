---
title: "Advanced Threat Analytics Yapılandırmasını Dışarı ve İçeri Aktarma| Microsoft Docs"
description: "ATA yapılandırmasını dışarı ve içeri aktarma."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: edbf553bf48d984f4864264643d197362c3d6042
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*



# <a name="export-and-import-the-ata-configuration"></a>ATA Yapılandırmasını Dışarı ve İçeri Aktarma
ATA’nın yapılandırması veritabanındaki "SystemProfile" koleksiyonunda depolanır.
Bu koleksiyon adı verilen dosyalara ATA Center hizmeti tarafından saatte yedeklenir: **SystemProfile_*zaman damgası*.json**. En son 10 sürüm depolanır.
Bu dosya adlı alt klasörde yer alan **yedekleme**. ATA’nın yüklendiği varsayılan konumda, şurada bulunabilir: *C:\Program Files\Microsoft Advanced Threat Analytics\Center\Backup\SystemProfile_*zamandamgası*.json*. 

**Not**: ATA’da önemli değişiklikler yaparken bu dosyayı herhangi bir yere yedeklemenizi öneririz.

Aşağıdaki komutu çalıştırarak ayarların tümünü geri yüklemek mümkündür:

`mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`

## <a name="see-also"></a>Ayrıca bkz:
- [ATA mimarisi](ata-architecture.md)
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

