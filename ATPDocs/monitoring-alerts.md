---
title: "İzleme uyarıları anlama Azure ATP | Microsoft Docs"
description: "Sorunları gidermek için Azure ATP günlüklerini nasıl kullanabileceğiniz açıklanır"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: d0551e91-3b21-47d5-ad9d-3362df6d47c0
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: cdb440e92aef0f9d09d3aa9411d0ce65435469d1
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*

# <a name="understanding-azure-atp-sensor-and-standalone-sensor-monitoring-alerts"></a>Azure ATP algılayıcı ve tek başına algılayıcı izleme uyarıları anlama

Azure ATP sistem durumu Merkezi, bir sorun olduğunda, Azure ATP worksapces biriyle izleme uyarı yükselterek bilmenizi sağlar. Bu makalede, sorunların sebebi ve çözüm yolunun bulunduğu bir listeyle her bir bileşen için izleme uyarıları açıklanmaktadır.

## <a name="read-only-user-password-to-expire-shortly"></a>Kısa bir süre sonra süresi dolacak şekilde salt okunur kullanıcı parolası

|Uyarı|Description|Çözüm|Önem Derecesi|
|----|----|----|----|
|Active Directory varlıklarının çözümü için kullanılan salt okunur kullanıcı parolasının 30 günden az bir süresi kaldı.|Bu kullanıcı için parola süresi dolarsa, çalışan tüm Azure ATP algılayıcılar durdurun ve yeni hiçbir veri toplanmadı.|[Etki alanı bağlantı parolasını değiştirme](modifying-atp-config-dcpassword.md) ve ardından Azure ATP konsolunda parolasını güncelleştirin.|Orta|

## <a name="read-only-user-password-expired"></a>Salt okunur kullanıcı parolasının süresi doldu

|Uyarı|Description|Çözüm|Önem Derecesi|
|----|----|----|----|
|Dizin verilerini almak için kullanılan salt okunur kullanıcı parolasının süresi doldu.|Tüm Azure ATP algılayıcılar çalışmıyor (veya en kısa sürede çalışmayı durdurur) ve yeni hiçbir veri toplanmadı.|[Etki alanı bağlantı parolasını değiştirme](modifying-atp-config-dcpassword.md) ve ardından Azure ATP konsolunda parolasını güncelleştirin.|Yüksek|

## <a name="domain-synchronizer-not-assigned"></a>Etki alanı eşitleyicisi atanmadı

|Uyarı|Description|Çözüm|Önem Derecesi|
|----|----|----|----|
|Etki alanı Eşitleyici tüm Azure ATP algılayıcı atanır. Bu, etki alanı Eşitleyici adayı yapılandırılmış hiçbir Azure ATP algılayıcı olup olmadığını ortaya çıkabilir.|Etki alanı değil eşitlendiğinde, değişiklikler varlıklar için varlık bilgilerini ATP eksik veya güncel olmasını Azure neden olabilir, ancak herhangi algılama etkilemez.|Emin olun, en az bir Azure ATP algılayıcı olarak ayarlanan bir [etki alanı Eşitleyici](install-atp-step5.md).|Düşük|

## <a name="allsome-of-the-capture-network-adapters-on-a-sensor-are-not-available"></a>Tüm/bazı algılayıcı yakalama ağ bağdaştırıcılarında kullanılabilir değil

|Uyarı|Description|Çözüm|Önem Derecesi|
|----|----|----|----|
|Tüm/bazı Azure ATP algılayıcı seçilen yakalama ağ bağdaştırıcısı veya devre dışı bağlantısı kesildi.|Bazı/tüm etki alanı denetleyicilerinin ağ trafiğini artık Azure ATP algılayıcı tarafından yakalanır. Bu etki alanı denetleyicileri için ilgili kuşkulu etkinlikleri algılama yeteneği etkiler.|Bu Azure ATP algılayıcı seçilen yakalama ağ bağdaştırıcılarında etkin ve bağlı olduğundan emin olun.|Orta|

## <a name="some-domain-controllers-are-unreachable-by-a-sensor"></a>Bazı etki alanı denetleyicileri tarafından algılayıcı erişilemiyor

|Uyarı|Description|Çözüm|Önem Derecesi|
|----|----|----|----|
|Bir Azure ATP algılayıcı yapılandırılmış etki alanı denetleyicileri, bazı bağlantı sorunları nedeniyle işlevleri sınırlıdır.|Geçişi karma algılama daha az doğru olduğunda bazı etki alanı denetleyicileri Azure ATP algılayıcı tarafından sorgulanamıyor olabilir.|Etki alanı denetleyicileri ve çalışıyor olduğundan ve bu Azure ATP algılayıcı bunlara LDAP bağlantıları'nı açmak emin olun.|Orta|

## <a name="all-domain-controllers-are-unreachable-by-a-sensor"></a>Tüm etki alanı denetleyicileri tarafından algılayıcı erişilemiyor

|Uyarı|Description|Çözüm|Önem Derecesi|
|----|----|----|----|
|Azure ATP algılayıcı tüm yapılandırılmış etki alanı denetleyicileri için bağlantı sorunu nedeniyle şu anda çevrimdışı.|Azure ATP'ın bu Azure ATP algılayıcı tarafından izlenen etki alanı denetleyicilerinin ilgili kuşkulu etkinlikleri algılama yeteneği etkiler.| Etki alanı denetleyicileri ve çalışıyor olduğundan ve bu Azure ATP algılayıcı bunlara LDAP bağlantıları'nı açmak emin olun.|Orta|

## <a name="sensor-stopped-communicating"></a>iletişim Algılayıcısı durduruldu

