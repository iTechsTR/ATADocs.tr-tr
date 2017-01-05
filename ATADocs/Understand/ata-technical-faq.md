---
title: "ATA hakkında Sık sorulan sorular | Microsoft Docs"
description: "ATA hakkında sık sorulan soruların ve bunlarla ilişkili yanıtların listesini sağlar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: a7d378ec-68ed-4a7b-a0db-f5e439c3e852
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 85e285c5d88e5916e0bf0eb7dd327cb4cb45b4cb
ms.openlocfilehash: f806437df3a2c581631e924798a367e5e48be6f8


---
*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*

# <a name="ata-frequently-asked-questions"></a>ATA sık sorulan sorular
Bu makalede, ATA hakkında sık sorulan soruların listesi ve öngörülerle yanıtlar sağlanır.


## <a name="what-should-i-do-if-the-ata-gateway-wont-start"></a>ATA Gateway başlatılmazsa ne yapmalıyım?
Geçerli hata günlüğünde ("Logs" klasörü altında ATA’nın yüklendiği yer) en son hataya bakın.
## <a name="how-can-i-test-ata"></a>ATA’yı nasıl test edebilirim?
Uçtan uca bir testle aşağıdakileri yaparak kuşkulu etkinliklerin benzetimini yapabilirsiniz:

1.  Nslookup.exe kullanarak DNS keşfi
2.  Psexec.exe kullanarak uzaktan yürütme


Bu, izlenmekte olan etki alanı denetleyici için uzaktan çalıştırılmalı ve ATA Gateway’den çalıştırılmamalıdır.

## <a name="how-do-i-verify-windows-event-forwarding"></a>Windows Olay İletme’yi nasıl doğrularım?
Aşağıdaki kodu bir dosyaya yerleştirerek komut isteminde şu dizinden çalıştırabilirsiniz: **\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin**:

mongo.exe ATA dosya adı

        db.getCollectionNames().forEach(function(collection) {
        if (collection.substring(0,10)=="NtlmEvent_") {
                if (db[collection].count() > 0) {
                                  print ("Found "+db[collection].count()+" NTLM events") 
                                }
                }
        });

## <a name="does-ata-work-with-encrypted-traffic"></a>ATA şifrelenmiş trafikle çalışır mı?
ATA birden çok ağ protokolünü analiz etmeye ve SIEM’den toplanan ya da Windows Olay İletme aracılığıyla toplanan olaylara dayalıdır ve bu sayede şifrelenmiş trafik analiz edilmemesine rağmen (örneğin LDAPS ve IPSEC ESP) ATA çalışmaya devam eder ve çoğu algılama işlemi etkilenmez

## <a name="does-ata-work-with-kerberos-armoring"></a>ATA Kerberos Koruması ile çalışır mı?
Esnek Kimlik Doğrulaması Güvenli Tüneli (FAST) olarak da bilinen Kerberos Koruması’nın etkinleştirilmesi ATA tarafından desteklenir; yalnızca karma değeri atlayarak geçiş algılaması çalışmaz.
## <a name="how-many-ata-gateways-do-i-need"></a>Kaç tane ATA Gateway’e ihtiyacım vardır?

