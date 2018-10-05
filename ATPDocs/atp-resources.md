---
title: Faydalı kaynaklara bir listesi için Azure Gelişmiş tehdit koruması | Microsoft Docs
description: Bu makalede Azure ATP için yararlı kaynakların bir listesini sağlar.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 34dc152c-6b7f-4128-93fe-aad56c282730
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 029077455f9b2800984065a10c3e221e62d7c606
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48783160"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="azure-atp-readiness-guide"></a>Azure ATP hazırlık Kılavuzu

Bu makale, Azure Gelişmiş tehdit koruması ile çalışmaya başlama yardımcı kaynakların bir listesini sağlayan bir hazırlık yol haritası sağlar. 

## <a name="understanding-azure-atp"></a>Azure ATP anlama

Azure Gelişmiş tehdit Koruması (ATP), tanımlamak ve kuruluşunuz birden fazla Gelişmiş hedef siber saldırı ve içeriden gelen tehditleri türlerinden korunmasına yardımcı olan bir bulut hizmetidir. Azure ATP hakkında daha fazla bilgi için: 
- [Azure ATP genel bakış](what-is-atp.md)
- [Azure ATP tanıtım videosunu (25 dakika) - tam](https://www.youtube.com/watch?v=EGY2m8yU_KE)
- [Azure ATP yakından bakış videosu (75 dakika) - tam](https://www.youtube.com/watch?v=QXZIfH0wP3Q)

## <a name="deployment-decisions"></a>Dağıtım kararları

Azure ATP Azure ve bir etki alanı denetleyicisine yüklenebilir tümleşik algılayıcı veya tek başına algılayıcı adanmış sunuculara bulunan bir bulut hizmeti içerir. Azure ATP çalışır duruma geçmeden önce en iyi dağıtım ve ihtiyaçlarınıza uyacak sensörlerden türünü seçmek önemlidir. Azure ATP tümleşik sensörlerden (Azure ATP algılayıcı) Artırılmış güvenlik, operasyonel maliyetleri ve Azure ATP tek başına algılayıcı daha kolay dağıtım sağlar. Azure ATP tek başına algılayıcı, fiziksel donanım, additionl yapılandırma adımları ve yoğun işlem maliyetlerini gerektirir. <br>Fiziksel sunucuları kullanıyorsanız, kapasite planlaması çok önemlidir. Boyutlandırma aracı, algılayıcılar için alan ayırmak için Yardım alabilirsiniz: 
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool) -Azure ATP izler trafik miktarını koleksiyonunu boyutlandırma aracı otomatikleştirir. Otomatik olarak desteklenebilirliği ve algılayıcılar için kaynak öneriler sağlar. 
- [ATP kapasite planlama Kılavuzu](atp-capacity-planning.md)

## <a name="deploy-azure-atp"></a>Azure ATP dağıtma

Bu kaynakları Azure ATP ' ayarlayın, Active Directory'ye bağlanın, algılayıcı paketini indirme, olay toplamayı ayarlama ve isteğe bağlı olarak, VPN ile tümleştirin ve Dışlamalar ve honeytoken hesapları ayarlama yardımcı olur. 
- [Azure ATP (EMS E5 parçası) deneyin](http://aka.ms/aatptrial) deneme süresi 90 gün boyunca geçerli olur.
- [Azure ATP ayarlama](install-atp-step1.md) dağıtma Azure ATP ortamınızdaki şu adımları izleyin.
- [Azure ATP Windows Defender ATP ile tümleştirme](integrate-wd-atp.md)

## <a name="azure-atp-settings"></a>Azure ATP ayarları

ATA'daki gereken temel ayarları, çalışma alanınızı oluştururken yapılandırılır. Ancak, ATA'daki yapma algılamalar daha doğru VPN tümleştirmesi, SAM gibi ortamınız için gereken izinler ve Gelişmiş Denetim İlkesi ayarları yapılandırabileceğiniz birkaç ek ayar vardır. 

- [VPN tümleştirmesi](install-atp-step6-vpn.md)
- [SAM-R gerektiren izinleri](install-atp-step8-samr.md)
- [Denetim İlkesi ayarlarını](atp-advanced-audit-policy.md) – önce ve sonra bir ATP dağıtımı, etki alanı denetleyicisi sistem durumu Denetim. 

## <a name="work-with-azure-atp"></a>Azure ATP ile çalışma

Azure ATP sonra çalışır durumda ve Azure ATP portalı etkinlik zaman çizelgesinde çalışıyorsa, güvenlik uyarıları görüntüleyebilirsiniz. Etkinlik zaman çizelgesi varsayılan giriş Azure ATP portalında oturum açtıktan sonra sayfasıdır. Varsayılan olarak, tüm açık güvenlik uyarıları, saldırı zaman çizelgesinde gösterilir. Her uyarı için atanmış olan önem düzeyini de görebilirsiniz. Her uyarı, varlıklar (bilgisayarlar, cihazlar, kullanıcılar) kendi profil sayfaları hakkında daha fazla bilgi açmak için araştırıp bulma tarafından araştırın. Bu kaynakları Azure ATP'nin güvenlik uyarıları ile çalışmanıza yardımcı olur: 

- [Azure ATP güvenlik uyarı Kılavuzu](suspicious-activity-guide.md) önceliklendirmenize ve sonraki adımlar, Azure ATP algılamalar ile bilgi edinin.
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
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)