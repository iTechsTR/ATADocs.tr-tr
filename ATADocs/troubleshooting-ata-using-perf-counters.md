---
title: "Performans sayaçlarını kullanarak Advanced Threat Analytics sorunlarını giderme | Microsoft Docs"
description: "ATA’yla ilgili sorunları gidermek için performans sayaçlarını nasıl kullanabileceğiniz açıklanır"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: df162a62-f273-4465-9887-94271f5000d2
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 78f23d3f2552ed7ddc086be2620fbb627b676722
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*



# <a name="troubleshooting-ata-using-the-performance-counters"></a>Performans sayaçlarını kullanarak ATA sorunlarını giderme
ATA performans sayaçları, ATA’nın her bileşeninin ne kadar iyi çalıştığı konusunda fikir sağlar. ATA’daki bileşenler verileri sıralı olarak işlediğinden, bir sorun çıktığında, bileşen zincirinin herhangi bir yerinde trafiğin kısmi olarak bırakılmasına neden olabilir. Sorunu çözmek için, hangi bileşende istenmeyen sonuç alındığını saptamanız ve sorunu zincirin başında çözmeniz gerekir. Her bileşenin nasıl çalıştığını anlamak için, performans sayaçlarında bulunan verileri kullanın.
İç ATA bileşenlerinin akışını anlamak için [ATA mimarisi](ata-architecture.md) konusuna bakın.

**ATA bileşeni işlemi**:

1.  Bileşenlerden biri boyut üst sınırına ulaştığında, önceki bileşenin kendisine daha fazla varlık göndermesini engeller.

2.  Sonunda önceki bileşen **kendi** boyutunu artırmaya başlar ve bu durum kendisinden önceki bileşenin daha fazla varlık göndermesini engelleyene kadar devam eder.

3.  Bu varlıklar artık iletebilir iletemediğinde trafiği Ağdinleyicisi bileşenine geriye gerçekleşir.


## <a name="retrieving-performance-monitor-files-for-troubleshooting"></a>Sorun giderme için performans izleyicisi dosyalarını alma

Çeşitli ATA bileşenlerinden performans izleyicisi dosyalarını (BLG) almak için:
1.  Perfmon aracını açın.
2.  Adlandırılmış veri toplayıcı durdurun: **Microsoft ATA Gateway** veya **Microsoft ATA Center**.
3.  Veri toplayıcı grubu klasörüne (varsayılan olarak "C:\Program Files\Microsoft Advanced Threat Analytics\Gateway\Logs\DataCollectorSets" veya “C:\Program Files\Microsoft Advanced Threat Analytics\Center\Logs\DataCollectorSets” konumundadır) gidin.
4.  En son değiştirilen BLG dosyasını kopyalayın.
5.  Adlandırılmış veri toplayıcı grubunu yeniden: **Microsoft ATA Gateway** veya **Microsoft ATA Center**.


## <a name="ata-gateway-performance-counters"></a>ATA Gateway performans sayaçları

Bu bölümde, ATA Gateway’e yapılan her gönderme aynı zamanda ATA Lightweight Gateway’e de yapılmıştır.

ATA Gateway'in performans sayaçlarını ekleyerek, ATA Gateway gerçek zamanlı performans durumunu gözlemleyebilirsiniz.
Bu açarak yapılır **Performans İzleyicisi** ve ATA Gateway için tüm sayaçlar eklenerek. Performans sayacı nesnesinin adı: **Microsoft ATA Gateway**.

Dikkat edilmesi gereken ana ATA Gateway sayaçlarının listesi:

