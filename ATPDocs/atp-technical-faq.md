---
title: Azure Gelişmiş tehdit koruması hakkında sık sorulan sorular | Microsoft Docs
description: Azure ATP ve bunlarla ilişkili yanıtların hakkında sık sorulan soruların listesini sunar
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/13/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 6a9b5273-eb26-414e-9cdd-f64406e24ed8
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 6550f6b6575af56eab7de911b22b1e4f27cff0f3
ms.sourcegitcommit: 121c49d559e71741136db1626455b065e8624ff9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2018
ms.locfileid: "41734722"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*

# <a name="azure-atp-frequently-asked-questions"></a>Azure ATP sık sorulan sorular
Bu makalede, Azure ATP hakkında sık sorulan soruların listesini sunar ve öngörülerle yanıtlar sağlanır.


## <a name="where-can-i-get-a-license-for-azure-advanced-threat-protection-atp"></a>Azure Gelişmiş tehdit Koruması (ATP için) bir lisans nereden alabilirim?

Enterprise Mobility + Security (EMS E5) 5 için doğrudan aracılığıyla lisans [Office 365 portalında](https://www.microsoft.com/cloud-platform/enterprise-mobility-security-pricing) veya Cloud Solution Partner (CSP) lisans modeli aracılığıyla.                  

## <a name="what-should-i-do-if-the-azure-atp-sensor-or-standalone-sensor-doesnt-start"></a>Azure ATP algılayıcı veya tek başına algılayıcı başlatılmazsa ne yapmalıyım?
En son hata geçerli hataya bakın [günlük](troubleshooting-atp-using-logs.md) ("Logs" klasörü altında olduğu Azure ATP yüklü).

## <a name="how-can-i-test-azure-atp"></a>Azure ATP nasıl test edebilirim?
Bir uçtan uca test olarak kuşkulu etkinliklerin benzetimini yapabilirsiniz. Aşağıdaki senaryoda, DNS keşfi kullanılmıştır:

1.  Azure ATP doğrula algılayıcılardan yüklenmiş ve yapılandırılmış etki alanı denetleyicilerinde (veya tek başına algılayıcı ve ilişkili bağlantı noktası yansıtma yüklenir ve yapılandırılır)
2.  Açık CMD
3.  Aşağıdaki komutu çalıştırın: nslookup -<DC iP address>
    1.  Enter tuşuna basın
    2.  : -D türüdür <FQDN>
    3.  Ortamınızın yapılandırmasına bağlı olarak, DNS kayıtlarınızı listesine yanıtları "Sorgu reddetti" değişir. 
4. Azure ATP konsolunda sanal DNS keşfi ilgili uyarıyı görüntüleyin. 

## <a name="does-azure-atp-work-with-encrypted-traffic"></a>Azure ATP şifrelenmiş trafikle çalışır mı?
Azure ATP birden çok ağ protokolleri yanı sıra SIEM veya Windows Olay iletme aracılığıyla toplanan olaylara çözümleme üzerinde kullanır.  Ağ protokolleri (örneğin LDAPS ve IPSec gibi) şifrelenmiş trafik ile şifresi, ancak analiz edilir.


## <a name="does-azure-atp-work-with-kerberos-armoring"></a>Azure ATP Kerberos koruması ile çalışır mı?
Kerberos koruması, olarak da bilinir esnek kimlik doğrulaması güvenli tüneli (FAST) etkinleştirme atlayarak Kerberos koruması ile çalışmaz hash algılamasının dışında ATP tarafından desteklenir.

## <a name="how-many-azure-atp-sensors-do-i-need"></a>Kaç tane Azure ATP algılayıcı ihtiyacım var?

Her etki alanı denetleyicisi ortamında, bir ATP algılayıcı veya tek başına algılayıcı tarafından anlatılmıştır. Daha fazla bilgi için [Azure ATP algılayıcısını boyutlandırma](atp-capacity-planning.md#sizing). 


## <a name="why-are-certain-accounts-considered-sensitive"></a>Neden bazı hesaplar hassas kabul edilir?
Böyle bir hesap, hassas olarak ayarlanmış grupların üyesi olduğunda (örneğin: "Domain Admins").

Hesabın neden hassas olduğunu anlamak için, grup üyeliğini gözden geçirerek hangi hassas gruplara üye olduğunu anlayabilirsiniz (üyesi olduğu grup başka bir grup nedeniyle de hassas olabilir, dolayısıyla en yüksek düzeydeki hassas grubu belirleyene kadar aynı işlem yapılmalıdır). Ayrıca [etiketi hesapları gibi hassas el ile](sensitive-accounts.md).

## <a name="how-do-i-monitor-a-virtual-domain-controller-using-azure-atp"></a>Azure ATP kullanarak bir sanal etki alanı denetleyicisini nasıl izlerim?
Çoğu sanal etki alanı denetleyicilerini Azure ATP algılayıcısı ortamınız için uygun olup olmadığını belirlemek için Azure ATP algılayıcı tarafından ele alınacak [Azure ATP kapasite planlaması](atp-capacity-planning.md).

Bir sanal etki alanı denetleyicisi tarafından Azure ATP algılayıcısını alınamıyorsa açıklandığı ya da bir sanal veya fiziksel Azure ATP tek başına algılayıcı olabilir [bağlantı noktası yansıtmayı yapılandırma](configure-port-mirroring.md).  <br />En kolay yolu, bir sanal etki alanı denetleyicisini mevcut olduğu her bir konakta sanal Azure ATP tek başına algılayıcı sağlamaktır.<br />Sanal etki alanı denetleyicileriniz ana bilgisayarlar arasında taşınıyorsa, aşağıdaki adımlardan birini gerçekleştirin gerekir:

-   Sanal etki alanı denetleyicisi başka bir konağa taşındığında, Azure ATP tek başına algılayıcı son taşınan etki alanı denetleyicisinden gelen trafiği almak için bu ana bilgisayarda önceden yapılandırın.
-   Taşınırsa, Azure ATP tek başına algılayıcı ile sanal Azure ATP tek başına algılayıcı sanal etki alanı denetleyicisiyle ilişkilendirdiğinizden emin emin olun.
-   Ana bilgisayarlar arasında trafik gönderebilen bazı sanal anahtarlar vardır.


## <a name="what-can-azure-atp-detect"></a>Hangi Azure ATP algılayabilir?

Azure ATP algılar bilinen kötü amaçlı saldırıları ve teknikleri, güvenlik sorunlarını ve riskleri.
Azure ATP algılamalarının tam listesi için bkz. [Azure ATP hangi algılamaları gerçekleştirir?](suspicious-activity-guide.md).

## <a name="how-many-nics-does-the-azure-atp-standalone-sensor-require"></a>Azure ATP tek başına algılayıcı kaç NIC gerektiriyor mu?
Azure ATP tek başına algılayıcı en az iki ağ bağdaştırıcısı gerekir:<br>1. İç ağ ve Azure ATP bulut hizmetine bağlanmak için bir NIC<br>2. Bir NIC bağlantı noktası yansıtma aracılığıyla etki alanı denetleyicisinin ağ trafiğini yakalamak için kullanılır.<br>* Bu, tüm etki alanı denetleyicisi kullanan ağ bağdaştırıcılarının yerel olarak kullanan Azure ATP algılayıcısını uygulanmaz.

## <a name="what-kind-of-integration-does-azure-atp-have-with-siems"></a>Azure ATP ata'yla sıem'ler arasında ne tür bir tümleştirme var mı?
Azure ATP şu şekilde bir çift yönlü tümleştirme sıem'lerle sahiptir:

1. Azure ATP sistem durumu uyarıları ve şüpheli bir etkinlik algılandığında olduğunda CEF biçimini kullanarak herhangi bir SIEM sunucusuna Syslog Uyarısı, gönderecek şekilde yapılandırılabilir.
2. Azure ATP Windows olayları için Syslog iletileri alacak şekilde yapılandırılabilir [bu Sıem'lerden](configure-event-collection.md).

## <a name="how-do-i-configure-the-azure-atp-sensors-to-communicate-with-azure-atp-cloud-service-when-i-have-a-proxy"></a>Bir proxy olduğunda Azure ATP bulut hizmetiyle iletişim kurmak için Azure ATP algılayıcı nasıl yapılandırabilirim?

Etki alanı denetleyicilerinizin bulut hizmetiyle iletişim kurmak açmanız gerekir: *. güvenlik duvarı/proxy'sinde atp.azure.com bağlantı noktası 443'tür. Bunun nasıl yapılacağı hakkında yönergeler için bkz [Ara sunucunuzda veya güvenlik duvarı Azure ATP algılayıcı ile iletişimi etkinleştirmek için yapılandırma](configure-proxy.md).
 

## <a name="can-azure-atp-monitor-domain-controllers-virtualized-on-your-iaas-solution"></a>Azure ATP, Iaas çözümünüzde sanallaştırılan etki alanı denetleyicilerini izleyebilir mi?
Evet, Azure ATP algılayıcısını herhangi bir Iaas çözümündeki etki alanı denetleyicilerini izlemek için kullanabilirsiniz.

## <a name="is-this-going-to-be-a-part-of-azure-active-directory-or-on-premises-active-directory"></a>Azure Active Directory’nin mi yoksa şirket içi Active Directory’nin mi parçası olacak?
Bu çözüm, şu anda tek başına sunulan teklifidir. Azure Active Directory bir parçası değil veya şirket içi Active Directory'nin.

## <a name="do-you-have-to-write-your-own-rules-and-create-a-thresholdbaseline"></a>Kendi kurallarınızı yazmanız ve bir eşik/temel oluşturmanız gerekiyor mu?
Azure Gelişmiş tehdit koruması ile kurallar, eşikler veya temeller oluşturmanız ve sonra bunların ince ayarını gerek yoktur. Azure ATP analiz eder, kullanıcılar, cihazlar ve kaynaklar arasındaki davranışları — hem de bunların birbirleriyle — ve şüpheli etkinlikleri ve bilinen saldırıları hızla algılayabilir. Üç hafta dağıtımdan sonra Azure ATP davranış açısından kuşkulu etkinlikleri algılamaya başlar. Öte yandan, Azure ATP dağıtımdan hemen sonra bilinen kötü amaçlı saldırıları ve güvenlik sorunlarını algılamaya başlar.

## <a name="does-this-only-leverage-traffic-from-active-directory"></a>Yalnızca Active Directory trafiğinden mi yararlanır?
Derin paket İnceleme teknolojisini kullanarak Active Directory trafiğini analiz etme, yanı sıra Azure ATP Ayrıca, güvenlik bilgileri ve Olay yönetimi (SIEM) ilgili olayları toplar ve Active Directory bilgilerini temel varlık profilleri oluşturur Etki Alanı Hizmetleri. Azure ATP algılayıcısını kullanırsanız, bu olayları otomatik olarak ayıklar. Azure ATP tek başına algılayıcı için bu olayları göndermek için Windows Olay iletme'yi kullanabilirsiniz. Azure ATP VPN günlüklerini (Microsoft, Cisco, F5 ve kontrol noktası), farklı satıcıların sunduğu alıcı RADIUS hesaplamaları da destekler.

## <a name="what-is-port-mirroring"></a>Bağlantı noktası yansıtma nedir?
SPAN (Anahtarlamalı Bağlantı Noktası Çözümleyicisi) olarak da bilinen bağlantı noktası yansıtma, bir ağ trafiği izleme yöntemidir. Bağlantı noktası yansıtma etkinleştirildiğinde, anahtar bir bağlantı noktasında görülen tüm ağ paketlerinin (veya VLAN’ın tamamının) kopyasını paketin çözümlenebileceği başka bir bağlantı noktasına gönderir.

## <a name="does-azure-atp-monitor-only-domain-joined-devices"></a>Azure ATP yalnızca etki alanına katılan cihazları mı izler?
Hayır. Azure ATP olmayan Windows ve mobil cihazları dahil olmak üzere Active Directory kimlik doğrulama ve yetkilendirme istekler gerçekleştiren ağdaki tüm cihazları izler.

## <a name="does-azure-atp-monitor-computer-accounts-as-well-as-user-accounts"></a>Azure ATP kullanıcı hesaplarının yanı sıra bilgisayar hesaplarını izler?
Evet. Azure ATP, bilgisayar hesapları (yanı sıra diğer tüm varlıklar), kötü amaçlı etkinlik gerçekleştirmek için kullanılabilir olmadığından, tüm bilgisayar hesaplarının davranışlarını ve ortamdaki diğer tüm varlıkları izler.

## <a name="can-azure-atp-support-multi-domain-and-multi-forest"></a>Azure ATP birden çok etki alanını ve birden çok ormanı destekler?
Azure Gelişmiş tehdit koruması, çok etki alanlı ortamları ve birden çok ormanı destekler. Bu özellik şu anda genel Önizleme aşamasındadır. Daha fazla bilgi ve bilinen sınırlamalar için bkz. [çok ormanlı Destek](atp-multi-forest.md).

## <a name="can-you-see-the-overall-health-of-the-deployment"></a>Dağıtımın bir bütün olarak durumunu görebilir misiniz?
Evet, genel sistem durumunu görüntüleyebilirsiniz oluşunca dağıtım yanı sıra yapılandırması ile ilgili belirli sorunları, bağlantı vb. ve uyarılırsınız.

## <a name="what-data-does-azure-atp-collect"></a>Azure ATP hangi verileri toplar? 
Azure ATP toplar ve izleme ve raporlama amacıyla hizmet yönetimi için özel bir veritabanındaki bilgileri yapılandırılmış sunucularınıza (etki alanı denetleyicileri, üye sunucuları vb.) depolar. Toplanan bilgiler içerir (örneğin, Kerberos kimlik doğrulaması, NTLM kimlik doğrulaması, DNS sorguları) etki alanı denetleyicileri, güvenlik günlükleri (örneğin, Windows Güvenlik olayları), gelen ve giden ağ trafiği Active Directory bilgilerini (yapısı, alt ağlar, siteler) ve varlık bilgilerini (örneğin, adları, e-posta adresi ve telefon numaraları). 

Microsoft bu verileri kullanır: 

-   Proaktif olarak saldırı (IOAs), kuruluşunuzdaki göstergeleri tanımlayın 
-   Olası bir saldırı algılanırsa uyarı oluştur 
-   Güvenlik sürecinizin araştırmanıza ve ağdaki güvenlik tehditlerini varlığını keşfedin etkinleştirme ağınızdan tehdit sinyalleri için ilgili varlıklar bir görünümünü sağlar. 

Microsoft, verilerinizin size hizmet sağlanması dışındaki başka bir amaç için veya reklam için benim değil. 

## <a name="do-i-have-the-flexibility-to-select-where-to-store-my-data"></a>Verilerim depolanacağı yeri seçme esnekliğine var mı? 

Verilerinizi depolamak için seçebileceğiniz Azure ATP çalışma alanı oluştururken, Microsoft Azure veri merkezlerinde Amerika Birleşik Devletleri veya Avrupa verilerinizi depolamak seçebilirsiniz. Yapılandırıldıktan sonra verilerin depolandığı konumu değiştirilemiyor. Microsoft, belirtilen konumdan veri aktarılmaz. 

## <a name="is-my-data-isolated-from-other-customer-data"></a>Diğer Müşteri verilerinden yalıtılmış verilerim mi? 

Evet, verilerinize erişimi kimlik doğrulaması ve mantıksal ayrım müşteri tanımlayıcısına göre yalıtılır. Her müşteri yalnızca kendi kuruluş ve Microsoft'un sunduğu genel veri toplanan verilere erişebilir. 

## <a name="how-does-microsoft-prevent-malicious-insider-activities-and-abuse-of-high-privilege-roles"></a>Microsoft kötü amaçlı etkinlikleri ve kötüye kullanımı yüksek ayrıcalıklı rollerin nasıl önlemek? 

Microsoft geliştiricilerinin ve yöneticilerinin tasarım gereği, çalıştırmak ve hizmeti geliştirmek için atanan görevlerini gerçekleştirmek için yeterli ayrıcalıkları verilmiş olan. Microsoft, önleyici, Dedektif ve aşağıdaki mekanizmalardan dahil olmak üzere reaktif denetimleri yetkisiz Geliştirici ve/veya yönetim etkinliği karşı korumaya yardımcı olmak için birleşimleri dağıtır: 

-   Hassas verilere sıkı erişim denetimi 
-   Kötü amaçlı etkinlik bağımsız algılama büyük ölçüde geliştiren denetimleri birleşimleri 
-   Birden çok düzeyde izleme, günlüğe kaydetme ve Raporlama 

Ayrıca, Microsoft, belirli bir operasyon personeli arka plan doğrulama denetimleri yapar ve uygulamalar, sistemler ve ağ altyapısını arka plan doğrulama düzeyini derlemekten erişimi sınırlar. Operasyon personeli, müşterinin hesap veya ilgili bilgiler, görevlerini performansını erişmek için gerekli olduğunda resmi bir işlemi izleyin. 

## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
