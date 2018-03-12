---
title: Azure ATP yenilikler | Microsoft Docs
description: "Azure ATP en son sürümlerini açıklar ve her sürümdeki yenilikler hakkında bilgi sağlar."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/11/2018
ms.topic: article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 7d0f33db-2513-4146-a395-290e001f4199
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 4a81d84a46b9710c2376bbc50f699966a24138db
ms.sourcegitcommit: 912e453753156902618ae6ebb8489c2320c06fc6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*


# <a name="whats-new-in-azure-atp"></a>Azure ATP yenilikler nelerdir? 

## <a name="azure-atp-release-224"></a>Azure ATP yayın 2,24

11 Mart 2018 yayımlanan

**Yeni & güncelleştirilmiş algılama**
  - Şüpheli hizmet oluşturma – saldırganların ağınızdaki kuşkulu Hizmetleri çalıştırmayı deneyin. Birisi belirli bir bilgisayardaki şüpheli yeni bir hizmet çalıştığını belirlediğinde azure ATP artık bir uyarı başlatır. Bu algılama (ağ trafiği değil) olaylara dayanarak ve olay 7045 Azure ATP iletme, ağınızdaki herhangi bir etki alanı denetleyicisinde algıladı. Daha fazla bilgi için bkz: [şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md).

**Geliştirilmiş araştırma**
  - Azure ATP içeren bir zenginleştirilmiş [varlık profili](entity-profiles.md). Varlık profili bu erişmeleri kaynakları içeren kullanıcı etkinlikleri derin Dalış araştırma için tasarlanmış bir platform, oturum açmış bilgisayarları ve çok daha fazlasını sağlar. Varlık profili Ayrıca, dizin verilerini sağlar ve olası yanal hareket yollarını ya da kuruluşunuzdaki olası ihlallerini hakkında daha fazla bilgi için etkinleştirme varlıktan belirlemenize olanak sağlar.

  - ATP sağlar el ile etiketi varlıklara *hassas* algılama ve izleme geliştirmek için. Bu etiketleme hassas grubu değiştirme algılama gibi birçok Azure ATP algılamaların etkiler ve [yanal hareket yolu](use-case-lateral-movement-path.md), gizli olarak kabul edilen varlıklarını kullanır.

**Araştırmanıza yardımcı olması için yeni raporlar**
  - [Parolaları düz metin raporda gösterilen](reports.md) hizmetleri hesabı kimlik bilgileri, düz metin olarak gönderilir gönderdiğinizde algılamasını sağlar. Bu, hizmetleri inceleyin ve ağ güvenlik düzeyini artırmak sağlar. Bu rapor doğrulamaya şüpheli etkinlik uyarıları değiştirir.
  - [Yanal hareket hassas hesapları rapor yollara](reports.md) yanal hareket yolları sunulan hassas hesaplarını listeler. Bu, bu yollar azaltmak ve saldırı yüzeyini riski en aza indirmek için ağınızı sağlamlaştırmak olanak sağlar. Bu, böylece sanal güvenlik ikramiye isabet kadar saldırganların ağınızda kullanıcıları ve bilgisayarları arasında taşınamıyor yanal hareket engellemenizi sağlar: hassas yönetici hesabı kimlik bilgilerinizi.

- Kolay erişim bağlantı belgelerinden sağlamak artık şüpheli etkinlik uyarısı içinde görüntülemek için şunları yapabilirsiniz [yapabileceğiniz araştırma adımları](suspicious-activity-guide.md). 

**Performans iyileştirmeleri**
 -  Azure ATP algılayıcı altyapı için performansı geliştirildi: trafiği toplanmış görünümünü iyileştirme CPU ve paket ardışık sağlar ve SSL oturumları DC'ye en aza indirmek için etki alanı denetleyicilerine yuva yeniden kullanır.

## <a name="see-also"></a>Ayrıca bkz:
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)