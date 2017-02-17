---
title: "Advanced Threat Analytics hangi tehditleri algılar? | Microsoft Docs"
description: "Advanced Threat Analytics’in algıladığı tehditler listesi"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 283e7b4e-996a-4491-b7f6-ff06e73790d2
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 22d08a20291b1651a36247e9ffbeff8c881aefc5
ms.openlocfilehash: 2378405d9d55ad40cb2cbfa21d2848536b86c1aa


---

*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*

# <a name="what-threats-does-ata-look-for"></a>ATA hangi tehditleri arar?

ATA gelişmiş bir tehdidin çeşitli aşamaları için algılama sağlar: keşif, kimlik bilgilerinin tehlikeye atılması, yanal hareket, ayrıcalık yükseltme, etki alanı hakimiyeti ve daha fazlası. Bu algılamaların amacı, gelişmiş saldırıları ve içeriden gelen tehditleri kuruluşunuza zarar vermeden önce algılamaktır.
Her aşamadaki algılama, söz konusu aşamayla ilgili birkaç şüpheli etkinlikle sonuçlanır ve burada her şüpheli etkinlik farklı türde olası saldırılarla ilişkilidir.
ATA’nın, ölüm zincirinde şu anda algılayabildiği bu aşamalar aşağıdaki resimde vurgulanmıştır.

![ATA, saldırı ölüm zincirindeki yanal etkinliklere odaklanır](media/attack-kill-chain-small.jpg)


### <a name="reconnaissance"></a>Keşif
ATA birçok keşif algılaması sağlar. Bu algılamalar şunları içerir:
-   **Hesap listeleme kullanarak keşif** Saldırganların bir kullanıcının mevcut olup olmadığını keşfetmek için Kerberos protokolünü kullanarak yaptığı girişimleri algılar. Üstelik, bu etkinlik etki alanı denetleyicisinde bir olay olarak günlüğe kaydedilmemiş olsa bile algılanır.
-   **Ağ Oturumu Listeleme** Saldırganlar, keşif aşamasının bir parçası olarak etki alanı denetleyicisini sorgulama yoluyla sunucudaki tüm etkin SMB oturumlarını bulabilir ve bu SMB oturumlarıyla ilişkili tüm kullanıcılara ve IP adreslerine erişme olanağı elde edebilir. SMB oturumu numaralandırması saldırganlar tarafından hassas hesapları hedeflemek için kullanılabilir ve bu da saldırganların ağda yanal olarak hareket etmelerine yardımcı olur.
-   **DNS kullanarak keşif** Hedef ağdaki DNS bilgileri genellikle çok yararlı keşif bilgileridir. DNS bilgileri tüm sunucuların ve genellikle tüm istemcilerin listesini ve IP adreslerinin eşlemesini içerir. DNS bilgilerini görüntülemek, saldırganlara ortamınızdaki bu varlıkların ayrıntılı görünümünü sağlayabilir ve bu kişilerin saldırıları kampanyayla ilgili varlıklara odaklamasına olanak tanır.
-   **Dizin hizmetleri listelemesi kullanarak keşif** Etki alanı denetleyicilerinde sorgu çalıştırmak için SAM uzak protokolü kullanılarak gerçekleştirilen varlık (kullanıcılar, gruplar vb.) keşfi işlemlerini algılama. Bu keşif yöntemi gerçek dünyadaki saldırı senaryolarında görülen birçok kötü amaçlı yazılım türünde yaygındır. 


