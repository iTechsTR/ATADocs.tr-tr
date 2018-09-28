---
title: Advanced Threat Analytics dağıtımınızı planlama | Microsoft Docs
description: Dağıtımınızı planlamanıza ve ağınızı desteklemek için kaç adet ATA sunucusu gerekeceğine karar vermenize yardımcı olur
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.service: ''
ms.prod: advanced-threat-analytics
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 7fd0ea627807b89a604ac32276bb43aa00262dd2
ms.sourcegitcommit: 1b23381ca4551a902f6343428d98f44480077d30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47403191"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="ata-capacity-planning"></a>ATA Kapasite Planlaması
Bu makale, ağınızı izlemek için kaç ATA sunucusuna ihtiyacınız olduğunu belirlemenize yardımcı olur. Yardımcı kaç ATA Gateway ve/veya ATA Lightweight Gateway hazır ve ATA Center ve ATA Gateway bileşenleri için sunucu kapasitesi şekil.

> [!NOTE] 
> Bu makalede açıklanan performans gereksinimleri karşılandığı sürece, ATA Center herhangi bir IaaS satıcısında dağıtılabilir.

## <a name="using-the-sizing-tool"></a>Boyutlandırma aracını kullanma
ATA dağıtımızın kapasitesini belirlemek için önerilen en kolay yol [ATA Boyutlandırma Aracı](http://aka.ms/atasizingtool)’nı kullanmaktır. ATA Boyutlandırma Aracı’nı çalıştırın ve Excel dosyasındaki sonuçlarda, ihtiyaç duyduğunuz ATA kapasitesini belirlemek için aşağıdaki alanları kullanın:

- ATA Center CPU ve Bellek: Sonuç dosyasındaki ATA Center tablosunda bulunan **Meşgul Paket/sn** alanını, [ATA Center tablosundaki](#ata-center-sizing) **SANİYE BAŞINA PAKET** alanıyla eşleştirin.

- ATA Center Depolama Alanı: Sonuç dosyasındaki ATA Center tablosunda bulunan **Ortalama Paket/sn** alanını, [ATA Center tablosundaki](#ata-center-sizing) **SANİYE BAŞINA PAKET** alanıyla eşleştirin.
- ATA Gateway: Sonuç dosyasındaki ATA Gateway tablosunda bulunan **Meşgul Paket/sn** bölümünü, [seçtiğiniz ağ geçidi türüne](#choosing-the-right-gateway-type-for-your-deployment) bağlı olarak [Ata Gateway tablosundaki](#ata-gateway-sizing) veya [ATA Lightweight Gateway tablosundaki](#ata-lightweight-gateway-sizing) **SANİYE BAŞINA PAKET** bölümüyle eşleştirin.


![Kapasite planlama aracı örneği](media/capacity tool.png)


> [!NOTE]
> Farklı ortamları değişir ve başlangıçta ATA dağıtma ve boyutlandırma Aracı'nı çalıştırdıktan sonra birden çok özel ve beklenmeyen bir ağ trafiği özelliklerine sahip olduğundan, ayarlamak ve dağıtımınız için kapasite ince gerekebilir.


Çeşitli nedenlerle ATA Boyutlandırma Aracını kullanamıyorsanız paket/sn sayaç bilgilerini tüm Etki Alanı Denetleyicilerinizden 24 saat boyunca düşük toplama aralığıyla (yaklaşık 5 saniye) el ile toplayın. Sonrasında, her Etki Alanı Denetleyicisi için günlük ortalamanızı ve en meşgul zaman aralığı (15 dakikalık) ortalamanızı hesaplamanız gerekir.
Aşağıdaki bölüm, bir Etki Alanı Denetleyicisi’nden paket/sn sayacı bilgilerini nasıl alabileceğinizi gösteren yönergeleri içerir.


> [!NOTE]
> Farklı ortamları değişir ve başlangıçta ATA dağıtma ve boyutlandırma Aracı'nı çalıştırdıktan sonra birden çok özel ve beklenmeyen bir ağ trafiği özelliklerine sahip olduğundan, ayarlamak ve dağıtımınız için kapasite ince gerekebilir.


### <a name="ata-center-sizing"></a>ATA Center Boyutlandırması
Kullanıcı davranış analizi için ATA Center’a en az 30 günlük veri gerekir.
 

|Tüm DC’lerden paket/saniye|CPU (çekirdekler&#42;)|Bellek (GB)|Günlük veritabanı depolaması (GB)|Aylık veritabanı depolaması (GB)|IOPS&#42;&#42;|
|---------------------------|-------------------------|-------------------|---------------------------------|-----------------------------------|-----------------------------------|
|1,000|2|32|0.3|9|30 (100)
|40,000|4|48|12|360|500 (750)
|200.000|8|64|60|1.800|1.000 (1.500)
|400.000|12|96|120|3.600|2.000 (2.500)
|750,000|24|112|225|6,750|2,500 (3,000)
|1,000,000|40|128|300|9,000|4.000 (5.000)

&#42;Bu fiziksel çekirdekleri içerir; hiper iş parçacıklı çekirdekleri içermez.

&#42;&#42;Ortalama sayılar (En yüksek sayılar)
> [!NOTE]
> -   ATA Center’ın izlenen tüm etki alanı denetleyicilerinden saniye başına işleyebileceği toplam miktar, en fazla 1 milyon pakettir. Bazı ortamlarda aynı ATA Center, 1 milyon yüksektir genel trafikle başa çıkabilir. Bu tür ortamlar konusunda yardım almak için askcesec@microsoft.com ile iletişime geçin.
> -   Boş alanınız en az 20 ulaşırsa % veya 200 GB, en eski veri koleksiyonu silinir. Bu düzey için veri toplama başarıyla azaltmak mümkün değilse bir uyarı günlüğe kaydedilir.  ATA %5 eşiğinin kadar çalışmaya devam eder veya 50 GB boş alan ulaşıldı.  Bu noktada, ATA veritabanını doldurma durdurur ve ek bir uyarı verilir.
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
> -   En az 5 GB alan gereklidir ve 10 GB önerilir, ATA ikili dosyaları için gereken alan dahil olmak üzere [ATA günlükleri](troubleshooting-ata-using-logs.md), ve [performans günlükleri](troubleshooting-ata-using-perf-counters.md).


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
> -   En az 5 GB alan gereklidir ve 10 GB önerilir, ATA ikili dosyaları için gereken alan dahil olmak üzere [ATA günlükleri](troubleshooting-ata-using-logs.md), ve [performans günlükleri](troubleshooting-ata-using-perf-counters.md).



## <a name="related-videos"></a>İlgili videolar
- [ATA Gateway türü sağ seçme](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA boyutlandırma aracı](http://aka.ms/atasizingtool)
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA mimarisi](ata-architecture.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
