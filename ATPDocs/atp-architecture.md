---
title: Azure Gelişmiş tehdit koruması mimarisi | Microsoft Docs
description: Azure Gelişmiş tehdit analizi (ATP) mimarisini açıklar
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/05/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 90f68f2c-d421-4339-8e49-1888b84416e6
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 8264799f3aad2fb27287f56513458f34a3a7b0c6
ms.sourcegitcommit: 14c05a210ae92d35100c984ff8c6d171db7c3856
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39567653"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="azure-atp-architecture"></a>Azure ATP mimarisi
Azure Gelişmiş tehdit koruması mimarisi:

![Azure ATP mimarisi topoloji diyagramı](media/atp-architecture-topology.png)

Azure ATP fiziksel veya sanal anahtarlar kullanan bir Azure ATP tek başına algılayıcı için bağlantı noktası yansıtma yararlanarak etki alanı denetleyicisi ağ trafiğinizi izler. Azure ATP algılayıcı doğrudan etki alanı denetleyicilerinize dağıtırsanız bağlantı noktası yansıtma için gereksinimini ortadan kaldırır. Ayrıca, Azure ATP (doğrudan etki alanı denetleyicilerinizden veya bir SIEM sunucusundan iletilen) Windows olaylarını da kullanabilir ve saldırı ve tehdit verilerini analiz edin. Azure ATP Azure ATP tek başına algılayıcı ve Azure ATP algılayıcısını gateway'den ayrıştırılmış trafiği alır. Daha sonra ağınız hakkında bilgi edinmek, anomali algılamayı etkinleştirmek ve şüpheli etkinliklerde sizi uyarmak için profil oluşturma işlemini yapar, belirlenimci algılama çalıştırır, makine öğrenimi ve davranışsal algoritmaları çalıştırır.

Bu bölümde ağ akışı ve olay yakalama açıklanmıştır ve ATP'ın şu temel bileşenlerinin işlevleri ayrıntılı açıklanmıştır: (Bu tek başına Azure ATP algılayıcısını aynı çekirdek işlevlere sahiptir) Azure ATP algılayıcısını, Azure ATP tek başına algılayıcı ve Azure ATP bulut hizmeti. 

Doğrudan etki alanı denetleyicisine yüklendiğinde, algılayıcı doğrudan etki alanı denetleyicisinden gerekli olay günlüklerini erişir. Bu günlükler ve ağ trafiğini algılayıcı tarafından ayrıştırıldıktan sonra Azure ATP bu ayrıştırılmış bilgiler Azure ATP hizmeti (değil tüm günlükler) gönderir.

## <a name="azure-atp-components"></a>Azure ATP bileşenleri
Azure ATP aşağıdaki bileşenlerden oluşur:

-   **Azure ATP çalışma alanı Yönetim Portalı** <br>
Azure ATP çalışma alanı yönetim portalında çalışma alanlarını oluşturmanıza olanak sağlar ve diğer Microsoft Hizmetleri ile tümleştirme sağlar.

> [!NOTE]
> Yalnızca tek bir Active Directory ormanı algılayıcılardan tek bir çalışma alanına bağlanabilir.

-   **Azure ATP çalışma alanı portalı** <br>
Azure ATP çalışma alanı portalı ATP algılayıcı ve tek başına algılayıcı verilerini alır. İzler, yönetir ve ortamınızdaki tehditlere araştırır.

-   **Azure ATP algılayıcısı**<br>
Azure ATP algılayıcı doğrudan etki alanı denetleyicilerinize yüklenir ve ayrılmış bir sunucuya veya bağlantı noktası yansıtmaya gerek kalmadan trafiğini doğrudan izler. 

-   **Azure ATP tek başına algılayıcı**<br>
Azure ATP tek başına algılayıcı bağlantı noktası yansıtmayı ya da ağ TAP'ı kullanarak etki alanı denetleyicilerinizden gelen trafiği izleyen ayrılmış bir sunucuya yüklenir. Azure ATP algılayıcısını için bir alternatiftir.

## <a name="deployment-options"></a>Dağıtım seçenekleri
Azure ATP algılayıcı aşağıdaki birleşimini kullanarak dağıtabilirsiniz:

