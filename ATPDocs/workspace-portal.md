---
title: Azure Gelişmiş tehdit koruması çalışma portalı anlama | Microsoft Docs
description: Azure ATP çalışma alanı portalı ve çalışma alanı portal bileşenlerini günlüğünün nasıl tutulduğunu açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 4ba46d60-3a74-480e-8f0f-9a082d62f343
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 0fa8c1e19fde1ec779699b3a2c5411dea0908451
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44166338"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="working-with-the-azure-atp-workspace-portal"></a>Azure ATP çalışma alanı portalıyla çalışma

Azure ATP çalışma alanı portalı izlemek ve ATP tarafından algılanan kuşkulu etkinliği yanıtlamak için kullanın.

Yazarak `?` anahtar Azure ATP çalışma alanı portal erişilebilirliği için klavye kısayolları sağlar. 

Azure ATP çalışma alanı portal kronolojik sırada tüm kuşkulu etkinliklerin hızlı bir görünümünü sunar. Herhangi bir etkinliği detayına gitmenize ve bu etkinliklere dayalı olarak eylemler yapmanıza olanak tanır. Çalışma alanı portal ayrıca uyarılar ve bildirimler Azure ATP veya kuşkulu sayılan yeni etkinlikleri tarafından görülen sorunları vurgulamak için görüntüler.

Bu makalede, Azure ATP çalışma portalının anahtar öğeleri ile çalışma konusunda açıklanır.


## <a name="enabling-access-to-the-azure-atp-workspace-portal"></a>Azure ATP çalışma alanı portal erişimini etkinleştirme
Azure ATP çalışma alanı portalına başarıyla oturum açmak için Azure ATP çalışma alanı portalına erişmek için uygun Azure Active Directory güvenlik grubu atandığı bir kullanıcıyla oturum açmalısınız. Azure ATP rol tabanlı access control (RBAC) hakkında daha fazla bilgi için bkz: [Azure ATP rol gruplarıyla çalışma](atp-role-groups.md).

## <a name="logging-into-the-azure-atp-workspace-portal"></a>Azure ATP çalışma alanı portalda oturumunuzu açarken

