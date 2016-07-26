---
title: Microsoft Advanced Threat Analytics (ATA) nedir? | Microsoft ATA
description: "Microsoft Advanced Threat Analytics (ATA) çözümünün ne olduğu ve ne tür kuşkulu etkinlikleri algılayabildiği açıklanır"
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 283e7b4e-996a-4491-b7f6-ff06e73790d2
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5c7163bc7b1989672e587bfb4fa6a65cd4e3751
ms.openlocfilehash: 58afbae96bce0075f0a58be648e82744ce279997


---


## ATA nedir?
Microsoft Advanced Threat Analytics (ATA), BT güvenlik uzmanlarının kuruluşlarını ileri düzey hedeflenmiş saldırılara (APT’lere) ve içeriden gelen tehditlere karşı korumalarına yardımcı olan, Kullanıcı ve Varlık Davranışları analizi pazarında önde gelen bir çözümdür. ATA, gelişmiş makine öğrenimi teknolojisini kullanarak normal ve anormal varlık (kullanıcı, cihaz ve kaynaklar) davranışlarını otomatik şekilde analiz ederek, öğrenerek ve tanımlayarak, bilinen kötü amaçlı saldırıları ve tekniklerini, güvenlik sorunlarını ve riskleri tanımlamaya yardımcı olur. Dünya çapındaki güvenlik araştırmacılarının zekasını ve öngörülerini kullanan bu yenilikçi teknoloji, kuruluşların önemli noktalara odaklanmasına yardımcı olmak ve güvenlik ihlallerini zarara neden olmadan önce belirlemek için tasarlanmıştır.

## ATA ne yapar?
ATA şunları algılar:

  - Gelişmiş kalıcı tehditler (APT); bunları saldırı sonlandırma zincirinde erken bir aşamada, zarara neden olmadan önce algılar

  - İçeriden gelen tehditler

ATA gerçek şüpheli etkinlikleri parazitlerden ayırarak kritik olanlara odaklanmanıza yardımcı olur.

ATA’nın algılama altyapısı kullanıcı ve varlık davranışını çözümlemek için makine öğrenimi özelliği, varlık için kavramsal derin paket incelemesi, günlük çözümlemesi ve Active Directory’den (AD) gelen bilgilerden yararlanır.

ATA, kuruluşun trafiği üzerinde derin çözümleme yapar ve makine öğrenme özelliğini kullanarak kuruluşunuzda normal etkinliklerin, trafiğin ve kullanımın neye benzediğini gösteren bir harita oluşturur. Ardından, ATA anormal durumları gözler ve böyle bir durum olduğunda size bildirir. Bu, daha derin bir ağ trafiği ayrıştırma düzeyinde varlık için kavramsal paket incelemesi sağladığından, ATA’nın ağ trafiğinizin tüm düzeylerini çözümlemesine olanak tanıyan Microsoft'un derinlemesine paket inceleme teknolojisi (DPI) çalıştırılarak sağlanır.

ATA ayrıca SIEM sistemlerinden ve Etki Alanı Denetleyicilerinden de ilgili olayları toplar. Çözümleme sonrasında, ATA kuruluş içindeki tüm kişi, cihaz ve kaynakların dinamik, sürekli güncelleştirilen bir görünümünü oluşturur. ATA bu kapsamlı görünümü kullanarak, ağınızdaki varlıkların davranışlarındaki anormallikleri aramanın yanı sıra karma değer geçişi, anahtar geçişi ve keşif saldırıları gibi bilinen saldırıları algılayabilir.

Kuşkulu bir etkinlik algılandığında ATA bir uyarı gönderir; böylelikle toplama ve bağlam doğrulama için gelişmiş algoritmalar kullanıldığında aldığınız hatalı pozitif uyarıların sayısını en aza indirir.



## ATA hangi tehditleri arar?

ATA gelişmiş bir tehdidin çeşitli aşamaları için algılama sağlar: keşif, kimlik bilgilerinin tehlikeye atılması, yanal hareket, ayrıcalık yükseltme, etki alanı hakimiyeti ve daha fazlası. Bu algılamaların amacı, gelişmiş saldırıları ve içeriden gelen tehditleri kuruluşunuza zarar vermeden önce algılamaktır.