ATA Gateway sayısı ağ düzeninize, paket hacmine ve ATA tarafından yakalanan olayların hacmine bağlıdır. Sayıyı tam olarak belirlemek için bkz: [ATA Lightweight Gateway Boyutu](/advanced-threat-analytics/plan-design/ata-capacity-planning#ata-lightweight-gateway-sizing). 

## <a name="how-much-storage-do-i-need-for-ata"></a>ATA için ne kadar depolamaya ihtiyacım vardır?
Ortalama 1000 paket/sn ile her tam gün için 0,3 GB depolamaya ihtiyacınız vardır.<br /><br />ATA Center boyutları hakkında daha fazla bilgi için bkz. [ATA Kapasite Planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning).


## <a name="why-are-certain-accounts-considered-sensitive"></a>Neden bazı hesaplar hassas kabul edilir?
Bir hesap, hassas olarak belirlediğiniz bazı grupların üyesi olduğunda (örneğin, "Domain Admins" grubu) bu durum ortaya çıkar.

Hesabın neden hassas olduğunu anlamak için, grup üyeliğini gözden geçirerek hangi hassas gruplara üye olduğunu anlayabilirsiniz (üyesi olduğu grup başka bir grup nedeniyle de hassas olabilir, dolayısıyla en yüksek düzeydeki hassas grubu belirleyene kadar aynı işlem yapılmalıdır).

## <a name="how-do-i-monitor-a-virtual-domain-controller-using-ata"></a>ATA kullanarak sanal etki alanı denetleyicisini nasıl izlerim?
Çoğu sanal etki alanı denetleyicileri ATA Lightweight Gateway kapsamına alınabilir; ATA Lightweight Gateway’in ortamınız için uygun olup olmadığını belirlemek bkz. [ATA Kapasite Planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning).

Bir sanal etki alanı denetleyicisi ATA Lightweight Gateway kapsamına alınamıyorsa, [Bağlantı noktası yansıtmayı yapılandırma](/advanced-threat-analytics/deploy-use/configure-port-mirroring) konusunda açıklandığı gibi sanal veya fiziksel ATA Gateway bileşenlerine sahip olabilirsiniz.  <br />En kolay yol, sanal bir etki alanı denetleyicisinin var olduğu her ana bilgisayarda sanal bir ATA Gateway’inizin olmasıdır.<br />Sanal etki alanı denetleyicileriniz ana bilgisayarlar arasında taşınıyorsa, aşağıdakilerden birini yapmalısınız:

-   Sanal etki alanı denetleyicisi başka bir ana bilgisayara taşındığında, son taşınan etki alanı denetleyicisinden gelen trafiği almak için ATA Gateway’i söz konusu ana bilgisayarda önceden yapılandırın.
-   Sanal etki alanı denetleyicisi taşındığında ATA Gateway’in de onunla birlikte taşınması için, sanal ATA Gateway’i sanal etki alanı denetleyicisiyle ilişkilendirdiğinizden emin olun.
-   Ana bilgisayarlar arasında trafik gönderebilen bazı sanal anahtarlar vardır.

## <a name="how-do-i-back-up-ata"></a>ATA’yı nasıl yedeklerim?
Yedeklenecek 2 öğe vardır:

-   ATA tarafından depolanan trafik ve olaylar. Bunlar desteklenen herhangi bir veritabanı yedekleme yordamı kullanılarak yedeklenebilir. Daha fazla bilgi için bkz. [ATA veritabanı yönetimi](/advanced-threat-analytics/deploy-use/ata-database-management) 
-   ATA yapılandırması. Veritabanında depolanır ve ATA Center dağıtım konumundaki **Yedekleme** klasöründe saatte bir kere yedeklenir.  Daha fazla bilgi için bkz: [ATA veritabanı yönetimi](https://docs.microsoft.com/advanced-threat-analytics/deploy-use/ata-database-management).
## <a name="what-can-ata-detect"></a>ATA neleri algılayabilir?
ATA bilinen kötü amaçlı saldırıları ve teknikleri, güvenlik sorunlarını ve riskleri algılar.
ATA algılamalarının tam listesi için bkz: [ATA hangi algılamaları gerçekleştirir?](ata-threats.md)

## <a name="what-kind-of-storage-do-i-need-for-ata"></a>ATA için ne tür bir depolamaya ihtiyacım vardır?
Düşük gecikme süreli disk erişimi (10 ms’den kısa) olan hızlı depolama alanı önerilir (7200 RPM diskler önerilmez). RAID yapılandırması ağır yazma yüklerini desteklemelidir (RAID-5/6 ve bunların türevleri önerilmez).

## <a name="how-many-nics-does-the-ata-gateway-require"></a>ATA Gateway’e kaç NIC gerekir?
ATA Gateway’e en az iki ağ bağdaştırıcısı gerekir:<br>1. İç ağa ve ATA Center’a bağlanmak için bir NIC<br>2. Bağlantı noktası yansıtma aracılığıyla etki alanı denetleyicisinin ağ trafiğini yakalamak için kullanılacak bir NIC.<br>* Bu, etki alanı denetleyicilerinin kullandığı tüm ağ bağdaştırıcılarını yerel olarak kullanan ATA Lightweight Gateway için geçerli değildir.

## <a name="what-kind-of-integration-does-ata-have-with-siems"></a>ATA’yla SIEM’ler arasında ne tür bir tümleştirme vardır?
ATA’nın SIEM’lerle şöyle çift yönlü bir tümleştirmesi vardır:

1. ATA, kuşkulu bir etkinlik olduğunda CEF biçimini kullanan herhangi bir SIEM sunucusuna Syslog uyarısı gönderecek şekilde yapılandırılabilir.
2. ATA, kimliği 4776 olan her Windows olayında [bu SIEM’lerden](/advanced-threat-analytics/deploy-use/configure-event-collection#siem-support) Syslog iletileri alacak şekilde yapılandırılabilir.

## <a name="can-ata-monitor-domain-controllers-virtualized-on-your-iaas-solution"></a>ATA, IaaS çözümünüzde sanallaştırılan etki alanı denetleyicilerini izleyebilir mi?

Evet, ATA Lightweight Gateway’i herhangi bir IaaS çözümündeki etki alanı denetleyicilerini izlemek için kullanabilirsiniz.

## <a name="is-this-an-on-premises-or-in-cloud-offering"></a>Bu şirket içi bir teklif mi yoksa bulut teklifi mi?
Microsoft Advanced Threat Analytics şirket içinde kullanılan bir üründür.

## <a name="is-this-going-to-be-a-part-of-azure-active-directory-or-on-premises-active-directory"></a>Azure Active Directory’nin mi yoksa şirket içi Active Directory’nin mi parçası olacak?
Bu çözüm şu anda tek başına sunulan bir tekliftir; Azure Active Directory’nin veya şirket içi Active Directory’nin parçası değildir.

## <a name="do-you-have-to-write-your-own-rules-and-create-a-thresholdbaseline"></a>Kendi kurallarınızı yazmanız ve bir eşik/temel oluşturmanız gerekiyor mu?
Microsoft Advanced Threat Analytics ile kurallar, eşikler veya temeller oluşturmanız ve sonra bunların ince ayarını yapmanız gerekmez. ATA hem kullanıcılar, cihazlar ve kaynaklar arasındaki davranışları hem de bunların birbirleriyle ilişkilerini çözümler; kuşkulu etkinlikleri ve bilinen saldırıları hızla algılayabilir. Dağıtımdan üç hafta sonra ATA davranış açısından kuşkulu etkinlikleri algılamaya başlar. Diğer yandan da, ATA dağıtımdan hemen sonra bilinen kötü amaçlı yazılım saldırılarını ve güvenlik sorunlarını algılamaya başlar.

## <a name="if-you-are-already-breached-will-microsoft-advanced-threat-analytics-be-able-to-identify-abnormal-behavior"></a>Zaten bir güvenlik ihlaliyle karşı karşıyaysanız, Microsoft Advanced Threat Analytics anormal davranışları belirleyebilir mi?
Evet, siz güvenlik ihlali yaşadıktan sonra bile yüklenmiş olsa, ATA korsanın kuşkulu etkinliklerini algılayabilir. ATA yalnızca kullanıcının davranışına değil kuruluşun güvenlik haritasındaki diğer kullanıcılara da bakar. İlk çözümleme sırasında, saldırganın davranışı anormalse bir “aykırı değer” olarak tanımlanır ve ATA anormal davranışları raporlamaya devam eder. Buna ek olarak, korsan başka kullanıcıların kimlik bilgilerini çalmaya çalışırsa (Anahtar Geçişi gibi) veya etki alanı denetleyicilerinden birinde uzaktan yürütme gerçekleştirmeye çalışırsa, ATA kuşkulu etkinliği algılayabilir.

## <a name="does-this-only-leverage-traffic-from-active-directory"></a>Yalnızca Active Directory trafiğinden mi yararlanır?
Derin paket inceleme teknolojisini kullanarak Active Directory trafiğini çözümlemenin yanı sıra, ATA Güvenlik Bilgileri ve Olay Yönetimi (SIEM) sistemlerinizden ilgili olayları toplayabilir ve Active Directory Dizin Etki Alanı Hizmetleri’nden alınan bilgiler temelinde varlık profilleri oluşturabilir. Kuruluşta Windows Olay Günlüğü iletme yapılandırıldıysa, ATA olay günlüklerinden de olayları toplayabilir.

## <a name="what-is-port-mirroring"></a>Bağlantı noktası yansıtma nedir?
SPAN (Anahtarlamalı Bağlantı Noktası Çözümleyicisi) olarak da bilinen bağlantı noktası yansıtma, bir ağ trafiği izleme yöntemidir. Bağlantı noktası yansıtma etkinleştirildiğinde, anahtar bir bağlantı noktasında görülen tüm ağ paketlerinin (veya VLAN’ın tamamının) kopyasını paketin çözümlenebileceği başka bir bağlantı noktasına gönderir.

## <a name="does-ata-monitor-only-domain-joined-devices"></a>ATA yalnızca etki alanına katılan cihazları mı izler?
Hayır. ATA, ağda yer alan ve Windows dışı ve mobil cihazlar da içinde olmak üzere Active Directory’den kimlik doğrulama ve yetkilendirme isteklerinde bulunan tüm cihazları izler.

## <a name="does-ata-monitor-computer-accounts-as-well-as-user-accounts"></a>ATA, kullanıcı hesaplarının yanı sıra bilgisayar hesaplarını da izler mi?
Evet. Bilgisayar hesapları (aynı diğer tüm varlıklar gibi) kötü amaçlı etkinlikler gerçekleştirmek için kullanılabildiğinden, ATA tüm bilgisayar hesaplarının davranışlarını ve ortamdaki diğer tüm varlıkları izler.

## <a name="can-ata-support-multi-domain-and-multi-forest"></a>ATA birden çok etki alanını ve birden çok ormanı destekliyor mu?
Microsoft Advanced Threat Analytics aynı orman sınırı içindeki çok etki alanlı ortamları destekler. Birden çok orman kullanımında, her orman için ayrı ATA dağıtımı gerekir.
## <a name="can-you-see-the-overall-health-of-the-deployment"></a>Dağıtımın bir bütün olarak durumunu görebilir misiniz?
Evet, hem dağıtımın gelen durumunu hem de yapılandırma, bağlantı, vb. ile ilgili belirli sorunları görebilir ve bunlar ortaya çıktığında uyarılırsınız.


## <a name="see-also"></a>Ayrıca bkz.
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [ATA kapasite planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [Olay koleksiyonunu yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [Windows olay iletme özelliğini yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection#Configuring-Windows-Event-Forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)




<!--HONumber=Jan17_HO1-->