> [!div class="mx-tableFixed"]
|Sayaç|Description|Eşik|Sorun giderme|
|-----------|---------------|-------------|-------------------|
|Microsoft ATA Gateway\NetworkListener PEF Ayrıştırılan İletiler\Sn|ATA Gateway tarafından her saniyede işlenen trafik miktarı.|Eşik yok|ATA Gateway tarafından ayrıştırılmakta olan trafiğin miktarını anlamanıza yardımcı olur.|
|NetworkListener PEF Bırakılan Olaylar\Sn|ATA Gateway tarafından her saniyede bırakılan trafik miktarı.|Bu sayı her zaman sıfır olmalıdır (seyrek olarak bırakma artışı yaşanması kabul edilebilir).|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Yukarıdaki **ATA Bileşen İşlemi** bölümüne bakın.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|Microsoft ATA Gateway\NetworkListener ETW Bırakılan Olaylar\Sn|ATA Gateway tarafından her saniyede bırakılan trafik miktarı.|Bu sayı her zaman sıfır olmalıdır (seyrek olarak bırakma artışı yaşanması kabul edilebilir).|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Yukarıdaki **ATA Bileşen İşlemi** bölümüne bakın.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|Microsoft ATA Gateway\NetworkActivityTranslator İleti Verileri Sayısı Blok Boyutu|Ağ Etkinliklerine (NA) çeviri için kuyruğa alınan trafik miktarı.|Üst sınır-1’den az olmalıdır (varsayılan üst sınır: 100.000)|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Yukarıdaki **ATA Bileşen İşlemi** bölümüne bakın.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|Microsoft ATA Gateway\EntityResolver Etkinlik Blok Boyutu|Çözüm için kuyruğa alınan ağ etkinliklerinin (na) sayısı.|Üst sınır-1’den az olmalıdır (varsayılan üst sınır: 10.000)|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Yukarıdaki **ATA Bileşen İşlemi** bölümüne bakın.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|Microsoft ATA Gateway\EntitySender Varlık Toplu İşlemi Blok Boyutu|ATA Center’a gönderilmek üzere kuyruğa alınan Ağ Etkinliklerinin (NA) miktarı.|Üst sınır-1’den az olmalıdır (varsayılan üst sınır: 1.000.000)|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Yukarıdaki **ATA Bileşen İşlemi** bölümüne bakın.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|Microsoft ATA Gateway\EntitySender Toplu İşlem Gönderme Zamanı|Son yığını gönderme işleminin süresi.|Çoğu durumda 1000 milisaniyeden kısa olmalıdır.|ATA Gateway ile ATA Center arasında herhangi bir ağ sorunu olup olmadığını denetleyin.|

> [!NOTE]
> -   Süre gösteren sayaçlar milisaniye cinsindendir.
> -   Bu bazen büyük kullanılarak sayaçların tam listesi izlemek kullanışlı **rapor** grafik türü (örnek: tüm sayaçları gerçek zamanlı izleme)

## <a name="ata-lightweight-gateway-performance-counters"></a>ATA Lightweight Gateway performans sayaçları
Performans sayaçları, ATA’nın yüklü olduğu etki alanı denetleyicilerinde çok fazla kaynak çekmediğinden emin olmak için Lightweight Gateway’de kota yönetimi için kullanılabilir.
ATA’nın Lightweight Gateway’de uyguladığı kaynak sınırlamalarını ölçmek için şu sayaçları ekleyin.

Bu açarak yapılır **Performans İzleyicisi** ve ATA Lightweight Gateway için tüm sayaçlar eklenerek. Performans sayacı nesneleri adlarıdır: **Microsoft ATA Gateway** ve **Microsoft ATA Gateway güncelleştirici**.