Her aşamadaki algılama, söz konusu aşamayla ilgili birkaç şüpheli etkinlikle sonuçlanır ve burada her şüpheli etkinlik farklı türde olası saldırılarla ilişkilidir.

### Keşif
ATA birçok keşif algılaması sağlar. Bu algılamalar şunları içerir:

-   **Hesap numaralandırma kullanarak keşif**<br>Saldırganların bir kullanıcının var olup olmadığını keşfetmek için Kerberos protokolünü kullanma girişimleri algılanır. Üstelik, bu etkinlik etki alanı denetleyicisinde olay olarak günlüğe kaydedilmemiş olsa bile algılanır.
-   **Ağ Oturumu Numaralandırma**<br>
Saldırganlar keşif aşamasının bir parçası olarak, etki alanı denetleyicisinde sunucudaki tüm etkin SMB oturumlarını sorgulayabilir ve bu da onlara bu SMB oturumlarıyla ilişkili tüm kullanıcılara ve IP adreslerine erişme olanağı sağlar. SMB oturumu numaralandırması saldırganlar tarafından hassas hesapları hedeflemek için kullanılabilir ve bu da saldırganların ağda yanal olarak hareket etmelerine yardımcı olur.
-   **DNS kullanarak keşif**<br>
Hedef ağdaki DNS bilgileri genellikle çok yararlı keşif bilgilerdir. DNS bilgileri tüm sunucuların ve genellikle tüm istemcilerin listesini ve IP adreslerinin eşlemesini içerir. DNS bilgilerini görüntülemek, saldırganlara ortamınızdaki bu varlıkların ayrıntılı görünümünü sağlayabilir ve bu kişilerin saldırıları kampanyayla ilgili varlıklara odaklamasına olanak tanır.

### Güvenliği tehlikede olan kimlik bilgileri

ATA, güvenliği tehlikede olan kimlik bilgilerinin algılanması için hem makine öğrenimi tabanlı davranış çözümlemesi özelliğinden hem de bilinen kötü amaçlı saldırıları ve teknikleri algılama özelliğinden yararlanır.

ATA, davranış analizi ve makine öğrenimini kullanarak, kimlik bilgileri güvenliğinin tehlike altında olduğuna işaret eden anormal oturumlar, olağan dışı kaynak erişimi ve olağan dışı çalışma saatleri gibi şüpheli etkinlikleri algılayabilir.
Tehlikeye atılmış kimlik bilgilerine karşı koruma sağlamak için, ATA aşağıdaki bilinen kötü amaçlı saldırıları ve teknikleri algılar:

 - **Deneme yanılma** <br>Deneme yanılma saldırılarında, saldırganlar birçok kullanıcı deneyip bunları birçok parola girişimiyle eşleştirerek kullanıcı kimlik bilgilerini tahmin etmeye çalışır. Saldırganlar, sistemin izin verdiği kadar çok değerle deneme yapmak için çoğunlukla karmaşık algoritmalar veya sözlükler kullanır.

- **Düz metin kimlik doğrulamasıyla açığa çıkarılan hassas hesap**<br>
Yüksek ayrıcalığa sahip bir hesabın kimlik bilgileri düz metin olarak gönderiliyorsa, bilgisayar yapılandırmasını güncelleştirebilmeniz için ATA sizi uyarır.

- **Hesapları düz metin kimlik doğrulamasıyla açığa çıkaran hizmet** <br>
Bilgisayardaki bir hizmet birden çok hesabın kimlik bilgilerini düz metin olarak gönderiyorsa, hizmet yapılandırmasını güncelleştirebilmeniz için ATA sizi uyarır.

