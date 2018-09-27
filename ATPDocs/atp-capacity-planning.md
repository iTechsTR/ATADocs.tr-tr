---
title: Azure Gelişmiş tehdit Koruması Dağıtımınızı planlama | Microsoft Docs
description: Dağıtımınızı planlamanıza ve ağınızı desteklemek için kaç adet Azure ATP sunucusu gerekeceğine karar vermenize yardımcı olur
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/22/2018
ms.topic: conceptual
ms.service: azure-advanced-threat-protection
ms.prod: ''
ms.assetid: da0ee438-35f8-4097-b3a1-1354ad59eb32
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: e894422e7264650186c6f4eea28d5a9099ca7914
ms.sourcegitcommit: 56065ee43dac299203871cd6f025315520750b3b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47233907"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="azure-atp-capacity-planning"></a>Azure ATP kapasite planlaması
Bu makalede Azure ATP algılayıcı ve ihtiyacınız olan tek başına algılayıcı sayısını belirlemenize yardımcı olur.

> [!NOTE] 
> İki e-tablolar - boyutlandırma aracı sahip biri ATA, diğeri Azure ATP için. Doğru sayfasında olduğundan emin olun.

## <a name="using-the-sizing-tool"></a>Boyutlandırma aracını kullanma
Azure ATP dağıtımınızı kullanmaktır kapasitesini belirlemek için önerilen ve en kolay yolu [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool). Azure ATP boyutlandırma aracı çalıştırın ve Excel dosyasındaki sonuçlarda, CPU ve bellek belirlemek için aşağıdaki alanları algılayıcı tarafından kullanılan:

