---
title: Azure Gelişmiş tehdit koruması mimarisi | Microsoft Docs
description: Azure Gelişmiş tehdit analizi (ATP) mimarisini açıklar
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 90f68f2c-d421-4339-8e49-1888b84416e6
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 6853a2a768fabde94c7aa613c9a6c0403f14e066
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48783568"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="azure-atp-architecture"></a>Azure ATP mimarisi

Azure ATP etki alanı denetleyicilerinizin yakalayarak ve ağ trafiği ayrıştırma ve yararlanarak doğrudan etki alanı denetleyicilerinizi Windows olayları izler ve saldırı ve tehdit verilerini analiz eder. Profil oluşturma, belirlenimci algılama, makine öğrenimi ve davranış algoritmalarını Azure ATP ağınız hakkında detaylı bilgi ediniyor yararlanarak anomali algılama sağlar ve şüpheli etkinliklerde sizi uyarır.

Azure Gelişmiş tehdit koruması mimarisi:

![Azure ATP mimarisi topoloji diyagramı](media/atp-architecture-topology.png)

Bu bölümde Azure ATP'ın ağ akışı ve olay yakalama nasıl çalışır ve aşağı temel bileşenlerinin işlevleri ayrıntılı açıklanmıştır açıklanmaktadır: Azure ATP portalı, Azure ATP algılayıcısını ve Azure ATP bulut hizmeti. 

Azure ATP algılayıcı doğrudan etki alanı denetleyicilerinize yüklü, doğrudan etki alanı denetleyicisinden gerekli olay günlüklerini erişir. Algılayıcı tarafından ağ trafiği ve günlükleri ayrıştırıldıktan sonra Azure ATP yalnızca ayrıştırılmış bilgileri (yalnızca günlükleri yüzdesi gönderilir) Azure ATP bulut hizmetine gönderir. 

## <a name="azure-atp-components"></a>Azure ATP bileşenleri
Azure ATP aşağıdaki bileşenlerden oluşur:

-   **Azure ATP portalı** <br>
Azure ATP portalı Azure ATP örneğinizin oluşturmanıza olanak sağlar, Azure ATP algılayıcılardan gelen verileri görüntüler ve izleme, yönetme ve ağ ortamınızdaki tehditlere araştırmanıza olanak sağlar.  
-   **Azure ATP algılayıcısı**<br>
Azure ATP algılayıcı doğrudan etki alanı denetleyicilerinize yüklenir. Algılayıcı adanmış sunucu veya bağlantı noktası yansıtmaya gerek kalmadan etki alanı denetleyicisi trafiğini doğrudan izler.

-   **Azure ATP bulut hizmeti**<br>
Azure ATP bulut hizmeti, Azure altyapısı üzerinde çalışır ve şu anda ABD, Avrupa ve Asya dağıtılır. Azure ATP bulut hizmeti için Microsoft akıllı güvenlik grafiği bağlıdır. 

## <a name="azure-atp-portal"></a>Azure ATP portalı 
Azure ATP portalına kullanın:
- Azure ATP örneğinizi oluşturma
- Diğer Microsoft Güvenlik Hizmetleri ile tümleştirme 
- Azure ATP algılayıcı yapılandırma ayarlarını yönetme 
- Azure ATP algılayıcılardan gelen verileri görüntüle
- Algılanan şüpheli etkinlikler ve saldırı sonlandırma zinciri modele dayalı tespit edildiğinde alınan önlemlerin saldırıları izleyin
- **İsteğe bağlı**: portal, e-postaları ve güvenlik uyarıları veya sistem durumu sorunu algılandığında olaylar göndermek için de yapılandırılabilir

> [!NOTE]
> - 60 gün içinde hiçbir algılayıcı, çalışma alanınızda yüklü değilse, çalışma alanı silinebilir ve yeniden oluşturmanız gerekir.