|Uyarı|Description|Çözüm|Önem Derecesi|
|----|----|----|----|
|Azure ATP algılayıcı iletişimi yok açıldı. Bu uyarı için varsayılan süre 5 dakikadır.|Ağ trafiği, artık Azure ATP algılayıcı ağ bağdaştırıcısında tarafından yakalanır. ATA'ın ağ trafiğini Azure ATP bulut hizmete erişmek değil bağlanamayacağından şüpheli etkinlikleri algılamanıza yeteneğini etkiler.|Azure ATP algılayıcı ve Azure ATP bulut hizmeti arasındaki iletişimi için kullanılan bağlantı herhangi bir yönlendirici veya güvenlik duvarı tarafından engellenmediğinden emin olun.|Orta|

## <a name="no-traffic-received-from-domain-controller"></a>Etki alanı denetleyicisinden trafik alınmıyor

|Uyarı|Description|Çözüm|Önem Derecesi|
|----|----|----|----|
|Hiçbir trafik bu Azure ATP algılayıcı aracılığıyla etki alanı denetleyicisinden alınmadı.|Bu etki alanı denetleyicilerinden Azure ATP algılayıcı bağlantı noktası yansıtma henüz yapılandırılmadığını gösterebilir veya çalışmıyor.|[Ağ cihazlarınızda bağlantı noktası yansıtmanın düzgün yapılandırıldığını](configure-port-mirroring.md) doğrulayın.<br></br>NIC üzerinde Azure ATP algılayıcı yakalama, Gelişmiş Ayarları'nda bu özellikleri devre dışı bırak:<br></br>Alma Kesimi Birleştirme (IPv4)<br></br>Alma Kesimi Birleştirme (IPv6)|Orta|

## <a name="some-forwarded-events-are-not-being-analyzed"></a>Bazı iletilen olaylar çözümlenmiyor

|Uyarı|Description|Çözüm|Önem Derecesi|
|----|----|----|----|
|Azure ATP algılayıcı işleyebileceğinden daha fazla olay alıyor.|Bazı iletilen olaylar, hangi bu Azure ATP algılayıcı tarafından izlenen etki alanı denetleyicilerinden kaynaklanan kuşkulu etkinlikleri algılama yeteneğini etkileyebilir çözümlenmekte değil.|Yalnızca gerekli olayları Azure ATP algılayıcı iletilmez veya başka bir Azure ATP algılayıcı olaylara bazıları iletmek deneyin doğrulayın.|Orta|

## <a name="some-network-traffic-is-not-being-analyzed"></a>Ağ trafiğinin bir kısmı çözümlenmiyor

|Uyarı|Description|Çözüm|Önem Derecesi|
|----|----|----|----|
|Azure ATP algılayıcı işleyebileceğinden daha fazla ağ trafiğini alıyor.|Bazı ağ trafiği, hangi bu Azure ATP algılayıcı tarafından izlenen etki alanı denetleyicilerinden kaynaklanan kuşkulu etkinlikleri algılama yeteneğini etkileyebilir analiz ediliyor değil.|Gerektiği kadar [ek işlemci ve bellek eklemeyi](atp-capacity-planning.md) deneyin. Bu tek başına Azure ATP algılayıcı ise, izlenmekte olan etki alanı denetleyicilerinin sayısını azaltın.<br></br>VMware sanal makinelerde etki alanı denetleyicileri kullanıyorsanız, bu da meydana gelebilir. Bu uyarıları önlemek için aşağıdaki ayarların sanal makinede 0 veya Devre Dışı olarak ayarlandığını denetleyebilirsiniz:<br></br>-TsoEnable<br></br>- LargeSendOffload(IPv4)<br></br>-IPv4 TSO boşaltma<br></br>Ayrıca, IPv4 Büyük TSO Boşaltma’yı devre dışı bırakabilirsiniz. Daha fazla bilgi için VMware belgelerinize bakın.|Orta|

## <a name="sensor-service-failed-to-start"></a>Algılayıcı hizmeti başlatılamadı

|Uyarı|Description|Çözüm|Önem Derecesi|
|----|----|----|----|
|En az 30 dakika için Azure ATP algılayıcı hizmeti başlatılamadı.|Bu, bu Azure ATP algılayıcı tarafından izlenen etki alanı denetleyicilerinden kaynaklanan kuşkulu etkinlikleri algılama yeteneğini etkileyebilir.|Azure ATP algılayıcı hizmet hatası kök nedeni anlamak için Azure ATP algılayıcı günlüklerini İzleyicisi.|Yüksek|

## <a name="sensor-reached-a-memory-resource-limit"></a>bellek kaynak sınırına algılayıcısı

|Uyarı|Description|Çözüm|Önem Derecesi|
|----|----|----|----|
|Azure ATP algılayıcı kendisini durdurulur ve etki alanı denetleyicisi düşük bellek durumundan korumak için otomatik olarak yeniden başlatılır.|Azure ATP algılayıcı etki alanı denetleyicisinin kaynak sınırlamaları yaşayan engeller kendisine bağlı bellek sınırlamaları zorlar. Bu durum, etki alanı denetleyicisinde bellek kullanımı fazla olduğunda ortaya çıkar. Bu etki alanı denetleyicisi verileri yalnızca kısmen izlenir.|Etki alanı denetleyicisindeki bellek (RAM) miktarını artırın veya bu siteye daha fazla etki alanı denetleyicisi ekleyerek bu etki alanı denetleyicisinin yükünü azaltın.|Orta|


## <a name="see-also"></a>Ayrıca bkz:

- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)