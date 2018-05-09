---
title: Azure ATP yenilikler | Microsoft Docs
description: Azure ATP en son sürümlerini açıklar ve her sürümdeki yenilikler hakkında bilgi sağlar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/8/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 7d0f33db-2513-4146-a395-290e001f4199
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 6d794e2d30b51d78bd3e4af76d8bd4a48b2d413f
ms.sourcegitcommit: 8472f3f46fc90da7471cd1065cdb2f6a1d5a9f69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*


# <a name="whats-new-in-azure-atp"></a>Azure ATP yenilikler nelerdir? 



## <a name="azure-atp-release-231"></a>Azure ATP sürüm 2.31

6 Mayıs 2018 yayımlanan
 
- Ad çözümlemesi için geliştirmeler yapılmıştır. RPC ve NetBIOS etkin çözümleme yanı sıra bu çalışmaların bir parçası olarak algılayıcı RDP uç noktası için bir TLS istemci Hello paket sorun (3389 numaralı) bağlantı noktası. 
- Bu sürüm, düzeltmeler ve birden çok sorunları için geliştirmeler içerir. 

## <a name="azure-atp-release-230"></a>Azure ATP sürüm 2.30

29 Nisan 2018 yayımlanan
 
- Şifreleme indirgeme kuşkulu etkinlikleri artık bir şifreleme indirgeme etkinlik ilkelerinden şüpheleniyorsanız neden Azure ATP tarafından algılanan Belirtiler tanımlayan bir kanıt bölümü içerir. 
-   Azure ATP Azure e-posta Orchestrator artık Azure ATP uyarılar ve raporlar izleme kuşkulu etkinlikler dahil olmak üzere gönderilen tüm e-postalar için kullanır. Bu e-posta bildirimleri artık kullanım kolaylığı için tutarlı bir biçim izleyin ve Excel dosyalarını konsoldan yüklenmek üzere e-posta gelen bağlanacağı görürsünüz.
 
 

## <a name="azure-atp-release-229"></a>Azure ATP sürüm 2.29

22 Nisan 2018 yayımlanan
 
- Bu sürüm, düzeltmeler ve birden çok sorunları için geliştirmeler içerir. 
 
 
## <a name="azure-atp-release-228"></a>Azure ATP sürüm 2.28

15 Nisan 2018 yayımlanan
 
-   Artık Azure ATP kullanıcıları ve Azure ATP görüntüleyiciler rol gruplarının üyeleri olan kullanıcılar izleme uyarıları görmek için izinlere sahip.
- Bu sürüm, düzeltmeler ve birden çok sorunları için geliştirmeler içerir. 


## <a name="azure-atp-release-227"></a>Azure ATP sürüm 2.27

8 Nisan 2018 yayımlanan

- Üst gezinti çubuğunda kullanıcı geri bildirim sağlama yeteneği artık sahipsiniz. Menü çubuğunda gülen yüz tıklatarak Geri bildiriminizi Azure Advanced Threat Protection ekibiyle bir e-posta göndermek etkinleştirir.

- Bu sürüm, düzeltmeler ve birden çok sorunları için geliştirmeler içerir. 
 

## <a name="azure-atp-release-226"></a>Azure ATP sürüm 2.26

25 Mart 2018 yayımlanan

- (Kuşkulu bir etkinlik değil yasal bir eylem), zararsız pozitif tanımlamak ve kuşkulu bir etkinlik Azure ATP uyarıları, bilgisayarların ve IP adresleri de dahil olmak üzere daha fazla algılamaları dışlamak için seçeneğiniz vardır: şifreleme indirgeme, LDAP deneme yanılma saldırısı, sahte PAC, kaba kuvvet ve Pass--hash.
-   Azure ATP algılayıcı performansı geliştirildi.
-   Yeni bir bölge eklenen çalışma dağıtımı için bir çalışma alanı Asya'da artık dağıtabilirsiniz. 


## <a name="azure-atp-release-225"></a>Azure ATP yayın 2,25

18 Mart 2018 yayımlanan

- Çok faktörlü kimlik doğrulaması (MFA) Azure ATP artık desteklenmektedir. MFA kullanarak kiracılar artık Azure ATP portal girebilirsiniz.
- Azure ATP şimdi sahip bir [ **sistem durumu** ](https://health.atp.azure.com/) çalışma Yönetim Portalı'nı algılamaların sorun varsa ve algılayıcı gönderebilmesi için ise yukarı ve etkin olup bilgileri sağlamak için sayfası Bulut trafiği. Erişebileceğiniz **sistem durumu** Azure ATP menü çubuğundan.


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