### <a name="compromised-credentials"></a>Güvenliği tehlikede olan kimlik bilgileri
ATA, güvenliği tehlikede olan kimlik bilgilerinin algılanması için hem makine öğrenimi tabanlı davranış çözümlemesi özelliğinden hem de bilinen kötü amaçlı saldırıları ve teknikleri algılama özelliğinden yararlanır.
ATA, davranış analizi ve makine öğrenimini kullanarak, kimlik bilgileri güvenliğinin tehlike altında olduğuna işaret eden anormal oturumlar, olağan dışı kaynak erişimi ve olağan dışı çalışma saatleri gibi şüpheli etkinlikleri algılayabilir. Tehlikeye atılmış kimlik bilgilerine karşı koruma sağlamak için, ATA aşağıdaki bilinen kötü amaçlı saldırıları ve teknikleri algılar:
-   **Deneme yanılma** Deneme yanılma saldırılarında, saldırganlar birçok kullanıcı deneyip bunları birçok parola girişimiyle eşleştirerek kullanıcı kimlik bilgilerini tahmin etmeye çalışır. Saldırganlar, sistemin izin verdiği kadar çok değerle deneme yapmak için çoğunlukla karmaşık algoritmalar veya sözlükler kullanır.
-   **Düz metin kimlik doğrulamasıyla açığa çıkarılan hassas hesap** Yüksek ayrıcalığa sahip bir hesabın kimlik bilgileri düz metin olarak gönderiliyorsa, ATA, bilgisayar yapılandırmasını güncelleştirebilmeniz için sizi uyarır.
-   **Hesapları düz metin kimlik doğrulamasıyla açığa çıkaran hizmet** Bilgisayardaki bir hizmet birden çok hesabın kimlik bilgilerini düz metin olarak gönderiyorsa, ATA, hizmet yapılandırmasını güncelleştirebilmeniz için sizi uyarır.
-   **Honey Token hesabının kuşkulu etkinlikleri** Honey Token hesapları sahte hesaplardır ve bu sahte hesapları kullanma girişiminde bulunan kötü amaçlı etkinliklere tuzak kurmak, bunları belirlemek ve izlemek için ayarlanır. ATA, bu Honey Token hesaplarında gerçekleştirilen etkinliklerle ilgili olarak sizi uyarır.
-   **Olağan dışı protokol uygulanması** Kimlik doğrulaması istekleri (Kerberos veya NTLM) genellikle normal bir dizi metot ve protokol kullanılarak gerçekleştirilir. Ancak başarıyla kimlik doğrulamak için, isteğin yalnızca belirli gereksinimleri karşılaması gerekir. Saldırganlar bu protokolleri, ortamda normal uygulamadan küçük sapmalarla uygulayabilir. Bu sapmalar, tehlikeye girmiş kimlik bilgilerinden yararlanmaya çalışan veya başarıyla yararlanan bir saldırganın varlığına işaret edebilir.
-   **Kötü Amaçlı Veri Koruma Özel Bilgi İsteği** Veri Koruma API’si (DPAPI) parola tabanlı bir veri koruma hizmetidir. Bu koruma hizmeti web sitesi parolaları ve dosya paylaşımı kimlik bilgileri gibi kullanıcının gizli bilgilerini depolayan çeşitli uygulamalar tarafından kullanılır. Parolanın kaybolması senaryolarını desteklemek için, kullanıcılar parolalarını içermeyen bir kurtarma anahtarı kullanılarak korunan verilerin şifresini çözebilir. Bir etki alanı ortamında, saldırganlar uzaktan kurtarma anahtarını çalabilir ve tüm etki alanına katılmış bilgisayarlarda korunan verilerin şifresini çözmek için kullanabilirler.
-   **Anormal Davranış** Gelişmiş saldırıların yanı sıra iç tehdit durumlarında çoğu zaman, sosyal mühendislik yöntemleri veya yeni ve henüz bilinmeyen yöntemlerle teknikler kullanılarak hesap kimlik bilgileri ele geçirilebilir. ATA varlığın davranışını analiz ederek ve varlık tarafından gerçekleştirilen işlemlerdeki anormallikleri algılayıp uyarı vererek bu tür tehditleri algılayabilir.

### <a name="lateral-movement"></a>Yanal hareket
Yanal hareket algılaması sağlamak için, kullanıcılar erişimleri olmaması gereken kaynaklara erişmek üzere, kaynaklara erişim sağlayan kimlik bilgilerinin avantajlarından yararlandığında, ATA bilinen kötü amaçlı saldırı ve teknikleri algılamanın yanı sıra makine eğitimi esaslı davranış analizini de kullanır.
ATA, davranış analizini ve makine eğitimini kullanarak, anormal cihazlar kullanıldığında ve yanal hareketin kanıtı olan başka göstergelerle anormal kaynak erişimini algılar.
Buna ek olarak, ATA saldırganlar tarafından yanal hareket yapmak için kullanılan aşağıdaki teknikleri algılama yoluyla da yanal hareketi algılayabilir:
-   **Anahtar geçişi** Anahtar geçişi saldırılarında, saldırganlar bir bilgisayardan Kerberos anahtarını çalar ve ağınızdaki bir varlığın kimliğine bürünerek başka bir bilgisayara erişim kazanmak için bu anahtarı kullanır.
-   **Karma geçişi** Karma geçişi saldırılarında, saldırganlar varlığın NTLM karmasını çalar, sonra NTLM’de kimlik doğrulaması yapmak ve varlığın kimliğine bürünüp ağınızdaki kaynaklara erişmek için bu karmayı kullanır.
-   **Karmayı atlayarak geçiş** Karmayı atlayarak geçiş saldırıları, saldırganın Kerberos’ta kimlik doğrulaması yapmak için çalınmış bir NTLM karmasını kullanması ve geçerli bir Kerberos TGT anahtarı almasıyla gerçekleştirilir. Daha sonra bu anahtar geçerli bir kullanıcı olarak kimliği doğrulamak ve ağınızdaki kaynaklara erişmek için kullanılır.
-   **Anormal davranış** Yanal hareket, genellikle saldırganlar tarafından, öncelikli kimlik bilgilerine veya ilgisini çeken hassas bilgilere erişim elde etmek amacıyla kurbanın ağındaki cihazlar ve alanlar arasında hareket etmek için kullanılan bir tekniktir. ATA, şirket ağı içinde kullanıcı ve cihazların davranışlarını ve ilişkilerini analiz ederek yanal hareketi algılayabilir ve bir saldırgan tarafından sergilenen bir yanal harekete işaret edebilen olağan dışı erişim kalıplarını algılayabilir.

