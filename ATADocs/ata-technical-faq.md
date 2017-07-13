---
title: "Advanced Threat Analytics sık sorulan sorular | Microsoft Docs"
description: "ATA hakkında sık sorulan soruların ve bunlarla ilişkili yanıtların listesini sağlar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 07/3/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: a7d378ec-68ed-4a7b-a0db-f5e439c3e852
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 5beabd2617f55ecbcc717338dc40d9f597cc25d4
ms.sourcegitcommit: fa50f37b134d7579d7c310852dff60e5f1996eaa
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*

# ATA sık sorulan sorular
<a id="ata-frequently-asked-questions" class="xliff"></a>
Bu makalede, ATA hakkında sık sorulan soruların listesi ve öngörülerle yanıtlar sağlanır.


## Advanced Threat Analytics (ATA) lisansını nereden alabilirim?
<a id="where-can-i-get-a-license-for-advanced-threat-analytics-ata" class="xliff"></a>

Etkin bir Kurumsal Anlaşmanız varsa bu yazılımı Microsoft Toplu Lisanslama Merkezi’nden (VLSC) indirebilirsiniz.

Doğrudan Office 365 portalı aracılığıyla veya Cloud Solution Partner (CSP) lisans modelinden Enterprise Mobility + Security (EMS) lisansı aldıysanız ve Microsoft Toplu Lisanslama Merkezi’nden (VLSC) ATA’ya erişiminiz yoksa Microsoft Müşteri Desteği ile iletişime geçerek Advanced Threat Analytics’i (ATA) etkinleştirme işlemini edinin.

## ATA Gateway başlatılmazsa ne yapmalıyım?
<a id="what-should-i-do-if-the-ata-gateway-wont-start" class="xliff"></a>
Geçerli hata günlüğünde ("Logs" klasörü altında ATA’nın yüklendiği yer) en son hataya bakın.

## ATA’yı nasıl test edebilirim?
<a id="how-can-i-test-ata" class="xliff"></a>
Uçtan uca bir testle aşağıdakileri yaparak kuşkulu etkinliklerin benzetimini yapabilirsiniz:

1.  Nslookup.exe kullanarak DNS keşfi
2.  Psexec.exe kullanarak uzaktan yürütme


Bu, izlenmekte olan etki alanı denetleyici için uzaktan çalıştırılmalı ve ATA Gateway’den çalıştırılmamalıdır.

## Her sürüme karşılık gelen ATA derlemeleri nelerdir?
<a id="which-ata-build-corresponds-to-each-version" class="xliff"></a>

|Sürüm|Derleme #|
|----|----|
|1.6|1.6.4103|
|1.6 Güncelleştirme 1|1.6.4317|
|1.7|1.7.5402| 
|1.7 Güncelleştirme 1|1.7.5647|
|1.7 Güncelleştirme 2|1.7.5757|
|1,8|1.8.6645|

## Mevcut ATA dağıtımımı en son sürüme yükseltmek için hangi sürümü kullanmalıyım?
<a id="what-version-should-i-use-to-upgrade-my-current-ata-deployment-to-the-latest-version" class="xliff"></a>

![ATA sürüm yükseltme matrisi](./media/version-matrix.png)


## Windows Olay İletme’yi nasıl doğrularım?
<a id="how-do-i-verify-windows-event-forwarding" class="xliff"></a>
Aşağıdaki kodu bir dosyaya yerleştirerek komut isteminde şu dizinden çalıştırabilirsiniz: **\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin**:

mongo.exe ATA dosya adı

        db.getCollectionNames().forEach(function(collection) {
        if (collection.substring(0,10)=="NtlmEvent_") {
                if (db[collection].count() > 0) {
                                  print ("Found "+db[collection].count()+" NTLM events") 
                                }
                }
        });

## ATA şifrelenmiş trafikle çalışır mı?
<a id="does-ata-work-with-encrypted-traffic" class="xliff"></a>
ATA birden çok ağ protokolünü analiz ederek ve SIEM’den ya da Windows Olay İletme aracılığıyla toplanan olaylara bağlı olarak çalışır ve bu sayede şifrelenmiş trafiğin çözümlenmemesine rağmen (LDAPS ve IPSEC ESP gibi) ATA çalışmaya devam eder ve çoğu algılama işlemi bundan etkilenmez.

