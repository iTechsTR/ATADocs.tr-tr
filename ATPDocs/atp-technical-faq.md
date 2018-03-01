---
title: "Azure Advanced Threat Protection sık sorulan sorular | Microsoft Docs"
description: "Azure ATP ve bunlarla ilişkili yanıtların hakkında sık sorulan sorular listesini sağlar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/27/2018
ms.topic: article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 6a9b5273-eb26-414e-9cdd-f64406e24ed8
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 6a6a34b9a2aae0e507fe18872a31368cf3f3e9d0
ms.sourcegitcommit: 21d8f9abf909fc5f0e0da03cd100fa8fb950baa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*

# <a name="azure-atp-frequently-asked-questions"></a>Azure ATP sık sorulan sorular
Bu makalede Azure ATP hakkında sık sorulan soruların listesi ve ve öngörülerle yanıtlar sağlar.


## <a name="where-can-i-get-a-license-for-azure-advanced-threat-protection-atp"></a>Azure Gelişmiş tehdit Koruması (ATP için) bir lisans nereden alabilirim?

İçin bir lisans Enterprise Mobility + Security 5 (EMS E5) Office 365 Portalı aracılığıyla doğrudan veya Bulut çözüm iş ortağı (CSP) lisans modeli aracılığıyla edinilen ve Azure ATP aracılığıyla Microsoft Toplu Lisanslama Merkezi (VLSC) erişimi yoksa, başvurun Azure Gelişmiş tehdit Koruması (ATP) etkinleştirmek için işlem almak için Microsoft müşteri desteği.

## <a name="what-should-i-do-if-the-azure-atp-sensor-or-standalone-sensor-doesnt-start"></a>Azure ATP algılayıcı veya tek başına algılayıcı başlamazsa ne yapmalıyım?
(Burada Azure ATP "Logs" klasörü altında yüklenir) geçerli hata günlüğünde en son hataya bakın.

## <a name="how-can-i-test-azure-atp"></a>Azure ATP nasıl test edebilirim?
Aşağıdaki komutu çalıştırarak bir uçtan uca test olarak kuşkulu etkinliklerin benzetimini yapabilirsiniz:

-  Nslookup.exe kullanarak DNS keşfi


Uzaktan izlenmekte olan etki alanı denetleyici çalıştırılmalı ve Azure ATP tek başına algılayıcı değil, bu gereklidir.


## <a name="does-azure-atp-work-with-encrypted-traffic"></a>Azure ATP şifrelenmiş trafikle çalışır mı?
Birden çok ağ protokolleri yanı sıra SIEM veya Windows Olay iletme yoluyla toplanan olayları analiz etme üzerinde Azure ATP kullanır. Şifrelenmiş trafik (örneğin, LDAPS ve IPSec) ile ağ protokollerini temel algılamaların analiz değil.


## <a name="does-azure-atp-work-with-kerberos-armoring"></a>Azure ATP Kerberos koruması ile çalışır mı?
Kerberos koruması, olarak da bilinen esnek kimlik doğrulaması güvenli tüneli (FAST), etkinleştirme atlayarak geçiş Kerberos koruması ile çalışmaz karma algılama dışında ATP tarafından desteklenir.

## <a name="how-many-azure-atp-sensors-do-i-need"></a>Kaç tane Azure ATP algılayıcılar ihtiyacım var mı?

