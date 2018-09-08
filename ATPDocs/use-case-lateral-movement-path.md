---
title: Azure ATP ile yanal hareket yolu saldırılarını araştırma | Microsoft Docs
description: Bu makalede, yanal hareket yolu olan Azure Gelişmiş tehdit Koruması (ATP) saldırıları açıklar.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/05/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: de15c920-8904-4124-8bdc-03abd9f667cf
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 0fcdfdbeaeed7e42aff9d63f4f88300346c73465
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44165584"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*

# <a name="investigating-lateral-movement-paths-with-azure-atp"></a>Azure ATP ile yanal hareket yollarını araştırma


Yanal hareket, bir saldırganın hassas hesaplara yönelik erişim elde etmek için hassas olmayan hesaplarını kullandığı durumdur. Bu yapılabilir açıklanan yöntemlerle [şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md). Yanal hareket, saldırganlar tarafından hassas hesapları ve ağınızda depolanan oturum açma kimlik bilgilerini hesapları, grupları ve makineler paylaştığınız hassas olmayan hesapları kullanarak makineleri erişmek üzere kullanılır. Erişim elde etmiş bir saldırganın sonra saldırgan ayrıca veri etki alanı denetleyicilerinize yararlanabilirsiniz.


## <a name="discover-your-at-risk-sensitive-accounts"></a>Dalgalanmasını hassas hesaplarınızı keşfedin

Hassas olmayan hesapları, grupları ve makineler, bağlantı nedeniyle ağınızdaki hassas hangi hesapların ortaya bulmak için aşağıdaki adımları izleyin. 

1. Azure ATP çalışma alanı portal menüde rapor simgesine tıklayın ![Raporlar simgesi](./media/atp-report-icon.png).

2. Altında **yana hareket yolları hassas hesaplara yönelik**, hiçbir olası yanal hareket yollarını bulundu, raporun gri varsa. Olası yanal hareket yollarını varsa, raporu otomatik olarak ilk önceden seçer tarih ilgili verileri olduğunda. Yanal hareket yolu raporun 60 güne kadar verileri sağlar.

 ![raporlar](./media/reports.png)

3. Tıklayın **indirme**.

4. Seçilen tarih için olası yanal hareket yollarını ve hassas hesap Etkilenme hakkında ayrıntılar sağlar bir Excel dosyası oluşturulur. **Özeti** sekmesi, hassas hesapları, bilgisayar ve ortalamalar dalgalanmasını erişim sayısı ayrıntı grafikler sağlar. **Ayrıntıları** sekmesi daha ayrıntılı olarak araştırmanız gereken hassas hesapların listesini sağlar. Son 60 gün içindeki algılandığından indirilebilir rapora ayrıntılı yolları artık kullanılabilir olabileceğine dikkat edin ve Mayıs değişmiş veya değiştirilmiş.


## <a name="investigate"></a>Araştırma



1. Varlık bir yanal hareket yolu olduğunda varlık profiline eklenir yanal hareket rozet Azure ATP çalışma alanı Portalı'nda arayın ![yanal simgesi](./media/lateral-movement-icon.png) veya ![Yol simgesi](./media/paths-icon.png). Son 48 saat içinde yanal hareket, Göstergeler yalnızca görüneceğini unutmayın. 

2. Açılan kullanıcı profili sayfasında tıklatın **yana hareket yollarını** sekmesi. 

3. Görüntülenen grafiği, hassas kullanıcı için olası yol haritası sağlar. Son 48 saat içindeki gözlemlenen olası bağlantıları grafik gösterir. Son iki gün içinde hiçbir etkinlik algılandı, grafik görünmez. 

4. Hassas kullanıcı kimlik bilgilerinin paylaşılmasını hakkında bilgi edinebilirsiniz görmek için grafikteki gözden geçirin. Örneğin, bu haritada izleyebilirsiniz **oturum açan** gri ok burada Samira kendi ayrıcalıklı kimlik bilgileriyle oturum görmek için. Bu durumda, hassas Samira'nın kimlik REDMOND Washington geliştirme bilgisayarda kaydedildi. Şimdi, oturum açmış hangi kullanıcıların dikkat edin ve güvenlik açığı en oranını oluşturulan hangi bilgisayarları. Bu bakarak görebilirsiniz **yönetici** siyah okları kimin kaynak üzerinde yönetici ayrıcalıklarına sahip görmek için. Bu örnekte, Contoso tüm gruptaki herkes bu kaynak kullanıcı kimlik bilgileriyle erişmeye özelliğine sahiptir.  

 ![Kullanıcı profili yatay hareket yolları](media/user-profile-lateral-movement-paths.png)


## <a name="preventative-best-practices"></a>Önleyici en iyi uygulamalar

- Yanal hareket önlemek için en iyi yolu, sağlamlaştırılmış bilgisayarlarda açarken hassas kullanıcılar'ın yönetici kimlik bilgilerini kullandığınızdan emin olmaktır. Örnekte, Samira yönetici REDMOND Washington geliştirme erişmesi gerekirse, bir kullanıcı adı ve parola dışında yönetici kimlik bilgilerinizle oturum emin olun.

- Hiç kimse gereksiz yönetici izinlerine sahip olduğundan emin olun önerilir. Herkes Contoso tüm gerçekten REDMOND Washington geliştirme yönetici haklarını gerektiriyorsa, bu örnekte denetlemeniz gerekir

- Kişilerin yalnızca gerekli kaynaklara erişebildiğinden emin olun. Bu örnekte Oscar Posada önemli ölçüde Samira'nın Etkilenme widens. Bu kullanıcı grubuna dahil edilmesini gereklidir **Contoso tüm**? Etkilenme en aza indirmek için oluşturulması alt gruplar var mı?

**İpucu** – son 48 saat hiçbir etkinlik algılandı ve graf kullanılamıyor yanal hareket yolu raporun hala kullanılabilir ve algıladı son 60 gün içindeki olası yanal hareket yolları hakkında bilgi sağlar. 

**İpucu** - yanal hareket yolu algılama için gereken SAM-R işlemleri gerçekleştirmek için istemcilerinize ayarlamak yönergeler ve sunucuları Azure ATP izin verecek şekilde görmek için [SAM-r'yi Yapılandır](install-atp-step8-samr.md).


## <a name="see-also"></a>Ayrıca Bkz.

- [SAM-R gerektiren izinleri yapılandırma](install-atp-step8-samr.md)
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)