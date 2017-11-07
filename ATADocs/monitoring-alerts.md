---
title: "ATA izleme uyarılarını anlama | Microsoft Docs"
description: "Sorunları gidermek için ATA günlüklerini nasıl kullanabileceğiniz açıklanır"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: b04fb8a4-b366-4b55-9d4c-6f054fa58a90
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 3b39014499d77c2671f946a693b47be5b8db0f38
ms.sourcegitcommit: e2cb3af9c1dbb0b75946dc70cc439b19d654541c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



ATA Sistem Durumu Merkezi, ATA dağıtımı ile ilgili bir sorun olduğunda izleme uyarısı göndererek sizi bilgilendirir.
Bu makalede, sorunların sebebi ve çözüm yolunun bulunduğu bir listeyle her bir bileşen için izleme uyarıları açıklanmaktadır.
## <a name="ata-center-issues"></a>ATA Center Sorunları
### <a name="center-running-out-of-disk-space"></a>Disk alanının azalıp Merkezi
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Center makine sürücüsünde, ATA veritabanını depolamak için kullanılan boş alan azalıyor.|Bu uyarı, sabit sürücüde 200 GB’tan veya %20’den (hangisi daha düşük bir miktara karşılık geliyorsa) az boş alan kaldığı anlamına gelir. ATA, sürücüde boş alanın azaldığını fark ettiğinde veritabanındaki eski verileri silmeye başlar. Ancak algılama altyapısı için hala eski verilere ihtiyacı varsa verileri silemez ve bu uyarıyı gönderir. Bu uyarıyı aldığınızda ATA, yeni etkinlikleri izlemeyi durdurur.|Sürücü boyutunu artırın veya mevcut sürücünüzde boş alan yaratın.|Yüksek|
### <a name="failure-sending-mail"></a>Posta gönderme hatası
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA, belirtilen posta sunucusuna bir e-posta bildirimi gönderemedi.|ATA’dan herhangi bir e-posta iletisi gönderilemez.|SMTP sunucusunun yapılandırmasını doğrulayın.|Düşük|

### <a name="center-overloaded"></a>Aşırı yüklenmiş Merkezi
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Center, ATA Gateway’lerinden aktarılan veri miktarını kaldıramıyor. |ATA Center, yeni ağ trafiğini ve olayları çözümlemeyi durdurur. Yani bu uyarı etkinken algılamanın ve profillerin doğruluk oranı düşecektir.|ATA Center için yeterli kaynağı sağladığınızdan emin olun. ATA Center kapasitesini nasıl doğru planlayacağınıza ilişkin ayrıntılar için bkz. [ATA kapasitesini planlama](ata-capacity-planning.md). [Performans sayaçlarını kullanarak ATA sorunlarını giderme](troubleshooting-ata-using-perf-counters.md) ile ATA Center’ın performansını denetleyin.|Yüksek|

### <a name="failure-connecting-to-the-siem-server-using-syslog"></a>Syslog kullanarak SIEM sunucusuna bağlanma başarısız
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA, belirtilen SIEM’e olay gönderemedi.|Bu uyarı ATA Center’ın, şüpheli etkinlikleri ve izleme uyarılarını SIEM’inize gönderemediği anlamına gelir.|[Syslog sunucusu ayarlarının düzgün yapılandırılmış olduğundan](setting-syslog-email-server-settings.md) emin olun.|Düşük|
### <a name="center-certificate-is-about-to-expire"></a>Merkezi sertifika dolmak üzere olduğu
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Center sertifikasının 3 haftadan az bir süresi kaldı.|Sertifikanın süresi dolduktan sonra: ATA Gateway’lerinden ATA Center’a bağlantı başarısız olacaktır. ATA Center süreci kilitlenecek ve ATA işlevleri duracaktır.|[ATA Center sertifikasını değiştirin](modifying-ata-center-configuration.md)|Orta|
### <a name="ata-center-certificate-expired"></a>ATA Center sertifikasının süresi doldu
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Center sertifikasının süresi doldu.|Sertifikanın süresi dolduktan sonra: ATA Gateway’lerinden ATA Center’a bağlantı başarısız olacaktır. ATA Center süreci kilitlenecek ve ATA işlevleri duracaktır.|[ATA Center sertifikasını değiştirin](modifying-ata-center-configuration.md)|Yüksek|
## <a name="ata-gateway-issues"></a>ATA Gateway sorunları
### <a name="read-only-user-password-to-expire-shortly"></a>Kısa bir süre sonra süresi dolacak şekilde salt okunur kullanıcı parolası
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Active Directory varlıklarının çözümü için kullanılan salt okunur kullanıcı parolasının 30 günden az bir süresi kaldı.|Bu kullanıcı için parola süresi dolarsa tüm ATA Gateway’leri çalışmayı durduracak ve yeni veri toplanmayacaktır.|[Etki alanı bağlantı parolasını değiştirin](modifying-ata-config-dcpassword.md) ve daha sonra ATA Konsolu’ndaki parolayı güncelleştirin.|Orta|
### <a name="read-only-user-password-expired"></a>Salt okunur kullanıcı parolasının süresi doldu
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Dizin verilerini almak için kullanılan salt okunur kullanıcı parolasının süresi doldu.|Tüm ATA Gateway’ler çalışmayı durdurdu (veya yakında durduracak) ve yeni veri toplanmayacak.|[Etki alanı bağlantı parolasını değiştirin](modifying-ata-config-dcpassword.md) ve daha sonra ATA Konsolu’ndaki parolayı güncelleştirin.|Yüksek|
### <a name="gateway-certificate-about-to-expire"></a>Ağ geçidi sertifikası dolmak üzere
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Gateway sertifikasının 3 haftadan az bir süresi kaldı.|Bu ATA Gateway’den ATA Center’a yapılan bağlantı başarısız olacaktır. ATA Gateway’den hiçbir veri gönderilmeyecektir.|ATA Gateway sertifikasının otomatik olarak yenilenmesi gerekir. Bu Sertifikanın neden otomatik olarak yenilenmediğini öğrenmek için ATA Gateway ve ATA Center günlüklerini okuyun.|Orta|