Her etki alanı denetleyicisi ortamında bir ATP algılayıcı veya tek başına algılayıcı kapsamında. Daha fazla bilgi için bkz: [Azure ATP algılayıcı boyutlandırma](atp-capacity-planning.md#sizing). 


## <a name="why-are-certain-accounts-considered-sensitive"></a>Neden bazı hesaplar hassas kabul edilir?
Bir hesap hassas olarak atanan grupların üyesi olduğunda bu olur (örneğin: "Domain Admins").

Hesabın neden hassas olduğunu anlamak için, grup üyeliğini gözden geçirerek hangi hassas gruplara üye olduğunu anlayabilirsiniz (üyesi olduğu grup başka bir grup nedeniyle de hassas olabilir, dolayısıyla en yüksek düzeydeki hassas grubu belirleyene kadar aynı işlem yapılmalıdır). Ayrıca [etiketi hesapları gibi hassas el ile](sensitive-accounts.md).

## <a name="how-do-i-monitor-a-virtual-domain-controller-using-azure-atp"></a>Azure ATP kullanarak bir sanal etki alanı denetleyicisini nasıl izlerim?
Çoğu sanal etki alanı denetleyicileri Azure ATP algılayıcı Azure ATP algılayıcı ortamınız için uygun olup olmadığını belirlemek bkz tarafından konulabilecek [Azure ATP kapasite planlaması](atp-capacity-planning.md).

Bir sanal etki alanı denetleyicisi Azure ATP algılayıcı tarafından karşılanamayan, açıklandığı gibi iki sanal veya fiziksel Azure ATP tek başına algılayıcı olabilir [bağlantı noktası yansıtmayı yapılandırma](configure-port-mirroring.md).  <br />En kolay yolu, burada bir sanal etki alanı denetleyicisinin var olduğu her ana bilgisayarda sanal Azure ATP tek başına algılayıcı sağlamaktır.<br />Sanal etki alanı denetleyicileriniz ana bilgisayarlar arasında taşınıyorsa, aşağıdaki adımlardan birini gerçekleştirin gerekir:

-   Sanal etki alanı denetleyicisi başka bir ana bilgisayara taşındığında, son taşınan sanal etki alanı denetleyicisinden gelen trafiği almak için barındıran Azure ATP tek başına algılayıcısını önceden yapılandırın.
-   Taşındığında, Azure ATP tek başına algılayıcı onunla birlikte taşınması için sanal Azure ATP tek başına algılayıcı sanal etki alanı denetleyicisiyle ilişkilendirdiğinizden emin olun.
-   Ana bilgisayarlar arasında trafik gönderebilen bazı sanal anahtarlar vardır.


## <a name="what-can-azure-atp-detect"></a>Azure ATP neleri algılayabilir?

Azure ATP algılar bilinen kötü amaçlı saldırıları ve teknikleri, güvenlik sorunlarını ve riskleri.
Azure ATP algılamalarının tam listesi için bkz: [hangi algılamalar Azure ATP yapıyor mu?](suspicious-activity-guide.md).

## <a name="how-many-nics-does-the-azure-atp-standalone-sensor-require"></a>Azure ATP tek başına algılayıcı kaç NIC gerekir?
Azure ATP tek başına algılayıcı en az iki ağ bağdaştırıcısı gerekir:<br>1. İç ağ ve Azure ATP bulut hizmetine bağlanmak için bir NIC<br>2. Bağlantı noktası yansıtma aracılığıyla etki alanı denetleyicisinin ağ trafiğini yakalamak için kullanılan NIC.<br>* Bu yerel olarak tüm etki alanı denetleyicisini kullanan ağ bağdaştırıcıları kullanan Azure ATP algılayıcı için geçerli değildir.

## <a name="what-kind-of-integration-does-azure-atp-have-with-siems"></a>Ne tür bir tümleştirme Azure ATP ata'yla sıem'ler arasında var mı?
Azure ATP Sıem'lerden ile çift yönlü tümleştirme gibi sahiptir:

1. Azure ATP durumu uyarıları ve kuşkulu bir etkinlik algılandığında olduğunda CEF biçimini kullanan herhangi bir SIEM sunucusuna Syslog Uyarısı, gönderecek şekilde yapılandırılabilir.
2. Azure ATP Windows olayları Syslog iletileri alacak şekilde yapılandırılabilir [bu Sıem'lerden](configure-event-collection.md).

## <a name="how-do-i-configure-the-azure-atp-sensors-to-communicate-with-azure-atp-cloud-service-when-i-have-a-proxy"></a>Bir proxy sunucu varsa Azure ATP bulut hizmetiyle iletişim kurmak için Azure ATP algılayıcılar nasıl yapılandırırım?

Etki alanı denetleyicileriniz bulut hizmetiyle iletişim kurmak açmanız gerekir: *. güvenlik duvarı/proxy'de atp.azure.com bağlantı noktası 443'tür. Bunun nasıl yapılacağı hakkında yönergeler için bkz [proxy veya güvenlik duvarı ile Azure ATP algılayıcılar iletişimi etkinleştirmek için yapılandırma](configure-proxy.md).
 

## <a name="can-azure-atp-monitor-domain-controllers-virtualized-on-your-iaas-solution"></a>Azure ATP, Iaas çözümünüzde sanallaştırılmış etki alanı denetleyicilerini izleyebilir mi?
Evet, Azure ATP algılayıcı herhangi bir Iaas çözümündeki etki alanı denetleyicilerini izlemek için kullanabilirsiniz.

## <a name="is-this-going-to-be-a-part-of-azure-active-directory-or-on-premises-active-directory"></a>Azure Active Directory’nin mi yoksa şirket içi Active Directory’nin mi parçası olacak?
Bu şu anda bir tek başına bir çözümdür sunar. Azure Active Directory'nin parçası değil veya şirket içi Active Directory.

## <a name="do-you-have-to-write-your-own-rules-and-create-a-thresholdbaseline"></a>Kendi kurallarınızı yazmanız ve bir eşik/temel oluşturmanız gerekiyor mu?
Azure Gelişmiş tehdit koruması ile kurallar, eşikler veya temeller oluşturmanız ve ardından ince ayar yapmak için gerek yoktur. Azure ATP kullanıcıları, aygıtları ve kaynaklar arasındaki davranışları analiz eder — bunların birbirleriyle ilişkilerini yanı sıra — ve şüpheli etkinlikleri ve bilinen saldırıları hızla algılayabilir. Dağıtımdan, üç hafta sonra Azure ATP davranış açısından kuşkulu etkinlikleri algılamaya başlar. Diğer taraftan, Azure ATP dağıtımdan hemen sonra bilinen kötü amaçlı saldırıları ve güvenlik sorunlarını algılamaya başlar.

## <a name="does-this-only-leverage-traffic-from-active-directory"></a>Yalnızca Active Directory trafiğinden mi yararlanır?
Derin paket İnceleme teknolojisini kullanarak Active Directory trafiğini çözümlemenin, yanı sıra Azure ATP Ayrıca, güvenlik bilgileri ve Olay yönetimi (SIEM) ilgili olayları toplar ve Active Directory bilgilerini temel varlık profilleri oluşturur Etki Alanı Hizmetleri. Azure ATP algılayıcı kullanırsanız, bu olayları otomatik olarak ayıklar. Bu olaylar için Azure ATP tek başına algılayıcı göndermek için Windows Olay iletme'ı kullanabilirsiniz. Azure ATP alıcı RADIUS hesaplama (Microsoft, Cisco, F5 ve denetim noktası) çeşitli satıcılardan VPN günlükler de destekler.

## <a name="what-is-port-mirroring"></a>Bağlantı noktası yansıtma nedir?
SPAN (Anahtarlamalı Bağlantı Noktası Çözümleyicisi) olarak da bilinen bağlantı noktası yansıtma, bir ağ trafiği izleme yöntemidir. Bağlantı noktası yansıtma etkinleştirildiğinde, anahtar bir bağlantı noktasında görülen tüm ağ paketlerinin (veya VLAN’ın tamamının) kopyasını paketin çözümlenebileceği başka bir bağlantı noktasına gönderir.

## <a name="does-azure-atp-monitor-only-domain-joined-devices"></a>Azure ATP yalnızca etki alanına katılan cihazları mı izler?
Hayır. Azure ATP Windows dışı ve mobil cihazlar dahil olmak üzere Active Directory kimlik doğrulama ve yetkilendirme isteklerinde ağda tüm cihazları izler.

## <a name="does-azure-atp-monitor-computer-accounts-as-well-as-user-accounts"></a>Azure ATP kullanıcı hesaplarının yanı sıra bilgisayar hesaplarını izler?
Evet. Bilgisayar hesapları (aynı zamanda herhangi bir varlık) kötü amaçlı etkinlikler gerçekleştirmek için kullanılabilir olduğundan, Azure ATP tüm bilgisayar hesaplarının davranışlarını ve ortamdaki diğer tüm varlıkları izler.

## <a name="can-azure-atp-support-multi-domain-and-multi-forest"></a>Azure ATP birden çok etki alanını ve birden çok ormanı destekliyor mu?
Azure Advanced Threat Protection aynı orman sınırı içinde birden çok etki alanı ortamını destekler. Birden çok orman her orman için bir Azure ATP çalışma alanı gerektirir.

## <a name="can-you-see-the-overall-health-of-the-deployment"></a>Dağıtımın bir bütün olarak durumunu görebilir misiniz?
Evet, genel durumunu görüntülemek bunlar ortaya çıktığında dağıtım yanı sıra yapılandırması ile ilgili belirli sorunları, bağlantı, vb. ve uyarılırsınız.

## <a name="what-data-does-azure-atp-collect"></a>Hangi verilerin Azure ATP topluyor? 
Azure ATP toplar ve izleme ve raporlama amacıyla hizmet yönetimi için özel bir veritabanındaki bilgileri sunucularınızdan yapılandırılmış (etki alanı denetleyicileri, üye sunucuları, vb.) depolar. Toplanan bilgiler içerir (örneğin, Kerberos kimlik doğrulaması, NTLM kimlik doğrulaması, DNS sorgularını) etki alanı denetleyicileri, güvenlik günlükleri (örneğin, Windows Güvenlik olayları), gelen ve giden ağ trafiği Active Directory bilgilerini (yapısı, alt ağlar, siteler) ve varlık bilgilerini (örneğin, adları, e-posta adresleri ve telefon numaraları). 

Microsoft bu verileri kullanır: 

-   Proaktif olarak saldırı (IOAs), kuruluşunuzdaki göstergeleri tanımlayın 
-   Olası bir saldırı algılandı olursa uyarı oluştur 
-   Araştırmak ve ağdaki güvenlik tehditlerini varlığını keşfetmek etkinleştirme ağınızdan tehdit sinyalleri ilgili varlıklar görünüme güvenlik işletim sağlar. 

Microsoft, verilerinizin reklam için ya da hizmet sağlayan dışında başka herhangi bir amaçla benim değil. 

## <a name="do-i-have-the-flexibility-to-select-where-to-store-my-data"></a>Verilerimi depolanacağı yeri seçin esnekliğine var mı? 

Verilerinizi depolamak için seçebileceğiniz Azure ATP çalışma alanı oluştururken, Microsoft Azure veri merkezlerinde Amerika Birleşik Devletleri veya Avrupa verilerinizi depolamak üzere seçebilirsiniz. Yapılandırdıktan sonra verilerinin depolandığı konumun değiştiremezsiniz. Microsoft, veri belirtilen konumdan aktarım değil. 

## <a name="is-my-data-isolated-from-other-customer-data"></a>Diğer Müşteri verilerinden yalıtılır verilerim mi? 

Evet, verilerinizi erişimi kimlik doğrulaması ve müşteri tanımlayıcısına göre mantıksal ayırma aracılığıyla yalıtılır. Her bir müşteri yalnızca kendi kuruluş ve Microsoft tarafından sağlanan genel veri toplanan verilere erişebilir. 

## <a name="how-does-microsoft-prevent-malicious-insider-activities-and-abuse-of-high-privilege-roles"></a>Microsoft, kötü amaçlı kişinin etkinlikleri ve kötüye yüksek ayrıcalıklı rollerin nasıl engellediği? 

Microsoft geliştiricilerinin ve yöneticilerinin tasarım gereği, çalıştırmak ve hizmeti gelişmesi, atanan görevlerini gerçekleştirmek için yeterli ayrıcalıkları verilmiş. Microsoft önleyici, Dedektif ve aşağıdaki mekanizmalardan dahil olmak üzere reaktif denetimleri yetkisiz Geliştirici ve/veya yönetim etkinliği karşı korunmasına yardımcı olmak için birleşimleri dağıtır: 

-   Hassas bilgilere sıkı erişim denetimi 
-   Büyük ölçüde kötü amaçlı etkinliğin bağımsız algılamasını iyileştirmek denetimleri birleşimlerini 
-   İzleme, günlüğe kaydetme ve rapor, birden çok düzeyi 

Ayrıca, Microsoft arka plan doğrulama denetimleri belirli işlemleri personel yürütür ve uygulamaları, sistemleri ve arka plan doğrulama düzeyini orantılı olarak ağ altyapısı erişimi sınırlar. Müşterinin hesap veya ilgili bilgiler, görevlerini performans erişmek için gerekli olduğunda işlemleri personel resmi bir işlemi izleyin. 

## <a name="see-also"></a>Ayrıca bkz:
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
