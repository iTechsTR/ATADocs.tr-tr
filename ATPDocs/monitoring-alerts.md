---
title: İzleme uyarılarını anlama Azure ATP | Microsoft Docs
description: Sorunları gidermek için Azure ATP günlüklerini nasıl kullanabileceğiniz açıklanır
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: d0551e91-3b21-47d5-ad9d-3362df6d47c0
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: eed1509cb31885bccdfcc40505284dbdbdfc4cca
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48783891"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*

# <a name="understanding-azure-atp-sensor-and-standalone-sensor-monitoring-alerts"></a>Azure ATP algılayıcısını ve tek başına algılayıcı izleme uyarılarını anlama

Azure ATP sistem durumu Merkezi, bir sorun olduğunda, Azure ATP çalışma alanı ile bir izleme uyarısı göndererek bilmenizi sağlar. Bu makalede, sorunların sebebi ve çözüm yolunun bulunduğu bir listeyle her bir bileşen için izleme uyarıları açıklanmaktadır.

## <a name="read-only-user-password-to-expire-shortly"></a>Salt okunur kullanıcı parolası, süresi yakında dolacak

|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Active Directory varlıklarının çözümü için kullanılan salt okunur kullanıcı parolasının 30 günden az bir süresi kaldı.|Bu kullanıcı için parola süresi dolarsa Azure ATP algılayıcı çalışmayı durdurur ve yeni veri toplanır.|[Etki alanı bağlantı parolasını değiştirme](modifying-atp-config-dcpassword.md) ve ardından Azure ATP portalında parolasını güncelleştirin.|Orta|

## <a name="read-only-user-password-expired"></a>Salt okunur kullanıcı parolasının süresi doldu

|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Dizin verilerini almak için kullanılan salt okunur kullanıcı parolasının süresi doldu.|Azure ATP algılayıcı çalışmayı durdurur (veya yakında durduracak) ve yeni veri toplanır.|[Etki alanı bağlantı parolasını değiştirme](modifying-atp-config-dcpassword.md) ve ardından Azure ATP portalında parolasını güncelleştirin.|Yüksek|

## <a name="domain-synchronizer-not-assigned"></a>Etki alanı eşitleyicisi atanmadı

|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Etki alanı Eşitleyici yoksa için herhangi bir Azure ATP algılayıcısını atanır. Bu, etki alanı Eşitleyici adayı olarak yapılandırılmış hiçbir Azure ATP algılayıcısını olup olmadığını ortaya çıkabilir.|Etki alanı eşitlenmediğinde varlıklarda yapılan değişiklikler varlık bilgilerini yitirmesine veya eski Azure ATP'de yol açabilir ancak algılamayı etkilemez.|Emin olun, en az bir Azure ATP algılayıcısını olarak ayarlandığında bir [etki alanı Eşitleyicisi](install-atp-step5.md).|Düşük|

## <a name="allsome-of-the-capture-network-adapters-on-a-sensor-are-not-available"></a>Tüm/bazı yakalama ağ bağdaştırıcıları bir algılayıcıdaki kullanılabilir değil

|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Tüm/bazı seçili yakalama ağ bağdaştırıcıları üzerinde Azure ATP algılayıcısını devre dışı veya bağlı değil.|Tüm/bazı etki alanı denetleyicilerinin ağ trafiği artık Azure ATP algılayıcı tarafından yakalanmıyor. Bu, bu etki alanı denetleyicileriyle ilgili şüpheli etkinlikleri algılama becerisini etkiler.|Azure ATP algılayıcısını bulunan bu seçili yakalama ağ bağdaştırıcılarının etkin ve bağlı olduğundan emin olun.|Orta|

## <a name="some-domain-controllers-are-unreachable-by-a-sensor"></a>Bir algılayıcı tarafından bazı etki alanı denetleyicilerine ulaşılamıyor

|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Azure ATP algılayıcısını bazı yapılandırılmış etki alanı denetleyicilerine bağlantı sorunlarından ötürü işlevleri sınırlıdır.|Pass the Hash algılamasının daha az doğru olduğunda Azure ATP algılayıcı tarafından bazı etki alanı denetleyicilerine sorgulanamıyor olabilir.|Etki alanı denetleyicilerinin çalışıyor olduğundan ve bu Azure ATP algılayıcısını bunlara LDAP bağlantıları yapabildiğinden emin olun.|Orta|

## <a name="all-domain-controllers-are-unreachable-by-a-sensor"></a>Bir algılayıcı tarafından tüm etki alanı denetleyicilerine ulaşılamıyor

|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Azure ATP algılayıcısını tüm yapılandırılmış etki alanı denetleyicilerine bağlantı sorunlarından ötürü şu anda çevrimdışı.|Bu, Azure ATP'ın bu Azure ATP algılayıcı tarafından izlenen etki alanı denetleyicileri ilgili şüpheli etkinlikleri algılama becerisini etkiler.| Etki alanı denetleyicilerinin çalışıyor olduğundan ve bu Azure ATP algılayıcısını bunlara LDAP bağlantıları yapabildiğinden emin olun.|Orta|

## <a name="sensor-stopped-communicating"></a>Algılayıcı iletişimi durdurdu

