---
title: "Yanal hareket yolu saldırılarına Azure ATP araştırma | Microsoft Docs"
description: "Bu makalede, yanal hareket yolu saldırılarını ile Azure Gelişmiş tehdit Koruması (ATP) algılamak üzere açıklar."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: de15c920-8904-4124-8bdc-03abd9f667cf
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 7deeec2c2ee2c2d964b6495921eba0fa378bd8ee
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
---
*Uygulandığı öğe: Azure Advanced Threat Protection sürüm 1.9*

# <a name="investigating-lateral-movement-paths-with-azure-atp"></a>Yanal hareket yollarını Azure ATP ile araştırma

Azure ATP yanal hareket yolları kullanma saldırıların önlenmesine yardımcı olabilir. Hatta en iyi hassas kullanıcılarınızın korumak için bunu yaptığınızda, sık sık değişen, kendi makinelerine sıkı ve verilerine güvenli bir şekilde, depolanan karmaşık parolalar, yöneticilere sahip saldırganlar kullanmaya devam edebilirsiniz yanal hareket yolları ağınız arasında taşıma Kullanıcılar ve sanal güvenlik ikramiye isabet kadar bilgisayarlar arasında: hassas yönetici hesabı kimlik bilgilerinizi.

## <a name="what-is-a-lateral-movement-path"></a>Yanal hareket yolu nedir?

Yanal hareket, saldırganın hassas hesapları erişim kazanmak için hassas olmayan hesapları proaktif olarak kullanır. durumdur. Açıklanan yöntemlerden birini kullanın [şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md) ilk hassas olmayan parola kazanmak ve Yöneticiler, ağınızda olan ve hangi makinelerin anlamak için Bloodhound gibi bir araç kullanmak için Bunlar erişilebilir. Ardından, kullanılabilir veri kimin hangi hesapları ve hangi kaynaklara ve dosyalarına erişimi olduğunu öğrenmek için etki alanı denetleyicilerinde saldırganlara yararlanabilir ve sahip oldukları bilgisayarlarda depolanan kimlik bilgileri diğer kullanıcıların (bazen hassas kullanıcılar) çalabilir zaten erişilen ve yönetici ayrıcalıkları ağınızdaki elde kadar yanal daha da fazla kullanıcılar hem de kaynaklar taşıyın. 

Azure ATP, saldırganlar yanal hareket başarılı önlemek için ağınızdaki önleyici harekete geçmenizi sağlar.

## <a name="discovery-your-at-risk-sensitive-accounts"></a>Bulma at-risk hassas hesaplarınızı

Ağınızdaki hassas hangi hesapların kendi bağlantı nedeniyle hassas olmayan hesaplar ve kaynaklara karşı savunmasız olduğunu öğrenmek için aşağıdaki adımları izleyin. Yanal hareket saldırılarına karşı ağınızın güvenliğini sağlamak için Azure ATP geriye dönük, son Azure ATP, ayrıcalıklı hesaplarınızdaki başlar ve ardından hangi kullanıcıların gösterir bir eşleme sağlar anlamına çalışır ve bu kullanıcılar yanal yolunda aygıtlardır ve bunların kimlik bilgileri.

1. Azure ATP çalışma portal menüde raporları simgesine tıklayın ![Raporlar simgesi](./media/atp-report-icon.png).

2. Altında **yanal hareketleri yollara hassas hesapları**, yoksa hiçbir yanal hareket yol bulundu, raporu gri çıkışı. Yanal hareket yolları varsa, daha sonra otomatik olarak seçme rapor tarihleri ilk tarih ilgili verileri olduğunda. Yanal hareket yolu raporun son 60 gün için veriler sağlar.

 ![raporlar](./media/reports.png)

3. Tıklatın **karşıdan**.

3. Oluşturulan Excel dosyası risk altındadır, hassas hesapları hakkında ayrıntılar sağlar. **Özet** sekmesi, hassas hesapları, bilgisayar ve at-risk kaynaklar için ortalama sayısı ayrıntı grafikleri sağlar. **Ayrıntıları** sekmesini endişe olması gereken hassas hesapları listesini sağlar.