> [!div class="mx-tableFixed"]
|Sayaç|Description|Eşik|Sorun giderme|
|-----------|---------------|-------------|-------------------|
|Microsoft ATA Gateway Updater\GatewayUpdaterResourceManager En Yüksek CPU Süresi %|Lightweight Gateway işleminin kullanabileceği en yüksek CPU süresi (yüzde cinsinden) miktarı. |Eşik yok. | Bu, etki alanı denetleyicisi kaynaklarının ATA Lightweight Gateway tarafından kullanılarak bitirilmesini engelleyen sınırlamadır. İşlemin belirli bir süre boyunca sık sık üst sınıra ulaştığını görüyorsanız (işlem sınıra ulaşır ve trafiği bırakmaya başlar) bu, etki alanı denetleyicisini çalıştıran sunucuya daha fazla kaynak eklemeniz gerektiği anlamına gelir.|
|Microsoft ATA Gateway Updater\GatewayUpdaterResourceManager İşlenen En Yüksek Bellek Boyutu|Lightweight Gateway işleminin kullanabileceği en yüksek işlenen bellek miktarı (bayt cinsinden).|Eşik yok. | Bu, etki alanı denetleyicisi kaynaklarının ATA Lightweight Gateway tarafından kullanılarak bitirilmesini engelleyen sınırlamadır. İşlemin belirli bir süre boyunca sık sık üst sınıra ulaştığını görüyorsanız (işlem sınıra ulaşır ve trafiği bırakmaya başlar) bu, etki alanı denetleyicisini çalıştıran sunucuya daha fazla kaynak eklemeniz gerektiği anlamına gelir.| 
|Microsoft ATA Gateway Updater\GatewayUpdaterResourceManager Çalışma Kümesi Sınırı Boyutu|Lightweight Gateway işleminin kullanabileceği en yüksek fiziksel bellek miktarı (bayt cinsinden).|Eşik yok. | Bu, etki alanı denetleyicisi kaynaklarının ATA Lightweight Gateway tarafından kullanılarak bitirilmesini engelleyen sınırlamadır. İşlemin belirli bir süre boyunca sık sık üst sınıra ulaştığını görüyorsanız (işlem sınıra ulaşır ve trafiği bırakmaya başlar) bu, etki alanı denetleyicisini çalıştıran sunucuya daha fazla kaynak eklemeniz gerektiği anlamına gelir.|



Gerçek kullanımınızı görmek için aşağıdaki sayaçlara bakın:


> [!div class="mx-tableFixed"]
|Sayaç|Description|Eşik|Sorun giderme|
|-----------|---------------|-------------|-------------------|
|İşlem(Microsoft.Tri.Gateway)\%İşlemci Zamanı|Lightweight Gateway işleminin gerçekte kullandığı CPU süresi (yüzde cinsinden) miktarı. |Eşik yok. | Bu sayacın sonuçlarını GatewayUpdaterResourceManager En Yüksek CPU Süresi % kısmında bulunan sınırla karşılaştırın. İşlemin belirli bir süre boyunca sık sık üst sınıra ulaştığını görüyorsanız (işlem sınıra ulaşır ve trafiği bırakmaya başlar) bu, Lightweight Gateway’e daha fazla kaynak ayırmanız gerektiği anlamına gelir.|
|İşlem(Microsoft.Tri.Gateway)\Özel Baytlar|Lightweight Gateway işleminin gerçekte kullandığı işlenen bellek miktarı (bayt cinsinden).|Eşik yok. | Bu sayacın sonuçlarını GatewayUpdaterResourceManager İşlenen En Yüksek Bellek Boyutu kısmında bulunan sınırla karşılaştırın. İşlemin belirli bir süre boyunca sık sık üst sınıra ulaştığını görüyorsanız (işlem sınıra ulaşır ve trafiği bırakmaya başlar) bu, Lightweight Gateway’e daha fazla kaynak ayırmanız gerektiği anlamına gelir.| 
|İşlem(Microsoft.Tri.Gateway)\Çalışma Kümesi|Lightweight Gateway işleminin gerçekte kullandığı fiziksel bellek miktarı (bayt cinsinden).|Eşik yok. |Bu sayacın sonuçlarını GatewayUpdaterResourceManager Kaydedilen Maksimum Bellek Boyutu kısmında bulunan sınırla karşılaştırın. İşlemin belirli bir süre boyunca sık sık üst sınıra ulaştığını görüyorsanız (işlem sınıra ulaşır ve trafiği bırakmaya başlar) bu, Lightweight Gateway’e daha fazla kaynak ayırmanız gerektiği anlamına gelir.|

