---
title: Advanced Threat Analytics mimarisi | Microsoft Docs
description: "Microsoft Advance Threat Analytics’in (ATA) mimarisini açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 892b16d2-58a6-49f9-8693-1e5f69d8299c
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 489d85e7e8250dffe8d40225b31ed308a9a79969
ms.sourcegitcommit: 49e892a82275efa5146998764e850959f20d3216
translationtype: HT
---
*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*




# <a name="ata-architecture"></a>ATA Mimarisi
Advanced Threat Analytics mimarisi bu diyagramda ayrıntılı olarak açıklanmıştır:

![ATA mimarisi topoloji diyagramı](media/ATA-architecture-topology.jpg)

ATA, fiziksel veya sanal anahtarlar kullanan bir ATA Gateway bileşenine bağlantı noktası yansıtma kullanarak veya ATA Lightweight Gateway’i doğrudan etki alanı denetleyicilerinizde dağıtarak (bu şekilde bağlantı noktası yansıtmaya gerek kalmaz) etki alanı denetleyicisi ağ trafiğinizi izler. Ayrıca, ATA doğrudan etki alanı denetleyicilerinizden veya bir SIEM sunucusundan iletilen Windows olaylarını da kullanabilir ve verilerde saldırı ve tehdit analizi yapabilir.
Bu bölümde, ağ akışı ve olay yakalama açıklanmıştır ve ATA’nın şu temel bileşenlerinin işlevleri ayrıntılı açıklanmıştır: ATA Gateway, ATA Lightweight Gateway (ATA Gateway ile aynı çekirdek işlevlere sahiptir) ve ATA Center.


![ATA trafik akışı diyagramı](media/ATA-traffic-flow.jpg)

## <a name="ata-components"></a>ATA Bileşenleri
ATA şunlardan oluşur:

-   **ATA Center** <br>
ATA dağıttığınız tüm ATA Gateway bileşenlerinden ve/veya ATA Lightweight Gateway bileşenlerinden veri alır.
-   **ATA Gateway**<br>
ATA Gateway, bağlantı noktası yansıtmayı ya da ağ TAP’ı kullanarak etki alanı denetleyicilerinizden gelen trafiği izleyen ayrılmış bir sunucuya yüklenir.
-   **ATA Lightweight Gateway**<br>
ATA Lightweight Gateway doğrudan etki alanı denetleyicilerinize yüklenir ve ayrılmış bir sunucuya veya bağlantı noktası yansıtmaya gerek olmadan bunların trafiğini doğrudan izler. Bu, ATA Gateway’e bir alternatiftir.

Bir ATA dağıtımı tüm ATA Gateway bileşenlerine, tüm ATA Lightweight Gateway bileşenlerine veya ATA Gateway ve ATA Lightweight Gateway bileşenlerinin bir birleşimine bağlı olan tek bir ATA Center’dan oluşabilir.


## <a name="deployment-options"></a>Dağıtım seçenekleri
Aşağıdaki ağ geçitlerinin birleşimini kullanarak ATA dağıtabilirsiniz:

-    **Yalnızca ATA Gateway bileşenleri kullanma** <br>
ATA dağıtımınız herhangi bir ATA Lightweight Gateway bileşeni olmadan yalnızca ATA Gateway bileşenleri içeriyorsa, tüm etki alanı denetleyicilerinin bir ATA Gateway bileşenine bağlantı noktası yansıtmaya olanak verecek şekilde yapılandırılması veya ağ TAP’ları bulunması gerekir.
-    **Yalnızca ATA Lightweight Gateway bileşenleri kullanma**<br>
ATA dağıtımınız yalnızca ATA Lightweight Gateway bileşenleri içeriyorsa, ATA Lightweight Gateway bileşenleri her bir etki alanı denetleyicisinde dağıtılır ve ek sunucu veya bağlantı noktası yansıtma yapılandırması gerekmez.
-    **Hem ATA Gateway hem de ATA Lightweight Gateway bileşenleri kullanma**<br>
ATA dağıtımınız hem ATA Gateway bileşenleri hem de ATA Lightweight Gateway bileşenleri içeriyorsa, bazı etki alanı denetleyicilerinize ATA Lightweight Gateway yüklenirken (örneğin, şubelerinizdeki tüm etki alanı denetleyicileri), diğer etki alanı denetleyicileri ATA Gateway bileşenleri tarafından izlenir (örneğin, ana veri merkezlerinizdeki daha büyük etki alanı denetleyicileri).

3 senaryonun hepsinde, tüm ağ geçitleri verilerini ATA Center’a gönderir.




## <a name="ata-center"></a>ATA Center
**ATA Center** aşağıdaki işlevleri gerçekleştirir:

-   ATA Gateway ve ATA Lightweight Gateway yapılandırma ayarlarını yönetir

-   ATA Gateway bileşenlerinden ve ATA Lightweight Gateway bileşenlerinden veri alır 

-   Kuşkulu etkinlikleri algılar

-   Olağan dışı davranışları algılamak için ATA davranışsal makine öğrenme algoritmalarını çalıştırır

-   Saldırı sonlandırma zincirine dayalı olarak gelişmiş saldırıları algılamak için çeşitli belirleyici algoritmaları çalıştırır

-   ATA Konsolu’nu çalıştırır

-   İsteğe bağlı: ATA Center, kuşkulu bir etkinlik algılandığında e-posta ve olay gönderecek şekilde yapılandırılabilir.

ATA Center ağınız hakkında bilgi sahibi olarak anormallikleri algılayabilmek ve kuşkulu etkinliklerde sizi uyarabilmek için, ATA Gateway ve ATA Lightweight Gateway’den ayrıştırılmış trafiği alır, profil oluşturma işlemini yapar, belirlenimci algılama çalıştırır, sonra da makine öğrenme ve davranış algoritmalarını çalıştırır.

|||
|-|-|
|Varlık Alıcısı|Tüm ATA Gateway bileşenlerinden ve ATA Lightweight Gateway bileşenlerinden varlık yığınlarını alır.|
|Ağ Etkinliği İşlemcisi|Alınan her yığın içindeki tüm ağ etkinliklerini işler. Örneğin, farklı bilgisayarlardan gerçekleştirilmiş olabilecek çeşitli Kerberos adımları arasında eşleştirme yapar|
|Varlık Profili Oluşturucu|Trafiğe ve olaylara göre tüm Benzersiz Varlıkların profilini oluşturur. Örneğin, ATA’nın her kullanıcı profili için oturum açılmış bilgisayarlar listesini güncelleştirdiği yer burasıdır.|
|Merkez Veritabanı|Ağ Etkinliklerini ve olayları veritabanına yazma sürecini yönetir. |
|Veritabanı|ATA, sistemdeki tüm verileri depolama amacıyla MongoDB kullanır:<br /><br />-   Ağ etkinlikleri<br />-   Event etkinlikleri<br />-   Benzersiz varlıklar<br />-   Kuşkulu etkinlikler<br />-   ATA yapılandırması|
|Algılayıcılar|Algılayıcılar ağınızdaki kuşkulu etkinlikleri ve anormal kullanıcı davranışlarını bulmak için makine öğrenme altyapılarını ve belirlenimci kuralları kullanır.|
|ATA Konsolu|ATA Konsolu, ATA’yı yapılandırmak ve ATA tarafından ağınızda algılanan kuşkulu etkinlikleri izlemek için kullanılır. ATA Konsolu ATA Center hizmetine bağımlı değildir ve veritabanıyla iletişim kurabildiği sürece hizmet durdurulduğunda bile çalışmaya devam eder.|
Ağınızda kaç ATA Center bileşeninin dağıtımını yapacağınıza karar verirken aşağıdaki noktaları dikkate alın:

-   ATA Center tek bir Active Directory ormanını izleyebilir. Birden çok Active Directory ormanınız varsa, her Active Directory ormanı için en az bir ATA Center’a ihtiyacınız olacaktır.

-    Çok büyük Active Directory dağıtımlarında, tek bir ATA Center tüm etki alanı denetleyicilerinizin trafiğinin tamamını işleyemeyebilir. Bu durumda, birden fazla ATA Center gerekir. ATA Center bileşenlerinin sayısı, [ATA kapasite planlaması](ata-capacity-planning.md) tarafından belirlenmelidir.

## <a name="ata-gateway-and-ata-lightweight-gateway"></a>ATA Gateway ve ATA Lightweight Gateway

### <a name="gateway-core-functionality"></a>Gateway çekirdek işlevleri
**ATA Gateway** ve **ATA Lightweight Gateway**’in her ikisi de aynı çekirdek işlevlere sahiptir:

-   Etki alanı denetleyicisi ağ trafiğini yakalama ve inceleme (ATA Gateway söz konusu olduğunda bağlantı noktası yansıtılmış trafik ve ATA Lightweight Gateway söz konusu olduğunda etki alanı denetleyicisinin yerel trafiği) 

-   SIEM ve Syslog sunucularından veya Windows Olay İletme’yi kullanarak etki alanı denetleyicilerinden Windows olaylarını alma

-   Active Directory etki alanından kullanıcılar ve bilgisayarlar hakkındaki verileri alma