-   **Yalnızca Azure ATP algılayıcı kullanma**<br>
Azure ATP dağıtımınız yalnızca Azure ATP algılayıcı içerebilir: Azure ATP algılayıcı dağıtılan her etki alanı denetleyicisi ve ek sunucu veya bağlantı noktası yansıtma yapılandırması gereklidir.

-   **Azure ATP tek başına algılayıcı kullanma** <br>
Azure ATP dağıtımınız yalnızca Azure ATP tek başına algılayıcı, herhangi bir Azure ATP algılayıcı olmadan içerebilir: tüm etki alanı denetleyicileri için bir Azure ATP tek başına algılayıcı bağlantı noktası yansıtmayı etkinleştirmek için yapılandırılması gerekir veya ağ Tap'leri bulunması gerekir.

-   **Azure ATP tek başına algılayıcı hem Azure ATP algılayıcı kullanma**<br>
Azure ATP dağıtımınız, hem Azure ATP tek başına algılayıcı hem de Azure ATP algılayıcı içerir. Azure ATP algılayıcı, bazı etki alanı denetleyicilerinizin (örneğin, tüm etki alanı denetleyicileri şubelerinizdeki) yüklenir. Aynı zamanda, diğer etki alanı denetleyicileri, Azure ATP tek başına algılayıcı (örneğin, ana veri merkezlerinizdeki daha büyük etki alanı denetleyicileri) tarafından izlenir.


### <a name="azure-atp-workspace-management-portal"></a>Azure ATP çalışma alanı Yönetim Portalı

Azure ATP çalışma alanı Yönetim Portalı ile yapabilecekleriniz:

-   Oluşturma ve Azure ATP çalışma alanlarını yönetme

-   Diğer Microsoft Güvenlik Hizmetleri ile tümleştirme

Ana çalışma alanınızı ayarlama **birincil**. Bir çalışma alanı birincil olarak etkileri tümleştirmeleri - ayarlama, yalnızca Azure ATP Windows Defender ATP ile birincil çalışma alanınız için tümleştirebilirsiniz. 

> [!NOTE]
> - Azure ATP, şu anda yalnızca bir çalışma alanı oluşturmayı destekler. Bir çalışma alanı sildikten sonra bunu yeniden etkinleştirmek için desteğe başvurabilirsiniz. En fazla üç silinmiş çalışma olabilir. Kaydedilmiş, silinen çalışma alanlarının sayısını artırmak için Azure ATP Hizmetleri ile görüşün.
> - 60 gün içinde hiçbir algılayıcı, çalışma alanınızda yüklü değilse, çalışma silinebilir ve yeniden oluşturmanız gerekir.



### <a name="azure-atp-workspace-portal"></a>Azure ATP çalışma alanı portalı

Azure ATP çalışma alanı, aşağıdaki Azure ATP işlevselliği yönetmenize olanak sağlar:

-   Azure ATP algılayıcısı ve tek başına algılayıcı yapılandırma ayarlarını yönetme

-   Azure ATP tek başına algılayıcı ve Azure ATP sensörlerden alınan verileri görüntüle 

-   Olağan dışı davranışları algılamak için davranışsal makine öğrenme algoritmalarını ve saldırı sonlandırma zincirine dayalı olarak Gelişmiş saldırıları algılamak için belirleyici algoritmaları göre kuşkulu etkinlikleri İzleyici algılandı

-   İsteğe bağlı: çalışma alanı Yönetim Portalı e-postaları ve şüpheli etkinlikler veya sistem durumu olayı algılandığında olaylar göndermek için yapılandırılabilir.


