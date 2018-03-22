---
title: "Yanal hareket yolu saldırılarına ATA araştırma | Microsoft Docs"
description: "Bu makalede, yanal hareket yolu saldırılarını Advanced Threat Analytics (ATA) ile algılamak üzere açıklar."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 710f01bd-c878-4406-a7b2-ce13f98736ea
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: dc03cfe1719541dac0f8509c0f8f22987ecb96bb
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*

# <a name="investigating-lateral-movement-paths-with-ata"></a>Yanal hareket yollarını ATA ile araştırma

Hatta hassas kullanıcılarınızın korumak için en iyi yapın ve sık sık değişen, kendi makinelerine sıkı ve verilerine güvenli şekilde depolanan karmaşık parolalar, yöneticilere sahip olduğunda, saldırganlar yanal hareket yolları hassas erişmek için kullanmaya devam edebilirsiniz hesapları. Bir makineye hassas kullanıcı oturum yanal hareket saldırılarında, saldırgan örnekleri hassas olmayan kullanıcı yerel haklarına sahip olduğu yararlanır. Saldırganlar sonra yanal, kullanıcının daha az hassas verilere erişme ve hassas kullanıcı için kimlik bilgilerini elde etmek için bilgisayar arasında taşıma taşıyabilirsiniz. 

## <a name="what-is-a-lateral-movement-path"></a>Yanal hareket yolu nedir?

Yanal hareket, saldırganın hassas hesapları erişim kazanmak için hassas olmayan hesapları proaktif olarak kullanır. durumdur. Açıklanan yöntemlerden birini kullanın [şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md) ilk hassas olmayan parola kazanmak ve Yöneticiler, ağınızda olan ve hangi makinelerin anlamak için Bloodhound gibi bir araç kullanmak için Bunlar erişilebilir. Bunlar ardından kimin hangi hesapların olduğunu biliyor ve hangi kaynaklara ve dosyaları zaten eriştiği bilgisayarlarda depolanan diğer kullanıcıların (bazen hassas kullanıcılar) kimlik bilgilerini çalmak erişmek için etki alanı denetleyicilerinde verilere erişebilir ve ardından yanal ağınızdaki yönetici ayrıcalıkları elde kadar kullanıcı ve kaynak arasında taşıyın. 

ATA, saldırganlar yanal hareket başarılı önlemek için ağınızdaki önleyici harekete geçmenizi sağlar.

## <a name="discovery-your-at-risk-sensitive-accounts"></a>Bulma at-risk hassas hesaplarınızı

Ağınızdaki hassas hangi hesapların kendi bağlantı nedeniyle hassas olmayan hesaplar ve kaynaklara karşı savunmasız olduğunu öğrenmek için aşağıdaki adımları izleyin. Yanal hareket saldırılarına karşı ağınızın güvenliğini sağlamak için ATA, ayrıcalıklı hesaplarınızdaki başlar ve ardından hangi kullanıcıların gösterir bir eşleme sağlar ve bu kullanıcıların kimlik bilgilerini ve yanal yolunda aygıtlardır anlamına geriye dönük, sonundan ATA çalışır.

1. ATA Konsolu menüde raporları simgesine tıklayın ![Raporlar simgesi](./media/ata-report-icon.png).

2. Altında **yanal hareketleri yollara hassas hesapları**, yoksa hiçbir yanal hareket yol bulundu, raporu gri çıkışı. Yanal hareket yolları varsa, daha sonra otomatik olarak seçme rapor tarihleri ilk tarih ilgili verileri olduğunda. 

 ![raporlar](./media/reports.png)

3. Tıklatın **karşıdan**.

3. Oluşturulan Excel dosyası risk altındadır, hassas hesapları hakkında ayrıntılar sağlar. **Özet** sekmesi, hassas hesapları, bilgisayar ve at-risk kaynaklar için ortalama sayısı ayrıntı grafikleri sağlar. **Ayrıntıları** sekmesini endişe olması gereken hassas hesapları listesini sağlar.


## <a name="investigate"></a>Araştırma

Artık hangi hassas hesapları risk altındadır bildiğinize göre derin olabilir. daha fazla bilgi edinmek ve önlemler almak için ATA daha yakından inceleyin.

1. ATA Konsolu'nda hesabı listelendiğini kullanıcının güvenlik açığı Ara **yanal hareketleri yollara hassas hesapları** , örneğin, Samira Abbasi rapor. Bir varlığın yanal hareket yolunda olduğunda varlık profile eklenmesini yanal hareket rozet da arayın ![yanal simgesi](./media/lateral-movement-icon.png) veya ![yolu simgesi](./media/paths-icon.png).

2. Açılan kullanıcı profili sayfasında tıklatın **yanal hareket yolları** sekmesi.

3. Görüntülenen diyagramı, hassas kullanıcı olası yolları bir haritasını sağlar. Grafik Etkilenme yeni nedenle son iki gün içinde yapılan bağlantıları gösterir.

4. Hassas kullanıcının kimlik bilgilerinin açıklanmasını hakkında bilgi edinebilirsiniz görmek için grafiği gözden geçirin. Örneğin, bu eşlemeyi Samira izleyin Abbasi içinde **tarafından oturum açtığınız** gri Samira kendi ayrıcalıklı kimlik bilgileriyle günlüğe nerede görmek için okları. Bu durumda, REDMOND Washington istisnası bilgisayarda Samira'nın harfe duyarlı kimlik bilgileri kaydedildi Ardından, diğer kullanıcılar oturum bkz en Etkilenme ve güvenlik açığı oluşturulan hangi bilgisayarların. Bu bakarak bkz **yönetici** siyah kaynak üzerinde yönetici ayrıcalıklarına sahip kişileri görmek için okları. Bu örnekte, herkesin Contoso tüm grubundaki kullanıcı kimlik bilgilerini bu kaynaktan erişim olanağı vardır.  

 ![Kullanıcı profili yanal hareket yolları](media/user-profile-lateral-movement-paths.png)


## <a name="preventative-best-practices"></a>Koruyucu en iyi uygulamalar

- Yanal hareket önlemek için en iyi yolu hassas kullanıcılar yalnızca sağlamlaştırılmış bilgisayarlara oturum açarken yönetici kimlik bilgilerini kullanmak emin olmaktır aynı bilgisayar üzerinde yönetici haklarına sahip hiçbir hassas olmayan kullanıcı olduğu. Örnekte, Samira REDMOND Washington geliştirme erişmesi gerekirse, bunları bir kullanıcı adı ve parolayla dışında her yönetici kimlik bilgileri kaydettiğini emin olun veya REDMOND Washington istisnası yerel Yöneticiler grubundan Contoso tüm grubunu Kaldır

- Hiç kimse gereksiz yerel yönetici izinlerine sahip olduğundan emin olun önerilir. Örnekte, Contoso tüm herkesin REDMOND Washington istisnası üzerinde yönetici hakları gerçekten gerekiyorsa bkz denetlemelisiniz

- Kişiler yalnızca gerekli kaynaklara erişimi olduğundan emin olmak için her zaman iyi bir fikirdir. Örnekte de görüldüğü gibi Oscar Posada Samira'nın Etkilenme önemli ölçüde widens. Kendisine Contoso tüm dahil edilmesi gerekli mi? Etkilenme en aza indirmek için oluşturabilirsiniz alt grupları var mı?


## <a name="see-also"></a>Ayrıca bkz:
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
