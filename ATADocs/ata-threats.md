---
title: "Advanced Threat Analytics hangi tehditleri algılar? | Microsoft Docs"
description: "Advanced Threat Analytics’in algıladığı tehditler listesi"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 07/2/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 283e7b4e-996a-4491-b7f6-ff06e73790d2
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 630bb2b74dafcf9ab9b3469c2afbf8abc59c2dbf
ms.sourcegitcommit: fa50f37b134d7579d7c310852dff60e5f1996eaa
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*

# ATA hangi tehditleri arar?
<a id="what-threats-does-ata-look-for" class="xliff"></a>

ATA gelişmiş bir tehdidin çeşitli aşamaları için algılama sağlar: keşif, kimlik bilgilerinin tehlikeye atılması, yanal hareket, ayrıcalık yükseltme, etki alanı hakimiyeti ve daha fazlası. Bu algılamaların amacı, gelişmiş saldırıları ve içeriden gelen tehditleri kuruluşunuza zarar vermeden önce algılamaktır.
Her aşamadaki algılama, söz konusu aşamayla ilgili birkaç şüpheli etkinlikle sonuçlanır ve burada her şüpheli etkinlik farklı türde olası saldırılarla ilişkilidir.
ATA’nın, ölüm zincirinde şu anda algılayabildiği bu aşamalar aşağıdaki resimde vurgulanmıştır.

![ATA, saldırı ölüm zincirindeki yanal etkinliklere odaklanır](media/attack-kill-chain-small.jpg)


### Keşif
<a id="reconnaissance" class="xliff"></a>

ATA birçok keşif algılaması sağlar. Bu algılamalar şunları içerir:

-   **Hesap listeleme kullanarak keşif**<br></br>Saldırganların bir kullanıcının var olup olmadığını keşfetmek için Kerberos protokolünü kullanma girişimleri algılanır. Üstelik, bu etkinlik etki alanı denetleyicisinde olay olarak günlüğe kaydedilmemiş olsa bile algılanır.

-   **Ağ Oturumu Listeleme**<br></br>Saldırganlar keşif aşamasının bir parçası olarak, etki alanı denetleyicisinde sunucudaki tüm etkin SMB oturumlarını sorgulayabilir ve bu da onlara bu SMB oturumlarıyla ilişkili tüm kullanıcılara ve IP adreslerine erişme olanağı sağlar. SMB oturumu numaralandırması saldırganlar tarafından hassas hesapları hedeflemek için kullanılabilir ve bu da saldırganların ağda yanal olarak hareket etmelerine yardımcı olur.

-   **DNS kullanarak keşif**<br></br>Hedef ağdaki DNS bilgileri genellikle çok yararlı keşif bilgilerdir. DNS bilgileri tüm sunucuların ve genellikle tüm istemcilerin listesini ve IP adreslerinin eşlemesini içerir. DNS bilgilerini görüntülemek, saldırganlara ortamınızdaki bu varlıkların ayrıntılı görünümünü sağlayabilir ve bu kişilerin saldırıları kampanyayla ilgili varlıklara odaklamasına olanak tanır.

-   **Dizin hizmetleri listelemesi kullanarak keşif**<br></br>Etki alanı denetleyicilerinde sorgu çalıştırmak için SAM uzak protokolü kullanılarak gerçekleştirilen varlık (kullanıcılar, gruplar vb.) keşfi işlemlerini algılama. Bu keşif yöntemi gerçek dünyadaki saldırı senaryolarında görülen birçok kötü amaçlı yazılım türünde yaygındır. 


### Güvenliği tehlikede olan kimlik bilgileri
<a id="compromised-credentials" class="xliff"></a>