### <a name="gateway-certificate-expired"></a>Ağ geçidi sertifikasının süresi doldu
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Gateway sertifikasının süresi doldu.|Bu ATA Gateway’den ATA Center’a bağlantı yapılamaz. ATA Gateway’den hiçbir veri gönderilmeyecektir.|[ATA Gateway’i kaldırma ve yeniden yükleme](install-ata-step3.md).|Yüksek|
### <a name="domain-synchronizer-not-assigned"></a>Etki alanı eşitleyicisi atanmadı
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Bir ATA Gateway’e hiçbir etki alanı eşitleyicisi atanmadı. Etki alanı eşitleyicisi adayı olarak yapılandırılmış bir ATA Gateway yoksa bu durum oluşabilir.|Etki alanı eşitlenmediğinde varlıklarda yapılan değişiklikler, ATA’daki bilgilerin güncelliğini yitirmesine veya kaybolmasına yol açabilir ancak algılamayı etkilemez.|En az bir ATA Gateway’in [Etki alanı eşitleyicisi](install-ata-step5.md) olarak ayarlandığından emin olun.|Düşük|
### <a name="allsome-of-the-capture-network-adapters-on-a-gateway-are-not-available"></a>Tüm/bazı bir ağ geçidi yakalama ağ bağdaştırıcılarında kullanılabilir değil
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Gateway’de bulunan tüm/bazı seçili yakalama ağ bağdaştırıcıları devre dışı veya bağlı değil.|Tüm/Bazı etki alanı denetleyicilerinin ağ trafiği artık ATA Gateway tarafından yakalanmıyor. Bu durum, bu etki alanı denetleyicileriyle ilgili şüpheli etkinlikleri algılama becerisini etkiler.|ATA Gateway’de bulunan bu seçili yakalama ağ bağdaştırıcılarının etkin ve bağlı olduğundan emin olun.|Orta|
### <a name="some-domain-controllers-are-unreachable-by-a-gateway"></a>Bazı etki alanı denetleyicileri Gateway tarafından erişilemiyor
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Bazı yapılandırılmış etki alanı denetleyicilerine bağlantı sorunlarından ötürü bir ATA Gateway’in işlevleri sınırlandırıldı.|Bazı etki alanı denetleyicileri ATA Gateway tarafından sorgulanamadığında Pass the Hash algılamasının doğruluğu azalabilir.|Etki alanı denetleyicilerinin çalışıyor olduğundan ve ATA Gateway’in bunlara LDAP bağlantıları yapabildiğinden emin olun.|Orta|
### <a name="all-domain-controllers-are-unreachable-by-a-gateway"></a>Tüm etki alanı denetleyicilerinin bir ağ geçidi tarafından erişilemiyor
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Tüm yapılandırılmış etki alanı denetleyicilerine bağlantı sorunlarından ötürü bir ATA Gateway şu anda çevrimdışı.|Bu durum, ATA’nın bu ATA Gateway tarafından izlenen etki alanı denetleyicileriyle ilgili şüpheli etkinlikleri algılama becerisini etkiler.| Etki alanı denetleyicilerinin çalışıyor olduğundan ve ATA Gateway’in bunlara LDAP bağlantıları yapabildiğinden emin olun.|Orta|
### <a name="gateway-stopped-communicating"></a>Ağ geçidi iletişim durduruldu
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Gateway’den hiçbir iletişim yok. Bu uyarı için varsayılan süre 5 dakikadır.|Ağ trafiği artık ATA Gateway’de bulunan ağ bağdaştırıcısı tarafından yakalanmıyor. Ağ trafiği ATA Center’a erişemeyeceği için bu durum, ATA’nın şüpheli etkinlikleri algılama becerisini etkiler.|ATA Gateway ve ATA Center arasında iletişimi sağlayan bağlantı noktasının bir yönlendirici veya güvenlik duvarı tarafından engellenip engellenmediğini kontrol edin.|Orta|
### <a name="no-traffic-received-from-domain-controller"></a>Etki alanı denetleyicisinden trafik alınmıyor
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Bu ATA Gateway, etki alanı denetleyicisinden trafik almıyor.|Bu uyarı, etki alanı denetleyicilerinden ATA Gateway’e bağlantı noktası yansıtmanın henüz yapılandırılmadığını veya çalışmadığını gösteriyor olabilir.|[Ağ cihazlarınızda bağlantı noktası yansıtmanın düzgün yapılandırıldığını](configure-port-mirroring.md) doğrulayın.<br></br>ATA Gateway'de NIC yakalama, Gelişmiş Ayarları'nda bu özellikleri devre dışı bırak:<br></br>Alma Kesimi Birleştirme (IPv4)<br></br>Alma Kesimi Birleştirme (IPv6)|Orta|
### <a name="some-forwarded-events-are-not-being-analyzed"></a>Bazı iletilen olaylar çözümlenmiyor
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Gateway, işleyebileceğinden daha fazla olay alıyor.|Bazı iletilen olayların çözümlenmemesi, etki alanı denetleyicilerinin bu ATA Gateway tarafından izlemesinden kaynaklanan şüpheli etkinlikleri algılama becerisini etkileyebilir.|Yalnızca gerekli olayların ATA Gateway’e iletildiğini doğrulayın veya olaylardan bazılarını başka bir ATA Gateway’e iletin.|Orta|
### <a name="some-network-traffic-is-not-being-analyzed"></a>Ağ trafiğinin bir kısmı çözümlenmiyor
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Gateway, işleyebileceğinden daha fazla ağ trafiği alıyor.|Ağ trafiğinin bir kısmının çözümlenmemesi, etki alanı denetleyicilerinin bu ATA Gateway tarafından izlemesinden kaynaklanan şüpheli etkinlikleri algılama becerisini etkileyebilir.|Gerektiği kadar [ek işlemci ve bellek eklemeyi](ata-capacity-planning.md) deneyin. Bu, tek başına bir ATA Gateway ise izlenen etki alanı denetleyicilerinin sayısını azaltın.<br></br>VMware sanal makinelerde etki alanı denetleyicileri kullanıyorsanız, bu da meydana gelebilir. Bu uyarıları önlemek için aşağıdaki ayarların sanal makinede 0 veya Devre Dışı olarak ayarlandığını denetleyebilirsiniz:<br></br>-TsoEnable<br></br>-LargeSendOffload(IPv4)<br></br>-IPv4 TSO boşaltma<br></br>Ayrıca, IPv4 Büyük TSO Boşaltma’yı devre dışı bırakabilirsiniz. Daha fazla bilgi için VMware belgelerinize başvurun.|Orta|

