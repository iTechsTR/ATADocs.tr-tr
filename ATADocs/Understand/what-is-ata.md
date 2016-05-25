---
# required metadata

title: Microsoft Advanced Threat Analytics (ATA) nedir? | Microsoft Advanced Threat Analytics
description: Microsoft Advanced Threat Analytics (ATA) çözümünün ne olduğu ve ne tür kuşkulu etkinlikleri algılayabildiği açıklanır
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 283e7b4e-996a-4491-b7f6-ff06e73790d2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


## ATA nedir?
Microsoft Advanced Threat Analytics (ATA), BT güvenlik uzmanlarının kuruluşlarını ileri düzey hedeflenmiş saldırılara ve içeriden gelen tehditlere karşı korumalarına yardımcı olan bir güvenlik çözümüdür. ATA bilinen kötü amaçlı saldırılar, teknikler ve güvenlik sorunları gibi riskleri belirlemek için normal ve anormal varlık (kullanıcı, cihaz ve kaynak) davranışlarını otomatik olarak çözümler, öğrenir ve belirler. Dünya çapındaki güvenlik araştırmacılarının zekasını ve öngörülerini kullanan bu yenilikçi teknoloji, kuruluşların önemli noktalara odaklanmasına yardımcı olmak ve güvenlik ihlallerini zarara neden olmadan önce belirlemek için tasarlanmıştır.

## ATA ne yapar?
ATA şunları algılar:

  - Gelişmiş kalıcı tehditler (APT); bunları saldırı sonlandırma zincirinde erken bir aşamada, zarara neden olmadan önce algılar

  - İçeriden gelen tehditler

  ATA ayrıca sinyali gürültüden ayırarak kritik konulara odaklanmanıza da olanak tanır.

ATA’nın, kullanıcı ve varlık davranışını çözümlemek için makine öğrenme özelliği, varlık için kavramsal derin paket incelemesi, günlük çözümlemesi ve Active Directory’den (AD) gelen bilgilerden yararlanan bir algılama altyapısı vardır.
Bu algılama altyapısı trafik üzerinde derin çözümleme yapar ve makine öğrenme özelliğini kullanarak kuruluşunuzda normal etkinliklerin, trafiğin ve kullanımın neye benzediğini gösteren bir harita oluşturur. Ardından, ATA anormal durumları gözler ve böyle bir durum olduğunda size bildirir. Bu sonuç, Microsoft’un derin paket inceleme teknolojisi (DPI) kullanılarak elde edilir. Bu teknoloji, daha derin bir ağ trafiği ayrıştırma düzeyinde varlık için kavramsal paket incelemesi sağladığından, ATA’nın ağ trafiğinizin tüm düzeylerini çözümlemesine olanak tanır. ATA ayrıca SIEM sistemlerinden ve Etki Alanı Denetleyicilerinden de ilgili olayları toplar. 

Çözümleme sonrasında, ATA kuruluş içindeki tüm kişilerin, cihazların ve kaynakların dinamik, sürekli güncelleştirilen bir görünümünü oluşturur. ATA bu kapsamlı görünümü kullanarak, karma değer geçişi, anahtar geçişi ve keşif saldırıları gibi bilinen kötü amaçlı saldırıları algılayabilir. ATA, ağınızdaki varlıkların davranışlarındaki olası anormallikleri de arar.  

Kuşkulu bir etkinlik algılandığında ATA bir uyarı gönderir; böylelikle toplama ve bağlam doğrulama için gelişmiş algoritmalar kullanıldığında aldığınız hatalı pozitif uyarıların sayısını en aza indirir.


## ATA hangi tehditleri arar?

ATA gelişmiş bir tehdidin çeşitli aşamaları için algılama sağlar: keşif, kimlik bilgilerinin tehlikeye atılması, yanal hareket, ayrıcalık yükseltme, etki alanı hakimiyeti ve diğerleri. Bu algılamaların amacı, gelişmiş saldırıları ve içeriden gelen tehditleri kuruluşunuza zarar vermeden önce algılamaktır.

