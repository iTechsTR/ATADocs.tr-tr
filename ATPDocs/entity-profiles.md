---
title: "Azure Advanced Threat Protection çalışma portalında kullanıcı profilleri ile çalışma | Microsoft Docs"
description: "Kullanıcılar Azure ATP çalışma portalında kullanıcı profilleri ekranından araştırmaya açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 17458706-79fb-4c23-aa42-66979164a45f
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 6ceefeeba6a52abf5da7ff44135cff55e9beab02
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="investigating-entity-profiles"></a>Varlık profilleri araştırma

Varlık profili ile kapsamlı varlık sayfası, kullanıcılar, bilgisayarlar, aygıtları ve erişime sahip oldukları kaynakları ve geçmişlerini tam derin Dalış araştırma için tasarlanmış sağlar. Profil sayfası, bir grup (en fazla bir dakika toplanmış) gerçekleştirilen etkinlikler bakın ve daha iyi anlamak gerçek etkinliklerini vermek için tek bir mantıksal etkinliğin gruplandırın yeni Azure ATP mantıksal etkinliği Çeviricisi yararlanır Kullanıcılarınızın.

Bir varlık profili sayfasına erişmek için bir kullanıcı şüpheli etkinlik zaman çizelgesi gibi varlık adı tıklayın.

Soldaki menüden tüm Active Directory bilgileri varlıkta - e-posta adresi, etki alanı, ilk görülen tarihi sağlar. Varlık duyarlı ise, bu, neden bildirir. Örneğin, kullanıcının hassas veya gizli bir grubun üyesi olarak etiketlenir?
Kullanıcının hassas ise, kullanıcının adı altında simgesini görürsünüz.

## <a name="view-entity-activities"></a>Varlık faaliyetleri görüntüle

Kullanıcı tarafından gerçekleştirilen tüm etkinlikler görüntülemek veya bir varlık üzerinde gerçekleştirilen tıklayın **etkinlikleri** sekmesi. 

 ![Kullanıcı profili etkinlikleri](media/user-profile-activities.png)

Varsayılan olarak, varlık profili ana bölmede, ayrıca aşağı varlıklar, varlık erişen kullanıcılar için veya kullanıcı tarafından erişilen varlıklar ayrıntılarına geçebilir olan bir zaman çizelgesi varlığın etkinliklerin en fazla altı ay geri geçmişini görüntüler.

En üstte, varlık - kaç kaç kaynak erişilen için kullanıcının oturum açtığı makineler ve kendisinden kullanıcı VPN (yapılandırılmışsa) oturum konumları hakkında bir bakışta anlamak ihtiyacınız olan hızlı bir genel bakış size Özet döşeme görüntüleyebilirsiniz . 

Kullanarak **göre filtre** düğmesi etkinlik zaman çizelgesi etkinlikleri etkinlik türüne göre filtreleyebilirsiniz. Ayrıca, belirli bir (gürültülü) türü etkinlik filtre uygulayabilirsiniz. Bir varlık ağ yaptıklarını temellerini anlamak istediğiniz zaman bu araştırma için yararlıdır. Belirli bir tarih de gidebilir ve etkinlikleri Excel'e filtre olarak dışa aktarabilirsiniz. Dışarı aktarılan dosyayı, Dizin Hizmetleri değişikliklerini (hesap için Active Directory içinde değiştirilen şeyler) için bir sayfa ve etkinlikler için ayrı bir sayfa sağlar. 

## <a name="view-directory-data"></a>Görünüm dizin verileri

**Dizin verilerini** sekmesi, etkin kullanıcı erişim denetimi güvenlik bayrakları dahil olmak üzere dizininden kullanılabilir statik bilgilerini sağlar. Böylece kullanıcı bir doğrudan üyelik veya bir özyinelemeli üyelik olup olmadığını söyleyebilir azure ATP kullanıcı için grup üyelikleri de görüntüler. Grupları için Azure ATP grubunun üyeleri listeler.

 ![Kullanıcı profili dizin verileri](media/user-profile-dir-data.png)

İçinde **kullanıcı erişim denetimi** , attentions gerekebilir Azure ATP yüzeyleri güvenlik ayarları bölümü. Kullanıcı hakkındaki önemli bayrakları görebilirsiniz, kullanıcı sahip her zaman geçerli olsun parola vb., gibi kullanıcı tuşuna gibi parola atlamak için girin. 

## <a name="view-lateral-movement-paths"></a>Görünüm yanal hareket yolları

Yanal hareket yolları sekmesine tıklayarak, yanal hareket yolları için ve ağınıza için kullanılan bu kullanıcı için görsel bir sunumdur sağlayan tam olarak dinamik ve tıklatılabilir bir harita görüntüleyebilirsiniz.

Harita, bilgisayarlar veya kullanıcılar arasında kaç atlama bir saldırganın hassas hesap tehlikeye kullanıcıya bu gelen ve giden yoktur, bir listesini sağlar ve kullanıcının hassas hesap varsa, kaç tane kaynaklar ve hesapları doğrudan bağlı görebilirsiniz.

Etkinlik için son iki gün, grafik artık görünür, algılanmaz, ancak [yanal hareket yolu rapor](reports.md) son 60 gün boyunca yanal hareket yolları hakkında bilgi sağlamak kullanılabilir olacak. 

Daha fazla bilgi için bkz: [yanal hareket yolları](use-case-lateral-movement-path.md). 

 ![Kullanıcı profili yanal hareket yolları](media/user-profile-lateral-movement-paths.png)


## <a name="see-also"></a>Ayrıca bkz:

- [Yanal hareket yollarını Azure ATP ile araştırın](use-case-lateral-movement-path.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)