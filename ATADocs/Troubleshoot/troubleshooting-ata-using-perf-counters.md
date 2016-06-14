---
# required metadata

title: Performans sayaçlarını kullanarak ATA sorunlarını giderme | Microsoft Advanced Threat Analytics
description: ATA’yla ilgili sorunları gidermek için performans sayaçlarını nasıl kullanabileceğiniz açıklanır
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: df162a62-f273-4465-9887-94271f5000d2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Performans sayaçlarını kullanarak ATA sorunlarını giderme
ATA performans sayaçları, ATA’nın her bileşeninin ne kadar iyi çalıştığı konusunda fikir sağlar. ATA’daki bileşenler verileri sıralı olarak işlediğinden, bir sorun olduğunda zincirleme tepki ortaya çıkar ve bu da trafiğin bırakılmasına neden olur. Sorunu çözmek için, hangi bileşende istenmeyen sonuç alındığını saptamanız ve sorunu zincirin başında çözmeniz gerekir.
İç ATA bileşenlerinin akışını anlamak için [ATA mimarisi](/advanced-threat-analytics/plan-design/ata-architecture) konusuna bakın.

**ATA bileşeni işlemi**:

1.  Bileşenlerden biri boyut üst sınırına ulaştığında, önceki bileşenin kendisine daha fazla varlık göndermesini engeller.

2.  Sonunda önceki bileşen **kendi** boyutunu artırmaya başlar ve bu durum kendisinden önceki bileşenin daha fazla varlık göndermesini engelleyene kadar devam eder.

3.  Bu durum geriye doğru ilk AğDinleyicisi bileşenine kadar devam eder ve o bileşen de artık varlıkları iletemediğinde trafiği bırakır.

4. Her bileşenin nasıl çalıştığını anlamak için, performans sayaçlarında bulunan verileri kullanın.

## ATA Gateway performans sayaçları

Bu bölümde, ATA Gateway’e yapılan her gönderme aynı zamanda ATA Lightweight Gateway’e de yapılmıştır.

ATA Gateway’in performans sayaçlarını ekleyerek, ATA Gateway ile ilgili gerçek zamanlı performans durumunu gözlemleyebilirsiniz.
Bu işlem, "Performans İzleyicisi" açılarak ve ATA Gateway için tüm sayaçlar eklenerek yapılır. Performans sayacı nesnesinin adı: "Microsoft ATA Gateway".

![ATA performans sayaçlarının resmi](media/ATA-performance-counters.png)

Dikkat edilmesi gereken ana ATA Gateway sayaçlarının listesi:

|Sayaç|Açıklama|Eşik|Sorun giderme|
|-----------|---------------|-------------|-------------------|
|AğDinleyicisi PEF Ayrıştırıcı İleti Sayısı/Sn|ATA Gateway tarafından her saniyede işlenen trafik miktarı.|Eşik yok|ATA Gateway tarafından ayrıştırılmakta olan trafiğin miktarını anlamanıza yardımcı olur.|
|AğDinleyicisi Bırakılan PEF Olay Sayısı/Sn|ATA Gateway tarafından her saniyede bırakılan trafik miktarı.|Bu sayı her zaman sıfır olmalıdır (seyrek olarak bırakma artışı yaşanması kabul edilebilir).|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Yukarıdaki **ATA Bileşen İşlemi** bölümüne bakın.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|AğDinleyicisi Bırakılan ETW Olay Sayısı/Sn|ATA Gateway tarafından her saniyede bırakılan trafik miktarı.|Bu sayı her zaman sıfır olmalıdır (seyrek olarak bırakma artışı yaşanması kabul edilebilir).|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Yukarıdaki **ATA Bileşen İşlemi** bölümüne bakın.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|AğEtkinliğiÇeviricisi İleti Veri # Blok Boyutu|Ağ Etkinliklerine (NA) çeviri için kuyruğa alınan trafik miktarı.|Üst sınır-1’den az olmalıdır (varsayılan üst sınır: 100.000)|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Yukarıdaki **ATA Bileşen İşlemi** bölümüne bakın.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|VarlıkÇözümleyicisi Etkinlik Blok Boyutu|Çözüm için kuyruğa alınan Ağ Etkinliklerinin (NA) miktarı.|Üst sınır-1’den az olmalıdır (varsayılan üst sınır: 10.000)|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Yukarıdaki **ATA Bileşen İşlemi** bölümüne bakın.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|VarlıkGöndericisi Varlık Yığın Blok Boyutu|ATA Center’a gönderilmek üzere kuyruğa alınan Ağ Etkinliklerinin (NA) miktarı.|Üst sınır-1’den az olmalıdır (varsayılan üst sınır: 1.000.000)|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Yukarıdaki **ATA Bileşen İşlemi** bölümüne bakın.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|VarlıkGöndericisi Yığın Gönderme Zamanı|Son yığını gönderme işleminin süresi.|Çoğu durumda 1000 milisaniyeden kısa olmalıdır.|ATA Gateway ile ATA Center arasında herhangi bir ağ sorunu olup olmadığını denetleyin.|

