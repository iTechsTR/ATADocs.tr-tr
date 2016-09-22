---
title: "ATA sürüm 1.7’daki yenilikler | Microsoft ATA"
description: "ATA sürüm 1.7’teki yenilikleri ve bilinen sorunları listeler"
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 08/28/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ae6a3295d2fffabdb8e5f713674379e4af499ac2
ms.openlocfilehash: af9101260b1a0d5d9da32398f638f76e0c8c40a7


---

# ATA sürüm 1.7’deki yenilikler
Bu sürüm notları, Advanced Threat Analytics’in bu sürümündeki bilinen sorunlar hakkında bilgi sağlar.

## ATA 1.7 güncelleştirmesindeki yenilikler
ATA 1.7 güncelleştirmesi aşağıdaki alanlarda geliştirmeler sağlar:

-   Yeni ve güncelleştirilmiş algılamalar

-   Rol tabanlı erişim denetimi

-   Windows Server 2016 R2 ve Windows Server Core desteği

-   Kullanıcı deneyimi iyileştirmeleri


### Yeni ve güncelleştirilmiş algılamalar


- **Dizin Hizmetleri Numaralandırması kullanarak keşif** Keşif aşamasının bir parçası olarak, saldırganlar farklı yöntemler kullanarak ağdaki varlıklar hakkında bilgi toplar. SAM-R protokolünü kullanan Dizin hizmetleri numaralandırması saldırganların bir etki alanındaki kullanıcıların ve grupların listesini ele geçirmesini ve farklı varlıklar arasındaki etkileşimi anlamasını sağlar. 

- **Karma Değer Geçişi Geliştirmeleri** Karma Değer Geçişi algılamayı geliştirmek için varlıkların kimlik doğrulama modellerine yönelik ek davranışsal modeller ekledik. Bu modeller ATA’nın varlık davranışını şüpheli NTLM kimlik doğrulamalarıyla ilişkilendirmesini ve gerçek zamanlı Karma Değer Geçişi saldırılarını yanlış pozitif senaryoların davranışından ayırt etmesini sağlar.

- **Anahtar Geçişi Geliştirmeleri** Gelişmiş saldırıları genel olarak ve özellikle Anahtar Geçişi için başarılı bir şekilde algılamak amacıyla bir IP adresi ve bilgisayar hesabı arasındaki bağıntının doğru olması gerekir. Bu, IP adreslerinin tasarımsal olarak hızla değiştiği ortamlarda (örneğin, Wi-Fi ağları ve aynı ana bilgisayarı paylaşan birden çok sanal makine) zordur. Bu zorluğun üstesinden gelmek ve Anahtar Geçişi algılamasının doğruluğunu artırmak için ATA’nın Ağ Adı Çözümleme (NNR) mekanizması yanlış pozitifleri azaltmak için önemli ölçüde iyileştirilmiştir.

- **Anormal Davranış Geliştirmeleri** ATA 1.7’de, NTLM kimlik doğrulama verileri anormal davranış algılamaları için bir veri kaynağı olarak eklenmiş ve böylece algoritmaların ağdaki varlık davranışını daha geniş bir şekilde kapsaması sağlanmıştır. 

- **Olağan Dışı Protokol Uygulaması Geliştirmeleri** ATA artık Kerberos protokolünde olağan dışı protokol uygulamalarını ve NTLM protokolündeki ek anormallikleri algılamaktadır. Özellikle, Kerberos’taki bu yeni anormallikler Karma Değeri Atlayarak Geçiş saldırılarında yaygın olarak kullanılır.


### Altyapı

- **Rol tabanlı erişim denetimi** Rol Tabanlı Erişim Denetimi (RBAC) kapasitesi. ATA 1.7 üç rol içerir: ATA Yöneticisi, ATA Analisti ve ATA İdarecisi.

- **Windows Server 2016 ve Windows Server Core Desteği** ATA 1.7, Windows Server 2012 için Server Core ve Windows Server 2012 R2 için Server Core çalıştıran etki alanı denetleyicilerinde Lightweight Gateway bileşenlerinin dağıtımını destekler. Ayrıca, bu sürüm Windows Server 2016’yı hem ATA Center hem de ATA Gateway bileşenleri için destekler.

### Kullanıcı Deneyimi
- **Yapılandırma Deneyimi** Bu sürümde, ATA yapılandırması deneyimi daha iyi bir kullanıcı deneyimi sağlama amacıyla ve birden çok ATA Gateway bileşenine sahip ortamları daha iyi destekleyecek şekilde tasarlanmıştır. Bu sürüm ayrıca, çeşitli Ağ Geçitlerinin otomatik güncelleştirme işlemlerinin daha kolay, daha iyi yönetilmesi için ATA Gateway güncelleştirme sayfasını getirmiştir.

## Bilinen sorunlar
Bu sürümün bilinen sorunları şunlardır:

### Ağ geçidi otomatik güncelleştirme işlemi başarısız olabilir
**Belirtiler:** Yavaş WAN bağlantılarına sahip ortamlarda, ATA Gateway güncelleştirmesi güncelleştirme zaman aşımına (100 saniye) ulaşabilir ve başarıyla tamamlanamayabilir.
ATA Konsolunda, ATA Gateway uzun bir süre “Güncelleştiriliyor (paket indiriliyor)” durumuna sahip olur ve sonunda başarısız olur.

