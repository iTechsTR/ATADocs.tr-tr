---
title: Azure Advanced Threat Protection mimarisi | Microsoft Docs
description: "Azure Advanced Threat Analytics (ATP) mimarisini açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/27/2018
ms.topic: article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 90f68f2c-d421-4339-8e49-1888b84416e6
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: ffa58d4e6ca24773f7168dd94ad0596878eaf151
ms.sourcegitcommit: 21d8f9abf909fc5f0e0da03cd100fa8fb950baa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*


# <a name="azure-atp-architecture"></a>Azure ATP mimarisi
Azure Advanced Threat Protection mimarisi Bu diyagramda ayrıntılı olarak açıklanmıştır:

![Azure ATP mimarisi topoloji diyagramı](media/atp-architecture-topology.png)

Azure ATP fiziksel veya sanal anahtarlar kullanan bir Azure ATP tek başına algılayıcı için bağlantı noktası yansıtma yararlanarak, etki alanı denetleyicisi ağ trafiğinizi izler. Etki alanı denetleyicilerinizde doğrudan Azure ATP algılayıcı dağıtırsanız, bağlantı noktası yansıtma için gerekliliğini ortadan kaldırır. Ayrıca, Azure ATP (doğrudan etki alanı denetleyicileriniz veya bir SIEM sunucusundan iletilen) Windows olaylarını da kullanabilir ve saldırı ve tehdit verilerini analiz edin. Azure ATP Azure ATP tek başına algılayıcı ve Azure ATP algılayıcı ayrıştırılmış trafiği alır. Daha sonra ağınız hakkında bilgi edinmek, anomali algılamayı etkinleştirmek ve şüpheli etkinliklerde sizi uyarmak için profil oluşturma işlemini yapar, belirlenimci algılama çalıştırır, makine öğrenimi ve davranışsal algoritmaları çalıştırır.

Bu bölümde, ağ akışı ve olay yakalama açıklanmıştır ve aşağı ATP ana bileşenlerinin işlevleri ayrıntılı açıklanmıştır: (hangi Azure ATP tek başına algılayıcı aynı çekirdek işlevlere sahiptir) Azure ATP algılayıcı, Azure ATP tek başına algılayıcısı ve Azure ATP bulut hizmeti. 

## <a name="azure-atp-components"></a>Azure ATP bileşenleri
Azure ATP aşağıdaki bileşenlerden oluşur:

-   **Azure ATP çalışma Yönetim Portalı** <br>
Azure ATP çalışma Yönetim Portalı'nı çalışma alanları oluşturmanıza olanak tanır ve diğer Microsoft Hizmetleri ile tümleştirme sağlar.

> [!NOTE]
> Yalnızca tek bir Active Directory ormanındaki algılayıcılar tek bir çalışma alanına bağlanabilir.

-   **Azure ATP çalışma portalı** <br>
Azure ATP çalışma portal ATP algılayıcılar ve tek başına algılayıcılar veri alır. İzler, yönetir ve ortamınızdaki tehditlere araştırır.

-   **Azure ATP algılayıcısı**<br>
Azure ATP algılayıcı doğrudan etki alanı denetleyicilerinize yüklenir ve ayrılmış bir sunucuya veya bağlantı noktası yansıtmaya gerek kalmadan bunların trafiğini doğrudan izler. 

-   **Azure ATP tek başına algılayıcısı**<br>
Azure ATP tek başına algılayıcı, bağlantı noktası yansıtmayı ya da ağ Tap'kullanarak etki alanı denetleyicilerinizden gelen trafiği izleyen ayrılmış bir sunucuya yüklenir. Azure ATP algılayıcı için bir alternatiftir.

## <a name="deployment-options"></a>Dağıtım seçenekleri
Azure algılayıcılar aşağıdaki birleşimini kullanarak ATP dağıtabilirsiniz:

-   **Yalnızca Azure ATP algılayıcılar kullanma**<br>
Azure ATP dağıtımınız yalnızca Azure ATP algılayıcılar içerebilir: Azure ATP algılayıcılar, her etki alanı denetleyicisi ve ek sunucu üzerinde dağıtıldığı veya bağlantı noktası yansıtma yapılandırması gereklidir.

