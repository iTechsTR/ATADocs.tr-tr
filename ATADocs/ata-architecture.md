---
title: Advanced Threat Analytics mimarisi | Microsoft Docs
description: "Microsoft Advance Threat Analytics’in (ATA) mimarisini açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 07/5/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 892b16d2-58a6-49f9-8693-1e5f69d8299c
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 4d95e5b13d06ea0963b7cac129be4eb1458e5d4c
ms.sourcegitcommit: 53b56220fa761671442da273364bdb3d21269c9e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/05/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*




# ATA Mimarisi
<a id="ata-architecture" class="xliff"></a>
Advanced Threat Analytics mimarisi bu diyagramda ayrıntılı olarak açıklanmıştır:

![ATA mimarisi topoloji diyagramı](media/ATA-architecture-topology.jpg)

ATA, fiziksel veya sanal anahtar kullanan bir ATA Gateway’e bağlantı noktası yansıtması yaparak etki alanı denetleyicisi ağ trafiğinizi izler. ATA Lightweight Gateway’i doğrudan etki alanı denetleyicilerinize dağıtırsanız bağlantı noktasını yansıtmaya gerek kalmaz. Ayrıca, ATA doğrudan etki alanı denetleyicilerinizden veya bir SIEM sunucusundan iletilen Windows olaylarını da kullanabilir ve verilerde saldırı ve tehdit analizi yapabilir.
Bu bölümde, ağ akışı ve olay yakalama açıklanmıştır ve ATA’nın şu temel bileşenlerinin işlevleri ayrıntılı açıklanmıştır: ATA Gateway, ATA Lightweight Gateway (ATA Gateway ile aynı temel işlevlere sahiptir) ve ATA Center.


![ATA trafik akışı diyagramı](media/ATA-traffic-flow.jpg)

## ATA Bileşenleri
<a id="ata-components" class="xliff"></a>
ATA aşağıdaki bileşenlerden oluşur:

-   **ATA Center** <br>
ATA dağıttığınız tüm ATA Gateway bileşenlerinden ve/veya ATA Lightweight Gateway bileşenlerinden veri alır.
-   **ATA Gateway**<br>
ATA Gateway, bağlantı noktası yansıtmayı ya da ağ TAP’ı kullanarak etki alanı denetleyicilerinizden gelen trafiği izleyen ayrılmış bir sunucuya yüklenir.
-   **ATA Lightweight Gateway**<br>
ATA Lightweight Gateway doğrudan etki alanı denetleyicilerinize yüklenir ve ayrılmış bir sunucuya veya bağlantı noktası yansıtmaya gerek olmadan bunların trafiğini doğrudan izler. Bu, ATA Gateway’e bir alternatiftir.

Bir ATA dağıtımı; tüm ATA Gateway’lere, tüm ATA Lightweight Gateway’lere veya ATA Gateway ve ATA Lightweight Gateway’lerin bir birleşimine bağlı olan tek bir ATA Center’dan oluşabilir.


## Dağıtım seçenekleri
<a id="deployment-options" class="xliff"></a>
Aşağıdaki ağ geçitlerinin birleşimini kullanarak ATA dağıtabilirsiniz:

-   **Yalnızca ATA Gateway bileşenleri kullanma** <br>
ATA dağıtımınız herhangi bir ATA Lightweight Gateway olmadan yalnızca ATA Gateway’ler içerebilir: Tüm etki alanı denetleyicilerinin bir ATA Gateway’e bağlantı noktası yansıtmsına olanak verecek şekilde yapılandırılması veya ağ TAP’leri bulunması gerekir.
-   **Yalnızca ATA Lightweight Gateway bileşenleri kullanma**<br>
ATA dağıtımınız yalnızca ATA Lightweight Gateway’leri içerebilir: Her etki alanı denetleyicisine ATA Lightweight Gateway dağıtılır ve ilave sunucu veya bağlantı noktası yansıtma yapılandırması gerekli değildir.
-   **Hem ATA Gateway hem de ATA Lightweight Gateway bileşenleri kullanma**<br>
ATA dağıtımınız ATA Gateway ve ATA Lightweight Gateway’leri içerir. Bazı etki alanı denetleyicilerinizde ATA Lightweight Gateway’ler yüklüdür (örneğin alt sitelerinizdeki tüm etki alanı denetleyicilerinde). Bunun yanında diğer etki alanı denetleyicileri ise ATA Gateway’ler tarafından izlenir (örneğin ana veri merkezlerinizdeki daha büyük etki alanı denetleyicileri).