- Azure ATP algılayıcısını: eşleşen **meşgul Paket/sn** sonuçları dosyasında Azure ATP algılayıcısı tablosundaki **paket başına saniye** alanındaki [Azure ATP tek başına algılayıcı tablo](#azure-atp-sensor-sizing)veya [Azure ATP algılayıcısı tablo](#azure-atp-standalone-sensor-sizing)bağlı olarak [seçtiğiniz algılayıcı türü](#choosing-the-right-sensor-type-for-your-deployment).


![Kapasite planlama aracı örneği](media/capacity-tool.png)


El ile herhangi bir nedenden dolayı Azure ATP boyutlandırma aracını kullanamıyorsanız Paket/sn sayaç bilgilerinizi düşük toplama aralığıyla (yaklaşık 5 saniye) 24 saat boyunca tüm etki alanı denetleyicilerinizden toplayın. Sonrasında, her Etki Alanı Denetleyicisi için günlük ortalamanızı ve en meşgul zaman aralığı (15 dakikalık) ortalamanızı hesaplamanız gerekir.
Aşağıdaki bölüm, bir Etki Alanı Denetleyicisi’nden paket/sn sayacı bilgilerini nasıl alabileceğinizi gösteren yönergeleri içerir.

## Dağıtımınız için doğru algılayıcı türü seçme<a name="choosing-the-right-sensor-type-for-your-deployment"></a>
Bir Azure ATP dağıtımında herhangi bir birleşimini Azure ATP tek başına algılayıcı türleri desteklenir:

- Azure ATP tek başına algılayıcı
- Yalnızca Azure ATP algılayıcısı
- Her ikisinin birleşimi

Algılayıcı dağıtım türüne karar verirken aşağıdaki faydaları göz önünde bulundurun:

|algılayıcı türü|Yararları|Maliyet|Dağıtım topolojisi|Etki alanı denetleyicisi kullanımı|
|----|----|----|----|-----|
|Azure ATP tek başına algılayıcı|Dağıtım bant dışı saldırganların Azure ATP var olduğunu keşfetmesini zorlaştırır|Daha yüksek|Etki alanı denetleyicisinin yanı sıra yüklenir (bant dışı)|Saniyede en fazla 100.000 paketi destekler|
|Azure ATP algılayıcısı|Ayrılmış bir sunucu ve bağlantı noktası yansıtma yapılandırması gerektirmez|Daha düşük|Etki alanı denetleyicisine yüklenir|Saniyede en fazla 100.000 paketi destekler|

Dağıtmak için kaç tane Azure ATP tek başına algılayıcı karar verirken aşağıdaki noktaları dikkate.

-   **Active Directory ormanları ve etki alanları**<br>
    Azure ATP oluşturduğunuz her bir çalışma alanı için birden çok Active Directory ormanları içinde birden çok etki alanından trafiği izleyebilir. 

-   **Bağlantı Noktası Yansıtma**<br>
Bağlantı noktası yansıtmayla ilgili faktörler, veri merkezi veya şube site başına birden çok Azure ATP tek başına algılayıcı dağıtmanızı gerektirebilir.

-   **Kapasite**<br>
    Bir Azure ATP tek başına algılayıcı, izlenmekte olan etki alanı denetleyicilerinin ağ trafiği miktarına bağlı olarak birden çok etki alanı denetleyicisinin izlenmesini destekleyebilir. 


## Azure ATP algılayıcısını ve tek başına algılayıcı boyutlandırma <a name="sizing"></a>

Azure ATP algılayıcısını etki alanı denetleyicisinin oluşturduğu ağ trafiği miktarına bağlı olarak bir etki alanı denetleyicisinin izlenmesini destekleyebilir. Aşağıdaki tabloda tahmini bir değerdir, algılayıcı ayrıştıran son trafiği ve trafiğinin dağıtımını miktarına bağlıdır. 
> [!NOTE]
> Aşağıdaki CPU ve bellek kapasitesini algılayıcının kendi tüketim – etki alanı denetleyicisi kapasitesi ifade eder.

|Saniye başına paket *|CPU (çekirdekler)|Bellek (GB)|
|----|----|-----|
|0-1 k|0.25|2.50|
|5 1k - k|0.75|6.00|
|5k - 10k|1.00|6.50|
|20 10k - k|2.00|9,00|
|20 bin - 50 bin|3.50|9.50|
|50 bin - 75 bin |3.50|9.50|
|100 bin 75 - k|3.50 |9.50|

> [!NOTE]
> - Algılayıcı hizmetinin kullanacağı çekirdek toplam sayısı.<br>Hiper iş parçacıklı çekirdekleri ile çalışmıyor önerilir.
> - Algılayıcı hizmetinin kullanacağı bellek toplam miktarı.
> -   Etki alanı denetleyicisi tarafından Azure ATP algılayıcısını gereken kaynaklar yoksa etki alanı denetleyicisi performansı etkilenmez, ancak Azure ATP algılayıcısını beklendiği gibi çalışmayabilir.
> -   Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.
> -   En iyi performans için ayarlanmış **güç seçeneğini** Azure ATP algılayıcı için **yüksek performanslı**.
> -   En az 2 Çekirdek ve 6 GB alan gereklidir ve Azure ATP ikili dosyaları ve günlükleri için gereken alan dahil olmak üzere, 10 GB önerilir.


## <a name="domain-controller-traffic-estimation"></a>Etki alanı denetleyicisi tahmini trafiği

Etki alanı denetleyicilerinizin saniyedeki ortalama paket sayısını bulmak için kullanabileceğiniz çeşitli araçlar vardır. Bu sayacı izleyen hiçbir aracınız yoksa, gerekli bilgileri toplamak için Performans İzleyicisi’ni kullanabilirsiniz.

Paket/saniye oranını belirlemek için her etki alanı denetleyicisinde aşağıdakileri adımları yerine getirin:

1.  Performans İzleyicisi'ni açın.

    ![Performans izleyicisi resmi](media/atp-traffic-estimation-1.png)

2.  **Veri Toplayıcı Kümeleri**’ni genişletin.

    ![Veri toplayıcı kümelerinin resmi](media/atp-traffic-estimation-2.png)

3.  **Kullanıcı Tanımlı**’ya sağ tıklayın ve **Yeni** &gt; **Veri Toplayıcı Kümesi**’ni seçin.

    ![Yeni veri toplayıcı kümesinin resmi](media/atp-traffic-estimation-3.png)

4.  Toplayıcı kümesi için bir ad girin ve **El İle Oluştur (Gelişmiş)** öğesini seçin.

5.  **Hangi veri türlerini eklemek istersiniz?** alanında **Veri günlükleri ve Performans sayacını oluştur**’u seçin.

    ![Yeni veri toplayıcı kümesi için veri türünün resmi](media/atp-traffic-estimation-5.png)

6.  **Hangi performans sayaçlarını günlüğe kaydetmek istersiniz?** alanında **Ekle**’ye tıklayın.

7.  **Ağ Bağdaştırıcısı**’nı genişletin, **Paket/sn**’yi seçin ve doğru örneği seçin. Emin değilseniz, **&lt;Tüm örnekler&gt;**’i seçebilir, ardından **Ekle**’ye ve **Tamam**’a tıklayabilirsiniz.

    > [!NOTE]
    > Bunu bir komut satırında yapmak için `ipconfig /all` komutunu çalıştırarak bağdaştırıcının ve yapılandırmanın adını görüntüleyin.

    ![Performans sayaçlarını ekleme resmi](media/atp-traffic-estimation-7.png)

8.  Değişiklik **örnekleme aralığı** için **beş saniye**.

9. Verilerin kaydedilmesini istediğiniz konumunu ayarlayın.

10. Altında **veri toplayıcı kümesi oluştur**seçin **bu veri toplayıcı kümesini Şimdi Başlat**, tıklatıp **son**.

    Artık oluşturduğunuz veri toplayıcı kümesini ve kümenin çalıştığını gösteren yeşil üçgeni görebilirsiniz.

11. 24 saat sonra, veri toplayıcı kümesine sağ tıklayıp **Durdur**’u seçerek veri toplayıcı kümesini durdurun.

    ![Veri toplayıcı kümesini durdurma resmi](media/atp-traffic-estimation-12.png)

12. Dosya Gezgini’nde, .blg dosyasının kaydedildiği klasöre gözatın ve çift tıklayarak dosyayı Performans İzleyicisi’nde açın.

13. Paket/sn sayacını seçin, ortalama ve en yüksek değerleri kaydedin.

    ![Saniyedeki paket sayısı sayacının resmi](media/atp-traffic-estimation-14.png)



## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP mimarisi](atp-architecture.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