Her aşamada algılama, söz konusu aşamaya uygun çeşitli kuşkulu etkinlik türlerini arar. Her kuşkulu etkinlik, farklı türdeki olası hatalarla ilintilidir.


### Keşif
ATA birçok keşif algılaması sağlar. Örneğin, **Hesap numaralandırma kullanarak keşif** kuşkulu etkinliğinde, saldırganların bir kullanıcının var olup olmadığını keşfetmek için Kerberos protokolünü kullanma girişimleri algılanır. Üstelik, bu etkinlik etki alanı denetleyicisinde olay olarak günlüğe kaydedilmemiş bile algılanır.

### Kimlik bilgilerinin tehlikeye atılması

ATA, hem davranış çözümlemesi temelinde makine öğrenme özelliğinden hem de bilinen kötü amaçlı saldırıları ve teknikleri algılama özeliğinden yararlanarak, tehlikeye atılmış kimlik bilgilerini algılar.  

ATA, anormal oturum açmalar, anormal kaynak erişimi ve anormal çalışma saatleri gibi kuşkulu etkinlikleri algılayabilir. Bu kuşkulu etkinliklerin hepsi, kimlik bilgilerinin tehlikeye atılmış olma olasılığını gösterir.

Tehlikeye atılmış kimlik bilgilerine karşı koruma sağlamak için, ATA aşağıdaki bilinen kötü amaçlı saldırıları ve teknikleri algılar:

 - **Deneme yanılma** - Deneme yanılma saldırılarında, saldırganlar birçok kullanıcı deneyip bunları birçok parola girişimiyle eşleştirerek kullanıcı kimlik bilgilerini tahmin etmeye çalışır. Saldırganlar, sistemin izin verdiği kadar çok değerle deneme yapmak için çoğunlukla karmaşık algoritmalar veya sözlükler kullanır.

- **Düz metin kimlik doğrulamasıyla açığa çıkarılan hassas hesap** - Yüksek ayrıcalığa sahip bir hesabın kimlik bilgileri düz metin olarak gönderiliyorsa, bilgisayar yapılandırmasını güncelleştirebilmeniz için ATA sizi uyarır.

- **Hesapları düz metin kimlik doğrulamasıyla açığa çıkaran hizmet** - Bilgisayardaki bir hizmet birden çok hesabın kimlik bilgilerini düz metin olarak gönderiyorsa, hizmet yapılandırmasını güncelleştirebilmeniz için ATA sizi uyarır.

- **Honey Token hesabının kuşkulu etkinlikleri** - Honey Token hesapları sahte hesaplardır ve bu sahte hesapları kullanma girişiminde bulunan kötü amaçlı etkinliklere tuzak kurmak, bunları belirlemek ve izlemek için ayarlanır. ATA, bu Honey Token hesaplarında gerçekleştirilen etkinliklerle ilgili olarak sizi uyarır.

### Yanal hareket
Yanal hareket, kullanıcılar bazı kaynaklara erişim sağlayan kimlik bilgilerinden yararlanarak, erişmemeleri gereken başka kaynaklara erişim kazandıklarında ortaya çıkar. ATA, hem davranış çözümlemesi temelinde makine öğrenme özelliğinden hem de bilinen kötü amaçlı saldırıları ve teknikleri algılama özeliğinden yararlanarak, bu tür yanal hareketleri belirler.  