-   Ağ varlıklarının (kullanıcılar, gruplar ve bilgisayarlar) çözümlemesini yapma

-   İlgili verileri ATA Center’a aktarma

-   Tek bir ATA Gateway bileşeninden birden çok etki alanı denetleyicisini izleyin veya ATA Lightweight Gateway için tek bir etki alanı denetleyicisi izleyin.

ATA Gateway ağınızdan ağ trafiğini ve Windows Olaylarını alır ve aşağıdaki ana bileşenlerde bu trafiği işler:

|||
|-|-|
|Ağ Dinleyicisi|Ağ Dinleyicisi, ağ trafiğini yakalamaktan ve trafiği ayrıştırmaktan sorumludur. Bu yoğun CPU kullanan bir görev olduğundan, ATA Gateway veya ATA Lightweight Gateway bileşeninizi planlarken [ATA Önkoşulları](ata-prerequisites.md)’nı gözden geçirmeniz özellikle önemlidir.|
|Olay Dinleyicisi|Olay Dinleyicisi, ağınızdaki SIEM sunucusundan iletilen Windows Olaylarını yakalamaktan ve ayrıştırmaktan sorumludur.|
|Windows Olay Günlüğü Okuyucusu|Windows Olay Günlüğü Okuyucusu, etki alanı denetleyicilerinden ATA Gateway’in Windows Olay Günlüğü’ne iletilen Windows Olaylarını okumaktan ve ayrıştırmaktan sorumludur.|
|Ağ Etkinliği Çeviricisi | Ayrıştırılan trafiği ATA tarafından kullanılan trafiğin mantıksal gösterimine çevirir (NetworkActivity).
|Varlık Çözümleyicisi|Varlık Çözümleyicisi ayrıştırılan verileri (ağ trafiği ve olaylar) alır, sonra da hesap ve kimlik bilgilerini bulmak için bunları Active Directory ile çözümler. Ardından bunlar ayrıştırılan verilerde bulunan IP adresleriyle eşleştirilir. Varlık Çözümleyicisi, makine adları, özellikler ve kimlikler için kimlik doğrulama paketlerinin ayrıştırılabilmesi için, paket üst bilgilerini verimli bir şekilde inceler. Varlık Çözümleyicisi ayrıştırılmış kimlik doğrulama paketlerini gerçek paketteki verilerle birleştirir.|
|Varlık Göndericisi|Varlık Göndericisi, ayrıştırılmış ve eşleştirilmiş verileri ATA Center’a göndermekten sorumludur.|

## <a name="ata-lightweight-gateway-features"></a>ATA Lightweight Gateway özellikleri

Aşağıdaki özellikler, bir ATA Gateway ya da ATA Lightweight Gateway bileşeni çalıştırdığınıza bağlı olarak farklı şekilde çalışır.

-    **Etki alanı eşitleyici adayı**<br>
Etki alanı eşitleyici ağ geçidi, belirli bir Active Directory etki alanından tüm varlıkların önceden tedbirli olarak eşitlenmesinden sorumludur (çoğaltma için etki alanı denetleyicilerinin kendi kullandıkları mekanizmaya benzer). Adaylar listesinden bir ağ geçidi, etki alanı eşitleyici görevi görmesi için rastgele seçilir. <br><br>
Eşitleyici 30 dakikadan fazla çevrimdışı olursa, bunun yerine başka bir aday seçilir. Belirli bir etki alanı için kullanılabilir etki alanı eşitleyici yoksa, ATA önceden tedbirli olarak varlıkları ve değişikliklerini eşitleyemez, ancak izlenen trafikte algılanan yeni varlıkları reaktif olarak alır. 
<br>Kullanılabilir etki alanı eşitleyici yoksa ve onunla ilgili trafik olmayan bir varlık için arama yaparsanız, hiçbir arama sonucu görüntülenmez.<br><br>
Varsayılan olarak, tüm ATA Gateway bileşenleri eşitleyici adayıdır.<br><br>
Tüm ATA Lightweight Gateway bileşenlerinin şubelerde ve küçük etki alanı denetleyicilerinde dağıtılması daha olası olduğundan, bunlar varsayılan olarak eşitleyici adayı değildir.


