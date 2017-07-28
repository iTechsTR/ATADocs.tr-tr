---
title: "Veritabanını kullanarak Advanced Threat Analytics sorunlarını giderme | Microsoft Docs"
description: "Sorunları gidermeye yardımcı olması için ATA veritabanını nasıl kullanabileceğiniz açıklanır"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 377a3c81-5c1d-486f-8942-85249aacf560
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 174918812562b9bfe892fcde90d92e208b26ffc3
ms.sourcegitcommit: 42ce07e3207da10e8dd7585af0e34b51983c4998
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="troubleshooting-ata-using-the-ata-database"></a>ATA veritabanını kullanarak ATA sorunlarını giderme
ATA veritabanı olarak MongoDB’yi kullanır.
Varsayılan komut satırını kullanarak veya gelişmiş görevler ve sorun giderme işlemleri yapmak için bir kullanıcı arabirimini kullanarak veritabanıyla etkileşim kurabilirsiniz.

## <a name="interacting-with-the-database"></a>Veritabanıyla etkileşim kurma
Veritabanını sorgulamanın varsayılan ve en temel yolu Mongo kabuğunu kullanmaktır:

1.  Komut satırı penceresi açın ve yolu MongoDB bin klasörüyle değiştirin. Varsayılan yol: **C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin**

2.  Şunu çalıştırın: `mongo.exe ATA`. ATA’yı tümüyle büyük harflerle yazmaya dikkat edin.

> [!div class="mx-tableFixed"]
|Nasıl yapılır...|Söz dizimi|Notlar|
|-------------|----------|---------|
|Veritabanında koleksiyonları denetleme.|`show collections`|Trafiğin veritabanına yazıldığını ve olay 4776’nın ATA tarafından alındığını görmeye yönelik uçtan uca bir test olarak yararlıdır.|
|Bir kullanıcı/bilgisayar/grup (UniqueEntity) ile ilgili kullanıcı kimliği gibi ayrıntıları alma.|`db.UniqueEntity.find({SearchNames: "<name of entity in lower case>"})`||
|Belirli bir günde belirli bir bilgisayardan kaynaklanan Kerberos kimlik doğrulama trafiğini bulma.|`db.KerberosAs_<datetime>.find({SourceComputerId: "<Id of the source computer>"})`|&lt;Kaynak bilgisayarın kimliğini&gt; almak için, örnekte gösterildiği gibi UniqueEntity koleksiyonlarını sorgulayabilirsiniz.<br /><br />Her ağ etkinliği türünün, örneğin Kerberos kimlik doğrulamalarının her UTC tarihi için kendi koleksiyonu vardır.|
|Belirli bir günde belirli bir hesapla ilgili olarak belirli bir bilgisayardan kaynaklanan NTLM trafiğini bulma.|`db.Ntlm_<datetime>.find({SourceComputerId: "<Id of the source computer>", SourceAccountId: "<Id of the account>"})`|&lt;Kaynak bilgisayarın kimliğini&gt; ve &lt;hesabın kimliğini&gt; almak için, örnekte gösterildiği gibi UniqueEntity koleksiyonlarını sorgulayabilirsiniz.<br /><br />Her ağ etkinliği türünün, örneğin NTLM kimlik doğrulamalarının her UTC tarihi için kendi koleksiyonu vardır.|
|Hesabın etkin tarihleri gibi gelişmiş özellikler için arama yapma. |`db.UniqueEntityProfile.find({UniqueEntityId: "<Id of the account>")`|&lt;Hesabın kimliğini&gt; almak için, örnekte gösterildiği gibi UniqueEntity koleksiyonlarını sorgulayabilirsiniz.<br>Hesabın etkin olduğu tarihleri gösteren özelliği adı: "ActiveDates". Örneğin, anormal davranış makine öğrenme algoritmasının bir hesap üzerinde çalıştırabilmesi için, hesabın en az 21 günlük etkinliği olup olmadığını bilmek isteyebilirsiniz.|
|Gelişmiş yapılandırma değişikliklerini yapın. Bu örnekte tüm ATA Gateway bileşenlerinde gönderme kuyruğu boyutunu 10.000 olarak değiştiriyoruz.|`db.SystemProfile.update( {_t: "GatewaySystemProfile"} ,`<br>`{$set:{"Configuration.EntitySenderConfiguration.EntityBatchBlockMaxSize" : "10000"}})`|`|

Aşağıdaki örnek, yukarıda sağlanan söz diziminin kullanıldığı örnek kodu sağlıyor. 20/10/2015 tarihinde gerçekleşen bir kuşkulu etkinliği araştırıyor ve "John Doe"nun o gün gerçekleştirdiği NTLM etkinlikleri hakkında daha fazla bilgi edinmek istiyorsanız:<br /><br />İlk olarak "John Doe"nun kimliğini bulun.

`db.UniqueEntity.find({Name: "John Doe"})`<br>`_id` değeri olarak gösterilen kimliğini bir yere not alın. Bizim örneğimizde, kimliğin şöyle olduğunu varsayalım: `123bdd24-b269-h6e1-9c72-7737as875351`<br>Ardından, aradığınız tarihten (bizim örneğimizde 20/10/2015) önceki en yakın tarihli koleksiyonu arayın.<br>Sonra, John Doe'nun hesabının NTLM etkinliklerini arayın: 

`db.Ntlms_<closest date>.find({SourceAccountId: "123bdd24-b269-h6e1-9c72-7737as875351"})`

## <a name="see-also"></a>Ayrıca bkz.
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
