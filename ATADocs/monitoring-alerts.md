---
title: "ATA izleme uyarılarını anlama | Microsoft Docs"
description: "Sorunları gidermek için ATA günlüklerini nasıl kullanabileceğiniz açıklanır"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 06/13/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: b04fb8a4-b366-4b55-9d4c-6f054fa58a90
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 4c232ea6bd25f1f13fe8e322719cda6388da9c0e
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



ATA Sistem Durumu Merkezi, ATA dağıtımı ile ilgili bir sorun olduğunda izleme uyarısı göndererek sizi bilgilendirir.
Bu makalede, sorunların sebebi ve çözüm yolunun bulunduğu bir listeyle her bir bileşen için izleme uyarıları açıklanmaktadır.
## ATA Center Sorunları
<a id="ata-center-issues" class="xliff"></a>
### ATA Center disk alanı azalıyor
<a id="ata-center-running-out-of-disk-space" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Center makine sürücüsünde, ATA veritabanını depolamak için kullanılan boş alan azalıyor.|Bu uyarı, sabit sürücüde 200 GB’tan veya %20’den (hangisi daha düşük bir miktara karşılık geliyorsa) az boş alan kaldığı anlamına gelir. ATA, sürücüde boş alanın azaldığını fark ettiğinde veritabanındaki eski verileri silmeye başlar. Ancak algılama altyapısı için hala eski verilere ihtiyacı varsa verileri silemez ve bu uyarıyı gönderir. Bu uyarıyı aldığınızda ATA, yeni etkinlikleri izlemeyi durdurur.|Sürücü boyutunu artırın veya mevcut sürücünüzde boş alan yaratın.|Yüksek|
### Posta Gönderme Başarısız
<a id="failure-sending-mails" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA, belirtilen posta sunucusuna bir e-posta bildirimi gönderemedi.|ATA’dan herhangi bir e-posta iletisi gönderilemez.|SMTP sunucusunun yapılandırmasını doğrulayın.|Düşük|

### ATA Center aşırı yüklendi
<a id="ata-center-overloaded" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Center, ATA Gateway’lerinden aktarılan veri miktarını kaldıramıyor. |ATA Center, yeni ağ trafiğini ve olayları çözümlemeyi durdurur. Yani bu uyarı etkinken algılamanın ve profillerin doğruluk oranı düşecektir.|ATA Center için yeterli kaynağı sağladığınızdan emin olun. ATA Center kapasitesini nasıl doğru planlayacağınıza ilişkin ayrıntılar için bkz. [ATA kapasitesini planlama](ata-capacity-planning.md). [Performans sayaçlarını kullanarak ATA sorunlarını giderme](troubleshooting-ata-using-perf-counters.md) ile ATA Center’ın performansını denetleyin.|Yüksek|

### Syslog kullanarak SIEM sunucusuna bağlanma başarısız
<a id="failure-connecting-to-the-siem-server-using-syslog" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA, belirtilen SIEM’e olay gönderemedi.|Bu uyarı ATA Center’ın, şüpheli etkinlikleri ve izleme uyarılarını SIEM’inize gönderemediği anlamına gelir.|[Syslog sunucusu ayarlarının düzgün yapılandırılmış olduğundan](setting-syslog-email-server-settings.md) emin olun.|Düşük|
### ATA Center sertifikasının süresi dolmak üzere
<a id="ata-center-certificate-is-about-to-expire" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Center sertifikasının 3 haftadan az bir süresi kaldı.|Sertifikanın süresi dolduktan sonra: ATA Gateway’lerinden ATA Center’a bağlantı başarısız olacaktır. ATA Center süreci kilitlenecek ve ATA işlevleri duracaktır.|[ATA Center sertifikasını değiştirin](modifying-ata-center-configuration.md)|Orta|
### ATA Center sertifikasının süresi doldu
<a id="ata-center-certificate-expired" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Center sertifikasının süresi doldu.|Sertifikanın süresi dolduktan sonra: ATA Gateway’lerinden ATA Center’a bağlantı başarısız olacaktır. ATA Center süreci kilitlenecek ve ATA işlevleri duracaktır.|[ATA Center sertifikasını değiştirin](modifying-ata-center-configuration.md)|Yüksek|
## ATA Gateway sorunları
<a id="ata-gateway-issues" class="xliff"></a>
### Salt okunur kullanıcı parolasının süresi dolmak üzere
<a id="read-only-user-password-is-about-to-expire" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Active Directory varlıklarının çözümü için kullanılan salt okunur kullanıcı parolasının 30 günden az bir süresi kaldı.|Bu kullanıcı için parola süresi dolarsa tüm ATA Gateway’leri çalışmayı durduracak ve yeni veri toplanmayacaktır.|[Etki alanı bağlantı parolasını değiştirin](modifying-ata-config-dcpassword.md) ve daha sonra ATA Konsolu’ndaki parolayı güncelleştirin.|Orta|
### Salt okunur kullanıcı parolasının süresi doldu
<a id="read-only-user-password-expired" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Dizin verilerini almak için kullanılan salt okunur kullanıcı parolasının süresi doldu.|Tüm ATA Gateway’ler çalışmayı durdurdu (veya yakında durduracak) ve yeni veri toplanmayacak.|[Etki alanı bağlantı parolasını değiştirin](modifying-ata-config-dcpassword.md) ve daha sonra ATA Konsolu’ndaki parolayı güncelleştirin.|Yüksek|
### ATA Gateway sertifikasının süresi dolmak üzere
<a id="ata-gateway-certificate-about-to-expire" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Gateway sertifikasının 3 haftadan az bir süresi kaldı.|Bu ATA Gateway’den ATA Center’a yapılan bağlantı başarısız olacaktır. ATA Gateway’den hiçbir veri gönderilmeyecektir.|ATA Gateway sertifikasının otomatik olarak yenilenmesi gerekir. Bu Sertifikanın neden otomatik olarak yenilenmediğini öğrenmek için ATA Gateway ve ATA Center günlüklerini okuyun.|Orta|