Bu senaryoların tamamında tüm ağ geçitleri, verilerini ATA Center’a gönderir.




## ATA Center
<a id="ata-center" class="xliff"></a>
**ATA Center** aşağıdaki işlevleri gerçekleştirir:

-   ATA Gateway ve ATA Lightweight Gateway yapılandırma ayarlarını yönetir

-   ATA Gateway bileşenlerinden ve ATA Lightweight Gateway bileşenlerinden veri alır 

-   Kuşkulu etkinlikleri algılar

-   Olağan dışı davranışları algılamak için ATA davranışsal makine öğrenme algoritmalarını çalıştırır

-   Saldırı sonlandırma zincirine dayalı olarak gelişmiş saldırıları algılamak için çeşitli belirleyici algoritmaları çalıştırır

-   ATA Konsolu’nu çalıştırır

-   İsteğe bağlı: ATA Center, kuşkulu bir etkinlik algılandığında e-posta ve olay gönderecek şekilde yapılandırılabilir.

ATA Center, ATA Gateway ve ATA Lightweight Gateway’den ayrıştırılmış trafik alır. Daha sonra ağınız hakkında bilgi edinmek, anomali algılamayı etkinleştirmek ve şüpheli etkinliklerde sizi uyarmak için profil oluşturma işlemini yapar, belirlenimci algılama çalıştırır, makine öğrenimi ve davranışsal algoritmaları çalıştırır.

|||
|-|-|
|Varlık Alıcısı|Tüm ATA Gateway ve ATA Lightweight Gateway’lerden varlık yığınlarını alır.|
|Ağ Etkinliği İşlemcisi|Alınan her yığın içindeki tüm ağ etkinliklerini işler. Örneğin, farklı bilgisayarlardan gerçekleştirilmiş olabilecek çeşitli Kerberos adımları arasında eşleştirme yapar|
|Varlık Profili Oluşturucu|Trafiğe ve olaylara göre tüm Benzersiz Varlıkların profilini oluşturur. Örneğin ATA, her kullanıcı profili için oturum açılmış bilgisayarlar listesini güncelleştirir.|
|Merkez Veritabanı|Ağ Etkinliklerini ve olayları veritabanına yazma sürecini yönetir. |
|Veritabanı|ATA, sistemdeki tüm verileri depolama amacıyla MongoDB kullanır:<br /><br />-   Ağ etkinlikleri<br />-   Event etkinlikleri<br />-   Benzersiz varlıklar<br />-   Kuşkulu etkinlikler<br />-   ATA yapılandırması|
|Algılayıcılar|Algılayıcılar ağınızdaki kuşkulu etkinlikleri ve anormal kullanıcı davranışlarını bulmak için makine öğrenme altyapılarını ve belirlenimci kuralları kullanır.|
|ATA Konsolu|ATA Konsolu, ATA’yı yapılandırmak ve ATA tarafından ağınızda algılanan kuşkulu etkinlikleri izlemek için kullanılır. ATA Konsolu, ATA Center hizmetine bağlı değildir ve veritabanıyla iletişim kurabildiği sürece hizmet durdurulduğunda bile çalışmaya devam eder.|
Ağınızda kaç ATA Center dağıtımı yapacağınıza karar verirken aşağıdaki ölçütleri dikkate alın:

-   ATA Center tek bir Active Directory ormanını izleyebilir. Birden çok Active Directory ormanınız varsa her Active Directory ormanı için en az bir ATA Center’a ihtiyacınız vardır.

-    Çok büyük Active Directory dağıtımlarında tek bir ATA Center’ın tüm etki alanı denetleyicilerinizdeki trafiği işlemesi mümkün olmayabilir. Bu durumda birden çok ATA Center gereklidir. ATA Center bileşenlerinin sayısı, [ATA kapasite planlaması](ata-capacity-planning.md) tarafından belirlenmelidir.