## ATA Kerberos Koruması ile çalışır mı?
<a id="does-ata-work-with-kerberos-armoring" class="xliff"></a>
Esnek Kimlik Doğrulaması Güvenli Tüneli (FAST) olarak da bilinen Kerberos Koruması’nın etkinleştirilmesi ATA tarafından desteklenir; yalnızca karma değeri atlayarak geçiş algılaması çalışmaz.

## Kaç tane ATA Gateway’e ihtiyacım vardır?
<a id="how-many-ata-gateways-do-i-need" class="xliff"></a>

ATA Gateway sayısı ağ düzeninize, paket hacmine ve ATA tarafından yakalanan olayların hacmine bağlıdır. Sayıyı tam olarak belirlemek için bkz: [ATA Lightweight Gateway Boyutu](ata-capacity-planning.md#ata-lightweight-gateway-sizing). 

## ATA için ne kadar depolamaya ihtiyacım vardır?
<a id="how-much-storage-do-i-need-for-ata" class="xliff"></a>
Ortalama 1000 paket/sn ile her tam gün için 0,3 GB depolamaya ihtiyacınız vardır.<br /><br />ATA Center boyutları hakkında daha fazla bilgi için bkz. [ATA Kapasite Planlaması](ata-capacity-planning.md).


## Neden bazı hesaplar hassas kabul edilir?
<a id="why-are-certain-accounts-considered-sensitive" class="xliff"></a>
Bir hesap, hassas olarak belirlediğiniz bazı grupların üyesi olduğunda (örneğin, "Domain Admins" grubu) bu durum ortaya çıkar.

Hesabın neden hassas olduğunu anlamak için, grup üyeliğini gözden geçirerek hangi hassas gruplara üye olduğunu anlayabilirsiniz (üyesi olduğu grup başka bir grup nedeniyle de hassas olabilir, dolayısıyla en yüksek düzeydeki hassas grubu belirleyene kadar aynı işlem yapılmalıdır).

## ATA kullanarak sanal etki alanı denetleyicisini nasıl izlerim?
<a id="how-do-i-monitor-a-virtual-domain-controller-using-ata" class="xliff"></a>
Çoğu sanal etki alanı denetleyicileri ATA Lightweight Gateway kapsamına alınabilir; ATA Lightweight Gateway’in ortamınız için uygun olup olmadığını belirlemek bkz. [ATA Kapasite Planlaması](ata-capacity-planning.md).

Bir sanal etki alanı denetleyicisi ATA Lightweight Gateway kapsamına alınamıyorsa, [Bağlantı noktası yansıtmayı yapılandırma](configure-port-mirroring.md) konusunda açıklandığı gibi sanal veya fiziksel ATA Gateway bileşenlerine sahip olabilirsiniz.  <br />En kolay yol, sanal bir etki alanı denetleyicisinin var olduğu her ana bilgisayarda sanal bir ATA Gateway’inizin olmasıdır.<br />Sanal etki alanı denetleyicileriniz ana bilgisayarlar arasında taşınıyorsa, aşağıdakilerden birini yapmalısınız:

-   Sanal etki alanı denetleyicisi başka bir ana bilgisayara taşındığında, son taşınan etki alanı denetleyicisinden gelen trafiği almak için ATA Gateway’i söz konusu ana bilgisayarda önceden yapılandırın.
-   Sanal etki alanı denetleyicisi taşındığında ATA Gateway’in de onunla birlikte taşınması için, sanal ATA Gateway’i sanal etki alanı denetleyicisiyle ilişkilendirdiğinizden emin olun.
-   Ana bilgisayarlar arasında trafik gönderebilen bazı sanal anahtarlar vardır.

## ATA’yı nasıl yedeklerim?
<a id="how-do-i-back-up-ata" class="xliff"></a>

[ATA olağanüstü durum kurtarma](disaster-recovery.md)’ya göz atın



## ATA neleri algılayabilir?
<a id="what-can-ata-detect" class="xliff"></a>

ATA bilinen kötü amaçlı saldırıları ve teknikleri, güvenlik sorunlarını ve riskleri algılar.
ATA algılamalarının tam listesi için bkz: [ATA hangi algılamaları gerçekleştirir?](ata-threats.md)

## ATA için ne tür bir depolamaya ihtiyacım vardır?
<a id="what-kind-of-storage-do-i-need-for-ata" class="xliff"></a>
Düşük gecikme süreli disk erişimi (10 ms’den kısa) olan hızlı depolama alanı önerilir (7200 RPM diskler önerilmez). RAID yapılandırması ağır yazma yüklerini desteklemelidir (RAID-5/6 ve bunların türevleri önerilmez).

## ATA Gateway’e kaç NIC gerekir?
<a id="how-many-nics-does-the-ata-gateway-require" class="xliff"></a>
ATA Gateway’e en az iki ağ bağdaştırıcısı gerekir:<br>1. İç ağa ve ATA Center’a bağlanmak için bir NIC<br>2. Bağlantı noktası yansıtma aracılığıyla etki alanı denetleyicisinin ağ trafiğini yakalamak için kullanılacak bir NIC.<br>* Bu, etki alanı denetleyicilerinin kullandığı tüm ağ bağdaştırıcılarını yerel olarak kullanan ATA Lightweight Gateway için geçerli değildir.

## ATA’yla SIEM’ler arasında ne tür bir tümleştirme vardır?
<a id="what-kind-of-integration-does-ata-have-with-siems" class="xliff"></a>
ATA’nın SIEM’lerle şöyle çift yönlü bir tümleştirmesi vardır:

1. ATA, kuşkulu bir etkinlik olduğunda CEF biçimini kullanan herhangi bir SIEM sunucusuna Syslog uyarısı gönderecek şekilde yapılandırılabilir.
2. ATA, [bu SIEM’lerdeki](install-ata-step6.md) Windows olayları için Syslog iletileri alacak şekilde yapılandırılabilir.

## ATA, IaaS çözümünüzde sanallaştırılan etki alanı denetleyicilerini izleyebilir mi?
<a id="can-ata-monitor-domain-controllers-virtualized-on-your-iaas-solution" class="xliff"></a>
Evet, ATA Lightweight Gateway’i herhangi bir IaaS çözümündeki etki alanı denetleyicilerini izlemek için kullanabilirsiniz.

## Bu şirket içi bir teklif mi yoksa bulut teklifi mi?
<a id="is-this-an-on-premises-or-in-cloud-offering" class="xliff"></a>
Microsoft Advanced Threat Analytics şirket içinde kullanılan bir üründür.

## Azure Active Directory’nin mi yoksa şirket içi Active Directory’nin mi parçası olacak?
<a id="is-this-going-to-be-a-part-of-azure-active-directory-or-on-premises-active-directory" class="xliff"></a>
Bu çözüm şu anda tek başına sunulan bir tekliftir; Azure Active Directory’nin veya şirket içi Active Directory’nin parçası değildir.

## Kendi kurallarınızı yazmanız ve bir eşik/temel oluşturmanız gerekiyor mu?
<a id="do-you-have-to-write-your-own-rules-and-create-a-thresholdbaseline" class="xliff"></a>
Microsoft Advanced Threat Analytics ile kurallar, eşikler veya temeller oluşturmanız ve sonra bunların ince ayarını yapmanız gerekmez. ATA hem kullanıcılar, cihazlar ve kaynaklar arasındaki davranışları hem de bunların birbirleriyle ilişkilerini çözümler; kuşkulu etkinlikleri ve bilinen saldırıları hızla algılayabilir. Dağıtımdan üç hafta sonra ATA davranış açısından kuşkulu etkinlikleri algılamaya başlar. Diğer yandan da, ATA dağıtımdan hemen sonra bilinen kötü amaçlı yazılım saldırılarını ve güvenlik sorunlarını algılamaya başlar.

## Zaten bir güvenlik ihlaliyle karşı karşıyaysanız, Microsoft Advanced Threat Analytics anormal davranışları belirleyebilir mi?
<a id="if-you-are-already-breached-will-microsoft-advanced-threat-analytics-be-able-to-identify-abnormal-behavior" class="xliff"></a>
Evet, siz güvenlik ihlali yaşadıktan sonra bile yüklenmiş olsa, ATA korsanın kuşkulu etkinliklerini algılayabilir. ATA yalnızca kullanıcının davranışına değil kuruluşun güvenlik haritasındaki diğer kullanıcılara da bakar. İlk çözümleme sırasında, saldırganın davranışı anormalse bir “aykırı değer” olarak tanımlanır ve ATA anormal davranışları raporlamaya devam eder. Buna ek olarak, korsan başka kullanıcıların kimlik bilgilerini çalmaya çalışırsa (Anahtar Geçişi gibi) veya etki alanı denetleyicilerinden birinde uzaktan yürütme gerçekleştirmeye çalışırsa, ATA kuşkulu etkinliği algılayabilir.

## Yalnızca Active Directory trafiğinden mi yararlanır?
<a id="does-this-only-leverage-traffic-from-active-directory" class="xliff"></a>
Derin paket inceleme teknolojisini kullanarak Active Directory trafiğini çözümlemenin yanı sıra, ATA Güvenlik Bilgileri ve Olay Yönetimi (SIEM) sistemlerinizden ilgili olayları toplayabilir ve Active Directory Dizin Etki Alanı Hizmetleri’nden alınan bilgiler temelinde varlık profilleri oluşturabilir. Kuruluşta Windows Olay Günlüğü iletme yapılandırıldıysa, ATA olay günlüklerinden de olayları toplayabilir.

## Bağlantı noktası yansıtma nedir?
<a id="what-is-port-mirroring" class="xliff"></a>
SPAN (Anahtarlamalı Bağlantı Noktası Çözümleyicisi) olarak da bilinen bağlantı noktası yansıtma, bir ağ trafiği izleme yöntemidir. Bağlantı noktası yansıtma etkinleştirildiğinde, anahtar bir bağlantı noktasında görülen tüm ağ paketlerinin (veya VLAN’ın tamamının) kopyasını paketin çözümlenebileceği başka bir bağlantı noktasına gönderir.

## ATA yalnızca etki alanına katılan cihazları mı izler?
<a id="does-ata-monitor-only-domain-joined-devices" class="xliff"></a>
Hayır. ATA, ağda yer alan ve Windows dışı ve mobil cihazlar da içinde olmak üzere Active Directory’den kimlik doğrulama ve yetkilendirme isteklerinde bulunan tüm cihazları izler.

## ATA, kullanıcı hesaplarının yanı sıra bilgisayar hesaplarını da izler mi?
<a id="does-ata-monitor-computer-accounts-as-well-as-user-accounts" class="xliff"></a>
Evet. Bilgisayar hesapları (aynı diğer tüm varlıklar gibi) kötü amaçlı etkinlikler gerçekleştirmek için kullanılabildiğinden, ATA tüm bilgisayar hesaplarının davranışlarını ve ortamdaki diğer tüm varlıkları izler.

## ATA birden çok etki alanını ve birden çok ormanı destekliyor mu?
<a id="can-ata-support-multi-domain-and-multi-forest" class="xliff"></a>
Microsoft Advanced Threat Analytics aynı orman sınırı içindeki çok etki alanlı ortamları destekler. Birden çok orman kullanımında, her orman için ayrı ATA dağıtımı gerekir.

## Dağıtımın bir bütün olarak durumunu görebilir misiniz?
<a id="can-you-see-the-overall-health-of-the-deployment" class="xliff"></a>
Evet, hem dağıtımın gelen durumunu hem de yapılandırma, bağlantı, vb. ile ilgili belirli sorunları görebilir ve bunlar ortaya çıktığında uyarılırsınız.


## Ayrıca bkz.
<a id="see-also" class="xliff"></a>
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

