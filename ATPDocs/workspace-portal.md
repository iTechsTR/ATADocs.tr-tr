---
title: "Azure Advanced Threat Protection çalışma Portalı'nı anlama | Microsoft Docs"
description: "Azure ATP çalışma portal ve çalışma portal bileşenlerini oturum açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 4ba46d60-3a74-480e-8f0f-9a082d62f343
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 21cc8b6b27efb514d2a313fc0959152d601d4344
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="working-with-the-azure-atp-workspace-portal"></a>Azure ATP çalışma Portalı'yla çalışma

İzlemek ve ATP tarafından algılanan kuşkulu etkinliği yanıtlamak için Azure ATP çalışma Portalı'nı kullanın.

Yazmaya `?` anahtar Azure ATP çalışma portal erişilebilirlik için klavye kısayolları sağlar. 

Azure ATP çalışma portal kronolojik sıraya göre tüm kuşkulu etkinliklerin hızlı bir görünümünü sağlar. Herhangi bir etkinliği detayına gitmenize ve bu etkinliklere dayalı olarak eylemler yapmanıza olanak tanır. Çalışma alanı portal, uyarılar ve bildirimler Azure ATP veya kuşkulu sayılan yeni etkinlikleri tarafından görülen sorunları vurgulamak için de görüntüler.

Bu makalede Azure ATP çalışma portal anahtar öğeleri ile çalışma konusunda açıklanmaktadır.


## <a name="enabling-access-to-the-azure-atp-workspace-portal"></a>Azure ATP çalışma portala erişimi etkinleştirmeden
Azure ATP çalışma Portalı'na başarıyla oturum açmak için Azure ATP çalışma portalına erişmek için uygun Azure Active Directory güvenlik grubunun atanmış bir kullanıcıyla oturum sahip. Rol tabanlı erişim denetimi (RBAC) Azure ATP hakkında daha fazla bilgi için bkz: [Azure ATP rol gruplarıyla çalışma](atp-role-groups.md).

## <a name="logging-into-the-azure-atp-workspace-portal"></a>Azure ATP çalışma portalda oturumunuzu açarken

1. Çalışma alanı Yönetim Portalı'na oturum açarak çalışma portal girebilirsiniz [https://portal.atp.azure.com](https://portal.atp.azure.com) ve ilgili çalışma alanını seçerek veya çalışma URL'sini tarama: [https://*workspacename*. atp.azure.com](https://*workspacename*.atp.azure.com).


2.  Azure ATP destekler çoklu oturum açma, zaten bilgisayarınıza Azure ATP oturum açtıysanız, tümleşik Windows kimlik doğrulaması ile - özelliğini Azure ATP çalışma Portalı'na oturum belirtecini kullanır. Ayrıca bir akıllı kart kullanarak da oturum açabilirsiniz. İle izinlerinizi Azure ATP içinde karşılık gelen, [Yönetici rolü](atp-role-groups.md).

 > [!NOTE]
 > Azure ATP yönetici kullanıcı adı ve parola kullanarak Azure ATP çalışma portalına erişmek istediğiniz bilgisayarda oturum açmak emin olun. Alternatif olarak, tarayıcınızı farklı bir kullanıcı ya da Windows ve günlük dışında günlük olarak, Azure ATP yönetici kullanıcı üzerinde çalışabilir. 


### <a name="attack-time-line"></a>Saldırı zaman çizelgesi

Bu, Azure ATP çalışma portalına oturum açtığınızda gittiğiniz varsayılan giriş sayfasıdır. Varsayılan olarak, tüm kuşkulu etkinliler saldırı zaman çizelgesinde gösterilir. Tüm, saldırı zaman çizelgesine filtre açık, çıkarılan veya Suppressed kuşkulu etkinlikler. Ayrıca, her etkinliğe atanmış olan önem düzeyini de görebilirsiniz.

![Azure ATP saldırı zaman çizelgesi resmi](media/atp-sa-timeline.png)

Daha fazla bilgi için bkz. [Kuşkulu etkinliklerle çalışma](working-with-suspicious-activities.md)

### <a name="whats-new"></a>Yenilikler

Azure ATP yeni bir sürümü yayımlandıktan sonra **yenilikler** penceresi görünür üst ne en son sürümde eklenen size bildirmek için sağ. Ayrıca, sürüm indirme bağlantı sağlar.

### <a name="filtering-panel"></a>Filtreleme paneli

Kuşkulu etkinlikleri Durum ve Önem Derecesi’ne göre filtreleyerek, saldırı zaman çizelgesinde veya varlık profili kuşkulu etkinlikler sekmesinde hangi etkinliklerin görüntüleneceğini belirtebilirsiniz.

### <a name="search-bar"></a>Arama çubuğu

Üst menüde arama çubuğunu bulabilirsiniz. Belirli bir kullanıcı, bilgisayar veya Azure ATP gruplarında arayabilirsiniz. Denemek için, yazmaya başlamanız yeterlidir. Arama çubuğunu alt kısmında bulunan arama sonuçları sayısı gösterilir. 

![Azure ATP çalışma portal arama resmi](media/atp-workspace-portal-search.png)

Sayı'yı tıklatırsanız, sonuçları daha fazla araştırma için varlık türüne göre filtreleyebilirsiniz arama sonuçları sayfasını erişebilirsiniz.

![Arama sonuçları](media/search-results.png)

### <a name="health-center"></a>Sistem durumu Merkezi

Sistem durumu merkezi düzgün Azure ATP çalışma alanınızda çalışmayan bir şey olduğunda size uyarılar sağlar.

![Azure ATP sistem durumu merkezinin resmi](media/atp-health-issue.png)

Sisteminizin bağlantı hatası veya bağlantısı kesilmiş bir Azure ATP tek başına algılayıcı gibi bir sorunla karşılaştığında her zaman sistem durumu Merkezi simgesi, kırmızı bir nokta göstererek bilmenizi sağlar. 

![Azure ATP sistem durumu merkezi kırmızı noktasının resmi](media/atp-health-bar.png)

### <a name="sensitive-groups"></a>Gizli gruplar

ATP hassas grupları hakkında daha fazla bilgi için bkz: [hassas gruplarıyla çalışma](sensitive-accounts.md).

### <a name="mini-profile"></a>Mini profil

Farenizi çalışma portal herhangi bir yerindeki bir varlık üzerine, söz konusu olduğunda, bir kullanıcı veya bir bilgisayar gibi bir mini profil otomatik olarak tek bir varlığın açar aşağıdaki bilgileri görüntüleme, kullanılabilir ve ilgili:

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
- – Oluşturulan varlığı Active Directory içinde oluşturulduğu. İzleme Azure ATP başlatmadan önce oluşturulduysa, görüntülenmez.
- İlk Azure bu varlıktaki bir etkinlik gözlenen ATP ilk kez – görülür.
- Son - görülen en son ne zaman Azure bu varlıktaki bir etkinlik gözlenen ATP.
- SA rozet - bu varlıkla ilişkilendirilen kuşkulu etkinlikler varsa görüntülenir.
- Windows Defender ATP bu varlıkla ilişkilendirilen kuşkulu etkinlikler varsa WD ATP rozet-Will görüntülenmesi.
- Yanal hareket yolları göstergeye - gösterileceği olmuştur, yanal hareket yolları Bu varlık için son iki gün içinde algılandı.


## <a name="see-also"></a>Ayrıca bkz:

- [Azure ATP çalışma alanları oluşturma](install-atp-step1.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)