|||
|-|-|
|Varlık Alıcısı|Tüm Azure ATP algılayıcı ve Azure ATP tek başına algılayıcı varlık yığınlarını alır.|
|Ağ Etkinliği İşlemcisi|Alınan her yığın içindeki tüm ağ etkinliklerini işler. Örneğin, farklı bilgisayarlardan gerçekleştirilmiş olabilecek çeşitli Kerberos adımları arasında eşleştirme yapar|
|Varlık Profili Oluşturucu|Trafiğe ve olaylara göre tüm Benzersiz Varlıkların profilini oluşturur. Örneğin, Azure ATP oturum açan her kullanıcı profili için bilgisayar listesini güncelleştirir.|
|Azure ATP çalışma alanı Yönetim Portalı|Azure ATP çalışma alanlarınızı yönetir.|
|Azure ATP çalışma alanı portalı|Azure ATP çalışma alanı, Azure ATP yapılandırma ve Azure ATP tarafından ağınızda algılanan kuşkulu etkinlikleri izlemek için kullanılır. Azure ATP çalışma alanı, üzerinde Azure ATP algılayıcısını bağımlı değildir ve hatta Azure ATP algılayıcı hizmeti durdurulduğunda çalıştırır. |
|Algılayıcılar|Algılayıcılar ağınızdaki kuşkulu etkinlikleri ve anormal kullanıcı davranışlarını bulmak için makine öğrenme altyapılarını ve belirlenimci kuralları kullanır.|

Ağınızda dağıtmayı, kaç Azure ATP çalışma alanları karar verirken aşağıdaki ölçütleri göz önünde bulundurun:

-   Bir Azure ATP çalışma alanı, tek bir Active Directory ormanı izleyebilirsiniz. Birden fazla Active Directory ormanınız varsa, en az bir Azure ATP bulut hizmetinin her Active Directory ormanı gerekir.


## <a name="azure-atp-sensor-and-azure-atp-standalone-sensor"></a>Azure ATP algılayıcısını ve Azure ATP tek başına algılayıcı

**Azure ATP algılayıcısını** ve **Azure ATP tek başına algılayıcı** aynı çekirdek işlevlere sahiptir:

-   Etki alanı denetleyicisi ağ trafiğini yakalayıp denetleyin. Azure ATP tek başına algılayıcı için bağlantı noktası yansıtılmış trafik ve Azure ATP algılayıcı etki alanı denetleyicisinin yerel trafiği budur. 

-   Doğrudan (ATP algılayıcı için) etki alanı denetleyicilerinden veya SIEM ve Syslog sunucularından (ATP tek başına algılayıcı için) Windows olayları alma

-   VPN sağlayıcınız RADIUS hesap bilgilerini alma

-   Active Directory etki alanından kullanıcılar ve bilgisayarlar hakkındaki verileri alma

-   Ağ varlıklarının (kullanıcılar, gruplar ve bilgisayarlar) çözümlemesini yapma

-   Azure ATP bulut hizmetine ilgili veri aktarımı

-   Tek bir Azure ATP tek başına algılayıcı birden çok etki alanı denetleyicilerini izlemek veya bir Azure ATP algılayıcısını tek etki alanı denetleyicisi izleyin.

Varsayılan olarak, en fazla 100 algılayıcınız Azure ATP destekler. Daha fazla yüklemek istiyorsanız, Azure ATP desteğe başvurun.

Azure ATP tek başına algılayıcı ağınızdan ağ trafiğini ve Windows olaylarını alır ve aşağıdaki ana bileşenlerde işler:

|||
|-|-|
|Ağ Dinleyicisi|Ağ dinleyicisi, ağ trafiğini yakalar ve trafiği ayrıştırır. Gözden geçirmeniz özellikle önemlidir bu olduğundan CPU yoğun bir görev [Azure ATP önkoşulları](atp-prerequisites.md) Azure ATP algılayıcı veya tek başına algılayıcı Azure ATP planlarken.|
|Olay Dinleyicisi|Olay dinleyicisi, ağınızdaki SIEM sunucusundan iletilen Windows olaylarını ayrıştırır ve yakalar.|
|Windows Olay Günlüğü Okuyucusu|Windows olay günlüğü okuyucusu okur ve etki alanı denetleyicilerinden Azure ATP tek başına algılayıcı'nın Windows Olay Günlüğü'ne iletilen Windows olaylarını ayrıştırır.|
|Ağ Etkinliği Çeviricisi | Azure ATP (NetworkActivity) tarafından kullanılan trafiğin mantıksal gösterimine çevirir ayrıştırılmış trafiği çevirir.
|Varlık Çözümleyicisi|Varlık Çözümleyicisi ayrıştırılan verileri (ağ trafiği ve olaylar) alır, sonra da hesap ve kimlik bilgilerini bulmak için bunları Active Directory ile çözümler. Ardından bunlar ayrıştırılan verilerde bulunan IP adresleriyle eşleştirilir. Varlık Çözümleyicisi, makine adları, özellikler ve kimlikler için kimlik doğrulama paketlerinin ayrıştırılabilmesi için, paket üst bilgilerini verimli bir şekilde inceler. Varlık Çözümleyicisi ayrıştırılmış kimlik doğrulama paketlerini gerçek paketteki verilerle birleştirir.|
|Varlık Göndericisi|Varlık göndericisi ayrıştırılmış ve eşleştirilmiş verileri Azure ATP bulut hizmetine gönderir.|