-   **Yalnızca Azure ATP tek başına algılayıcılar kullanma** <br>
Azure ATP dağıtımınız yalnızca Azure ATP tek başına algılayıcılar, tüm Azure ATP algılayıcılar olmadan içerebilir: tüm etki alanı denetleyicilerinin bir Azure ATP tek başına algılayıcı için bağlantı noktası yansıtmaya olanak verecek şekilde yapılandırılması gerekir veya ağ Tap'ları bulunması gerekir.

-   **Azure ATP tek başına algılayıcılar ve Azure ATP algılayıcılar kullanma**<br>
Azure ATP dağıtımınızı Azure ATP tek başına algılayıcılar ve Azure ATP algılayıcılar içerir. Azure ATP algılayıcılar bazı etki alanı denetleyicileriniz (örneğin, tüm etki alanı denetleyicileri şubelerinizdeki) yüklenir. Aynı zamanda diğer etki alanı denetleyicilerine Azure ATP tek başına algılayıcılar (örneğin, ana veri merkezlerinizdeki daha büyük etki alanı denetleyicileri) tarafından izlenir.


### <a name="azure-atp-workspace-management-portal"></a>Azure ATP çalışma Yönetim Portalı

Azure ATP çalışma Yönetim Portalı sağlar:

-   Oluşturma ve Azure ATP çalışma alanlarını yönetme

-   Diğer Microsoft güvenlik hizmetleriyle tümleştirme

Ana çalışma alanı olarak ayarla **birincil**. Yalnızca bir çalışma alanı birincil olarak ayarlanabilir. Bir çalışma alanı birincil olarak etkileri tümleştirmeler - ayarını, yalnızca Azure ATP Windows Defender ATP için birincil çalışma alanınızda tümleştirebilirsiniz. Hangi çalışma alanının birincil daha sonra geçerli birincil çalışma alanı için zaten ayarlanmış tümleştirmeler kaldırmak zorunda şekilde yapmak amacıyla ancak olduğunu değiştirebilirsiniz.

> [!NOTE]
> Azure ATP şu anda iki çalışma alanları oluşturmayı destekler. Üretim ortamınıza ve hazırlık ortamı olarak ek bir çalışma alanı için birincil çalışma oluşturmanız önerilir.

### <a name="azure-atp-workspace-portal"></a>Azure ATP çalışma portalı

Azure ATP çalışma alanı aşağıdaki Azure ATP işlevleri yönetmenizi sağlar:

-   Azure ATP algılayıcı ve tek başına algılayıcı yapılandırma ayarlarını yönet

-   Azure ATP tek başına algılayıcılar ve Azure ATP algılayıcılar alınan verilerini görüntüleme 

-   İzleyici anormal davranışlarını algılamak için davranış makine öğrenme altyapılarını ve saldırı sonlandırma zincirine dayalı olarak Gelişmiş saldırıları algılamak için belirleyici algoritmaları göre şüpheli etkinlikler algılandı

-   İsteğe bağlı: çalışma alanı Yönetim Portalı'nı e-posta ve şüpheli etkinlikler veya sistem durumu olayları algılandığında olayları göndermek üzere yapılandırılabilir.


|||
|-|-|
|Varlık Alıcısı|Tüm Azure ATP algılayıcılar ve Azure ATP tek başına algılayıcılar varlık yığınlarını alır.|
|Ağ Etkinliği İşlemcisi|Alınan her yığın içindeki tüm ağ etkinliklerini işler. Örneğin, farklı bilgisayarlardan gerçekleştirilmiş olabilecek çeşitli Kerberos adımları arasında eşleştirme yapar|
|Varlık Profili Oluşturucu|Trafiğe ve olaylara göre tüm Benzersiz Varlıkların profilini oluşturur. Örneğin, Azure ATP oturum açan her kullanıcı profili için bilgisayarların listesini güncelleştirir.|
|Azure ATP çalışma Yönetim Portalı|Azure ATP alanlarınızı yönetir.|
|Azure ATP çalışma portalı|Azure ATP çalışma Azure ATP yapılandırmak ve Azure ATP tarafından ağınızda algılanan kuşkulu etkinlikleri izlemek için kullanılır. Azure ATP çalışma üzerinde Azure ATP algılayıcı bağımlı değildir ve hatta Azure ATP algılayıcı hizmet durdurulduğunda çalıştırır. |
|Algılayıcılar|Algılayıcılar ağınızdaki kuşkulu etkinlikleri ve anormal kullanıcı davranışlarını bulmak için makine öğrenme altyapılarını ve belirlenimci kuralları kullanır.|

