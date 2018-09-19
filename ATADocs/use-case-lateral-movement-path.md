---
title: ATA ile yanal hareket yolu saldırılarını araştırma | Microsoft Docs
description: Bu makalede, yanal hareket yolu Advanced Threat Analytics (ATA) ile saldırıları açıklar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/14/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 710f01bd-c878-4406-a7b2-ce13f98736ea
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 0d247671c43e4c62f740eca263f2e0e680c7d319
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133995"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*

# <a name="investigating-lateral-movement-paths-with-ata"></a>ATA ile yanal hareket yollarını araştırma

Bile, hassas kullanıcıları korumak için en iyi yapın ve sık sık değişiklik, kendi makinelerine sıkı ve verilerine güvenli şekilde depolanan karmaşık parolalar yöneticilerinize sahip olduğunda, saldırganlar yanal hareket yollarını hassas erişmek için kullanmaya devam edebilirsiniz hesaplar. Bir makineye hassas kullanıcılar oturum açtığında yanal hareket saldırılarında, saldırgan örnekleri hassas olmayan kullanıcı yerel haklarına sahip olduğu yararlanır. Saldırganlar ardından riskli, daha az hassas kullanıcı erişme ve bilgisayar arasında taşımak için hassas kullanıcı kimlik bilgilerini elde etmek taşıyabilirsiniz. 

## <a name="what-is-a-lateral-movement-path"></a>Yanal hareket yolunun nedir?

Yanal hareket, bir saldırganın hassas hesaplara yönelik erişim elde etmek için hassas olmayan hesaplarını kullandığı durumdur. Bu yapılabilir açıklanan yöntemlerle[şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md). Ağınızda yöneticisi olan ve makineler anlamak için saldırgan erişebilir, saldırgan veri etki alanı denetleyicilerinize yararlanabilirsiniz. 

ATA saldırganlar yanal hareket bulunulmasını önlemek için ağınızdaki preemptive harekete geçmenizi sağlar.

## <a name="discovery-your-at-risk-sensitive-accounts"></a>Bulma, dalgalanmasını hassas hesaplar

Ağınızda hangi hassas hesapları bulmak için hassas olmayan hesaplar, bağlantı nedeniyle güvenlik açığı bulunan veya belirli bir zaman çerçevesinde kaynakları şu adımları izleyin. 

1. ATA Konsolu menüde rapor simgesine tıklayın ![Raporlar simgesi](./media/ata-report-icon.png).

2. Altında **yana hareket yolları hassas hesaplara yönelik**, yatay hareket yolu bulunamadı, raporun gri varsa. Yanal hareket yollarını varsa, daha sonra otomatik olarak Seç raporun tarih ilk tarih ilgili verileri olduğunda. 

 ![raporlar](./media/reports.png)

3. Tıklayın **indirme**.

3. Oluşturulan Excel dosyası, risk altında olan hassas hesaplarınızı hakkında ayrıntılar sağlar. **Özeti** sekmesi, hassas hesapları, bilgisayar ve risk altında bulunan kaynaklar için ortalama sayısı ayrıntı grafikler sağlar. **Ayrıntıları** sekmesi endişe olmanız gereken hassas hesapların listesini sağlar. Yollarının önceden var ve hemen kullanılamayabilir yollar olduğunu unutmayın.


## <a name="investigate"></a>Araştırma

Artık hangi hassas hesapları risk altında olduğunu bildiğinize göre derin olabilir. daha fazla bilgi edinin ve önlemler almak için ATA öğrenebilirsiniz.

1. Varlık bir yanal hareket yolu olduğunda varlık profiline eklenir yanal hareket rozet ATA Konsolu'nda arayın ![yanal simgesi](./media/lateral-movement-icon.png) veya ![Yol simgesi](./media/paths-icon.png). Bu son iki gün içinde bir yanal hareket yolunun olduğunda kullanılabilir.

2. Açılan kullanıcı profili sayfasında tıklatın **yana hareket yollarını** sekmesi.

3. Görüntülenen grafiği, hassas kullanıcı için olası yol haritası sağlar. Grafik son iki gün içinde yapılan bağlantıları gösterir.

4. Hassas kullanıcı kimlik bilgilerinin paylaşılmasını hakkında bilgi edinebilirsiniz görmek için grafikteki gözden geçirin. Örneğin, bu haritada izleyebilirsiniz **oturum açan** gri ok burada Samira kendi ayrıcalıklı kimlik bilgileriyle oturum görmek için. Bu durumda, hassas Samira'nın kimlik REDMOND Washington geliştirme bilgisayarda kaydedildi Daha sonra diğer kullanıcılar oturum bakın ve güvenlik açığı en oranını oluşturulan hangi bilgisayarların. Bu bakarak görebilirsiniz **yönetici** siyah okları kimin kaynak üzerinde yönetici ayrıcalıklarına sahip görmek için. Bu örnekte, Herkes grubunun **Contoso tüm** bu kaynak kullanıcı kimlik bilgileriyle erişmeye özelliğine sahiptir.  

 ![Kullanıcı profili yatay hareket yolları](media/user-profile-lateral-movement-paths.png)


## <a name="preventative-best-practices"></a>Önleyici en iyi uygulamalar

- Yanal hareket önlemek için en iyi yolu sağlamlaştırılmış bilgisayarlarda açarken hassas kullanıcılar'ın yönetici kimlik bilgilerini kullandığınızdan emin olmak için olan aynı bilgisayarda yönetici haklarına sahip hiçbir hassas olmayan kullanıcı olduğu. Örnekte, REDMOND Washington geliştirme Samira erişmesi gerekirse Filiz adı ve parola ile oturum dışında her yönetici kimlik bilgileri kaydettiğini emin olun veya yerel Yöneticiler grubundan REDMOND Washington geliştirme Contoso tüm grubunu Kaldır

- Hiç kimse gereksiz yerel yönetici izinlerine sahip olduğundan emin olun önerilir. Örnekte, Contoso tüm herkes gerçekten REDMOND Washington geliştirme yönetici hakları gerekiyorsa görmek için denetlemelisiniz

- Kişilerin yalnızca gerekli kaynaklara erişebildiğinden emin olun. Bu örnekte Oscar Posada önemli ölçüde Samira'nın Etkilenme widens. O gruba dahil edilmesi gerekirse **Contoso tüm**? Etkilenme en aza indirmek için oluşturabileceğiniz alt gruplar var mı?

**İpucu** – etkinliği, son iki gün içinde değil algılandığında graf görünmez, ancak yanal hareket yolu raporun son 60 güne yatay hareket yolları hakkında bilgi sağlamak kullanılabilir olmaya devam edecektir.

**İpucu** - Ata'nın yanal hareket yolu algılama için gereken SAM-R işlemleri gerçekleştirmek sunucularınızı ayarlama konusunda yönergeler için [SAM-r'yi Yapılandır](install-ata-step9-samr.md).




## <a name="see-also"></a>Ayrıca Bkz.
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