## ATA Gateway ve ATA Lightweight Gateway
<a id="ata-gateway-and-ata-lightweight-gateway" class="xliff"></a>

### Gateway çekirdek işlevleri
<a id="gateway-core-functionality" class="xliff"></a>
**ATA Gateway** ve **ATA Lightweight Gateway**’in her ikisi de aynı çekirdek işlevlere sahiptir:

-   Etki alanı denetleyicisi ağ trafiğini yakalayıp denetleyin. Bu, ATA Gateway’ler için bağlantı noktası yansıtma trafiği ve ATA Lightweight Gateway’ler için etki alanı denetleyicisi yerel trafiğidir. 

-   SIEM ve Syslog sunucularından veya Windows Olay İletme’yi kullanarak etki alanı denetleyicilerinden Windows olaylarını alma

-   Active Directory etki alanından kullanıcılar ve bilgisayarlar hakkındaki verileri alma

-   Ağ varlıklarının (kullanıcılar, gruplar ve bilgisayarlar) çözümlemesini yapma

-   İlgili verileri ATA Center’a aktarma

-   Tek bir ATA Gateway bileşeninden birden çok etki alanı denetleyicisini izleyin veya ATA Lightweight Gateway için tek bir etki alanı denetleyicisi izleyin.

ATA Gateway ağınızdan ağ trafiğini ve Windows Olaylarını alır ve aşağıdaki ana bileşenlerde bu trafiği işler:

|||
|-|-|
|Ağ Dinleyicisi|Ağ Dinleyicisi, ağ trafiğini yakalar ve trafiği ayrıştırır. Bu yoğun CPU kullanan bir görev olduğundan, ATA Gateway veya ATA Lightweight Gateway bileşeninizi planlarken [ATA Önkoşulları](ata-prerequisites.md)’nı gözden geçirmeniz özellikle önemlidir.|
|Olay Dinleyicisi|Olay Dinleyicisi, ağınızdaki SIEM sunucusundan iletilen Windows Olaylarını yakalar ve ayrıştırır.|
|Windows Olay Günlüğü Okuyucusu|Windows Olay Günlüğü Okuyucusu, etki alanı denetleyicilerinden ATA Gateway’in Windows Olay Günlüğü’ne iletilen Windows Olaylarını okur ve ayrıştırır.|
|Ağ Etkinliği Çeviricisi | Ayrıştırılan trafiği ATA tarafından kullanılan trafiğin mantıksal gösterimine çevirir (NetworkActivity).
|Varlık Çözümleyicisi|Varlık Çözümleyicisi ayrıştırılan verileri (ağ trafiği ve olaylar) alır, sonra da hesap ve kimlik bilgilerini bulmak için bunları Active Directory ile çözümler. Ardından bunlar ayrıştırılan verilerde bulunan IP adresleriyle eşleştirilir. Varlık Çözümleyicisi, makine adları, özellikler ve kimlikler için kimlik doğrulama paketlerinin ayrıştırılabilmesi için, paket üst bilgilerini verimli bir şekilde inceler. Varlık Çözümleyicisi ayrıştırılmış kimlik doğrulama paketlerini gerçek paketteki verilerle birleştirir.|
|Varlık Göndericisi|Varlık Göndericisi, ayrıştırılmış ve eşleştirilmiş verileri ATA Center’a gönderir.|

## ATA Lightweight Gateway özellikleri
<a id="ata-lightweight-gateway-features" class="xliff"></a>

Aşağıdaki özellikler, bir ATA Gateway ya da ATA Lightweight Gateway bileşeni çalıştırdığınıza bağlı olarak farklı şekilde çalışır.

-   ATA Lightweight Gateway olayları, olay iletmeyi yapılandırmaya gerek kalmadan yerel olarak okuyabilir.