4. Yanal hareket yolu algılanması için gerekli SAM-R işlemlerini gerçekleştirmek Azure ATP izin vermek, sunucularınızın ayarlama hakkında yönergeler için [yapılandırma SAM-R](install-atp-step8-samr.md).

## <a name="investigate"></a>Araştırma

Hangi hassas hesapları risk altındadır bildiğinize göre derin yapabilecekleriniz ATP daha fazla bilgi edinmek ve önlemler almak için Azure daha yakından inceleyin.

1. Azure ATP çalışma Portalı'nda kullanıcı hesabı listelendiğini güvenlik açığı Ara **yanal hareketleri yollara hassas hesapları** , örneğin, Samira Abbasi rapor. Varlık yanal hareket yolunda olduğunda varlık profile eklenmesini yanal hareket rozet da arayabilirsiniz ![yanal simgesi](./media/lateral-movement-icon.png) veya ![yolu simgesi](./media/paths-icon.png). Bu, son iki gün içinde yanal hareket varsa kullanılabilir. 

2. Açılan kullanıcı profili sayfasında tıklatın **yanal hareket yolları** sekmesi. 

3. Görüntülenen diyagramı, hassas kullanıcı olası yolları bir haritasını sağlar. Grafik Etkilenme yeni nedenle son iki gün içinde yapılan bağlantıları gösterir. Etkinlik için son iki gün, grafik görüntülenmezse, algılanmaz, ancak [yanal hareket yolu rapor](reports.md) son 60 gün boyunca yanal hareket yolları hakkında bilgi sağlamak kullanılabilir olmaya devam edecektir.

4. Hassas kullanıcının kimlik bilgilerinin açıklanmasını hakkında bilgi edinebilirsiniz görmek için grafiği gözden geçirin. Örneğin, bu eşlemeyi Samira izleyin Abbasi içinde **tarafından oturum açtığınız** gri Samira kendi ayrıcalıklı kimlik bilgileriyle günlüğe nerede görmek için okları. Bu durumda, REDMOND Washington istisnası bilgisayarda Samira'nın harfe duyarlı kimlik bilgileri kaydedildi Ardından, diğer kullanıcılar oturum bkz en Etkilenme ve güvenlik açığı oluşturulan hangi bilgisayarların. Bu bakarak bkz **yönetici** siyah kaynak üzerinde yönetici ayrıcalıklarına sahip kişileri görmek için okları. Bu örnekte, herkesin Contoso tüm grubundaki kullanıcı kimlik bilgilerini bu kaynaktan erişim olanağı vardır.  

 ![Kullanıcı profili yanal hareket yolları](media/user-profile-lateral-movement-paths.png)


## <a name="preventative-best-practices"></a>Koruyucu en iyi uygulamalar

- Yanal hareket önlemek için en iyi yolu, hassas kullanıcılar yalnızca sağlamlaştırılmış bilgisayarlara oturum açarken yönetici kimlik bilgilerini kullanmak emin olmaktır. Örnekte yönetici Samira REDMOND Washington geliştirme erişmesi gerekirse, bir kullanıcı adı ve parola yönetici kimlik bilgilerini dışındaki oturum oturum olduğundan emin olun.

- Hiç kimse gereksiz yönetim izinlerine sahip olduğundan emin olun önerilir. Örnekte, Contoso tüm herkesin REDMOND Washington istisnası üzerinde yönetici hakları gerçekten gerekiyorsa bkz denetlemelisiniz

- Kişiler yalnızca gerekli kaynaklara erişimi olduğundan emin olmak için her zaman iyi bir fikirdir. Örnekte de görüldüğü gibi Oscar Posada Samira'nın Etkilenme önemli ölçüde widens. Contoso tüm kullanıcı dahil edilmesi gerekli mi? Etkilenme en aza indirmek için oluşturabilirsiniz alt grupları var mı?


## <a name="see-also"></a>Ayrıca bkz:

- [SAM-R gerekli izinleri yapılandırma](install-atp-step8-samr.md)
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)