- **Honey Token hesabının kuşkulu etkinlikleri**<br>
Honey Token hesapları sahte hesaplardır ve bu sahte hesapları kullanma girişiminde bulunan kötü amaçlı etkinliklere tuzak kurmak, bunları belirlemek ve izlemek için ayarlanır. ATA, bu Honey Token hesaplarında gerçekleştirilen etkinliklerle ilgili olarak sizi uyarır.
-   **Olağan dışı protokol uygulanması**<br>
Kimlik doğrulama istekleri (Kerberos veya NTLM) genellikle normal bir dizi yöntem ve protokoller kullanılarak gerçekleştirilir. Ancak başarıyla kimlik doğrulamak için, isteğin yalnızca belirli gereksinimleri karşılaması gerekir. Saldırganlar bu protokolleri, ortamda normal uygulamadan küçük sapmalarla uygulayabilir. Bu sapmalar, tehlikeye girmiş kimlik bilgilerinden yararlanmaya çalışan veya başarıyla yararlanan bir saldırganın varlığına işaret edebilir.
-   **Kötü Amaçlı Veri Koruma Özel Bilgi İsteği**<br>
Veri Koruma API’si (DPAPI) parola tabanlı bir veri koruma hizmetidir. Bu koruma hizmeti web sitesi parolaları ve dosya paylaşımı kimlik bilgileri gibi kullanıcının gizli bilgilerini depolayan çeşitli uygulamalar tarafından kullanılır. Parolanın kaybolması senaryolarını desteklemek için, kullanıcılar parolalarını içermeyen bir kurtarma anahtarı kullanılarak korunan verilerin şifresini çözebilir. Bir etki alanı ortamında, saldırganlar uzaktan kurtarma anahtarını çalabilir ve tüm etki alanına katılmış bilgisayarlarda korunan verilerin şifresini çözmek için kullanabilirler.
-   **Olağan Dışı Davranış**<br>
Gelişmiş saldırıların yanı sıra iç tehdit durumlarında çoğu zaman, sosyal mühendislik yöntemleri veya yeni ve henüz bilinmeyen yöntem ve teknikler kullanılarak hesap kimlik bilgileri ele geçirilebilir. ATA varlığın davranışını analiz ederek ve varlık tarafından gerçekleştirilen işlemlerdeki anormallikleri algılayıp uyarı vererek bu tür tehditleri algılayabilir.

### Yanal hareket
Yanal hareket algılaması sağlamak için, kullanıcılar erişimleri olmaması gereken kaynaklara erişmek üzere, kaynaklara erişim sağlayan kimlik bilgilerinin avantajlarından yararlandığında, ATA bilinen kötü amaçlı saldırı ve teknikleri algılamanın yanı sıra makine eğitimi esaslı davranış analizini de kullanır.

ATA, davranış analizini ve makine eğitimini kullanarak, anormal cihazlar kullanıldığında ve yanal hareketin kanıtı olan başka göstergelerle anormal kaynak erişimini algılar.

Buna ek olarak, ATA saldırganlar tarafından yanal hareket yapmak için kullanılan aşağıdaki teknikleri algılama yoluyla da yanal hareketi algılayabilir:

- **Anahtar geçişi** <br>
Anahtar geçişi saldırılarında, saldırganlar bir bilgisayardan Kerberos anahtarını çalar ve ağınızdaki bir varlığın kimliğine bürünerek başka bir bilgisayara erişim kazanmak için bu anahtarı kullanır.
- **Karma değer geçişi** <br>
Karma değer geçişi saldırılarında, saldırganlar varlığın NTLM karmasını çalar, sonra NTLM’yle kimlik doğrulaması yapmak ve varlığın kimliğine bürünüp ağınızdaki kaynaklara erişmek için bu karmayı kullanır.
- **Karma değeri atlayarak geçiş**<br>
Karma değeri atlayarak geçiş saldırıları, saldırganın Kerberos’la kimlik doğrulaması yapmak için çalınmış bir NTLM karmasını kullanması ve geçerli bir Kerberos TGT anahtarı almasıdır. Daha sonra bu anahtar geçerli bir kullanıcı olarak kimliği doğrulamak ve ağınızdaki kaynaklara erişmek için kullanılır.
-   **Olağan dışı davranış**<br>
Yanal hareket, genellikle saldırganlar tarafından, öncelikli kimlik bilgilerine veya ilgisini çeken hassas bilgilere erişim elde etmek amacıyla kurbanın ağındaki cihazlar ve alanlar arasında hareket etmek için kullanılan bir tekniktir. ATA, şirket ağı içinde kullanıcı ve cihazların davranışlarını ve ilişkilerini analiz ederek yanal hareketi algılayabilir ve bir saldırgan tarafından sergilenen bir yanal harekete işaret edebilen olağan dışı erişim kalıplarını algılayabilir.