ATA, anormal cihazlar kullanıldığında ve yanal hareketin kanıtı olan başka göstergelerle anormal kaynak erişimini algılar. Buna ek olarak, ATA saldırganlar tarafından yanal hareket yapmak için kullanılan aşağıdaki teknikleri algılama yoluyla da yanal hareketi algılayabilir:
- **Anahtar geçişi** - Anahtar geçişi saldırılarında, saldırganlar bir bilgisayardan Kerberos anahtarını çalar ve ağınızdaki bir varlığın kimliğine bürünerek başka bir bilgisayara erişim kazanmak için bu anahtarı kullanır.
- **Karma değer geçişi** - Karma değer geçişi saldırılarında, saldırganlar varlığın NTLM karmasını çalar, sonra NTLM’yle kimlik doğrulaması yapmak ve varlığın kimliğine bürünüp ağınızdaki kaynaklara erişmek için bu karmayı kullanır.
- **Karma değeri atlayarak geçiş** - Karma değeri atlayarak geçiş saldırıları, saldırganın Kerberos’la kimlik doğrulaması yapmak için çalınmış bir NTLM karmasını kullanması ve geçerli bir Kerberos TGT anahtarı almasıdır. Daha sonra bu anahtar geçerli bir kullanıcı olarak kimliği doğrulamak ve ağınızdaki kaynaklara erişmek için kullanılır.

### Ayrıcalık yükseltme
Ayrıcalık yükseltme saldırısı, saldırganlar var olan ayrıcalıkları artırma ve bunları birkaç kez kullanıp sonunda kurbanın ortamı üzerinde tam denetim kazanma girişiminde bulunduklarında ortaya çıkar. ATA hem başarılı olan ayrıcalık yükseltme saldırılarını hem de saldırı girişimlerini algılar. ATA, ayrıcalıklı hesapların anormal davranışlarını algılamak için davranış çözümlemesini kullanır. Ayrıca ATA ayrıcalıkları yükseltmek için sıklıkla kullanıldığı bilinen kötü amaçlı saldırıları ve teknikleri de algılar; örneğin:
- **MS14-068 açığından yararlanma (Sahte PAC)** - Sahte PAC, saldırganın geçerli TGT anahtarlarına sahte yetkilendirme üst bilgisi biçiminde yetkilendirme verileri yerleştirdikleri saldırılardır. Bu teknikle, saldırgan kuruluşu tarafından kendisine verilmemiş olan izinleri alır.
- Daha önce güvenliği aşılmış kimlik bilgileri veya yanal hareket işlemleri sırasında toplanan kimlik bilgileri kullanılır.

### Etki alanı hakimiyeti
Etki alanı hakimiyeti, saldırganlar kurbanın ortamında tam denetim ve hakimiyeti ele geçirme girişiminde bulunduğunda veya ele geçirmeyi başardığında ortaya çıkar. ATA, saldırganlarca kullanıldığı bilinen teknikleri arayarak bu girişimleri algılar. Bu teknikler şunlardır:
- **İskelet anahtar kötü amaçlı yazılımı** - İskelet anahtar saldırılarında, etki alanı denetleyicinize bir yandan saldırganların herhangi bir kullanıcı gibi kimlik doğrulaması yapmalarına izin veren ve diğer yandan da normal kullanıcıların oturum açmasına olanak tanıyan kötü amaçlı bir yazılım yüklenir.
- **Altın anahtar** - Altın anahtar saldırılarında, saldırgan KBTGT’nin (Kerberos Altın Anahtarı) kimlik bilgilerini çalar. Bu anahtar, saldırganın ağdaki kaynakları erişim kazanmak amacıyla kullanılacak çevrimdışı bir TGT anahtarı oluşturmasına olanak tanır.
- **Uzaktan yürütme** - Saldırganlar etki alanı denetleyicinizde uzaktan kod çalıştırarak ağınızı denetleme girişiminde bulunabilir.


## Sırada ne var?

-   ATA’nın ağınıza nasıl uyum sağladığı hakkında daha fazla bilgi için: [ATA mimarisi](ata-architecture.md)

-   ATA’nın dağıtımına başlamak için: [ATA’yı yükleme](/advanced-threat-analytics/deploy-useinstall-ata)

## Ayrıca Bkz.
[ATA desteği için forumumuzu gözden geçirin!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=Apr16_HO4-->