### ATA Gateway sertifikasının süresi doldu
<a id="ata-gateway-certificate-expired" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Gateway sertifikasının süresi doldu.|Bu ATA Gateway’den ATA Center’a bağlantı yapılamaz. ATA Gateway’den hiçbir veri gönderilmeyecektir.|[ATA Gateway’i kaldırma ve yeniden yükleme](install-ata-step3.md).|Yüksek|
### Etki alanı eşitleyicisi atanmadı
<a id="domain-synchronizer-not-assigned" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Bir ATA Gateway’e hiçbir etki alanı eşitleyicisi atanmadı. Etki alanı eşitleyicisi adayı olarak yapılandırılmış bir ATA Gateway yoksa bu durum oluşabilir.|Etki alanı eşitlenmediğinde varlıklarda yapılan değişiklikler, ATA’daki bilgilerin güncelliğini yitirmesine veya kaybolmasına yol açabilir ancak algılamayı etkilemez.|En az bir ATA Gateway’in [Etki alanı eşitleyicisi](install-ata-step5.md) olarak ayarlandığından emin olun.|Düşük|
### ATA Gateway’de bulunan tüm/bazı yakalama ağ bağdaştırıcıları kullanılamıyor
<a id="allsome-of-the-capture-network-adapters-on-an-ata-gateway-are-not-available" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Gateway’de bulunan tüm/bazı seçili yakalama ağ bağdaştırıcıları devre dışı veya bağlı değil.|Tüm/Bazı etki alanı denetleyicilerinin ağ trafiği artık ATA Gateway tarafından yakalanmıyor. Bu durum, bu etki alanı denetleyicileriyle ilgili şüpheli etkinlikleri algılama becerisini etkiler.|ATA Gateway’de bulunan bu seçili yakalama ağ bağdaştırıcılarının etkin ve bağlı olduğundan emin olun.|Orta|
### Bir ATA Gateway, bazı etki alanı denetleyicilerine erişemiyor
<a id="some-domain-controllers-are-unreachable-by-a-ata-gateway" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Bazı yapılandırılmış etki alanı denetleyicilerine bağlantı sorunlarından ötürü bir ATA Gateway’in işlevleri sınırlandırıldı.|Bazı etki alanı denetleyicileri ATA Gateway tarafından sorgulanamadığında Pass the Hash algılamasının doğruluğu azalabilir.|Etki alanı denetleyicilerinin çalışıyor olduğundan ve ATA Gateway’in bunlara LDAP bağlantıları yapabildiğinden emin olun.|Orta|
### Bir ATA Gateway, hiçbir etki alanı denetleyicisine erişemiyor
<a id="all-domain-controllers-are-unreachable-by-a-ata-gateway" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Tüm yapılandırılmış etki alanı denetleyicilerine bağlantı sorunlarından ötürü bir ATA Gateway şu anda çevrimdışı.|Bu durum, ATA’nın bu ATA Gateway tarafından izlenen etki alanı denetleyicileriyle ilgili şüpheli etkinlikleri algılama becerisini etkiler.| Etki alanı denetleyicilerinin çalışıyor olduğundan ve ATA Gateway’in bunlara LDAP bağlantıları yapabildiğinden emin olun.|Orta|
### ATA Gateway iletişimi durdurdu
<a id="ata-gateway-stopped-communicating" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Gateway’den hiçbir iletişim yok. Bu uyarı için varsayılan süre 5 dakikadır.|Ağ trafiği artık ATA Gateway’de bulunan ağ bağdaştırıcısı tarafından yakalanmıyor. Ağ trafiği ATA Center’a erişemeyeceği için bu durum, ATA’nın şüpheli etkinlikleri algılama becerisini etkiler.|ATA Gateway ve ATA Center arasında iletişimi sağlayan bağlantı noktasının bir yönlendirici veya güvenlik duvarı tarafından engellenip engellenmediğini kontrol edin.|Orta|
### Etki alanı denetleyicisinden trafik alınmıyor
<a id="no-traffic-received-from-domain-controller" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Bu ATA Gateway, etki alanı denetleyicisinden trafik almıyor.|Bu uyarı, etki alanı denetleyicilerinden ATA Gateway’e bağlantı noktası yansıtmanın henüz yapılandırılmadığını veya çalışmadığını gösteriyor olabilir.|[Ağ cihazlarınızda bağlantı noktası yansıtmanın düzgün yapılandırıldığını](configure-port-mirroring.md) doğrulayın.|Orta|
### Bazı iletilen olaylar çözümlenmiyor
<a id="some-forwarded-events-are-not-being-analyzed" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Gateway, işleyebileceğinden daha fazla olay alıyor.|Bazı iletilen olayların çözümlenmemesi, etki alanı denetleyicilerinin bu ATA Gateway tarafından izlemesinden kaynaklanan şüpheli etkinlikleri algılama becerisini etkileyebilir.|Yalnızca gerekli olayların ATA Gateway’e iletildiğini doğrulayın veya olaylardan bazılarını başka bir ATA Gateway’e iletin.|Orta|
### Ağ trafiğinin bir kısmı çözümlenmiyor
<a id="some-network-traffic-is-not-being-analyzed" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Gateway, işleyebileceğinden daha fazla ağ trafiği alıyor.|Ağ trafiğinin bir kısmının çözümlenmemesi, etki alanı denetleyicilerinin bu ATA Gateway tarafından izlemesinden kaynaklanan şüpheli etkinlikleri algılama becerisini etkileyebilir.|Gerektiği kadar [ek işlemci ve bellek eklemeyi](ata-capacity-planning.md) deneyin. Bu, tek başına bir ATA Gateway ise izlenen etki alanı denetleyicilerinin sayısını azaltın.|Orta|