### Ayrıcalık yükseltme
ATA başarıyla gerçekleştirilen veya girişimde bulunulan ayrıcalık yükseltme saldırılarını algılar; burada saldırganlar var olan ayrıcalıkları artırmaya ve bunları birkaç kez kullanıp sonunda kurbanın ortamı üzerinde tam denetim kazanmaya çalışır. 

ATA bilinen ve kötü amaçlı saldırıları ve aşağıdaki gibi, ayrıcalıkları yükseltmek için sık kullanılan teknikleri algılamanın yanı sıra, ayrıcalıklı hesapların olağan dışı davranışlarını algılamak üzere davranış analizini birleştirerek ayrıcalık yükseltme algılamasına olanak sağlar:

- **MS14-068 açığından yararlanma (Sahte PAC)**<br>
Sahte PAC, saldırganın geçerli TGT anahtarlarına sahte yetkilendirme üst bilgisi biçiminde yetkilendirme verileri yerleştirdikleri saldırılardır ve kuruluşun kendilerine vermediği ek izinler verir. Bu senaryoda saldırgan, daha önce güvenliği aşılmış kimlik bilgileri veya yanal hareket işlemleri sırasında toplanan kimlik bilgilerini kullanır.
- **MS11-013 açığından yararlanma (Gümüş PAC)**<br>
MS11-013 açığından yararlanma saldırıları, bir Kerberos hizmet biletinin belirli yönlerden sahtesini üretmeye olanak sağlayan Kerberos’taki ayrıcalık güvenlik açığından yararlanılarak gerçekleştirilir. Bu güvenlik açığından yararlanmayı başaran kötü amaçlı bir kullanıcı veya saldırgan Etki Alanı Denetleyicisinde yükseltilmiş ayrıcalıklarla bir belirteç elde edebilir. Bu senaryoda saldırgan, daha önce güvenliği aşılmış kimlik bilgileri veya yanal hareket işlemleri sırasında toplanan kimlik bilgilerini kullanır.

### Etki alanı hakimiyeti
ATA aşağıdakiler gibi, saldırganlar tarafından bilinen teknikler sayesinde algılama gerçekleştirerek kurbanın ortamı üzerinde tam denetim veya egemenlik elde etmeye çalışan veya bunu başaran saldırganları algılar:

- **İskelet anahtar kötü amaçlı yazılımı**<br>
İskelet anahtar saldırılarında, etki alanı denetleyicinize bir yandan saldırganların herhangi bir kullanıcı gibi kimlik doğrulaması yapmalarına izin veren ve diğer yandan da normal kullanıcıların oturum açmasına olanak tanıyan kötü amaçlı bir yazılım yüklenir.
- **Altın anahtar**<br>
Altın anahtar saldırılarında, saldırgan KBTGT’nin (Kerberos Altın Anahtarı) kimlik bilgilerini çalar. Bu anahtar, saldırganın ağdaki kaynakları erişim kazanmak amacıyla kullanılacak çevrimdışı bir TGT anahtarı oluşturmasına olanak tanır.
- **Uzaktan yürütme**<br>
Saldırganlar etki alanı denetleyicinizde uzaktan kod çalıştırarak ağınızı denetleme girişiminde bulunabilir.
-   **Kötü amaçlı çoğaltma istekleri** Active Directory (AD) ortamlarında, Etki Alanı Denetleyicileri arasında düzenli olarak çoğaltma yapılır. Bir saldırgan (bazen bir Etki Alanı Denetleyicisinin kimliğe bürünerek), AD çoğaltma isteğini taklit edebilir ve bu da saldırganın Birim Gölge Kopyası gibi daha kullanışsız tekniklerden yararlanmadan, parola karmaları dahil olmak üzere AD’de depolanan verileri almasına izin verir.

## Sırada ne var?

-   ATA’nın ağınıza nasıl uyum sağladığı hakkında daha fazla bilgi için: [ATA mimarisi](/advanced-threat-analytics/plan-design/ata-architecture)

-   ATA’nın dağıtımına başlamak için: [ATA’yı yükleme](/advanced-threat-analytics/deploy-use/install-ata)

## Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jul16_HO3-->


