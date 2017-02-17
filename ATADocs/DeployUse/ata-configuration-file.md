---
title: "Advanced Threat Analytics Yapılandırmasını Dışarı ve İçeri Aktarma| Microsoft Docs"
description: "ATA yapılandırmasını dışarı ve içeri aktarma."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b28cb3a0da844b7c460c03726222bc775a9e47da
ms.openlocfilehash: 5ea29a5b64fd1f786200d3bbb62cd3964f8802e2


---

*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*



# <a name="export-and-import-the-ata-configuration"></a>ATA Yapılandırmasını Dışarı ve İçeri Aktarma
ATA’nın yapılandırması veritabanındaki "SystemProfile" koleksiyonunda depolanır.
Bu toplama, ATA Center hizmeti tarafından saatte bir "SystemProfile_*zamandamgası*json" adlı dosyalara yedeklenir. En son 10 sürüm depolanır.
Bu dosya "Backup" adlı alt klasörde yer alır. ATA’nın yüklendiği varsayılan konumda, şurada bulunabilir: *C:\Program Files\Microsoft Advanced Threat Analytics\Center\Backup\SystemProfile_*zamandamgası*.json*. 

**Not**: ATA’da önemli değişiklikler yaparken bu dosyayı herhangi bir yere yedeklemenizi öneririz.

Aşağıdaki komutu çalıştırarak ayarların tümünü geri yüklemek mümkündür:

`mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`

## <a name="see-also"></a>Ayrıca Bkz.
- [ATA mimarisi](/advanced-threat-analytics/plan-design/ata-architecture)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)




<!--HONumber=Feb17_HO1-->