-   **Etki alanı eşitleyici adayı**<br>
Etki alanı eşitleyici ağ geçidi, belirli bir Active Directory etki alanından tüm varlıkların önceden tedbirli olarak eşitlenmesinden sorumludur (çoğaltma için etki alanı denetleyicilerinin kendi kullandıkları mekanizmaya benzer). Adaylar listesinden bir ağ geçidi, etki alanı eşitleyici görevi görmesi için rastgele seçilir. <br><br>
Eşitleyici 30 dakikadan fazla çevrimdışı olursa, bunun yerine başka bir aday seçilir. Belirli bir etki alanı için kullanılabilir etki alanı eşitleyici yoksa, ATA önceden tedbirli olarak varlıkları ve değişikliklerini eşitleyemez, ancak izlenen trafikte algılanan yeni varlıkları reaktif olarak alır. 
<br>Kullanılabilir etki alanı eşitleyici yoksa ve onunla ilgili trafik olmayan bir varlık için arama yaparsanız, hiçbir arama sonucu görüntülenmez.<br><br>
Varsayılan olarak, tüm ATA Gateway bileşenleri eşitleyici adayıdır.<br><br>
Tüm ATA Lightweight Gateway bileşenlerinin şubelerde ve küçük etki alanı denetleyicilerinde dağıtılması daha olası olduğundan, bunlar varsayılan olarak eşitleyici adayı değildir.


-   **Kaynak sınırlamaları**<br>
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



## Ağ bileşenleriniz
<a id="your-network-components" class="xliff"></a>
ATA ile çalışabilmesi için aşağıdakilerden emin olun:

### Bağlantı noktası yansıtma
<a id="port-mirroring" class="xliff"></a>
ATA Gateway kullanıyorsanız izlenecek etki alanları için bağlantı noktası yansıtmasını ayarlamanız ve ATA Gateway’i fiziksel veya sanal anahtarlar kullanan hedef olarak ayarlamanız gerekir. Başka bir seçenek de ağ TAP’ları kullanmaktır. Etki alanı denetleyicilerinizin hepsi olmasa da bir kısmı izleniyorsa ATA çalışır, ancak algılamalar daha az etkili olur.

Bağlantı noktası yansıtma etki alanı denetleyicisi ağ trafiğinin tümünü ATA Gateway’e yansıtsa da, bu trafiğin yalnızca küçük bir yüzdesi sıkıştırılıp çözümlenmek üzere ATA Center’a gönderilir.

Etki alanı denetleyicileriniz ve ATA Gateway bileşenleri fiziksel veya sanal olabilir. Daha fazla bilgi için bkz. [Bağlantı noktası yansıtmayı yapılandırma](configure-port-mirroring.md).


### Olaylar
<a id="events" class="xliff"></a>
ATA’nın Pass-the-Hash, Deneme Yanılma, Gizli grup değişiklikleri ve Honey Token algılamasını geliştirmek için şu Windows olaylarına ihtiyacı vardır: 4776, 4732, 4733, 4728, 4729, 4756, 4757. Bunlar, ATA Lightweight Gateway tarafından otomatik olarak okunabilir veya ATA Lightweight Gateway’in dağıtılmamış olduğu durumlarda şu iki yöntemden biriyle ATA Gateway’e iletilebilir: ATA Gateway’i SIEM olaylarını dinleyecek şekilde yapılandırarak ya da [Windows Olay İletme’yi yapılandırarak](#configuring-windows-event-forwarding).

-   ATA Gateway’i SIEM olaylarını dinleyecek şekilde yapılandırma <br>SIEM sisteminizi belirli Windows olaylarını ATA’ya iletecek şekilde yapılandırın. ATA, bir dizi SIEM satıcısını destekler. Daha fazla bilgi için bkz. [Olay koleksiyonunu yapılandırma](configure-event-collection.md).

-   Windows Olay İletme’yi yapılandırma<br>ATA’nın olaylarınızı almasının bir diğer yolu da etki alanı denetleyicilerinizi Windows olayları 4776, 4732, 4733, 4728, 4729, 4756 ve 4757’yi ATA Gateway’inize iletecek şekilde yapılandırmaktır. Bir SIEM’iniz olmadığında veya SIEM’iniz şu anda ATA tarafından desteklenmediğinde, bu özellikle yararlı olur. ATA’da Windows Olay İletme hakkında daha fazla bilgi için bkz. [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding). Bunun ATA Lightweight Gateway’de değil, yalnızca fiziksel ATA Gateway’lerde geçerli olduğunu unutmayın.

## Ayrıca Bkz.
<a id="see-also" class="xliff"></a>
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

