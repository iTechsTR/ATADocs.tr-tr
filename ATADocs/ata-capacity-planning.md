---
title: "Advanced Threat Analytics dağıtımınızı planlama | Microsoft Docs"
description: "Dağıtımınızı planlamanıza ve ağınızı desteklemek için kaç adet ATA sunucusu gerekeceğine karar vermenize yardımcı olur"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/7/2017
ms.topic: get-started-article
ms.service: advanced-threat-analytics
ms.prod: 
ms.assetid: 279d79f2-962c-4c6f-9702-29744a5d50e2
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: a0cc958cd7c802d02c96b6d7d3bc7e7180bd3d95
ms.sourcegitcommit: 4d2ac5b02c682840703edb0661be09055d57d728
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="ata-capacity-planning"></a>ATA Kapasite Planlaması
Bu makalede izlemesi için kaç ATA sunucusuna ihtiyacınız belirlemenize yardımcı olur. Yardımcı kaç ATA Gateway ve/veya ATA Lightweight Gateway gereksinimini ve ATA Center ve ATA Gateway için sunucu kapasitesini şekil.

> [!NOTE] 
> Bu makalede açıklanan performans gereksinimleri karşılandığı sürece, ATA Center herhangi bir IaaS satıcısında dağıtılabilir.

##<a name="using-the-sizing-tool"></a>Boyutlandırma aracını kullanma
ATA dağıtımızın kapasitesini belirlemek için önerilen en kolay yol [ATA Boyutlandırma Aracı](http://aka.ms/atasizingtool)’nı kullanmaktır. ATA Boyutlandırma Aracı’nı çalıştırın ve Excel dosyasındaki sonuçlarda, ihtiyaç duyduğunuz ATA kapasitesini belirlemek için aşağıdaki alanları kullanın:

- ATA Center CPU ve Bellek: Sonuç dosyasındaki ATA Center tablosunda bulunan **Meşgul Paket/sn** alanını, [ATA Center tablosundaki](#ata-center-sizing) **SANİYE BAŞINA PAKET** alanıyla eşleştirin.

- ATA Center Depolama Alanı: Sonuç dosyasındaki ATA Center tablosunda bulunan **Ortalama Paket/sn** alanını, [ATA Center tablosundaki](#ata-center-sizing) **SANİYE BAŞINA PAKET** alanıyla eşleştirin.
- ATA Gateway: Sonuç dosyasındaki ATA Gateway tablosunda bulunan **Meşgul Paket/sn** bölümünü, [seçtiğiniz ağ geçidi türüne](#choosing-the-right-gateway-type-for-your-deployment) bağlı olarak [Ata Gateway tablosundaki](#ata-gateway-sizing) veya [ATA Lightweight Gateway tablosundaki](#ata-lightweight-gateway-sizing) **SANİYE BAŞINA PAKET** bölümüyle eşleştirin.


![Kapasite planlama aracı örneği](media/capacity tool.png)



Çeşitli nedenlerle ATA Boyutlandırma Aracını kullanamıyorsanız paket/sn sayaç bilgilerini tüm Etki Alanı Denetleyicilerinizden 24 saat boyunca düşük toplama aralığıyla (yaklaşık 5 saniye) el ile toplayın. Sonrasında, her Etki Alanı Denetleyicisi için günlük ortalamanızı ve en meşgul zaman aralığı (15 dakikalık) ortalamanızı hesaplamanız gerekir.
Aşağıdaki bölüm, bir Etki Alanı Denetleyicisi’nden paket/sn sayacı bilgilerini nasıl alabileceğinizi gösteren yönergeleri içerir.



### <a name="ata-center-sizing"></a>ATA Center Boyutlandırması
Kullanıcı davranış analizi için ATA Center’a en az 30 günlük veri gerekir.
 

|Tüm DC’lerden paket/saniye|CPU (çekirdekler&#42;)|Bellek (GB)|Günlük veritabanı depolaması (GB)|Aylık veritabanı depolaması (GB)|IOPS&#42;&#42;|
|---------------------------|-------------------------|-------------------|---------------------------------|-----------------------------------|-----------------------------------|
|1,000|2|32|0.3|9|30 (100)
|40.000|4|48|12|360|500 (750)
|200.000|8|64|60|1.800|1.000 (1.500)
|400.000|12|96|120|3.600|2.000 (2.500)
|750,000|24|112|225|6,750|2,500 (3,000)
|1,000,000|40|128|300|9,000|4.000 (5.000)

&#42;Bu fiziksel çekirdekleri içerir; hiper iş parçacıklı çekirdekleri içermez.

&#42;&#42;Ortalama sayılar (En yüksek sayılar)
> [!NOTE]
> -   ATA Center’ın izlenen tüm etki alanı denetleyicilerinden saniye başına işleyebileceği toplam miktar, en fazla 1 milyon pakettir. Bazı ortamlarda, aynı ATA Center 1 M yüksektir genel trafiği işleyebilir. Bu tür ortamlar konusunda yardım almak için askcesec@microsoft.com ile iletişime geçin.
> -   Burada belirtilen depolama alanı miktarları net değerlerdir. Her zaman gelecekteki büyümeyi de hesaba katmalı ve veritabanının bulunduğu diskte en az %20 boş alan bulunduğundan emin olmalısınız.
> -   Boş alanınız en az 20 ulaşırsa % ya da 200 GB, eski veri koleksiyonu silinir. Bu silme işlemi, boş alan %5 veya 50 GB’a inene kadar devam eder; bu noktaya ulaşıldığında ise veri koleksiyonu çalışmayı durdurur.
> - Bu makalede açıklanan performans gereksinimleri karşılandığı sürece, ATA Center’ın herhangi bir IaaS satıcısında dağıtılması mümkündür.
> -   Okuma ve yazma etkinlikleri için depolama gecikmesi 10 ms’nin altında olmalıdır.
> -   Okuma ve yazma etkinlikleri arasındaki oran, saniyede 100.000 paketin altında yaklaşık 1:3 ve saniyede 100.000 paketin üstünde 1:6’dır.
> -   Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.
> -   En iyi performans için, ATA Center’ın **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.<br>
> -   Fiziksel bir sunucuda çalışırken, ATA veritabanı için BIOS’ta Tekdüzen olmayan bellek erişimini (NUMA) **devre dışı bırakmanız** gerekir. Sisteminizde NUMA, Düğüm Araya Ekleme (Node Interleaving) olarak geçiyor olabilir ve bu durumda NUMA’yı devre dışı bırakmak için Düğüm Araya Ekleme’yi **etkinleştirmeniz** gerekecektir. Daha fazla bilgi için BIOS belgelerinize bakın. ATA Center bir sanal sunucuda çalışırken bu durum geçerli değildir.


## <a name="choosing-the-right-gateway-type-for-your-deployment"></a>Dağıtımınız için doğru ağ geçidi türünü seçme
ATA dağıtımında, ATA Gateway türlerinin tüm bileşimleri desteklenir:

- Yalnızca ATA Gateway’ler
- Yalnızca ATA Lightweight Gateway’ler
- Her ikisinin birleşimi

Ağ Geçidi dağıtım türüne karar verirken aşağıdaki faydaları göz önünde bulundurun:

|Ağ Geçidi türü|Yararları|Maliyet|Dağıtım topolojisi|Etki alanı denetleyicisi kullanımı|
|----|----|----|----|-----|
|ATA Gateway|Bant dışı dağıtım, saldırganların ATA’nın var olduğunu keşfetmesini zorlaştırır|Daha yüksek|Etki alanı denetleyicisinin yanı sıra yüklenir (bant dışı)|Saniyede en çok 50.000 paketi destekler|
|ATA Lightweight Gateway|Ayrılmış bir sunucu ve bağlantı noktası yansıtma yapılandırması gerektirmez|Daha düşük|Etki alanı denetleyicisine yüklenir|Saniyede en çok 10.000 paketi destekler|

Aşağıda, etki alanı denetleyicilerinin ATA Lightweight Gateway kapsamında olmasının gerektiği örnek senaryolar verilmiştir:


- Şube yerleri

- Bulutta dağıtılan sanam etki alanı denetleyicileri (IaaS)


Aşağıda, etki alanı denetleyicilerinin ATA Gateway kapsamında olmasının gerektiği örnek senaryolar verilmiştir:


- Yönetim veri merkezleri (saniyedeki paket sayısı 10.000’i aşan etki alanı denetleyicilerine sahip)


### <a name="ata-lightweight-gateway-sizing"></a>ATA Lightweight Gateway Boyutu

Bir ATA Lightweight Gateway, etki alanı denetleyicisinin oluşturduğu ağ trafiği miktarına bağlı olarak bir etki alanı denetleyicisinin izlenmesini destekleyebilir. 


|Paket/saniye&#42;|CPU (çekirdekler&#42;&#42;)|Bellek (GB)&#42;&#42;&#42;|
|---------------------------|-------------------------|---------------|
|1.000|2|6|
|5,000|6|16|
    |10.000|10|24|

&#42;Belirli bir ATA Lightweight Gateway tarafından izlenen etki alanı denetleyicilerinde bir saniyedeki paket sayısının toplamı.

&#42;&#42;Bu etki alanı denetleyicisinin yüklediği toplam hiper iş parçacıklı olmayan çekirdek sayısı.<br>Hiper iş parçacığı oluşturma ATA Lightweight Gateway için kabul edilebilir olmakla birlikte, kapasite planlaması yaparken hiper iş parçacıklı çekirdekleri değil gerçek çekirdekleri saymanız gerekir.

&#42;&#42;&#42;Bu etki alanı denetleyicisinde takılı belleğin toplam miktarı.

> [!NOTE]   
> -   Etki alanı denetleyicisinde, ATA Lightweight Gateway için gereken kaynaklar yoksa etki alanı denetleyicisi performansı bundan etkilenmez ancak ATA Lightweight Gateway gerektiği gibi çalışmayabilir.
> -   Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.
> -   En iyi performans için, ATA Lightweight Gateway’in **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.
> -   En az 5 GB alanı gereklidir ve 10 GB önerilir, ATA ikili dosyaları için gerekli alanı dahil olmak üzere [ATA günlüklerini](troubleshooting-ata-using-logs.md), ve [performans günlükleri](troubleshooting-ata-using-perf-counters.md).


### <a name="ata-gateway-sizing"></a>ATA Gateway Boyutlandırması

Kaç adet ATA Gateway dağıtımı yapacağınıza karar verirken aşağıdakileri dikkate alın.

-   **Active Directory ormanları ve etki alanları**<br>
    ATA tek bir Active Directory ormanındaki birden çok etki alanından trafiği izleyebilir. Birden çok Active Directory ormanını izlemek için ayrı ATA dağıtımları gerekir. Farklı ormanlardaki etki alanı denetleyicilerinin ağ trafiğini izlemek için tek bir ATA dağıtımı yapılandırmayın.

-   **Bağlantı Noktası Yansıtma**<br>
Bağlantı noktası yansıtmayla ilgili önemli noktalar, her bir veri merkezi veya şube için birden fazla ATA Gateway bileşeni yapılandırmanızı gerektirebilir.

-   **Kapasite**<br>
    ATA Gateway, izlenmekte olan etki alanı denetleyicilerinin ağ trafiği miktarına bağlı olarak, birden çok etki alanı denetleyicisinin izlenmesini destekleyebilir. 
<br>



|Paket/saniye&#42;|CPU (çekirdekler&#42;&#42;)|Bellek (GB)|
|---------------------------|-------------------------|---------------|
|1.000|1|6|
|5,000|2|10|
|10.000|3|12|
|20,000|6|24|
|50.000|16|48|
&#42;Günün en yoğun saatinde belirli bir ATA Gateway tarafından izlenen tüm etki alanı denetleyicilerinden bir saniyedeki ortalama paket sayısının toplamı.

&#42;Etki alanı denetleyicisi bağlantı noktası yansıtmalı trafiğinin toplam miktarı, ATA Gateway’deki yakalama NIC’in kapasitesini aşamaz.

&#42;&#42;Hiper iş parçacığı devre dışı bırakılmalıdır.

> [!NOTE] 
> -   Dinamik bellek desteklenmez.
> -   En iyi performans için, ATA Gateway’in **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.
> -   En az 5 GB alanı gereklidir ve 10 GB önerilir, ATA ikili dosyaları için gerekli alanı dahil olmak üzere [ATA günlüklerini](troubleshooting-ata-using-logs.md), ve [performans günlükleri](troubleshooting-ata-using-perf-counters.md).


## <a name="domain-controller-traffic-estimation"></a>Etki alanı denetleyicisi tahmini trafiği
Etki alanı denetleyicilerinizin saniyedeki ortalama paket sayısını bulmak için kullanabileceğiniz çeşitli araçlar vardır. Bu sayacı izleyen hiçbir aracınız yoksa, gerekli bilgileri toplamak için Performans İzleyicisi’ni kullanabilirsiniz.

Paket/saniye oranını belirlemek için her etki alanı denetleyicisinde aşağıdakileri adımları yerine getirin:

1.  Performans İzleyicisi'ni açın.

    ![Performans izleyicisi resmi](media/ATA-traffic-estimation-1.png)

2.  **Veri Toplayıcı Kümeleri**’ni genişletin.

    ![Veri toplayıcı kümelerinin resmi](media/ATA-traffic-estimation-2.png)

3.  **Kullanıcı Tanımlı**’ya sağ tıklayın ve **Yeni** &gt; **Veri Toplayıcı Kümesi**’ni seçin.

    ![Yeni veri toplayıcı kümesinin resmi](media/ATA-traffic-estimation-3.png)

4.  Toplayıcı kümesi için bir ad girin ve **El İle Oluştur (Gelişmiş)** öğesini seçin.

5.  **Hangi veri türlerini eklemek istersiniz?** alanında **Veri günlükleri ve Performans sayacını oluştur**’u seçin.

    ![Yeni veri toplayıcı kümesi için veri türünün resmi](media/ATA-traffic-estimation-5.png)

6.  **Hangi performans sayaçlarını günlüğe kaydetmek istersiniz?** alanında **Ekle**’ye tıklayın.

7.  **Ağ Bağdaştırıcısı**’nı genişletin, **Paket/sn**’yi seçin ve doğru örneği seçin. Emin değilseniz, **&lt;Tüm örnekler&gt;**’i seçebilir, ardından **Ekle**’ye ve **Tamam**’a tıklayabilirsiniz.

    > [!NOTE]
    > Bunu bir komut satırında yapmak için `ipconfig /all` komutunu çalıştırarak bağdaştırıcının ve yapılandırmanın adını görüntüleyin.

    ![Performans sayaçlarını ekleme resmi](media/ATA-traffic-estimation-7.png)

8.  **Örnek aralığı** değerini **1 saniye** olarak değiştirin.

9. Verilerin kaydedilmesini istediğiniz konumunu ayarlayın.

10. Altında **veri toplayıcı kümesi oluştur**seçin **bu veri toplayıcı kümesini Şimdi Başlat**, tıklatıp **son**.

    Artık oluşturduğunuz veri toplayıcı kümesini ve kümenin çalıştığını gösteren yeşil üçgeni görebilirsiniz.

11. 24 saat sonra, veri toplayıcı kümesine sağ tıklayıp **Durdur**’u seçerek veri toplayıcı kümesini durdurun.

    ![Veri toplayıcı kümesini durdurma resmi](media/ATA-traffic-estimation-12.png)

12. Dosya Gezgini’nde, .blg dosyasının kaydedildiği klasöre gözatın ve çift tıklayarak dosyayı Performans İzleyicisi’nde açın.

13. Paket/sn sayacını seçin, ortalama ve en yüksek değerleri kaydedin.

    ![Saniyedeki paket sayısı sayacının resmi](media/ATA-traffic-estimation-14.png)


## <a name="related-videos"></a>İlgili videolar
- [ATA Gateway türü sağ seçme](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA boyutlandırma aracı](http://aka.ms/atasizingtool)
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA mimarisi](ata-architecture.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