> [!NOTE]
> -   Süre gösteren sayaçlar milisaniye cinsindendir.
> -   Bazen "Rapor" grafik türü kullanılarak sayaçların tam listesi daha rahat izlenebilir (örnek: tüm sayaçları gerçek zamanlı izleme)

## ATA Center performans sayaçları
ATA Center’ın performans sayaçlarını ekleyerek, ATA Center ile ilgili gerçek zamanlı performans durumunu gözlemleyebilirsiniz.

Bu işlem, "Performans İzleyicisi" açılarak ve ATA Center için tüm sayaçlar eklenerek yapılır. Performans sayacı nesnesinin adı: "Microsoft ATA Center".

![ATA Center performans sayaçlarını ekleme](media/ATA-Gateway-perf-counters.png)

Dikkat edilmesi gereken ana ATA Center sayaçlarının listesi:

|Sayaç|Açıklama|Eşik|Sorun giderme|
|-----------|---------------|-------------|-------------------|
|VarlıkAlıcısı Varlık Yığın Blok Boyutu|ATA Center tarafından kuyruğa alınan varlık yığınlarının sayısı.|Üst sınır-1’den az olmalıdır (varsayılan üst sınır: 10.000)|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin.  Yukarıdaki **ATA Bileşen İşlemi** bölümüne bakın.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|AğEtkinliğiİşlemcisi Ağ Etkinliği Blok Boyutu|İşleme için kuyruğa alınan Ağ Etkinliklerinin (NA) sayısı.|Üst sınır-1’den az olmalıdır (varsayılan üst sınır: 50.000)|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Yukarıdaki **ATA Bileşen İşlemi** bölümüne bakın.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|VarlıkProfiliOluşturucu Ağ Etkinliği Blok Boyutu|Profil oluşturma için kuyruğa alınan Ağ Etkinliklerinin (NA) sayısı.|Üst sınır-1’den az olmalıdır (varsayılan üst sınır: 10.000)|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Yukarıdaki **ATA Bileşen İşlemi** bölümüne bakın.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|
|CenterVeritabanı &#42; Blok Boyutu|Veritabanına yazılmak üzere kuyruğa alınan belirli bir türdeki Ağ Etkinliklerinin sayısı.|Üst sınır-1’den az olmalıdır (varsayılan üst sınır: 50.000)|Boyut üst sınırına ulaşmış olan ve AğDinleyicisi’ne gelene kadar tüm önceki bileşenleri engelleyen bir bileşen olup olmadığını denetleyin. Yukarıdaki **ATA Bileşen İşlemi** bölümüne bakın.<br /><br />CPU veya bellekle ilgili sorun olmadığından emin olun.|


> [!NOTE]
> -   Süre gösteren sayaçlar milisaniye cinsindendir.
> -   Bazen Rapor grafik türü kullanılarak sayaçların tam listesi daha rahat izlenebilir (örnek: tüm sayaçları gerçek zamanlı izleme)

## İşletim sistemi sayaçları
Aşağıda, dikkat edilmesi gereken ana işletim sistemi sayaçları listelenmiştir:

