---
# required metadata

title: ATA Kapasite Planlaması | Microsoft Advanced Threat Analytics
description: Ağınızı desteklemek için kaç ATA sunucusuna ihtiyacınız olacağını saptamanıza yardımcı olur
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 279d79f2-962c-4c6f-9702-29744a5d50e2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ATA Kapasite Planlaması
Bu konu, ağınızı desteklemek için kaç ATA sunucusuna ihtiyacınız olacağını saptamanıza yardımcı olur.

## ATA Center Boyutlandırması
Kullanıcı davranış analizi için ATA Center’a en az 30 günlük veri gerekir. Etki alanı denetleyicisi başına ATA veritabanına gereken disk alanı aşağıda tanımlanmıştır. Birden çok etki alanı denetleyiciniz varsa, ATA veritabanına gereken tüm alan miktarını hesaplamak için etki alanı denetleyicisi başına gereken disk alanlarını toplayın.

|Paket/saniye&#42;|CPU (çekirdekler&#42;&#42;)|Bellek (GB)|İşletim Sistemi Depolaması (GB)|Günlük veritabanı depolaması (GB)|Aylık veritabanı depolaması (GB)|IOPS&#42;&#42;&#42;|
|---------------------------|-------------------------|---------------|-------------------|---------------------------------|-----------------------------------|-----------------------------------|
|1.000|4|48|200|1,5|45|30 (100)
|10.000|4|48|200|15|450|200 (300)
|40.000|8|64|200|60|1.800|500 (1.000)
|100.000|12|96|200|150|4.500|1.000 (1.500)
|200.000|16|128|200|300|9,000|2.000 (2.500)
&#42;Tüm ATA Gateway’ler tarafından izlenen tüm etki alanı denetleyicilerinden bir saniyedeki paket sayısının toplam günlük ortalaması.

&#42;&#42;Bu fiziksel çekirdekleri içerir; hiper iş parçacıklı çekirdekleri içermez.

&#42;&#42;&#42;Ortalama sayılar (En yüksek sayılar)
> [!NOTE]
> -   ATA Center, tüm izlenen etki alanı denetleyicilerinden saniyede toplam en çok 200.000 çerçeveyi (FPS) işleyebilir.
> -   Büyük dağıtımlar için (saniyede yaklaşık 100.000 paketten başlayan), veritabanı günlüğünün veritabanından farklı bir riskte yer almasını zorunlu tutarız.
> -   Burada belirtilen depolama miktarları net değerlerdir, gelecekteki büyümeyi de hesaba katmalı ve üzerinde veritabanının bulunduğu diskte en az %20 boş alan bulunduğundan emin olmalısınız.
> -   Boş alanınız en az %20’ye veya 100 GB’a ulaşırsa, en eski 24 saatin verileri silinir. Bu işlem, yalnızca iki günlük veri kalana ya da boş alan %5 veya 50 GB’a inene kadar devam eder; bu noktaya ulaşıldığında veri koleksiyonu çalışmayı durdurur.
> -  Okuma ve yazma etkinlikleri için depolama gecikmesi 10 ms’nin altında olmalıdır.
> -  Okuma ve yazma etkinlikleri arasındaki oran, saniyede 100.000 paketin altında yaklaşık 1:3 ve saniyede 100.000 paketin üstünde 1:6’dır.

## ATA Gateway Boyutlandırması
ATA Gateway, izlenmekte olan etki alanı denetleyicilerinin ağ trafiği miktarına bağlı olarak, birden çok etki alanı denetleyicisinin izlenmesini destekleyebilir.

|Paket/saniye&#42;|CPU (çekirdekler&#42;&#42;)|Bellek (GB)|İşletim sistemi depolaması (GB)|
|---------------------------|-------------------------|---------------|-------------------|
|10.000|4|12|80|
|20,000|8|24|100|
|40.000|16|64|200|
&#42;Belirli bir ATA Gateway tarafından izlenen tüm etki alanı denetleyicilerinden bir saniyedeki paket sayısının toplamı.