Aşağıdaki ölçütleri ağınızda dağıtmak için kaç tane Azure ATP çalışma alanları karar verirken göz önünde bulundurun:

-   Bir Azure ATP çalışma tek bir Active Directory ormanı izleyebilirsiniz. Birden fazla Active Directory ormanınız varsa, bir Azure ATP bulut hizmeti Active Directory orman başına en az gerekir.


## <a name="azure-atp-sensor-and-azure-atp-standalone-sensor"></a>Azure ATP algılayıcı ve Azure ATP tek başına algılayıcısı

**Azure ATP algılayıcı** ve **Azure ATP algılayıcı** her ikisi de aynı çekirdek işlevlere sahiptir:

-   Etki alanı denetleyicisi ağ trafiğini yakalayıp denetleyin. Azure ATP tek başına algılayıcılar için bağlantı noktası yansıtılmış trafik ve Azure ATP algılayıcılar yer alan etki alanı denetleyicisinin yerel trafiği budur. 

-   Doğrudan (için ATP algılayıcılar) etki alanı denetleyicilerinden veya SIEM veya Syslog sunucusu (ATP tek başına algılayıcılar) Windows olaylarını alma

-  VPN sağlayıcınızdan RADIUS hesap bilgilerini alma

-   Active Directory etki alanından kullanıcılar ve bilgisayarlar hakkındaki verileri alma

-   Ağ varlıklarının (kullanıcılar, gruplar ve bilgisayarlar) çözümlemesini yapma

-   Azure ATP bulut hizmetine ilgili veri aktarımı

-   Tek bir Azure ATP tek başına algılayıcı birden çok etki alanı denetleyicilerini izlemek veya bir Azure ATP algılayıcı tek etki alanı denetleyicisi izleyin.

Azure ATP tek başına algılayıcı ağınızdan ağ trafiğini ve Windows olaylarını alır ve aşağıdaki ana bileşenlerde işler:

|||
|-|-|
|Ağ Dinleyicisi|Ağ dinleyicisi, ağ trafiğini yakalar ve trafiği ayrıştırır. Dolayısıyla denetlemek özellikle önemlidir bu yoğun CPU kullanan bir görev olduğundan [Azure ATP Önkoşullar](atp-prerequisites.md) Azure ATP algılayıcı veya Azure ATP tek başına algılayıcı planlarken.|
|Olay Dinleyicisi|Olay dinleyicisi yakalar ve ağınızdaki SIEM sunucusundan iletilen Windows olaylarını ayrıştırır.|
|Windows Olay Günlüğü Okuyucusu|Windows olay günlüğü okuyucusu okur ve Windows Azure ATP tek başına algılayıcının Windows olay günlüğü için etki alanı denetleyicilerinden iletilen olaylar ayrıştırır.|
|Ağ Etkinliği Çeviricisi | Ayrıştırılmış trafiği Azure ATP (NetworkActivity) tarafından kullanılan trafiğin mantıksal gösterimine çevirir.
|Varlık Çözümleyicisi|Varlık Çözümleyicisi ayrıştırılan verileri (ağ trafiği ve olaylar) alır, sonra da hesap ve kimlik bilgilerini bulmak için bunları Active Directory ile çözümler. Ardından bunlar ayrıştırılan verilerde bulunan IP adresleriyle eşleştirilir. Varlık Çözümleyicisi, makine adları, özellikler ve kimlikler için kimlik doğrulama paketlerinin ayrıştırılabilmesi için, paket üst bilgilerini verimli bir şekilde inceler. Varlık Çözümleyicisi ayrıştırılmış kimlik doğrulama paketlerini gerçek paketteki verilerle birleştirir.|
|Varlık Göndericisi|Varlık göndericisi ayrıştırılmış ve eşleştirilmiş verileri Azure ATP bulut hizmetine gönderir.|