### ATA Gateway sürümü güncel değil
<a id="ata-gateway-version-outdated" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Center, ATA Gateway'de yüklü olan sürümden daha yeni. Bu, ATA Gateway’in olması gerektiği gibi çalışmasına engel oluyor.|Bu durum, etki alanı denetleyicilerinin ATA Gateway tarafından izlenmesinden kaynaklanan şüpheli etkinlikleri algılama becerisini etkileyebilir.|ATA Gateway’i ATA Konsolu’nda [otomatik güncelleştirmeyi](install-ata-step1.md) etkinleştirip otomatik olarak veya ATA Konsolu’nda kullanılabilir olan son ATA Gateway paketini indirip el ile son sürüme güncelleştirin.|Yüksek|
### ATA Gateway hizmeti başlatılamadı
<a id="ata-gateway-service-failed-to-start" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Gateway hizmeti en az 30 dakika boyunca başlatılamadı.|Bu durum, etki alanı denetleyicilerinin ATA Gateway tarafından izlenmesinden kaynaklanan şüpheli etkinlikleri algılama becerisini etkileyebilir.|[ATA Gateway hizmet hatasının kök nedenini anlamak](troubleshooting-ata-using-logs.md) için ATA Gateway günlüklerini izleyin.|Yüksek|
## Lightweight Gateway
<a id="lightweight-gateway" class="xliff"></a>
### Lightweight ATA Gateway bellek kaynağı sınırına ulaştı
<a id="lightweight-ata-gateway-reached-a-memory-resource-limit" class="xliff"></a>
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Lightweight ATA Gateway kendini durdurdu ve etki alanı denetleyicisini düşük bellek durumundan korumak için otomatik olarak yeniden başlayacak.|Lightweight ATA Gateway, etki alanı denetleyicisinin kaynak sınırlamaları yaşamasını engellemek için kendisine bellek sınırlamaları uygular. Bu durum, etki alanı denetleyicisinde bellek kullanımı fazla olduğunda ortaya çıkar. Bu etki alanı denetleyicisi verileri yalnızca kısmen izlenir.|Etki alanı denetleyicisindeki bellek (RAM) miktarını artırın veya bu siteye daha fazla etki alanı denetleyicisi ekleyerek bu etki alanı denetleyicisinin yükünü azaltın.|Orta|


## Ayrıca Bkz.
<a id="see-also" class="xliff"></a>
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