&#42;Etki alanı denetleyicisi bağlantı noktası yansıtmalı trafiğinin toplam miktarı, ATA Gateway’deki yakalama NIC’in kapasitesini aşamaz.

&#42;&#42;Hiper iş parçacığı devre dışı bırakılmalıdır.

## Etki alanı denetleyicisi tahmini trafiği
Etki alanı denetleyicilerinizin saniyedeki ortalama paket sayısını bulmak için kullanabileceğiniz çeşitli araçlar vardır. Bu sayacı izleyen hiçbir aracınız yoksa, gerekli bilgileri toplamak için Performans İzleyicisi’ni kullanabilirsiniz.

Saniyedeki paket sayısını belirlemek için, her etki alanı denetleyicisinde aşağıdakileri yapın:

1.  Performans İzleyicisi'ni açın.

    ![Performans izleyicisi resmi](media/ATA-traffic-estimation-1.png)

2.  **Veri Toplayıcı Kümeleri**’ni genişletin..

    ![Veri toplayıcı kümelerinin resmi](media/ATA-traffic-estimation-2.png)

3.  **Kullanıcı Tanımlı**’ya sağ tıklayın ve **Yeni** &gt; **Veri Toplayıcı Kümesi**’ni seçin..

    ![Yeni veri toplayıcı kümesinin resmi](media/ATA-traffic-estimation-3.png)

4.  Toplayıcı kümesi için bir ad girin ve **El İle Oluştur (Gelişmiş)** öğesini seçin..

5.  **Hangi veri türlerini eklemek istersiniz?** alanında **Veri günlüklerini ve performans sayacını oluştur**’u seçin..

    ![Yeni veri toplayıcı kümesi için veri türünün resmi](media/ATA-traffic-estimation-5.png)

6.  **Hangi performans sayaçlarını günlüğe kaydetmek istersiniz?** alanında **Ekle**’ye tıklayın..

7.  **Ağ Bağdaştırıcısı**’nı genişletin, **Paket/sn**’yi seçin ve doğru örneği seçin. Emin değilseniz, **&lt;Tüm örnekler&gt;**’i seçebilir, ardından **Ekle**’ye ve **Tamam**’a tıklayabilirsiniz..

    > [!NOTE]
    > Bunu yapmak için, komut satırında `ipconfig /all` komutunu çalıştırarak bağdaştırıcının ve yapılandırmanın adını görüntüleyin.

    ![Performans sayaçlarını ekleme resmi](media/ATA-traffic-estimation-7.png)

8.  **Örnek aralığı** değerini **1 saniye** olarak değiştirin..

9. Verilerin kaydedilmesini istediğiniz konumunu ayarlayın.

10. **Veri toplayıcı kümesi oluştur**’un altında **Bu veri toplayıcı kümesini şimdi başlat**’ı seçin ve **Son**’a tıklayın..

    Şimdi yeni oluşturduğunuz veri toplayıcı kümesini, çalıştığını gösteren yeşil üçgenle birlikte görüyor olmalısınız.

11. 24 saat sonra, veri toplayıcı kümesine sağ tıklayıp **Durdur**’u seçerek veri toplayıcı kümesini durdurun.

    ![Veri toplayıcı kümesini durdurma resmi](media/ATA-traffic-estimation-12.png)

12. Dosya Gezgini’nde, .blg dosyasının kaydedildiği klasöre göz atın ve dosyayı çift tıklayarak Performans İzleyicisi’nde açın.

13. Paket/sn sayacını seçin, ortalama ve en yüksek değerleri kaydedin.

    ![Saniyedeki paket sayısı sayacının resmi](media/ATA-traffic-estimation-14.png)

## Ayrıca Bkz.
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA mimarisi](/advanced-threat-analytics/understand-explore/ata-architecture)
- [Destek için forumumuzu gözden geçirin!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=Apr16_HO4-->