## <a name="azure-atp-sensor-features"></a>Azure ATP algılayıcı özellikleri

Aşağıdaki özellikler, Azure ATP tek başına algılayıcı veya bir Azure ATP algılayıcı çalıştıran bağlı olarak farklı şekilde çalışır.

-   Azure ATP algılayıcı yerel olarak olayları Olay iletme özelliğini yapılandırmak zorunda kalmadan okuyabilir.

-   **Etki alanı eşitleyici adayı**<br>
Etki alanı Eşitleyici adayı belirli bir Active Directory etki alanından tüm varlıkların önceden tedbirli olarak eşitlenmesinden sorumludur (etki alanı denetleyicileri kendileri için çoğaltma tarafından kullanılan mekanizma benzer). Bir algılayıcı adaylar listesinden, etki alanı Eşitleyici görevi görmesi için rastgele seçilir. <br><br>
Eşitleyici 30 dakikadan fazla çevrimdışı olursa, bunun yerine başka bir aday seçilir. Belirli bir etki alanı için etki alanı Eşitleyici yoksa, izlenen trafikte algılanan gibi yeni varlıklar Azure ATP alır ancak Azure ATP proaktif olarak varlıkları ve değişikliklerini eşitleyemez. 
<br>Bununla ilgili trafik olmayan bir varlık için arama yapın ve etki alanı Eşitleyici kullanılabilir değilse, hiçbir arama sonuçları görüntülenir.<br><br>
Varsayılan olarak, tüm Azure ATP tek başına algılayıcılar Eşitleyici adaylardır.<br><br>
Azure ATP algılayıcılar varsayılan olarak Eşitleyici adayı değildir.


-   **Kaynak sınırlamaları**<br>
Azure ATP algılayıcı üzerinde çalıştığı etki alanı denetleyicisindeki kullanılabilir bilgi işlem ve bellek kapasitesini değerlendiren bir izleme bileşeni içerir. İzleme işlemi 10 saniyede çalışır ve herhangi bir anda zaman, en az % 15 boş bilgi işlem ve bellek kaynakları etki alanı denetleyicisi olduğundan emin olmak için Azure ATP algılayıcı işlem CPU ve bellek kullanım kotasını dinamik olarak güncelleştirir.<br><br>
Etki alanı denetleyicisinde ne olursa olsun, bu işlem etki alanı denetleyicisinin çekirdek işlevlerinin etkilenmemesini sağlamak için her zaman kaynakları serbest bırakır.<br><br>
Bu Azure ATP algılayıcı kalmasına neden olursa, trafiğin yalnızca bir kısmı izlenir ve sağlık durumu sayfasında izleme uyarı "bağlantı noktası yansıtılan ağ trafiği bırakıldı" görünür.

Aşağıdaki tabloda, tüm trafiğin izlenmesi için halen gerekli olandan daha büyük kotaya izin verecek kadar bilgi işlem kaynağına sahip bir etki alanı denetleyicisi örneği görülmektedir:

> [!div class="mx-tableFixed"]
||||||
|-|-|-|-|-|
|Active Directory (Lsass.exe)|Azure ATP algılayıcısı (Microsoft.Tri.sensor.exe)|Çeşitli (diğer işlemler) |Azure ATP algılayıcı kota|Algılayıcı trafiği bırakılıyor|
|30%|20%|%10|45%|Hayır|

Active Directory daha fazla bilgi işlem gücü gerekiyorsa, Azure ATP algılayıcı tarafından gerekli kota azalır. Aşağıdaki örnekte, Azure ATP algılayıcı birden çok ayrılmış kotasını gerekir ve bazı (yalnızca kısmi trafiği izleme) trafiği bırakır:

> [!div class="mx-tableFixed"]
||||||
|-|-|-|-|-|
|Active Directory (Lsass.exe)|Azure ATP algılayıcısı (Microsoft.Tri.sensor.exe)|Çeşitli (diğer işlemler) |Azure ATP algılayıcı kota|Algılayıcı trafiği bırakılıyor|
|60%|15%|%10|15%|Evet|


## <a name="your-network-components"></a>Ağ bileşenleriniz
Azure ATP ile çalışmak için aşağıdaki bileşenler ayarlanır denetlediğinizden emin olun.

### <a name="port-mirroring"></a>Bağlantı noktası yansıtma
Azure ATP tek başına algılayıcılar kullanıyorsanız, izlenen ve Azure ATP tek başına algılayıcı fiziksel veya sanal anahtarlar kullanan hedef olarak ayarlayın etki alanı denetleyicileri yansıtma bağlantı noktasına ayarlamanız gerekir. Başka bir seçenek de ağ TAP’ları kullanmaktır. Azure ATP bazıları çalışır, ancak tüm etki alanı denetleyicileriniz izlenir, ancak algılamalar daha az etkili.

Bağlantı noktası yansıtma tüm etki alanı denetleyicisi ağ trafiğinin Azure ATP tek başına algılayıcı yansıtsa da bu trafiğin yalnızca küçük bir yüzdesi yapılır ve ardından gönderilen sıkıştırılmış, Azure ATP çözümleme için bulut hizmeti.

Etki alanı denetleyicileriniz ve Azure ATP tek başına algılayıcılar fiziksel veya sanal olabilir. Daha fazla bilgi için bkz: [bağlantı noktası yansıtmayı yapılandırma](configure-port-mirroring.md).


### <a name="events"></a>Olaylar
Pass--Hash, deneme yanılma saldırısı, hassas gruplarını, şüpheli Hizmetleri oluşturulmasını, bal kapları değişiklikleri değişiklik Azure ATP algılamasını iyileştirmek için aşağıdaki Windows olaylarını Azure ATP gerekir: 4776, 4732, 4733, 4728, 4729, 4756, 4757 ve 7045. Bu da otomatik olarak Azure ATP algılayıcı tarafından okunabilen veya Azure ATP algılayıcı dağıtılmaz durumunda bunu iki yoldan biriyle Azure ATP tek başına algılayıcı Azure ATP tek başına algılayıcı SIEM olaylarını dinleyecek şekilde yapılandırarak veya iletilebilir[Windows Olay iletme özelliğini yapılandırma](configure-event-forwarding.md).

-   Azure ATP tek başına algılayıcı SIEM olaylarını dinleyecek şekilde yapılandırma <br>SIEM'iniz belirli Windows olaylarını ATP için iletecek şekilde yapılandırın. Azure ATP bir dizi SIEM satıcısını destekler. Daha fazla bilgi için bkz: [Olay iletme özelliğini yapılandırma](configure-event-forwarding.md).

-   Windows Olay İletme’yi yapılandırma<br>Azure ATP'ın olaylarınızı almasının başka bir etki alanı denetleyicilerinizi Windows olay 4776, 4732, 4733, 4728, 4729, 4756, 4757 ve Azure ATP tek başına algılayıcı 7045 iletecek şekilde yapılandırarak yoludur. Bu, bir sıem'iniz olmadığında veya SIEM'iniz şu anda ATP tarafından desteklenmiyorsa özellikle yararlıdır. Windows Olay iletme ATP içinde hakkında daha fazla bilgi için bkz: [Windows Olay iletme özelliğini yapılandırma](configure-event-forwarding.md). Bu yalnızca - Azure ATP algılayıcı için fiziksel Azure ATP tek başına algılayıcılar geçerlidir.


## <a name="see-also"></a>Ayrıca bkz:
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP boyutlandırma aracı](http://aka.ms/trisizingtool)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay iletme özelliğini yapılandırma](configure-event-forwarding.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md)

- - [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
