---
title: Faydalı kaynaklara bir listesi için Azure Gelişmiş tehdit koruması | Microsoft Docs
description: Bu makalede Azure ATP için yararlı kaynakların bir listesini sağlar.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/15/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 34dc152c-6b7f-4128-93fe-aad56c282730
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 56b74b2e02fcab2b7584afbabd5d4384f066261c
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44166440"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="azure-atp-readiness-guide"></a>Azure ATP hazırlık Kılavuzu

Bu makale, Azure Gelişmiş tehdit koruması ile çalışmaya başlama yardımcı kaynakların bir listesini sağlayan bir hazırlık yol haritası sağlar. 

## <a name="understanding-azure-atp"></a>Azure ATP anlama

Azure Gelişmiş tehdit Koruması (ATP), tanımlamak ve kuruluşunuz birden fazla Gelişmiş hedef siber saldırı ve içeriden gelen tehditleri türlerinden korunmasına yardımcı olan bir bulut hizmetidir. Azure ATP hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları kullanın: 
- [Azure ATP genel bakış](what-is-atp.md)
- [Azure ATP tanıtım videosunu - tam](https://www.youtube.com/watch?v=KX-xpFc0sBw) 

## <a name="deployment-decisions"></a>Dağıtım kararları

Azure ATP Azure ve bir etki alanı denetleyicisine yüklenebilir tümleşik algılayıcı veya tek başına algılayıcı adanmış sunuculara bulunan bir bulut hizmeti içerir. Azure ATP çalışır duruma geçmeden önce en iyi dağıtım ve ihtiyaçlarınıza uyacak sensörlerden türünü seçmek önemlidir. Azure ATP tümleşik algılayıcılar, Gelişmiş güvenlik, operasyonel maliyetleri ve daha kolay dağıtım sağlar. Azure ATP tek başına algılayıcı, fiziksel donanım, additionl yapılandırma adımları ve yoğun işlem maliyetlerini gerektirir. <br>Fiziksel sunucuları kullanıyorsanız, kapasite planlaması çok önemlidir. Boyutlandırma aracı, algılayıcılar için alan ayırmak için Yardım alabilirsiniz: 
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool) -Azure ATP izler trafik miktarını koleksiyonunu boyutlandırma aracı otomatikleştirir. Otomatik olarak desteklenebilirliği ve algılayıcılar için kaynak öneriler sağlar. 
- [ATA kapasite planlama Kılavuzu](atp-capacity-planning.md)

## <a name="deploy-azure-atp"></a>Azure ATP dağıtma

Bu kaynakları Azure ATP ' ayarlayın, Active Directory'ye bağlanın, algılayıcı paketini indirme, olay toplamayı ayarlama ve isteğe bağlı olarak, VPN ile tümleştirin ve Dışlamalar ve honeytoken hesapları ayarlama yardımcı olur. 
- [Azure ATP (EMS E5 parçası) deneyin](http://aka.ms/aatptrial) deneme süresi 90 gün boyunca geçerli olur.
- [Dağıtım Kılavuzu](install-atp-step1.md) dağıtma Azure ATP ortamınızdaki şu adımları izleyin.
- [Azure ATP Windows Defender ATP ile tümleştirme](integrate-wd-atp.md)

## <a name="azure-atp-settings"></a>Azure ATP ayarları

Çalışma alanını oluşturan ATA'daki gereken temel ayarları yapılandırılır. Ancak, SIEM tümleştirmesi gibi ortamınız için daha doğru algılama yapmak ve denetim ayarlarını Azure ATP ince ayar yapmak için yapılandırabileceğiniz birçok ek ayarlar vardır. 

- [Azure ATP genel belgeler](what-is-atp.md)
- [Denetim ayarları](https://blogs.technet.microsoft.com/positivesecurity/2017/08/18/ata-auditing-auditpol-advanced-audit-settings-enforcement-lightweight-gateway-service-discovery/) – önce ve sonra bir ATP dağıtımı, etki alanı denetleyicisi sistem durumu Denetim. 

## <a name="work-with-azure-atp"></a>Azure ATP ile çalışma

Azure ATP sonra çalışır durumda ve çalışan, Azure ATP portalı etkinlik zaman çizelgesinde algılanan kuşkulu etkinlikleri görüntüleyin. Etkinlik zaman çizelgesi varsayılan giriş Azure ATP portalında oturum açtıktan sonra sayfasıdır. Varsayılan olarak, tüm kuşkulu etkinliler saldırı zaman çizelgesinde gösterilir. Ayrıca, her etkinliğe atanmış olan önem düzeyini de görebilirsiniz. Her kuşkulu etkinlik, varlıklar (bilgisayarlar, cihazlar, kullanıcılar) kendi profil sayfaları hakkında daha fazla bilgi açmak için araştırıp bulma tarafından araştırın. Bu kaynakları Azure ATP'nin kuşkulu etkinliklerle çalışma yardımcı olur: 

- [Azure ATP şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md) önceliklendirmenize ve sonraki adımlar, Azure ATP algılamalar ile bilgi edinin.
- [Grupları hassas olarak etiket](sensitive-accounts.md) kimlik bilgisi ifşa hassas güvenlik grupları üzerinde görünürlük elde edin.

## <a name="security-best-practices"></a>En iyi güvenlik uygulamaları

- [Azure ATP ile ilgili sık sorulan sorular](atp-technical-faq.md) -bu makalede Azure ATP hakkında sık sorulan soruların bir listesi ve öngörülerle yanıtlar sağlanır. 

## <a name="community-resources"></a>Topluluk kaynakları

Blog: [Azure ATP blogu](https://aka.ms/aatpblog)

Genel topluluk: [Azure ATP Teknoloji Topluluğu](https://aka.ms/AatpCom)

Özel topluluk: [Azure ATP Yammer grubu](https://www.yammer.com/azureadvisors/#/threads/inGroup?type=in_group&feedId=9386893&view=all)

Kanal 9: [Microsoft Güvenlik Channel 9 sayfası](https://channel9.msdn.com/Shows/Microsoft-Security/)



## <a name="see-also"></a>Ayrıca Bkz.

- [Hassas hesaplar ile çalışma](sensitive-accounts.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)