## <a name="ata-center-performance-counters"></a>ATA Center performans sayaçları
ATA Center’ın performans sayaçlarını ekleyerek, ATA Center ile ilgili gerçek zamanlı performans durumunu gözlemleyebilirsiniz.

Bu açarak yapılır **Performans İzleyicisi** ve ATA Center için tüm sayaçlar eklenerek. Performans sayacı nesnesinin adı: **Microsoft ATA Center**.

Dikkat edilmesi gereken ana ATA Center sayaçlarının listesi:

> [!div class="mx-tableFixed"]
|Sayaç|Description|Eşik|Sorun giderme|
|-----------|---------------|-------------|-------------------|
|Microsoft ATA Center\EntityReceiver Varlık Yığın Blok Boyutu|ATA Center tarafından kuyruğa alınan varlık yığınlarının sayısı.|Üst sınır-1’den az olmalıdır (varsayılan üst sınır: 10.000)|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin.  Önceki başvuran **ATA bileşen işlemi**.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|Microsoft ATA Center\NetworkActivityProcessor Ağ Etkinliği Blok Boyutu|İşleme için kuyruğa alınan Ağ Etkinliklerinin (NA) sayısı.|Üst sınır-1’den az olmalıdır (varsayılan üst sınır: 50.000)|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Önceki başvuran **ATA bileşen işlemi**.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|Microsoft ATA Center\EntityProfiler Ağ Etkinliği Blok Boyutu|Profil oluşturma için kuyruğa alınan Ağ Etkinliklerinin (NA) sayısı.|Üst sınır-1’den az olmalıdır (varsayılan üst sınır: 10.000)|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Önceki başvuran **ATA bileşen işlemi**.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|Microsoft ATA Center\Database &#42; Blok Boyutu|Veritabanına yazılmak üzere kuyruğa alınan belirli bir türdeki Ağ Etkinliklerinin sayısı.|Üst sınır-1’den az olmalıdır (varsayılan üst sınır: 50.000)|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Önceki başvuran **ATA bileşen işlemi**.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|


> [!NOTE]
> -   Süre gösteren sayaçlar milisaniye cinsindendir.
> -   Bazen daha fazla olduğu için rapor grafik türü kullanılarak sayaçların tam listesi kullanışlı (örnek: tüm sayaçları gerçek zamanlı izleme).

## <a name="operating-system-counters"></a>İşletim sistemi sayaçları
Aşağıdaki tabloda, dikkat edilmesi gereken ana işletim sistemi sayaçları listelenmiştir:

