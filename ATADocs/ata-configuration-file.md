---
title: Advanced Threat Analytics Yapılandırmasını Dışarı ve İçeri Aktarma| Microsoft Docs
description: ATA yapılandırmasını dışarı ve içeri aktarma.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 9/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: ad28af9c8e1f274fe3d97f6f28ed60f2e57694a3
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44166706"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="export-and-import-the-ata-configuration"></a>ATA Yapılandırmasını Dışarı ve İçeri Aktarma
ATA’nın yapılandırması veritabanındaki "SystemProfile" koleksiyonunda depolanır.
Bu koleksiyon 4 saatte ATA Center hizmeti tarafından adlı dosyalara yedeklenir: **SystemProfile_*zaman damgası*.json**. 300 en son sürüm depolanır.
Bu dosya adlı alt klasörde yer alan **yedekleme**. ATA’nın yüklendiği varsayılan konumda, şurada bulunabilir: *C:\Program Files\Microsoft Advanced Threat Analytics\Center\Backup\SystemProfile_* zamandamgası *.json*. 

**Not**: ATA’da önemli değişiklikler yaparken bu dosyayı herhangi bir yere yedeklemenizi öneririz.

Aşağıdaki komutu çalıştırarak ayarların tümünü geri yüklemek mümkündür:

`mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`

## <a name="see-also"></a>Ayrıca Bkz.
- [ATA mimarisi](ata-architecture.md)
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