ATA, güvenliği tehlikede olan kimlik bilgilerinin algılanması için hem makine öğrenimi tabanlı davranış çözümlemesi özelliğinden hem de bilinen kötü amaçlı saldırıları ve teknikleri algılama özelliğinden yararlanır.
ATA, davranış analizi ve makine öğrenimini kullanarak, kimlik bilgileri güvenliğinin tehlike altında olduğuna işaret eden anormal oturumlar, olağan dışı kaynak erişimi ve olağan dışı çalışma saatleri gibi şüpheli etkinlikleri algılayabilir. Tehlikeye atılmış kimlik bilgilerine karşı koruma sağlamak için, ATA aşağıdaki bilinen kötü amaçlı saldırıları ve teknikleri algılar:

-   **Deneme yanılma**<br></br>Deneme yanılma saldırılarında, saldırganlar birçok kullanıcı deneyip bunları birçok parola girişimiyle eşleştirerek kullanıcı kimlik bilgilerini tahmin etmeye çalışır. Saldırganlar, sistemin izin verdiği kadar çok değerle deneme yapmak için çoğunlukla karmaşık algoritmalar veya sözlükler kullanır.

- **Şüpheli kimlik doğrulama hataları** (Davranışsal deneme yanılma saldırısı) <br></br> Saldırganlar, kimlik bilgilerinde deneme yanılma yaparak hesapların güvenliğini aşmayı dener. ATA, anormal bir kimlik doğrulama davranışı hatası algıladığında uyarı gönderir.

-   **Düz metin kimlik doğrulamasıyla açığa çıkarılan gizli hesap**<br></br>Yüksek ayrıcalığa sahip bir hesabın kimlik bilgileri düz metin olarak gönderiliyorsa, bilgisayar yapılandırmasını güncelleştirebilmeniz için ATA sizi uyarır.

-   **Hesapları düz metin kimlik doğrulamasıyla açığa çıkaran hizmet** <br></br>Bilgisayardaki bir hizmet birden çok hesabın kimlik bilgilerini düz metin olarak gönderiyorsa, hizmet yapılandırmasını güncelleştirebilmeniz için ATA sizi uyarır.

-   **Honey Token hesabının şüpheli etkinlikleri**<br></br>Honey Token hesapları sahte hesaplardır ve bu sahte hesapları kullanma girişiminde bulunan kötü amaçlı etkinliklere tuzak kurmak, bunları belirlemek ve izlemek için ayarlanır. ATA, bu Honey Token hesaplarında gerçekleştirilen etkinliklerle ilgili olarak sizi uyarır.

-   **Olağan dışı protokol uygulaması**<br></br>Kimlik doğrulama istekleri (Kerberos veya NTLM) genellikle normal bir dizi yöntem ve protokoller kullanılarak gerçekleştirilir. Ancak başarıyla kimlik doğrulamak için, isteğin yalnızca belirli gereksinimleri karşılaması gerekir. Saldırganlar bu protokolleri, ortamda normal uygulamadan küçük sapmalarla uygulayabilir. Bu sapmalar, tehlikeye girmiş kimlik bilgilerinden yararlanmaya çalışan veya başarıyla yararlanan bir saldırganın varlığına işaret edebilir.

-   **Kötü Amaçlı Veri Koruması Özel Bilgi İsteği**<br></br>Veri Koruma API’si (DPAPI) parola tabanlı bir veri koruma hizmetidir. Bu koruma hizmeti web sitesi parolaları ve dosya paylaşımı kimlik bilgileri gibi kullanıcının gizli bilgilerini depolayan çeşitli uygulamalar tarafından kullanılır. Parolanın kaybolması senaryolarını desteklemek için, kullanıcılar parolalarını içermeyen bir kurtarma anahtarı kullanılarak korunan verilerin şifresini çözebilir. Bir etki alanı ortamında, saldırganlar uzaktan kurtarma anahtarını çalabilir ve tüm etki alanına katılmış bilgisayarlarda korunan verilerin şifresini çözmek için kullanabilirler.