|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Azure ATP algılayıcısını iletişimi yok geldi. Bu uyarı için varsayılan süre 5 dakikadır.|Ağ trafiği artık Azure ATP algılayıcısını üzerindeki ağ bağdaştırıcısı tarafından yakalanmıyor. Bu, ATA'ın ağ trafiğini bulut hizmetini Azure ATP ulaşabildiğinden bulunmaz şüpheli etkinlikleri algılama becerisini etkiler.|Azure ATP algılayıcısını Azure ATP bulut hizmeti arasında iletişim için kullanılan bağlantı noktası bir yönlendirici veya güvenlik duvarı tarafından engellenip engellenmediğini kontrol edin.|Orta|

## <a name="no-traffic-received-from-domain-controller"></a>Etki alanı denetleyicisinden trafik alınmıyor

|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Bu Azure ATP algılayıcısını aracılığıyla etki alanı denetleyicisinden trafik alınmadı.|Bu Azure ATP algılayıcısını için etki alanı denetleyicilerinden bağlantı noktası yansıtmanın henüz yapılandırılmadığını belirtebilir veya çalışmıyor.|[Ağ cihazlarınızda bağlantı noktası yansıtmanın düzgün yapılandırıldığını](configure-port-mirroring.md) doğrulayın.<br></br>Azure ATP algılayıcısını üzerinde yakalama NIC'SİNDEKİ, Gelişmiş ayarları bu özellikleri devre dışı bırakın:<br></br>Alma Kesimi Birleştirme (IPv4)<br></br>Alma Kesimi Birleştirme (IPv6)|Orta|

## <a name="some-forwarded-events-are-not-being-analyzed"></a>Bazı iletilen olaylar çözümlenmiyor

|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Azure ATP algılayıcısı, işleyebileceğinden daha fazla olay alıyor.|Bazı iletilen olaylar, hangi etki alanı denetleyicilerinin bu Azure ATP algılayıcı tarafından izlemesinden kaynaklanan şüpheli etkinlikleri algılama becerisini etkileyebilir analiz edilmiyor.|Yalnızca gerekli olayları için Azure ATP algılayıcısını iletilen veya bazı başka bir Azure ATP algılayıcısını olaylara iletin doğrulayın.|Orta|

## <a name="some-network-traffic-is-not-being-analyzed"></a>Ağ trafiğinin bir kısmı çözümlenmiyor

|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Azure ATP algılayıcısı, işleyebileceğinden daha fazla ağ trafiği alıyor.|Ağ trafiğinin bir kısmı, hangi etki alanı denetleyicilerinin bu Azure ATP algılayıcı tarafından izlemesinden kaynaklanan şüpheli etkinlikleri algılama becerisini etkileyebilir edilmiyor.|Gerektiği kadar [ek işlemci ve bellek eklemeyi](atp-capacity-planning.md) deneyin. Bu bir tek başına Azure ATP algılayıcısını ise, izlenen etki alanı denetleyicilerinin sayısını azaltın.<br></br>VMware sanal makinelerindeki etki alanı denetleyicileri kullanıyorsanız, bu da oluşabilir. Bu uyarıları önlemek için aşağıdaki ayarların sanal makinede 0 veya Devre Dışı olarak ayarlandığını denetleyebilirsiniz:<br></br>-TsoEnable<br></br>-LargeSendOffload(IPv4)<br></br>-IPv4 TSO boşaltma<br></br>Ayrıca, IPv4 Büyük TSO Boşaltma’yı devre dışı bırakabilirsiniz. Daha fazla bilgi için VMware belgelerinize bakın.|Orta|

## <a name="sensor-service-failed-to-start"></a>Algılayıcı hizmeti başlatılamadı

|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Azure ATP algılayıcı hizmetinin en az 30 dakika boyunca başlatılamadı.|Bu, bu Azure ATP algılayıcı tarafından izlenen etki alanı denetleyicilerinin kaynaklanan şüpheli etkinlikleri algılama becerisini etkileyebilir.|Azure ATP algılayıcı hizmeti hatasının kök nedenini anlamak için Azure ATP algılayıcı günlüklerini İzleyici.|Yüksek|

## <a name="sensor-reached-a-memory-resource-limit"></a>Algılayıcı bir bellek kaynağı sınırına ulaştı

|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Azure ATP algılayıcısını kendini durdurdu ve etki alanı denetleyicisini düşük bellek durumundan korumak için otomatik olarak yeniden başlatır.|Azure ATP algılayıcısını etki alanı denetleyicisinin kaynak sınırlamaları yaşamasını engellemek için kendisine bellek sınırlamaları uygular. Bu durum, etki alanı denetleyicisinde bellek kullanımı fazla olduğunda ortaya çıkar. Bu etki alanı denetleyicisi verileri yalnızca kısmen izlenir.|Etki alanı denetleyicisindeki bellek (RAM) miktarını artırın veya bu siteye daha fazla etki alanı denetleyicisi ekleyerek bu etki alanı denetleyicisinin yükünü azaltın.|Orta|

## <a name="sensor-outdated"></a>eski algılayıcısı

|Uyarı|Açıklama|Çözüm|Önem Derecesi|
|----|----|----|----|
|Azure ATP algılayıcısını güncel değil.|Azure ATP algılayıcısını üç veya daha fazla sürümü eski bir sürümünü çalıştırıyor.|El ile güncelleştirme sensör ve neden algılayıcı otomatik olarak güncelleştirilmiyor kontrol edin. Bu işe yaramazsa, en son algılayıcısı Kurulum paketini indirin ve kaldırın ve algılayıcıyı yükleyin. Daha fazla bilgi için [Azure ATP algılayıcısını yükleme](install-atp-step4.md).|Orta|

## <a name="see-also"></a>Ayrıca Bkz.

- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)