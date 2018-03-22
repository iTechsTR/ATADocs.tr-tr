---
title: "Gelişmiş tehdit analizi kaynaklarını ve hazırlık roadamp | Microsoft Docs"
description: "ATA kaynakları, videoları, Başlarken, dağıtım ve hazırlık yol haritası bağlantılar listesini sağlar."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 42a1a34f-ed6b-4538-befb-452168a30e8c
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: a56a24a2012239ed05f0a2f214dba345a817df39
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*

# <a name="ata-readiness-roadmap"></a>ATA hazırlık yol haritası 
Bu belge, Advanced Threat Analytics ile çalışmaya başlamak için yardımcı olacak bir hazırlık yol haritası sağlar.

## <a name="understanding-ata"></a>ATA anlama

Advanced Threat Analytics (ATA), kuruluşunuzu çeşitli türlerdeki, gelişmiş ve hedefe yönelik siber saldırıların yanı sıra dahili tehditlerden de korumaya yardımcı olan şirket içi bir platformdur. ATA hakkında daha fazla bilgi için aşağıdaki kaynakları kullanın:

- [ATA genel bakış](https://aka.ms/ATAOverview)

- [ATA giriş video - kısa](https://aka.ms/ATAShort)

- [ATA tanıtım videosunu - tam](https://aka.ms/ATAVideo) 


## <a name="deployment-decisions"></a>Dağıtım kararları

ATA bir sunucuya yükleyebilirsiniz, ATA Center ve ATA Lightweight Gateway doğrudan etki alanı denetleyicilerinizde kullanarak veya ayrı bilgisayarlara yükleyebilirsiniz, ağ geçitleri oluşur. Hazır ve çalışır ulaşmadan önce aşağıdaki dağıtım kararları önemlidir:

|YAPILANDIRMA|KARAR|
|----|----|
|Donanım türü|Fiziksel, sanal Azure VM|
|Çalışma grubu veya etki alanı|Çalışma grubu, etki alanı|
|Ağ geçidi boyutlandırma|Tam ağ geçidi, basit ağ geçidi|
|Sertifikalar|PKI, otomatik olarak imzalanan|

Fiziksel sunucuları kullanıyorsanız, kapasite planlamanız gerekir. ATA'ın alan ayırmak için boyutlandırma aracından Yardım alabilirsiniz:

[ATA boyutlandırma aracı](http://aka.ms/atasizing) -ATA gereken trafik miktarı koleksiyonunu boyutlandırma aracı otomatikleştirir. Otomatik olarak desteklenebilirlik ve kaynak öneriler ATA Center ve ATA Lightweight Gateway için sağlar.

[ATA kapasite planlaması](https://docs.microsoft.com/en-us/advanced-threat-analytics/ata-capacity-planning)

## <a name="deploy-ata"></a>Ata'yı dağıtma

Bu kaynaklar, indirin ve ATA Center Active Directory'ye bağlamanın, ATA Gateway paketini karşıdan yükleyin, olay toplamayı ayarlama ve isteğe bağlı olarak VPN ile tümleştirmek ve honeytoken hesapları ve özel durumları ayarlamanız yardımcı olur.

[ATA'yı indirin](http://aka.ms/ataeval) -ATA, satın kararı yapmadıysanız, Ata'yı dağıtmadan önce değerlendirme sürümünü indirebilirsiniz. 

[ATA POC playbook](http://aka.ms/atapoc) -ATA başarılı POC dağıtımını yapmak gereken tüm adımları Kılavuzu.

[ATA dağıtım video](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes) -ATA dağıtımına genel bakış adımları 10 dakikadan daha kısa bir süre içinde bu video sağlar.

## <a name="ata-settings"></a>ATA ayarları

ATA temel gerekli ayarlarında Yükleme Sihirbazı'nın bir parçası olarak yapılandırılır. Ancak, çeşitli algılamaların SIEM tümleştirme gibi ortamınız için daha kesin ve denetim ayarları ATA ince ayar yapmak için yapılandırabileceğiniz diğer ayarlar vardır.

[Denetim ayarları](https://aka.ms/ataauditingblog) – önce ve sonra bir ATA dağıtımı, etki alanı denetleyicisi durumunu denetleme.

[ATA genel belgeler](https://docs.microsoft.com/en-us/advanced-threat-analytics/)

## <a name="work-with-ata"></a>ATA ile çalışma

ATA kurulup çalışmaya başladıktan sonra saldırı zaman çizelgesinde algılanan kuşkulu etkinlikleri görüntüleyebilirsiniz. Bu, ATA Konsolu’nda oturum açtığınızda gittiğiniz varsayılan giriş sayfasıdır. Varsayılan olarak, tüm kuşkulu etkinliler saldırı zaman çizelgesinde gösterilir. Ayrıca, her etkinliğe atanmış olan önem düzeyini de görebilirsiniz. Daha fazla bilgi sağlayan varlıklarının içinde (bilgisayarlar, cihazlar, kullanıcılar) kendi profil sayfalarını açmak için detaya tarafından her kuşkulu etkinlik araştırın. Bu kaynaklar, ATA'ın kuşkulu etkinliklerle çalışmanıza yardımcı olur:

[ATA kuşkulu etkinlik playbook](http://aka.ms/ataplaybook) -bu makalede, Internet'te kullanıma hazır araştırma araçlarını kullanarak kimlik bilgisi hırsızlığı saldırısına tekniklerinin açıklanmaktadır. Her saldırı noktada ATA, bu tehditleri görünürlük elde etmek nasıl yardımcı olduğunu görebilirsiniz.

[ATA kuşkulu etkinlik Kılavuzu](http://aka.ms/atasaguide)



## <a name="security-best-practices"></a>En iyi güvenlik uygulamaları

[ATA en iyi yöntemler](https://aka.ms/atasecbestpractices) -en iyi uygulamalar ATA güvenliğini sağlamak için.

[ATA sık sorulan sorular](http://aka.ms/atafaq) -bu makalede, ATA hakkında sık sorulan sorular listesini sağlar ve ve öngörülerle yanıtlar sağlanır.

## <a name="additional-resources"></a>Ek kaynaklar

[Microsoft Güvenlik Channel 9 sayfası](https://channel9.msdn.com/Shows/Microsoft-Security/)

## <a name="community-resources"></a>Topluluk kaynakları

[ATA blogu](https://aka.ms/ATABlog)
[ATA topluluk](https://aka.ms/ATACommunity)
[ATA hakkında geri bildirim sağlayın](https://aka.ms/ATAUserVoice)