## <a name="azure-atp-sensor-features"></a>Azure ATP algılayıcısı özellikleri

Aşağıdaki özellikler, bir Azure ATP tek başına algılayıcı veya bir Azure ATP algılayıcısını çalıştıran bağlı olarak farklı şekilde çalışır.

-   Azure ATP algılayıcısını olay iletmeyi yapılandırmaya gerek kalmadan olayları yerel olarak okuyabilir.

-   **Etki alanı eşitleyici adayı**<br>
Etki alanı Eşitleyici adayı, belirli bir Active Directory etki alanından tüm varlıkların önceden tedbirli olarak eşitlenmesinden sorumludur (etki alanı denetleyicileri tarafından kendileri çoğaltma için kullanılan mekanizmaya benzer). Bir algılayıcı adaylar listesinden, etki alanı Eşitleyici görevi görmesi için rastgele seçilir. <br><br>
Eşitleyici 30 dakikadan fazla çevrimdışı olursa, bunun yerine başka bir aday seçilir. Belirli bir etki alanı için etki alanı Eşitleyici yoksa, Azure ATP gibi izlenen trafikte algılanan yeni varlıkları Azure ATP alır ancak proaktif olarak varlıkları ve değişikliklerini eşitleyemez. 
<br>Kullanılabilir etki alanı Eşitleyici yoksa ve onunla ilgili trafik olmayan olmayan bir varlık araması, arama sonucu görüntülenir.<br><br>
Varsayılan olarak, tüm Azure ATP tek başına algılayıcı Eşitleyici adayıdır.<br><br>
Azure ATP algılayıcı varsayılan olarak Eşitleyici adayı değildir.


-   **Kaynak sınırlamaları**<br>
Azure ATP algılayıcısını üzerinde çalıştığı etki alanı denetleyicisindeki kullanılabilir işlem ve bellek kapasitesini değerlendiren bir izleme bileşeni içerir. İzleme işlemi 10 saniyede bir çalışan ve herhangi belirli bir noktada, en az % 15 boş bilgi işlem ve bellek kaynaklarının etki alanı denetleyicisi olduğundan emin olun Azure ATP algılayıcısı işlemin CPU ve bellek kullanım kotasını dinamik olarak güncelleştirir.<br><br>
Etki alanı denetleyicisinde ne olursa olsun, bu işlem etki alanı denetleyicisinin çekirdek işlevlerinin etkilenmemesini sağlamak için her zaman kaynakları serbest bırakır.<br><br>
Bu Azure ATP algılayıcısını kalmasına neden olursa, trafiğin yalnızca bir kısmı izlenir ve sağlık durumu sayfasında izleme uyarı "bağlantı noktası yansıtılan ağ trafiği bırakıldı" görünür.

Aşağıdaki tabloda, tüm trafiğin izlenmesi için halen gerekli olandan daha büyük kotaya izin verecek kadar bilgi işlem kaynağına sahip bir etki alanı denetleyicisi örneği görülmektedir:

> [!div class="mx-tableFixed"]
||||||
|-|-|-|-|-|
|Active Directory (Lsass.exe)|Azure ATP algılayıcısını (Microsoft.Tri.sensor.exe)|Çeşitli (diğer işlemler) |Azure ATP algılayıcısı kotası|Algılayıcı trafiği bırakılıyor|
|30%|20%|%10|45%|Hayır|