## <a name="azure-atp-sensor"></a>Azure ATP algılayıcısı
Azure ATP algılayıcısını aşağıdaki temel işlevleri vardır:
- Yakalama ve etki alanı denetleyicisi ağ trafiğinin (etki alanı denetleyicisinin yerel trafiği) denetleyin
- Doğrudan etki alanı denetleyicilerinden Windows olaylarını alma 
- VPN sağlayıcınız RADIUS hesap bilgilerini alma
- Active Directory etki alanından kullanıcılar ve bilgisayarlar hakkındaki verileri alma
- Ağ varlıklarının (kullanıcılar, gruplar ve bilgisayarlar) çözümlemesini yapma
- Azure ATP bulut hizmetine ilgili veri aktarımı

 
## <a name="azure-atp-sensor-features"></a>Azure ATP algılayıcısını özellikleri
Azure ATP algılayıcısını satın alın ve ek donanım veya yapılandırmaları gerek kalmadan olayları yerel olarak okur. Azure ATP algılayıcısını olay izleme için Windows (birden çok algılama için günlük bilgileri sağlayan ETW) da destekler. Şüpheli çoğaltma isteği ve şüpheli etki alanı denetleyicisi yükseltme ETW dayalı algılamalar şunları içerir, hem de olası DCShadow saldırılara karşı.
- Etki alanı eşitleyici adayı

    Etki alanı Eşitleyici adayı, belirli bir Active Directory etki alanından tüm varlıkların önceden tedbirli olarak eşitlenmesinden sorumludur (etki alanı denetleyicileri tarafından kendileri çoğaltma için kullanılan mekanizmaya benzer). Bir algılayıcı adaylar listesinden, etki alanı Eşitleyici görevi görmesi için rastgele seçilir. 

    Eşitleyici 30 dakikadan fazla çevrimdışı olursa, bunun yerine başka bir aday seçilir. Belirli bir etki alanı için etki alanı Eşitleyici yoksa gibi izlenen trafikte algılanan yeni varlıkları Azure ATP alır ancak Azure ATP proaktif olarak varlıkları ve değişikliklerini eşitler. 
    
    Kullanılabilir etki alanı Eşitleyici yoksa ve onunla ilgili trafik olmayan olmayan bir varlık araması, arama sonucu görüntülenir.

    Varsayılan olarak, Azure ATP algılayıcı Eşitleyici adayı değildir. Azure ATP algılayıcısını bir etki alanı Eşitleyici adayı olarak el ile ayarlamak için adımları izleyin. [Azure ATP yükleme iş akışı](install-atp-step5.md#step-5-configure-the-azure-atp-sensor-settings).
- Kaynak sınırlamaları

    Azure ATP algılayıcısını üzerinde çalıştığı etki alanı denetleyicisindeki kullanılabilir işlem ve bellek kapasitesini değerlendiren bir izleme bileşeni içerir. İzleme işlemi 10 saniyede bir çalışan ve Azure ATP algılayıcısı işlemin CPU ve bellek kullanım kotasını dinamik olarak güncelleştirir. İzleme işlemi, etki alanı denetleyicisinde her zaman en az %15 ücretsiz işlem ve bellek kaynakları kullanılabilir olduğundan emin olur.

    Etki alanı denetleyicisinde neler ne olursa olsun, izleme işleminin sürekli olarak bir etki alanı denetleyicisinin çekirdek işlevlerinin hiçbir zaman etkilenen emin olmak için kaynakları serbest bırakır.

    İzleme işlemi Azure ATP algılayıcısını kalmasına neden olursa, trafiğin yalnızca bir kısmı izlenir ve izleme Uyarısı "bağlantı noktası yansıtılan ağ trafiği bırakıldı" Azure ATP portalı sağlık durumu sayfasında görünür.

-  Windows olayları

    Azure ATP Pass--Hash olan algılama kapsamını artırmak için şüpheli kimlik doğrulama hataları, gizli Grup değişiklikleri şüpheli Hizmetleri ve Honeytoken etkinliği türleri saldırı, aşağıdakilerin günlükleri analiz etmek için Azure ATP gereksinimleri oluşturma Windows olayları: 4776,4732,4733,4728,4729,4756,4757 ve 7045. Bu olaylar ile doğru Azure ATP algılayıcı tarafından otomatik olarak okunur [Gelişmiş Denetim İlkesi ayarlarının](atp-advanced-audit-policy.md). 

## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP boyutlandırma aracı](http://aka.ms/trisizingtool)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay iletme'yi yapılandırma](configure-event-forwarding.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
