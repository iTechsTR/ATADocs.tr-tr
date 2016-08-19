---
title: "ATA Sık sorulan sorular | Microsoft ATA"
description: "ATA hakkında sık sorulan soruların ve bunlarla ilişkili yanıtların listesini sağlar"
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: a7d378ec-68ed-4a7b-a0db-f5e439c3e852
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 09de79e1f8fee6b27c7ba403df1af4431bd099a9
ms.openlocfilehash: 51440757c89130f8454e9c2b1abe7182f2b7eb41


---

# ATA sık sorulan sorular
Bu makalede, ATA hakkında sık sorulan soruların listesi ve öngörülerle yanıtlar sağlanır.


## ATA nasıl lisanslanır?
Lisans bilgileri için bkz. [Advanced Threat Analytics satın alma](https://www.microsoft.com/cloud-platform/advanced-threat-analytics-pricing)


## ATA Gateway başlatılmazsa ne yapmalıyım?
Geçerli hata günlüğünde ("Logs" klasörü altında ATA’nın yüklendiği yer) en son hataya bakın.
## ATA’yı nasıl test edebilirim?
Uçtan uca bir testle aşağıdakileri yaparak kuşkulu etkinliklerin benzetimini yapabilirsiniz:

1.  Nslookup.exe kullanarak DNS keşfi
2.  Psexec.exe kullanarak uzaktan yürütme


Bu, izlenmekte olan etki alanı denetleyici için uzaktan çalıştırılmalı ve ATA Gateway’den çalıştırılmamalıdır.

## Windows Olay İletme’yi nasıl doğrularım?
Dizindeki komut isteminden şu komutu çalıştırabilirsiniz:  **\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin**:

        mongo ATA --eval "printjson(db.getCollectionNames())" | find /C "NtlmEvents"`
## ATA şifrelenmiş trafikle çalışır mı?
Şifrelenmiş trafik çözümlenmez (örneğin: LDAPS, IPSEC ESP).
## ATA Kerberos Koruması ile çalışır mı?
Esnek Kimlik Doğrulaması Güvenli Tüneli (FAST) olarak da bilinen Kerberos Koruması’nın etkinleştirilmesi ATA tarafından desteklenir; yalnızca karma değeri atlayarak geçiş algılaması çalışmaz.
## Kaç tane ATA Gateway’e ihtiyacım vardır?

İlk olarak, uyum sağlayabilecek tüm etki alanı denetleyicilerinde ATA Lightweight Gateway bileşenlerini kullanmanız önerilir; bunu saptamak için bkz. [ATA Lightweight Gateway Boyutu](/advanced-threat-analytics/plan-design/ata-capacity-planning#ata-lightweight-gateway-sizing). 

Tüm etki alanı denetleyicileri ATA Lightweight Gateway bileşenleri kapsamına alınabiliyorsa, ATA Gateway gerekmez.

ATA Lightweight Gateway kapsamına alınamayan etki alanı denetleyicileri söz konusu olduğunda, kaç adet ATA Gateway bileşenine ihtiyacınız olduğuna karar verirken aşağıdakileri dikkate alın:

 - Ağ mimarisinin yanı sıra (bağlantı noktası yansıtma yapılandırmak için), etki alanı denetleyicilerinizin ürettiği toplam trafik miktarı. Etki alanı denetleyicilerinizin ürettiği trafik miktarını saptama konusunda daha fazla bilgi edinmek için bkz. [Etki alanı denetleyicisi tahmini trafiği](/advanced-threat-analytics/plan-design/ata-capacity-planning#Domain-controller-traffic-estimation).
 - Bağlantı noktası yansıtma özelliğinin işlem sınırlamaları da, etki alanı denetleyicilerinizi desteklemek için ihtiyacınız olan ATA Gateway sayısını belirler, örneğin: anahtar başına, veri merkezi başına, bölge başına (her ortamın kendine göre dikkat edilmesi gereken noktaları vardır). 

## ATA için ne kadar depolamaya ihtiyacım vardır?
Ortalama 1000 paket/sn ile her tam gün için 0,3 GB depolamaya ihtiyacınız vardır.<br /><br />ATA Center boyutları hakkında daha fazla bilgi için bkz. [ATA Kapasite Planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning).


## Neden bazı hesaplar hassas kabul edilir?
Bir hesap, hassas olarak belirlediğiniz bazı grupların üyesi olduğunda (örneğin, "Domain Admins" grubu) bu durum ortaya çıkar.

Hesabın neden hassas olduğunu anlamak için, grup üyeliğini gözden geçirerek hangi hassas gruplara üye olduğunu anlayabilirsiniz (üyesi olduğu grup başka bir grup nedeniyle de hassas olabilir, dolayısıyla en yüksek düzeydeki hassas grubu belirleyene kadar aynı işlem yapılmalıdır).

## ATA kullanarak sanal etki alanı denetleyicisini nasıl izlerim?
Çoğu sanal etki alanı denetleyicileri ATA Lightweight Gateway kapsamına alınabilir; ATA Lightweight Gateway’in ortamınız için uygun olup olmadığını belirlemek bkz. [ATA Kapasite Planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning).

Bir sanal etki alanı denetleyicisi ATA Lightweight Gateway kapsamına alınamıyorsa, [Bağlantı noktası yansıtmayı yapılandırma](/advanced-threat-analytics/deploy-use/configure-port-mirroring) konusunda açıklandığı gibi sanal veya fiziksel ATA Gateway bileşenlerine sahip olabilirsiniz.  <br />En kolay yol, sanal bir etki alanı denetleyicisinin var olduğu her ana bilgisayarda sanal bir ATA Gateway’inizin olmasıdır.<br />Sanal etki alanı denetleyicileriniz ana bilgisayarlar arasında taşınıyorsa, aşağıdakilerden birini yapmalısınız:

-   Sanal etki alanı denetleyicisi başka bir ana bilgisayara taşındığında, son taşınan etki alanı denetleyicisinden gelen trafiği almak için ATA Gateway’i söz konusu ana bilgisayarda önceden yapılandırın.
-   Sanal etki alanı denetleyicisi taşındığında ATA Gateway’in de onunla birlikte taşınması için, sanal ATA Gateway’i sanal etki alanı denetleyicisiyle ilişkilendirdiğinizden emin olun.
-   Ana bilgisayarlar arasında trafik gönderebilen bazı sanal anahtarlar vardır.

## ATA’yı nasıl yedeklerim?
Yedeklenecek 2 öğe vardır:

-   ATA tarafından depolanan trafik ve olaylar. Bunlar desteklenen herhangi bir veritabanı yedekleme yordamı kullanılarak yedeklenebilir. Daha fazla bilgi için bkz. [ATA veritabanı yönetimi](/advanced-threat-analytics/deploy-use/ata-database-management) 
-   ATA’nın yapılandırması. Bu veritabanında depolanır ve saatte bir otomatik olarak yedeklenir. 

## ATA neleri algılayabilir?
ATA bilinen kötü amaçlı saldırıları ve teknikleri, güvenlik sorunlarını ve riskleri algılar.
ATA algılamalarının tam listesi için bkz. [Microsoft Advanced Threat Analytics nedir?](what-is-ata.md)

## ATA için ne tür bir depolamaya ihtiyacım vardır?
Düşük gecikme süreli disk erişimi (10 ms’den kısa) olan hızlı depolama alanı önerilir (7200 RPM diskler önerilmez). RAID yapılandırması ağır yazma yüklerini desteklemelidir (RAID-5/6 ve bunların türevleri önerilmez).

## ATA Gateway’e kaç NIC gerekir?
ATA Gateway’e en az iki ağ bağdaştırıcısı gerekir:<br>1. İç ağa ve ATA Center’a bağlanmak için bir NIC<br>2. Bağlantı noktası yansıtma aracılığıyla etki alanı denetleyicisinin ağ trafiğini yakalamak için kullanılacak bir NIC.<br>* Bu, etki alanı denetleyicilerinin kullandığı tüm ağ bağdaştırıcılarını yerel olarak kullanan ATA Lightweight Gateway için geçerli değildir.

## ATA’yla SIEM’ler arasında ne tür bir tümleştirme vardır?
ATA’nın SIEM’lerle şöyle çift yönlü bir tümleştirmesi vardır:

1. ATA, kuşkulu bir etkinlik olduğunda CEF biçimini kullanan herhangi bir SIEM sunucusuna Syslog uyarısı gönderecek şekilde yapılandırılabilir.
2. ATA, kimliği 4776 olan her Windows olayında [bu SIEM’lerden](/advanced-threat-analytics/deploy-use/configure-event-collection#siem-support) Syslog iletileri alacak şekilde yapılandırılabilir.

## ATA, IaaS çözümünüzde görselleştirilen etki alanı denetleyicilerini izleyebilir mi?

Evet, ATA Lightweight Gateway’i herhangi bir IaaS çözümündeki etki alanı denetleyicilerini izlemek için kullanabilirsiniz.

## Bu şirket içi bir teklif mi yoksa bulut teklifi mi?
Microsoft Advanced Threat Analytics şirket içinde kullanılan bir üründür.

## Azure Active Directory’nin mi yoksa şirket içi Active Directory’nin mi parçası olacak?
Bu çözüm şu anda tek başına sunulan bir tekliftir; Azure Active Directory’nin veya şirket içi Active Directory’nin parçası değildir.

## Kendi kurallarınızı yazmanız ve bir eşik/temel oluşturmanız gerekiyor mu?
Microsoft Advanced Threat Analytics ile kurallar, eşikler veya temeller oluşturmanız ve sonra bunların ince ayarını yapmanız gerekmez. ATA hem kullanıcılar, cihazlar ve kaynaklar arasındaki davranışları hem de bunların birbirleriyle ilişkilerini çözümler; kuşkulu etkinlikleri ve bilinen saldırıları hızla algılayabilir. Dağıtımdan üç hafta sonra ATA davranış açısından kuşkulu etkinlikleri algılamaya başlar. Diğer yandan da, ATA dağıtımdan hemen sonra bilinen kötü amaçlı yazılım saldırılarını ve güvenlik sorunlarını algılamaya başlar.

## Zaten bir güvenlik ihlaliyle karşı karşıyaysanız, Microsoft Advanced Threat Analytics anormal davranışları belirleyebilir mi?
Evet, siz güvenlik ihlali yaşadıktan sonra bile yüklenmiş olsa, ATA korsanın kuşkulu etkinliklerini algılayabilir. ATA yalnızca kullanıcının davranışına değil kuruluşun güvenlik haritasındaki diğer kullanıcılara da bakar. İlk çözümleme sırasında, saldırganın davranışı anormalse bir “aykırı değer” olarak tanımlanır ve ATA anormal davranışları raporlamaya devam eder. Buna ek olarak, korsan başka kullanıcıların kimlik bilgilerini çalmaya çalışırsa (Anahtar Geçişi gibi) veya etki alanı denetleyicilerinden birinde uzaktan yürütme gerçekleştirmeye çalışırsa, ATA kuşkulu etkinliği algılayabilir.

## Yalnızca Active Directory trafiğinden mi yararlanır?
Derin paket inceleme teknolojisini kullanarak Active Directory trafiğini çözümlemenin yanı sıra, ATA Güvenlik Bilgileri ve Olay Yönetimi (SIEM) sistemlerinizden ilgili olayları toplayabilir ve Active Directory Dizin Etki Alanı Hizmetleri’nden alınan bilgiler temelinde varlık profilleri oluşturabilir. Kuruluşta Windows Olay Günlüğü iletme yapılandırıldıysa, ATA olay günlüklerinden de olayları toplayabilir.

## Bağlantı noktası yansıtma nedir?
SPAN (Anahtarlamalı Bağlantı Noktası Çözümleyicisi) olarak da bilinen bağlantı noktası yansıtma, bir ağ trafiği izleme yöntemidir. Bağlantı noktası yansıtma etkinleştirildiğinde, anahtar bir bağlantı noktasında görülen tüm ağ paketlerinin (veya VLAN’ın tamamının) kopyasını paketin çözümlenebileceği başka bir bağlantı noktasına gönderir.

## ATA yalnızca etki alanına katılan cihazları mı izler?
Hayır. ATA, ağda yer alan ve Windows dışı ve mobil cihazlar da içinde olmak üzere Active Directory’den kimlik doğrulama ve yetkilendirme isteklerinde bulunan tüm cihazları izler.

## ATA, kullanıcı hesaplarının yanı sıra bilgisayar hesaplarını da izler mi?
Evet. Bilgisayar hesapları (aynı diğer tüm varlıklar gibi) kötü amaçlı etkinlikler gerçekleştirmek için kullanılabildiğinden, ATA tüm bilgisayar hesaplarının davranışlarını ve ortamdaki diğer tüm varlıkları izler.

## ATA birden çok etki alanını ve birden çok ormanı destekliyor mu?
Genel kullanıma sunulduğunda Microsoft Advanced Threat Analytics aynı orman sınırı içinde birden çok etki alanını destekleyecektir. Ormanın kendisi gerçek “güvenlik sınırını” oluşturduğundan, birden çok etki alanı desteği ATA’yla müşterilerimizin ortamlarını %100 kapsama alanına alabilmelerini sağlar.

## Dağıtımın bir bütün olarak durumunu görebilir misiniz?
Evet, hem dağıtımın gelen durumunu hem de yapılandırma, bağlantı, vb. ile ilgili belirli sorunları görebilir ve bunlar ortaya çıktığında uyarılırsınız.


## Ayrıca Bkz.
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [ATA kapasite planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [Olay koleksiyonunu yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [Windows olay iletme özelliğini yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection#Configuring-Windows-Event-Forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)




<!--HONumber=Aug16_HO2-->


