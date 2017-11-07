---
title: "Advanced Threat Analytics Yapılandırmasını Dışarı ve İçeri Aktarma| Microsoft Docs"
description: "ATA yapılandırmasını dışarı ve içeri aktarma."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 9653cca6c600abe311a6a557ab67d427d238899a
ms.sourcegitcommit: e2cb3af9c1dbb0b75946dc70cc439b19d654541c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="export-and-import-the-ata-configuration"></a>ATA Yapılandırmasını Dışarı ve İçeri Aktarma
ATA’nın yapılandırması veritabanındaki "SystemProfile" koleksiyonunda depolanır.
Bu toplama, ATA Center hizmeti tarafından saatte bir "SystemProfile_*zamandamgası*json" adlı dosyalara yedeklenir. En son 10 sürüm depolanır.
Bu dosya "Backup" adlı alt klasörde yer alır. ATA’nın yüklendiği varsayılan konumda, şurada bulunabilir: *C:\Program Files\Microsoft Advanced Threat Analytics\Center\Backup\SystemProfile_*zamandamgası*.json*. 

**Not**: ATA’da önemli değişiklikler yaparken bu dosyayı herhangi bir yere yedeklemenizi öneririz.

Aşağıdaki komutu çalıştırarak ayarların tümünü geri yüklemek mümkündür:

`mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`

## <a name="see-also"></a>Ayrıca Bkz.
- [ATA mimarisi](ata-architecture.md)
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