### <a name="privilege-escalation"></a>Ayrıcalık yükseltme
ATA başarıyla gerçekleştirilen veya girişimde bulunulan ayrıcalık yükseltme saldırılarını algılar; burada saldırganlar var olan ayrıcalıkları artırmaya ve bunları birkaç kez kullanıp sonunda kurbanın ortamı üzerinde tam denetim kazanmaya çalışır.
ATA bilinen ve kötü amaçlı saldırıları ve aşağıdaki gibi, ayrıcalıkları yükseltmek için sık kullanılan teknikleri algılamanın yanı sıra, ayrıcalıklı hesapların olağan dışı davranışlarını algılamak üzere davranış analizini birleştirerek ayrıcalık yükseltme algılamasına olanak sağlar:
-   **MS14-068 açığından yararlanma (Forged PAC)** Sahte PAC, saldırganın geçerli TGT anahtarlarına sahte yetkilendirme üst bilgisi biçiminde yetkilendirme verileri yerleştirdiği saldırılardır ve kuruluşun kendilerine vermediği ek izinler verir. Bu senaryoda saldırgan, daha önce güvenliği aşılmış kimlik bilgileri veya yanal hareket işlemleri sırasında toplanan kimlik bilgilerini kullanır.
-   **MS11-013 açığından yararlanma (Gümüş PAC)** MS11-013 açığından yararlanma saldırıları, bir Kerberos hizmet biletinin belirli yönlerden sahtesini üretmeye olanak sağlayan Kerberos’taki ayrıcalık güvenlik açığından yararlanılarak gerçekleştirilir. Bu güvenlik açığından yararlanmayı başaran kötü amaçlı bir kullanıcı veya saldırgan Etki Alanı Denetleyicisinde yükseltilmiş ayrıcalıklarla bir belirteç elde edebilir. Bu senaryoda saldırgan, daha önce güvenliği aşılmış kimlik bilgileri veya yanal hareket işlemleri sırasında toplanan kimlik bilgilerini kullanır.

### <a name="domain-dominance"></a>Etki alanı hakimiyeti
ATA aşağıdakiler gibi, saldırganlar tarafından bilinen teknikler sayesinde algılama gerçekleştirerek kurbanın ortamı üzerinde tam denetim veya egemenlik elde etmeye çalışan veya bunu başaran saldırganları algılar:
-   **Maymuncuk kötü amaçlı yazılımı** Maymuncuk saldırılarında, etki alanı denetleyicinize bir yandan saldırganların herhangi bir kullanıcı olarak kimlik doğrulaması yapmalarına izin veren ve diğer yandan da normal kullanıcıların oturum açmasına olanak tanıyan kötü amaçlı bir yazılım yüklenir.
-   **Altın bilet** Altın bilet saldırılarında, saldırgan KBTGT’nin kimlik bilgilerini (Kerberos Altın Bileti) çalar. Bu anahtar, saldırganın ağdaki kaynakları erişim kazanmak amacıyla kullanılacak çevrimdışı bir TGT anahtarı oluşturmasına olanak tanır.
-   **Uzaktan yürütme** Saldırganlar etki alanı denetleyicinizde uzaktan kod çalıştırarak ağınızı denetleme girişiminde bulunabilir.
-   **Kötü amaçlı çoğaltma istekleri** Active Directory (AD) ortamlarında, Etki Alanı Denetleyicileri arasında düzenli olarak çoğaltma yapılır. Bir saldırgan (bazen bir Etki Alanı Denetleyicisinin kimliğe bürünerek), AD çoğaltma isteğini taklit edebilir ve bu da saldırganın Birim Gölge Kopyası gibi daha kullanışsız tekniklerden yararlanmadan, parola karmaları dahil olmak üzere AD’de depolanan verileri almasına izin verir.


## <a name="whats-next"></a>Sırada ne var?

-   ATA’nın ağınıza nasıl uyum sağladığı hakkında daha fazla bilgi için: [ATA mimarisi](/advanced-threat-analytics/plan-design/ata-architecture)

-   ATA’nın dağıtımına başlamak için: [ATA’yı yükleme](/advanced-threat-analytics/deploy-use/install-ata)

## <a name="see-also"></a>Ayrıca bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Feb17_HO1-->