-   **Anormal Davranış**<br></br>Gelişmiş saldırıların yanı sıra iç tehdit durumlarında çoğu zaman, sosyal mühendislik yöntemleri veya yeni ve henüz bilinmeyen yöntem ve teknikler kullanılarak hesap kimlik bilgileri ele geçirilebilir. ATA varlığın davranışını analiz ederek ve varlık tarafından gerçekleştirilen işlemlerdeki anormallikleri algılayıp uyarı vererek bu tür tehditleri algılayabilir.

### Yanal hareket
<a id="lateral-movement" class="xliff"></a>

Yanal hareket algılaması sağlamak için, kullanıcılar erişimleri olmaması gereken kaynaklara erişmek üzere, kaynaklara erişim sağlayan kimlik bilgilerinin avantajlarından yararlandığında, ATA bilinen kötü amaçlı saldırı ve teknikleri algılamanın yanı sıra makine eğitimi esaslı davranış analizini de kullanır.
ATA, davranış analizini ve makine eğitimini kullanarak, anormal cihazlar kullanıldığında ve yanal hareketin kanıtı olan başka göstergelerle anormal kaynak erişimini algılar.
Buna ek olarak, ATA saldırganlar tarafından yanal hareket yapmak için kullanılan aşağıdaki teknikleri algılama yoluyla da yanal hareketi algılayabilir:

-   **Pass the ticket** <br></br>Anahtar geçişi saldırılarında, saldırganlar bir bilgisayardan Kerberos anahtarını çalar ve ağınızdaki bir varlığın kimliğine bürünerek başka bir bilgisayara erişim kazanmak için bu anahtarı kullanır.

-   **Pass the hash** <br></br>Karma değer geçişi saldırılarında, saldırganlar varlığın NTLM karmasını çalar, sonra NTLM’yle kimlik doğrulaması yapmak ve varlığın kimliğine bürünüp ağınızdaki kaynaklara erişmek için bu karmayı kullanır.

-   **Over-pass the hash**<br></br>Karma değeri atlayarak geçiş saldırıları, saldırganın Kerberos’la kimlik doğrulaması yapmak için çalınmış bir NTLM karmasını kullanması ve geçerli bir Kerberos TGT anahtarı almasıdır. Daha sonra bu anahtar geçerli bir kullanıcı olarak kimliği doğrulamak ve ağınızdaki kaynaklara erişmek için kullanılır.

-   **Anormal davranış**<br></br>Yanal hareket, genellikle saldırganlar tarafından, öncelikli kimlik bilgilerine veya ilgisini çeken hassas bilgilere erişim elde etmek amacıyla kurbanın ağındaki cihazlar ve alanlar arasında hareket etmek için kullanılan bir tekniktir. ATA, şirket ağı içinde kullanıcı ve cihazların davranışlarını ve ilişkilerini analiz ederek yanal hareketi algılayabilir ve bir saldırgan tarafından sergilenen bir yanal harekete işaret edebilen olağan dışı erişim kalıplarını algılayabilir.

### Ayrıcalık yükseltme
<a id="privilege-escalation" class="xliff"></a>

ATA başarıyla gerçekleştirilen veya girişimde bulunulan ayrıcalık yükseltme saldırılarını algılar; burada saldırganlar var olan ayrıcalıkları artırmaya ve bunları birkaç kez kullanıp sonunda kurbanın ortamı üzerinde tam denetim kazanmaya çalışır.
ATA bilinen ve kötü amaçlı saldırıları ve aşağıdaki gibi, ayrıcalıkları yükseltmek için sık kullanılan teknikleri algılamanın yanı sıra, ayrıcalıklı hesapların olağan dışı davranışlarını algılamak üzere davranış analizini birleştirerek ayrıcalık yükseltme algılamasına olanak sağlar:

-   **MS14-068 açığından yararlanma (Sahte PAC)**<br></br>Sahte PAC, saldırganın geçerli TGT anahtarlarına sahte yetkilendirme üst bilgisi biçiminde yetkilendirme verileri yerleştirdikleri saldırılardır ve kuruluşun kendilerine vermediği ek izinler verir. Bu senaryoda saldırgan, daha önce güvenliği aşılmış kimlik bilgileri veya yanal hareket işlemleri sırasında toplanan kimlik bilgilerini kullanır.

