---
# required metadata

title: ATA Veritabanı Yönetimi | Microsoft Advanced Threat Analytics
description: ATA veritabanını taşımanıza, yedeklemenize veya geri yüklemenize yardımcı olacak yordamlar.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ATA Veritabanı Yönetimi
ATA veritabanını taşımanız, yedeklemeniz veya geri yüklemeniz gerekiyorsa, MongoDB ile çalışmak için bu yordamları kullanın.

## ATA veritabanını yedekleme
[İlgili MongoDB belgelerine](http://docs.mongodb.org/manual/administration/backup/) bakın..

## ATA veritabanını geri yükleme
[İlgili MongoDB belgelerine](http://docs.mongodb.org/manual/administration/backup/) bakın..

## ATA veritabanını başka bir sürücüye taşıma

1.  **Microsoft Advanced Threat Analytics Center** hizmetini durdurun.

2.  **MongoDB** hizmetini durdurun.

3.  Varsayılan olarak C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\mongod.cfg konumunda yer alan Mongo yapılandırma dosyasını açın.

    Şu parametreyi bulun: `storage: dbPath`

4.  `dbPath` parametresinde listelenen klasörü yeni konuma taşıyın.

5.  Mongo yapılandırma dosyasının içindeki `dbPath` parametresini yen klasörün yoluyla değiştirin, ardından dosyayı kaydedin ve kapatın.

    ![MongoDB yapılandırmasını değiştirme resmi](media/ATA-mongoDB-moveDB.png)

6.  **MongoDB** hizmetini başlatın.

7.  Komut istemini açın ve Mongo kabuğunu çalıştırmak için şu komutu çalıştırın: `mongo.exe ATA` .

    Varsayılan olarak, mongo.exe dosyası C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin yolunda bulunur.

8.  Şu komutu çalıştırın: `db.SystemProfiles.update( {_t: "CenterSystemProfile"} , {$set:{"Configuration.CenterDatabaseClientConfiguration.DataPath" : "<New DB Location>"}}) Instead of <New DB Location>` burada &lt;New DB Location&gt;, yeni klasör yoludur.

9.  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Advanced Threat Analytics\Center\DatabaseDataPath değerini yeni klasör yoluna güncelleştirin.

9. **Microsoft Advanced Threat Analytics Center** hizmetini başlatın.

## Ayrıca Bkz.
- [ATA mimarisi](/advanced-threat-analytics/plan-design/ata-architecture)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)



<!--HONumber=May16_HO1-->