> [!div class="mx-tableFixed"]
|Sayaç|Description|Eşik|Sorun giderme|
|-----------|---------------|-------------|-------------------|
|İşlemci(_Toplam)\% İşlemci Zamanı|İşlemcinin boş olmayan bir iş parçacığı çalıştırırken harcadığı geçen sürenin yüzdesi.|Ortalamada %80’den az|Gerekenden çok daha fazla işlemci zamanı alan bir işlem olup olmadığını denetleyin.<br /><br />Daha fazla işlemci ekleyin.<br /><br />Sunucu başına trafik miktarını azaltın.<br /><br />"İşlemci(_Toplam)\% İşlemci Zamanı" sayacı sanal sunucularda tam doğru olmayabilir; bu durumda işlemci gücündeki eksilmeyi "Sistem\İşlemci Kuyruğu Uzunluğu" sayacı aracılığıyla ölçmek daha doğru olur.|
|Sistem\Bağlam Değişimleri\sn|Tüm işlemcilerin bir iş parçacığından diğerine birleşik geçiş hızı.|5000’den az çekirdek (fiziksel çekirdekler)|Gerekenden çok daha fazla işlemci zamanı alan bir işlem olup olmadığını denetleyin.<br /><br />Daha fazla işlemci ekleyin.<br /><br />Sunucu başına trafik miktarını azaltın.<br /><br />"İşlemci(_Toplam)\% İşlemci Zamanı" sayacı sanal sunucularda tam doğru olmayabilir; bu durumda işlemci gücündeki eksilmeyi "Sistem\İşlemci Kuyruğu Uzunluğu" sayacı aracılığıyla ölçmek daha doğru olur.|
|Sistem\İşlemci Kuyruğu Uzunluğu|Yürütülmeye hazır olan ve zamanlanmayı bekleyen iş parçacıklarının sayısı.|Beşten küçük&#42;çekirdek (fiziksel çekirdekler)|Gerekenden çok daha fazla işlemci zamanı alan bir işlem olup olmadığını denetleyin.<br /><br />Daha fazla işlemci ekleyin.<br /><br />Sunucu başına trafik miktarını azaltın.<br /><br />"İşlemci(_Toplam)\% İşlemci Zamanı" sayacı sanal sunucularda tam doğru olmayabilir; bu durumda işlemci gücündeki eksilmeyi "Sistem\İşlemci Kuyruğu Uzunluğu" sayacı aracılığıyla ölçmek daha doğru olur.|
|Bellek\Kullanılabilir MBayt|Ayırma için kullanılabilen fiziksel bellek (RAM) miktarı.|En çok 512 olmalıdır|Gerekenden çok daha fazla fiziksel bellek alan bir işlem olup olmadığını denetleyin.<br /><br />Fiziksel bellek miktarını artırın.<br /><br />Sunucu başına trafik miktarını azaltın.|
|MantıksalDisk(&#42;)\Ort. Disk sn\Okuma|Diskten verileri okumak için ortalama gecikme süresi (örnek olarak veritabanı sürücüsünü seçmelisiniz).|10 milisaniyeden kısa olmalıdır.|Veritabanı sürücüsünü gerektiğinden fazla kullanan belirli bir işlem bulunup bulunmadığını denetleyin.<br /><br />Bu sürücünün 10 MS'den kısa gecikme yaparken geçerli iş yükü sunabilir varsa, depolama ekibinize/satıcınıza başvurun. Geçerli iş yükü, disk kullanım sayaçları aracılığıyla belirlenebilir.|
|MantıksalDisk(&#42;)\Ort. Disk sn\Yazma|Diske veri yazmak için ortalama gecikme süresi (örnek olarak veritabanı sürücüsünü seçmelisiniz).|10 milisaniyeden kısa olmalıdır.|Veritabanı sürücüsünü gerektiğinden fazla kullanan belirli bir işlem bulunup bulunmadığını denetleyin.<br /><br />Bu sürücünün 10 MS'den kısa gecikme yaparken geçerli iş yükü sunabilir yoksa, depolama team\vendor ile bakın. Geçerli iş yükü, disk kullanım sayaçları aracılığıyla belirlenebilir.|
|\LogicalDisk(&#42;)\Disk Okuma\sn|Diskte okuma işlemlerini gerçekleştirme hızı.|Eşik yok|Disk kullanım sayaçları, depolama gecikmesi sorunlarını giderirken fikir verebilir.|
|\LogicalDisk(&#42;)\Disk Okuma Bayt\sn|Diskten bir saniyede okunan bayt sayısı.|Eşik yok|Disk kullanım sayaçları, depolama gecikmesi sorunlarını giderirken fikir verebilir.|
|\LogicalDisk&#42;\Disk Yazma\sn|Diskte yazma işlemlerini gerçekleştirme hızı.|Eşik yok|Disk kullanım sayaçları (depolama gecikmesi sorunlarını giderirken fikir verebilir).|
|\LogicalDisk(&#42;)\Disk Yazma Bayt\sn|Diske bir saniyede yazılan bayt sayısı.|Eşik yok|Disk kullanım sayaçları, depolama gecikmesi sorunlarını giderirken fikir verebilir.|

## <a name="see-also"></a>Ayrıca bkz:
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