-   **MS11-013 açığından yararlanma (Gümüş PAC)**<br></br>MS11-013 açığından yararlanma saldırıları, bir Kerberos hizmet biletinin belirli yönlerden sahtesini üretmeye olanak sağlayan Kerberos’taki ayrıcalık güvenlik açığından yararlanılarak gerçekleştirilir. Bu güvenlik açığından yararlanmayı başaran kötü amaçlı bir kullanıcı veya saldırgan Etki Alanı Denetleyicisinde yükseltilmiş ayrıcalıklarla bir belirteç elde edebilir. Bu senaryoda saldırgan, daha önce güvenliği aşılmış kimlik bilgileri veya yanal hareket işlemleri sırasında toplanan kimlik bilgilerini kullanır.

-   **Gizli gruplarda yapılan anormal değişiklikler**  <br></br>Ayrıcalık yükseltme işleminin bir parçası olarak saldırganlar, gizli kaynaklara erişebilmek adına yüksek ayrıcalıklara sahip gruplarda değişiklikler yapar. ATA artık yükseltilmiş bir grupta anormal bir değişiklik olduğunda bunu algılar.

### Etki alanı hakimiyeti
<a id="domain-dominance" class="xliff"></a>

ATA aşağıdakiler gibi, saldırganlar tarafından bilinen teknikler sayesinde algılama gerçekleştirerek kurbanın ortamı üzerinde tam denetim veya egemenlik elde etmeye çalışan veya bunu başaran saldırganları algılar:

-   **Skeleton Key kötü amaçlı yazılımı**<br></br>İskelet anahtar saldırılarında, etki alanı denetleyicinize bir yandan saldırganların herhangi bir kullanıcı gibi kimlik doğrulaması yapmalarına izin veren ve diğer yandan da normal kullanıcıların oturum açmasına olanak tanıyan kötü amaçlı bir yazılım yüklenir.

-   **Altın anahtar**<br></br>Altın anahtar saldırılarında, saldırgan KBTGT’nin (Kerberos Altın Anahtarı) kimlik bilgilerini çalar. Bu anahtar, saldırganın ağdaki kaynakları erişim kazanmak amacıyla kullanılacak çevrimdışı bir TGT anahtarı oluşturmasına olanak tanır.

-   **Uzaktan yürütme**<br></br>Saldırganlar etki alanı denetleyicinizde uzaktan kod çalıştırarak ağınızı denetleme girişiminde bulunabilir.

- **Uzaktan yürütme denemesi – WMI exec**<br></br>Saldırganlar etki alanı denetleyicinizde uzaktan kod çalıştırarak ağınızı denetleme girişiminde bulunabilir. ATA, kodu uzaktan çalıştırmak için WMI yöntemlerinden yararlanan uzaktan yürütmeleri algılar.

-   **Kötü amaçlı çoğaltma istekleri** <br></br>Active Directory (AD) ortamlarında, Etki Alanı Denetleyicileri arasında düzenli olarak çoğaltma yapılır. Bir saldırgan (bazen bir Etki Alanı Denetleyicisinin kimliğe bürünerek), AD çoğaltma isteğini taklit edebilir ve bu da saldırganın Birim Gölge Kopyası gibi daha kullanışsız tekniklerden yararlanmadan, parola karmaları dahil olmak üzere AD’de depolanan verileri almasına izin verir.


## Sırada ne var?
<a id="whats-next" class="xliff"></a>

-   ATA’nın ağınıza nasıl uyum sağladığı hakkında daha fazla bilgi için: [ATA mimarisi](ata-architecture.md)

-   ATA’nın dağıtımına başlamak için: [ATA’yı yükleme](install-ata-step1.md)

## Ayrıca bkz.
<a id="see-also" class="xliff"></a>
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
