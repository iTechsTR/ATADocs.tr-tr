---
title: "Advanced Threat Analytics Veritabanı Yönetimi | Microsoft Docs"
description: "ATA veritabanını taşımanıza, yedeklemenize veya geri yüklemenize yardımcı olacak yordamlar."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 05e49e23-6e0a-4ec0-9a63-a2093173c8a1
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b28cb3a0da844b7c460c03726222bc775a9e47da
ms.openlocfilehash: 95ac5a45fb69e8b23c60ec95e285a8f8d361853c


---

*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*



# <a name="ata-database-management"></a>ATA Veritabanı Yönetimi
ATA veritabanını taşımanız, yedeklemeniz veya geri yüklemeniz gerekiyorsa, MongoDB ile çalışmak için bu yordamları kullanın.

## <a name="backing-up-the-ata-database"></a>ATA veritabanını yedekleme
[İlgili MongoDB belgelerine](http://docs.mongodb.org/manual/administration/backup/) bakın.

## <a name="restoring-the-ata-database"></a>ATA veritabanını geri yükleme
[İlgili MongoDB belgelerine](http://docs.mongodb.org/manual/administration/backup/) bakın.

## <a name="moving-the-ata-database-to-another-drive"></a>ATA veritabanını başka bir sürücüye taşıma

1.  **Microsoft Advanced Threat Analytics Center** hizmetini durdurun.
> [!Important] 
> Sonraki adıma geçmeden önce ATA Center hizmetinin durdurulduğundan emin olun.

2.  **MongoDB** hizmetini durdurun.

3.  Varsayılan olarak C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\mongod.cfg konumunda yer alan Mongo yapılandırma dosyasını açın.

    `storage: dbPath` parametresini bulma

4.  `dbPath` parametresinde listelenen klasörü yeni konuma taşıyın.

5.  Mongo yapılandırma dosyasının içindeki `dbPath` parametresini yen klasörün yoluyla değiştirin, ardından dosyayı kaydedin ve kapatın.

    ![MongoDB yapılandırmasını değiştirme resmi](media/ATA-mongoDB-moveDB.png)

6.  **MongoDB** hizmetini başlatın.

7. **Microsoft Advanced Threat Analytics Center** hizmetini başlatın.

## <a name="see-also"></a>Ayrıca Bkz.
- [ATA mimarisi](/advanced-threat-analytics/plan-design/ata-architecture)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)




<!--HONumber=Feb17_HO1-->