|Sayaç|Açıklama|Eşik|Sorun giderme|
|-----------|---------------|-------------|-------------------|
|İşlemci(_Toplam)\% İşlemci Zamanı|İşlemcinin boş olmayan bir iş parçacığı çalıştırırken harcadığı geçen sürenin yüzdesi.|Ortalamada %80’den az|Gerekenden çok daha fazla işlemci zamanı alan bir işlem olup olmadığını denetleyin.<br /><br />Daha fazla işlemci ekleyin.<br /><br />Sunucu başına trafik miktarını azaltın.<br /><br />"İşlemci(_Toplam)\% İşlemci Zamanı" sayacı sanal sunucularda tam doğru olmayabilir; bu durumda işlemci gücündeki eksilmeyi "Sistem\İşlemci Kuyruğu Uzunluğu" sayacı aracılığıyla ölçmek daha doğru olur.|
|Sistem\Bağlam Geçişi/sn|Tüm işlemcilerin bir iş parçacığından diğerine birleşik geçiş hızı.|5000’den az çekirdek (fiziksel çekirdekler)|Gerekenden çok daha fazla işlemci zamanı alan bir işlem olup olmadığını denetleyin.<br /><br />Daha fazla işlemci ekleyin.<br /><br />Sunucu başına trafik miktarını azaltın.<br /><br />"İşlemci(_Toplam)\% İşlemci Zamanı" sayacı sanal sunucularda tam doğru olmayabilir; bu durumda işlemci gücündeki eksilmeyi "Sistem\İşlemci Kuyruğu Uzunluğu" sayacı aracılığıyla ölçmek daha doğru olur.|
|Sistem\İşlemci Kuyruğu Uzunluğu|Yürütülmeye hazır olan ve zamanlanmayı bekleyen iş parçacıklarının sayısı.|5’ten az çekirdek (fiziksel çekirdekler)|Gerekenden çok daha fazla işlemci zamanı alan bir işlem olup olmadığını denetleyin.<br /><br />Daha fazla işlemci ekleyin.<br /><br />Sunucu başına trafik miktarını azaltın.<br /><br />"İşlemci(_Toplam)\% İşlemci Zamanı" sayacı sanal sunucularda tam doğru olmayabilir; bu durumda işlemci gücündeki eksilmeyi "Sistem\İşlemci Kuyruğu Uzunluğu" sayacı aracılığıyla ölçmek daha doğru olur.|
|Bellek\Kullanılabilir MBayt|Ayırma için kullanılabilen fiziksel bellek (RAM) miktarı.|512’den fazla olmalıdır|Gerekenden çok daha fazla fiziksel bellek alan bir işlem olup olmadığını denetleyin.<br /><br />Fiziksel bellek miktarını artırın.<br /><br />Sunucu başına trafik miktarını azaltın.|
|MantıksalDisk(&#42;)\Ort. Disk sn/Okuma|Diskten verileri okumak için ortalama gecikme süresi (örnek olarak veritabanı sürücüsünü seçmelisiniz).|10 milisaniyeden kısa olmalıdır.|Veritabanı sürücüsünü gerektiğinden fazla kullanan belirli bir işlem bulunup bulunmadığını denetleyin.<br /><br />Bu sürücünün 10 ms’den daha kısa bir gecikme süresiyle geçerli iş yükünü sağlayıp sağlayamayacağını öğrenmek için depolama ekibinize/satıcınıza danışın. Geçerli iş yükü, disk kullanım sayaçları aracılığıyla belirlenebilir.|
|MantıksalDisk(&#42;)\Ort. Disk sn/Yazma|Diske veri yazmak için ortalama gecikme süresi (örnek olarak veritabanı sürücüsünü seçmelisiniz).|10 milisaniyeden kısa olmalıdır.|Veritabanı sürücüsünü gerektiğinden fazla kullanan belirli bir işlem bulunup bulunmadığını denetleyin.<br /><br />Bu sürücünün 10 ms’den daha kısa bir gecikme süresiyle geçerli iş yükünü sağlayıp sağlayamayacağını öğrenmek için depolama ekibinize/satıcınıza danışın. Geçerli iş yükü, disk kullanım sayaçları aracılığıyla belirlenebilir.|
|\MantıksalDisk(&#42;)\Disk Okuma/sn|Diskte okuma işlemlerini gerçekleştirme hızı.|Eşik yok|Disk kullanım sayaçları, depolama gecikmesi sorunlarını giderirken fikir verebilir.|
|\MantıksalDisk(&#42;)\Disk Okuma Bayt/sn|Diskten bir saniyede okunan bayt sayısı.|Eşik yok|Disk kullanım sayaçları, depolama gecikmesi sorunlarını giderirken fikir verebilir.|
|\MantıksalDisk(&#42;)\Disk Yazma/sn|Diskte yazma işlemlerini gerçekleştirme hızı.|Eşik yok|Disk kullanım sayaçları (depolama gecikmesi sorunlarını giderirken fikir verebilir).|
|\MantıksalDisk(&#42;)\Disk Yazma Bayt/sn|Diske bir saniyede yazılan bayt sayısı.|Eşik yok|Disk kullanım sayaçları, depolama gecikmesi sorunlarını giderirken fikir verebilir.|

## Ayrıca Bkz.
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [ATA kapasite planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [Olay koleksiyonunu yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [Windows olay iletme özelliğini yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=May16_HO3-->