**Geçici çözüm:** Bu sorunu çözmek için en son ATA Gateway paketini ATA Konsolundan indirin ve ATA Gateway’i el ile güncelleştirin.

### ATA 1.6’dan güncelleştirirken geçiş hatası
ATA 1.7’ye güncelleştirirken, güncelleştirme işlemi *0x80070643* hata koduyla başarısız olabilir:

![ATA’yı 1.7’ye güncelleştirme hatası](media/ata-update-error.png)

Hatanın nedenini bulmak için dağıtım günlüğünü gözden geçirin. Dağıtım günlüğü **%temp%\..\Microsoft Advanced Thread Analytics Center_{date_stamp}_MsiPackage.log** konumunda bulunur. 

Aşağıdaki tabloda aranacak hataların ve hatayı çözmek için ilgili Mongo betiklerinin listesi verilmiştir. Mongo betiğinin nasıl çalıştırılacağını gösteren aşağıdaki örneği inceleyin:

| Dağıtım günlüğü dosyasında hata                                                                                                                  | Mongo betiği                                                                                                                                                                         |
|---|---|
| System.FormatException: Size {size},is larger than MaxDocumentSize 16777216 <br>Dosyada ilerleyin:<br>  Microsoft.Tri.Center.Deployment.Package.Actions.DatabaseActions.MigrateUniqueEntityProfiles(Boolean isPartial)                                                                                        | db.UniqueEntityProfile.find().forEach(function(obj){if(Object.bsonsize(obj) > 12582912) {print(obj._id);print(Object.bsonsize(obj));db.UniqueEntityProfile.remove({_id:obj._id});}}) |
| System.OutOfMemoryException: Exception of type 'System.OutOfMemoryException' was thrown<br>Dosyada ilerleyin:<br>Microsoft.Tri.Center.Deployment.Package.Actions.DatabaseActions.ReduceSuspiciousActivityDetailsRecords(IMongoCollection`1 suspiciousActivityCollection, Int32 deletedDetailRecordMaxCount) | db.SuspiciousActivity.find().forEach(function(obj){if(Object.bsonsize(obj) > 500000),{print(obj._id);print(Object.bsonsize(obj));db.SuspiciousActivity.remove({_id:obj._id});}})     |
|System.Security.Cryptography.CryptographicException: Bad Length<br>Dosyada ilerleyin:<br> Microsoft.Tri.Center.Deployment.Package.Actions.DatabaseActions.MigrateCenterSystemProfile(IMongoCollection`1 systemProfileCollection)| CenterThumbprint db =. SystemProfile.find({_t:"CenterSystemProfile"}).toArray() [0]. Configuration.SecretManagerConfiguration.CertificateThumbprint;db. SystemProfile.update ({_t: "CenterSystemProfile"},{$set:{"Configuration.ManagementClientConfiguration.ServerCertificateThumbprint":CenterThumbprint}})|


Uygun betiği çalıştırmak için aşağıdaki adımları izleyin. 

1.  Yükseltilmiş komut isteminden **\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin** konumuna göz atın.
2.  Tür: **Mongo.exe ATA**   (*Not*: ATA büyük harfle yazılmalıdır.)
3.  Yukarıda bulunan tablodaki dağıtım günlüğünden hatayla eşleşen betiği yapıştırın.

![ATA Mongo Betiği](media/ATA-mongoDB-script.png)

Bu noktada, yükseltmeyi yeniden başlatabiliyor olmanız gerekir.

### ATA birçok "*Dizin hizmetleri listeleme keşfi *" şüpheli etkinlikleri bildirir:
 
Bu, kuruluştaki istemci makinelerinin hepsinde (veya çoğunda) ağ tarayan araç bulunmasından kaynaklanıyor olabilir. Bu sorunu görüyorsanız:

1. Sebebi veya istemci makinelerde çalışan belirli uygulamaları tanımlayabiliyorsanız, Microsoft.com’dan ATAEval’e gereken bilgiyi içeren bir e-posta atın.
2. Bu olayların hepsini iptal etmek için aşağıdaki mongo betiklerini kullanın (mongo betiklerinin nasıl yürütüleceğini öğrenmek için yukarıyı inceleyin):

db.SuspiciousActivity.update({_t: "SamrReconnaissanceSuspiciousActivity"}, {$set: {Status: "Dismissed"}}, {multi: true})

### ATA kapatılmış şüpheli etkinlikler için bildirim gönderir:
Bildirimler yapılandırıldıysa, ATA kapatılmış şüpheli etkinlikler için bildirim (e-posta, syslog ve olay günlükleri) göndermeye devam edebilir.
Şu an sorun için geçici çözüm yoktur. 

### ATA Gateway, TLS 1.0 ve TLS 1.1 devre dışı bırakılmazsa ATA Center’a kaydolmayabilir:
TLS 1.0 ve TLS 1.1 ATA Gateway’de (veya Lightweight Gateway’de) devre dışı bırakılırsa, ağ geçidi kendini ATA Center’a kaydedemeyebilir

### ATA tarafından kullanılan sertifikalar için otomatik sertifika yenileme desteklenmez
Otomatik sertifika yenilemenin kullanılması, sertifika otomatik olarak yenilendiğinde ATA’nın çalışmasının durmasına neden olabilir. 


## Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

[ATA 1.7’ye güncelleştirme - taşıma rehberi](ata-update-1.7-migration-guide.md)




<!--HONumber=Sep16_HO2-->


