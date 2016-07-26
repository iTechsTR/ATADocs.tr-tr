---
title: "ATA Veritabanı Yönetimi | Microsoft ATA"
description: "ATA veritabanını taşımanıza, yedeklemenize veya geri yüklemenize yardımcı olacak yordamlar."
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 115ec28877665c79e5cbcd557528da156c8d7149
ms.openlocfilehash: fd00623f9be396b3a2c384cce436996b5093cc3f


---

# ATA Veritabanı Yönetimi
ATA veritabanını taşımanız, yedeklemeniz veya geri yüklemeniz gerekiyorsa, MongoDB ile çalışmak için bu yordamları kullanın.

## ATA veritabanını yedekleme
[İlgili MongoDB belgelerine](http://docs.mongodb.org/manual/administration/backup/) bakın.

## ATA veritabanını geri yükleme
[İlgili MongoDB belgelerine](http://docs.mongodb.org/manual/administration/backup/) bakın.

## ATA veritabanını başka bir sürücüye taşıma

1.  **Microsoft Advanced Threat Analytics Center** hizmetini durdurun.

2.  **MongoDB** hizmetini durdurun.

3.  Varsayılan olarak C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\mongod.cfg konumunda yer alan Mongo yapılandırma dosyasını açın.

    Şu parametreyi bulun: `storage: dbPath`

4.  `dbPath` parametresinde listelenen klasörü yeni konuma taşıyın.

5.  Mongo yapılandırma dosyasının içindeki `dbPath` parametresini yen klasörün yoluyla değiştirin, ardından dosyayı kaydedin ve kapatın.

    ![MongoDB yapılandırmasını değiştirme resmi](media/ATA-mongoDB-moveDB.png)

6.  **MongoDB** hizmetini başlatın.

7.  Komut istemini açın ve `mongo.exe ATA` komutuyla Mongo kabuğunu çalıştırın.

    Varsayılan olarak, mongo.exe dosyası C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin yolunda bulunur.

8.  Şu komutu çalıştırın: `db.SystemProfiles.update( {_t: "CenterSystemProfile"} , {$set:{"Configuration.CenterDatabaseClientConfiguration.DataPath" : "<New DB Location>"}})`

   <New DB Location> (burada `&lt;New DB Location&gt;`, yeni klasör yoludur) yerine onu kullanın.

9.  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Advanced Threat Analytics\Center\DatabaseDataPath değerini yeni klasör yoluna güncelleştirin.

9. **Microsoft Advanced Threat Analytics Center** hizmetini başlatın.

## Ayrıca Bkz.
- [ATA mimarisi](/advanced-threat-analytics/plan-design/ata-architecture)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)




<!--HONumber=Jul16_HO3-->