Active Directory daha fazla bilgi işlem gücüne gerekiyorsa, Azure ATP algılayıcı tarafından gereken kota azaltılır. Aşağıdaki örnekte, Azure ATP algılayıcısını en fazla ayrılmış kotasını gerekir ve bazı (trafiğin yalnızca izleme) trafiği bırakır:

> [!div class="mx-tableFixed"]
||||||
|-|-|-|-|-|
|Active Directory (Lsass.exe)|Azure ATP algılayıcısını (Microsoft.Tri.sensor.exe)|Çeşitli (diğer işlemler) |Azure ATP algılayıcısı kotası|Algılayıcı trafiği bırakılıyor|
|60%|15%|%10|15%|Evet|


## <a name="your-network-components"></a>Ağ bileşenleriniz
Aşağıdaki bileşenler, Azure ATP ile çalışmak için ayarlandığından emin olun.

### <a name="port-mirroring"></a>Bağlantı noktası yansıtma
Azure ATP tek başına algılayıcı kullanıyorsanız, bağlantı noktası yansıtma izlenen ve fiziksel veya sanal anahtarlar kullanan hedef olarak Azure ATP tek başına algılayıcı ayarlayın etki alanı denetleyicileri ayarlamanız gerekir. Başka bir seçenek de ağ TAP’ları kullanmaktır. Azure ATP bazıları çalışır ancak izlenen tüm etki alanı denetleyicilerinizin değil, ancak algılamalar daha az etkili.

Bağlantı noktası yansıtmanın tüm etki alanı denetleyicisi ağ trafiğinin tek başına Azure ATP algılayıcısını yansıtsa da, bu trafiğin yalnızca küçük bir yüzdesine yapılır ve ardından gönderilen, sıkıştırılmış, Azure ATP için analiz için bulut hizmeti.

Etki alanı denetleyicileriniz ve Azure ATP tek başına algılayıcı fiziksel veya sanal olabilir. Daha fazla bilgi için [bağlantı noktası yansıtmayı yapılandırma](configure-port-mirroring.md).


### <a name="events"></a>Olaylar
Azure ATP Pass--Hash, deneme yanılma, gizli gruplarda, şüpheli Hizmetleri oluşturulmasını Honey Token değişiklikler değişiklik Azure ATP algılanmasını iyileştirmek için aşağıdaki Windows olaylarına ihtiyacı vardır: 4776, 4732, 4733, 4728, 4729, 4756, 4757'yi ve 7045. Bunlar ya da otomatik olarak Azure ATP algılayıcı tarafından okunabilir veya Azure ATP algılayıcısını dağıtılmamış olması durumunda, bu iki yoldan biriyle Azure ATP tek başına algılayıcı Azure ATP tek başına algılayıcı SIEM olaylarını dinleyecek şekilde yapılandırarak veya iletilebilir[Windows Olay iletme özelliğini yapılandırma](configure-event-forwarding.md).

-   Azure ATP tek başına algılayıcı SIEM olaylarını dinleyecek şekilde yapılandırma <br>SIEM'İNİZE belirli Windows olaylarını ATP'ye iletecek şekilde yapılandırın. Azure ATP bir dizi SIEM satıcısını destekler. Daha fazla bilgi için [olay iletmeyi yapılandırmaya](configure-event-forwarding.md).

-   Windows Olay İletme’yi yapılandırma<br>Azure ATP olaylarınızı almasının başka bir etki alanı denetleyicilerinizi Windows olayları 4776, 4732, 4733, 4728, 4729, 4756, 4757'yi ve 7045, Azure ATP tek başına algılayıcı için iletecek şekilde yapılandırarak yoludur. Bu, bir SIEM yoksa veya SIEM'iniz şu anda ATP tarafından desteklenmiyorsa özellikle yararlı olur. Windows Olay iletme ATP içinde hakkında daha fazla bilgi için bkz. [yapılandırma Windows Olay iletme'yi](configure-event-forwarding.md). Bu yalnızca - Azure ATP algılayıcısını için fiziksel Azure ATP tek başına algılayıcı için geçerlidir.


## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP boyutlandırma aracı](http://aka.ms/trisizingtool)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay iletme'yi yapılandırma](configure-event-forwarding.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md)

- - [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
