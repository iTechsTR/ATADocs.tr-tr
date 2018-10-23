---
title: Gelişmiş Threat Analytics kaynakları ve hazırlık yol haritası | Microsoft Docs
description: ATA kaynakları, videoları, kullanmaya başlama, dağıtım ve hazırlık yol haritası bağlantıların bir listesini sağlar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/15/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 42a1a34f-ed6b-4538-befb-452168a30e8c
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 069ee0f367c52de897486291f761bf0dde6016e0
ms.sourcegitcommit: 8ecb76ddfbf48c361d3637d15bd48313a3e68685
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2018
ms.locfileid: "49634758"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*

# <a name="ata-readiness-roadmap"></a>ATA hazırlık yol haritası 
Bu makalede, Advanced Threat Analytics ile çalışmaya başlamanıza yardımcı olacak bir hazırlık yol haritası sağlar.

## <a name="understanding-ata"></a>Ata'yı anlama

Advanced Threat Analytics (ATA), kuruluşunuzu çeşitli türlerdeki, gelişmiş ve hedefe yönelik siber saldırıların yanı sıra dahili tehditlerden de korumaya yardımcı olan şirket içi bir platformdur. ATA hakkında daha fazla bilgi için aşağıdaki kaynakları kullanın:

- [ATA genel bakış](what-is-ata.md)

- [ATA giriş video - kısa](https://aka.ms/ATAShort)

- [ATA tanıtım videosunu - tam](https://aka.ms/ATAVideo) 


## <a name="deployment-decisions"></a>Dağıtım kararları

ATA bir sunucuya yükleyebilirsiniz, ATA Center ve ATA Gateway bileşenleri ayrı bilgisayarlara veya Lightweight Gateway doğrudan etki alanı denetleyicilerinize kullanarak yükleyebileceğiniz oluşur. Çalışır duruma geçmeden önce aşağıdaki dağıtım kararları önemlidir:

|Yapılandırma | Karar verme |
|----|----|
|Donanım türü|Fiziksel, sanal Azure VM|
|Çalışma grubu veya etki alanı|Çalışma grubu, etki alanı|
|Ağ geçidi boyutlandırma|Tam ağ geçidi, basit ağ geçidi|
|Sertifikalar|PKI, otomatik imzalı|

Fiziksel sunucuları kullanıyorsanız, kapasite planlamanız gerekir. ATA için alan ayırmak için boyutlandırma aracından Yardım alabilirsiniz:

[ATA boyutlandırma aracı](ata-capacity-planning.md) -boyutlandırma aracı gereken ATA trafik miktarını koleksiyonunu otomatikleştirir. Bu otomatik olarak desteklenebilirliği ve kaynak öneriler ATA Center ve ATA Lightweight Gateway için sağlar.


[ATA kapasite planlaması](ata-capacity-planning.md)


## <a name="deploy-ata"></a>Ata'yı dağıtma

Bu kaynaklar, indirin ve ATA Center'ı yüklemek, Active Directory'ye bağlanın, ATA Gateway paketini indirme, olay toplamayı ayarlama ve isteğe bağlı olarak VPN'iniz ile tümleştirin ve Dışlamalar ve honeytoken hesapları ayarlama yardımcı olur.

[Ata'yı indirin](http://aka.ms/ataeval) -kararı, ATA satın oluşturmadıysanız, Ata'yı dağıtmadan önce değerlendirme sürümünü indirebilirsiniz. 

[ATA POC el kitabı](http://aka.ms/atapoc) -ATA'ın başarılı bir POC dağıtımı yapmak için gereken tüm adımları Kılavuzu.

[ATA dağıtım video](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes) -bu video, ATA dağıtımı genel bakış, 10 dakikadan kısa bir süre içinde adımları sağlar.

## <a name="ata-settings"></a>ATA ayarları

Ata'da temel gerekli ayarları, yükleme sihirbazının bir parçası olarak yapılandırılır. Ancak, ATA algılamaları SIEM tümleştirmesi gibi ortamınız için daha doğru yapan ince ayar yapmak ve denetim ayarları yapılandırabileceğiniz diğer ayar vardır.

[Denetim ayarları](https://aka.ms/ataauditingblog) – önce ve sonra bir ATA dağıtımı, etki alanı denetleyicisi sistem durumu Denetim.

[ATA genel belgeler](https://docs.microsoft.com/advanced-threat-analytics/)

## <a name="work-with-ata"></a>ATA ile çalışma

ATA çalışır duruma geldikten sonra saldırı zaman çizelgesinde algılanan kuşkulu etkinlikleri görüntüleyebilirsiniz. Bu, ATA Konsolu’nda oturum açtığınızda gittiğiniz varsayılan giriş sayfasıdır. Varsayılan olarak, tüm kuşkulu etkinliler saldırı zaman çizelgesinde gösterilir. Ayrıca, her etkinliğe atanmış olan önem düzeyini de görebilirsiniz. Daha fazla bilgi sağlayan varlıklarının içinde (bilgisayarlar, cihazlar, kullanıcılar) kendi profili sayfalarını açmak için aşağı indikçe her kuşkulu etkinlik araştırın. Bu kaynaklar, ATA'ın kuşkulu etkinlikler ile çalışmanıza yardımcı olur:

[ATA şüpheli etkinlik playbook](http://aka.ms/ataplaybook) -bu makalede, internet'te kullanıma açık araştırma araçlarının kullanarak kimlik bilgisi hırsızlığı saldırı tekniklerini gösterilmektedir. Saldırının her noktada ATA, bu tehditleri görmenize nasıl yardımcı olduğunu görebilirsiniz.

[ATA şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md)



## <a name="security-best-practices"></a>En iyi güvenlik uygulamaları

[ATA en iyi](https://aka.ms/atasecbestpractices) -ATA güvenliğini sağlamak için en iyi yöntemler.

[ATA sık sorulan sorular](ata-technical-faq.md) -bu makalede ATA hakkında sık sorulan soruların bir listesi ve öngörülerle yanıtlar sağlanır.

## <a name="additional-resources"></a>Ek kaynaklar

[Microsoft Güvenlik Channel 9 sayfası](https://channel9.msdn.com/Shows/Microsoft-Security/)

## <a name="community-resources"></a>Topluluk kaynakları

[ATA blogu](https://aka.ms/ATABlog)
[ATA topluluk](https://aka.ms/ATACommunity)
[ATA hakkında geri bildirim sağlayın](https://aka.ms/ATAUserVoice)