### <a name="gateway-version-outdated"></a>Eski ağ geçidi sürümü
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Center, ATA Gateway'de yüklü olan sürümden daha yeni. Bu, ATA Gateway’in olması gerektiği gibi çalışmasına engel oluyor.|Bu durum, etki alanı denetleyicilerinin ATA Gateway tarafından izlenmesinden kaynaklanan şüpheli etkinlikleri algılama becerisini etkileyebilir.|ATA Gateway’i ATA Konsolu’nda [otomatik güncelleştirmeyi](install-ata-step1.md) etkinleştirip otomatik olarak veya ATA Konsolu’nda kullanılabilir olan son ATA Gateway paketini indirip el ile son sürüme güncelleştirin.|Yüksek|
### <a name="gateway-service-failed-to-start"></a>Ağ Geçidi Hizmeti başlatılamadı
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|ATA Gateway hizmeti en az 30 dakika boyunca başlatılamadı.|Bu durum, etki alanı denetleyicilerinin ATA Gateway tarafından izlenmesinden kaynaklanan şüpheli etkinlikleri algılama becerisini etkileyebilir.|[ATA Gateway hizmet hatasının kök nedenini anlamak](troubleshooting-ata-using-logs.md) için ATA Gateway günlüklerini izleyin.|Yüksek|
## <a name="lightweight-gateway"></a>Lightweight Gateway
### <a name="lightweight--gateway-reached-a-memory-resource-limit"></a>Bellek kaynak sınırına lightweight Gateway
|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Lightweight ATA Gateway kendini durdurdu ve etki alanı denetleyicisini düşük bellek durumundan korumak için otomatik olarak yeniden başlayacak.|Lightweight ATA Gateway, etki alanı denetleyicisinin kaynak sınırlamaları yaşamasını engellemek için kendisine bellek sınırlamaları uygular. Bu durum, etki alanı denetleyicisinde bellek kullanımı fazla olduğunda ortaya çıkar. Bu etki alanı denetleyicisi verileri yalnızca kısmen izlenir.|Etki alanı denetleyicisindeki bellek (RAM) miktarını artırın veya bu siteye daha fazla etki alanı denetleyicisi ekleyerek bu etki alanı denetleyicisinin yükünü azaltın.|Orta|


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