1. Çalışma alanı yönetim portalında oturum açarak çalışma portalı girebilirsiniz [ https://portal.atp.azure.com ](https://portal.atp.azure.com) ve ilgili çalışma alanını seçerek veya çalışma alanı URL'sine göz atma: [https:// *workspacename*. atp.azure.com](https://*workspacename*.atp.azure.com).


2.  Azure ATP destekleyen tek oturum, zaten bilgisayarınıza Azure ATP oturum açtıysanız, Windows kimlik doğrulaması ile tümleştirilmiş açma, Azure ATP çalışma alanı portalda oturum açarken belirtecini kullanır. Ayrıca bir akıllı kart kullanarak da oturum açabilirsiniz. İzinleriniz, Azure ATP ile karşılık gelen, [Yönetici rolü](atp-role-groups.md).

 > [!NOTE]
 > Azure ATP yönetici kullanıcı adı ve parola kullanarak Azure ATP çalışma alanı portalına erişmek istediğiniz bilgisayara oturum açmak emin olun. Alternatif olarak, tarayıcınızı farklı bir kullanıcı veya oturumunuzu Windows ve günlük olarak, Azure ATP yönetici kullanıcınızla üzerinde çalışabilir. 


### <a name="attack-time-line"></a>Saldırı zaman çizelgesi

Azure ATP çalışma alanı portalında oturum açtığınızda yönlendirilirsiniz varsayılan giriş sayfasıdır. Varsayılan olarak, tüm kuşkulu etkinliler saldırı zaman çizelgesinde gösterilir. Tüm, saldırı zaman çizelgesine filtre uygulayabilirsiniz çıkarıldı veya Suppressed şüpheli etkinlikleri Aç. Ayrıca, her etkinliğe atanmış olan önem düzeyini de görebilirsiniz.

![Azure ATP saldırı zaman çizelgesi resmi](media/atp-sa-timeline.png)

Daha fazla bilgi için bkz. [Kuşkulu etkinliklerle çalışma](working-with-suspicious-activities.md)

### <a name="whats-new"></a>Yenilikler

Azure ATP yeni bir sürümü kullanıma sunulduktan sonra **yenilikler** penceresi görünür üst en son sürümde eklendikten sonra size bildirmek için sağ. Ayrıca, sürüm indirme bağlantısını içeren sağlar.

### <a name="filtering-panel"></a>Filtreleme paneli

Kuşkulu etkinlikleri Durum ve Önem Derecesi’ne göre filtreleyerek, saldırı zaman çizelgesinde veya varlık profili kuşkulu etkinlikler sekmesinde hangi etkinliklerin görüntüleneceğini belirtebilirsiniz.

### Arama çubuğu <a name="search-bar"></a>

Üst menüde arama çubuğunu bulabilirsiniz. Belirli bir kullanıcı, bilgisayar veya Azure ATP grupları arayabilirsiniz. Denemek için, yazmaya başlamanız yeterlidir. Arama çubuğunun alt kısmında bulunan Arama sonuç sayısı gösterilir. 

![Azure ATP çalışma alanı portal arama resmi](media/atp-workspace-portal-search.png)

Sayıya tıklarsanız, sonuçları araştırılması için varlık türüne göre filtrelemek arama sonuçları sayfası erişebilirsiniz.

![Arama sonuçları](media/search-results.png)

### <a name="health-center"></a>Sistem durumu Merkezi

Sistem durumu merkezi düzgün çalışmayan bir şey Azure ATP çalışma alanınızda olduğunda size uyarılar sağlar.

![Azure ATP sistem durumu merkezinin resmi](media/atp-health-issue.png)

Sisteminizde bağlantı hatası veya bağlantısı kesilmiş bir Azure ATP tek başına algılayıcı gibi bir sorunla karşılaşıldığında dilediğiniz zaman sistem durumu Merkezi simgesi kırmızı bir nokta göstererek bilmenizi sağlar. 

![Azure ATP sistem durumu merkezi kırmızı noktasının resmi](media/atp-health-bar.png)

### <a name="sensitive-groups"></a>Gizli gruplar

Gizli gruplarda ATP hakkında daha fazla bilgi için bkz: [hassas gruplarıyla çalışma](sensitive-accounts.md).

### <a name="mini-profile"></a>Mini profil

Farenizi çalışma Portalı'nda herhangi bir varlığın üzerine durumunda olduğunda, bir kullanıcı veya bir bilgisayar gibi bir mini profil otomatik olarak tek bir varlığın açılır aşağıdaki bilgileri görüntüleme, kullanılabilir ve ilgili:

![Azure ATP mini profilinin resmi](media/atp-mini-profile.png)

- Ad
- Başlık
- Bölüm
- AD etiketleri
- E-posta
- Office
- Telefon numarası
- Etki Alanı
- SAM adı
- – Oluşturulan varlığın Active Directory'de oluşturulduğu zaman. Azure ATP İzleme başlamadan önce oluşturulduysa, görüntülenmez.
- İlk – görülen ilk kez Azure ATP bu varlık etkinliği gözlemlendi.
- Son - görülen en son ne zaman Azure ATP bu varlık etkinliği gözlemlendi.
- SA rozet - bu varlıkla ilişkili kuşkulu etkinlikler varsa görüntülenir.
- Windows Defender ATP bu varlıkla ilişkili kuşkulu etkinlikler varsa WD ATP rozet-Will gösterilecek.
- Yanal hareket yollarını rozet - gösterilecek yapıldı, yanal hareket yollarını bu varlık için son iki gün içinde algılandı.


## <a name="see-also"></a>Ayrıca Bkz.

- [Azure ATP çalışma alanları oluşturma](install-atp-step1.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)