-    **Kaynak sınırlamaları**<br>
ATA Lightweight Gateway, çalıştığı etki alanı denetleyicisindeki kullanılabilir bilgi işlem ve bellek kapasitesini değerlendiren bir izleme bileşeni içerir. İzleme işlemi 10 saniyede bir çalışır ve herhangi bir anda etki alanı denetleyicisinde en az %15 boş bilgi işlem ve bellek kaynağı bulunduğundan emin olmak için, ATA Lightweight Gateway işlemindeki CPU ve bellek kullanım kotasını dinamik olarak güncelleştirir.<br><br>
Etki alanı denetleyicisinde ne olursa olsun, bu işlem etki alanı denetleyicisinin çekirdek işlevlerinin etkilenmemesini sağlamak için her zaman kaynakları serbest bırakır.<br><br>
Bu durum ATA Lightweight Gateway’in kaynaksız kalmasına neden olursa, trafiğin yalnızca bir kısmı izlenir ve Sağlık Durumu sayfasında "Bağlantı noktası yansıtılan ağ trafiği bırakıldı" uyarısı görüntülenir.

Aşağıdaki tabloda, tüm trafiğin izlenmesi için halen gerekli olandan daha büyük kotaya izin verecek kadar bilgi işlem kaynağına sahip bir etki alanı denetleyicisi örneği görülmektedir:

||||||
|-|-|-|-|-|
|Active Directory (Lsass.exe)|ATA Lightweight Gateway (Microsoft.Tri.Gateway.exe)|Çeşitli (diğer işlemler) |ATA Lightweight Gateway Kotası|Ağ geçidi bırakılıyor|
|30%|20%|%10|45%|Hayır|

Active Directory daha fazla bilgi işleme gereksinim duyuyorsa, ATA Lightweight Gateway için gereken kota azaltılır. Aşağıdaki örnekte, ATA Lightweight Gateway ayrılandan daha fazla kotaya gereksinim duymakta ve trafiğin bir kısmını bırakmaktadır (trafiğin yalnızca bir kısmını izlemektedir):

||||||
|-|-|-|-|-|
|Active Directory (Lsass.exe)|ATA Lightweight Gateway (Microsoft.Tri.Gateway.exe)|Çeşitli (diğer işlemler) |ATA Lightweight Gateway Kotası|Ağ geçidi bırakılıyor|
|60%|15%|%10|15%|Evet|



## <a name="your-network-components"></a>Ağ bileşenleriniz
ATA ile çalışabilmesi için aşağıdakilerden emin olun:

### <a name="port-mirroring"></a>Bağlantı noktası yansıtma
ATA Gateway bileşenleri kullanıyorsanız, izlenecek etki alanları için bağlantı noktası yansıtmayı ayarlamanız ve ATA Gateway’i fiziksel veya sanal anahtarlar kullanan hedef olarak ayarlamanız gerekir. Başka bir seçenek de ağ TAP’ları kullanmaktır. Etki alanı denetleyicilerinizin hepsi olmasa da bir kısmı izleniyorsa ATA çalışır, ancak algılamalar daha az etkili olur.

Bağlantı noktası yansıtma etki alanı denetleyicisi ağ trafiğinin tümünü ATA Gateway’e yansıtsa da, bu trafiğin yalnızca küçük bir yüzdesi sıkıştırılıp çözümlenmek üzere ATA Center’a gönderilir.

Etki alanı denetleyicileriniz ve ATA Gateway bileşenleri fiziksel veya sanal olabilir. Daha fazla bilgi için bkz. [Bağlantı noktası yansıtmayı yapılandırma](/advanced-threat-analytics/deploy-use/configure-port-mirroring).


### <a name="events"></a>Olaylar
ATA’nın Karma Değer Geçişi, Deneme Yanılma ve Bal Kapları algılamasını iyileştirmek için ATA’ya Windows Olay günlüğü kimliği 4776 gerekir. Bu ATA Gateway’e iki yoldan biriyle, ATA Gateway’i SIEM olaylarını dinleyecek şekilde yapılandırarak veya Windows Olay İletme’yi kullanarak iletilebilir.

-   ATA Gateway’i SIEM olaylarını dinleyecek şekilde yapılandırma <br>SIEM sisteminizi belirli Windows olaylarını ATA’ya iletecek şekilde yapılandırın. ATA, bir dizi SIEM satıcısını destekler. Daha fazla bilgi için bkz. [Olay koleksiyonunu yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection).

-   Windows Olay İletme’yi yapılandırma<br>ATA’nın olaylarınızı almasının bir diğer yolu da, etki alanı denetleyicilerinizi Windows olayı 4776’yı ATA Gateway bileşeninize iletecek şekilde yapılandırmaktır. Bir SIEM’iniz olmadığında veya SIEM’iniz şu anda ATA tarafından desteklenmediğinde, bu özellikle yararlı olur. ATA’da Windows Olay İletme hakkında daha fazla bilgi için bkz. [Windows olay iletme özelliğini yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection#configuring-windows-event-forwarding).

## <a name="see-also"></a>Ayrıca bkz.
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [Windows olay iletme özelliğini yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

