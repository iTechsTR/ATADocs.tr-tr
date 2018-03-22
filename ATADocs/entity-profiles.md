---
title: "Advanced Threat Analytics konsolundaki varlık profilleri ile çalışma | Microsoft Docs"
description: "ATA konsolu kullanıcı profillerini ekranında varlıklardan araştırmaya açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 581a3257-32dc-453f-b84e-b9f99186f5d3
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: f9e19a1d033238f506fc0523bf50af6e204ba0cf
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*



# <a name="investigating-entity-profiles"></a>Varlık profilleri araştırma

Varlık profili, sizinle bir pano, kullanıcılar, bilgisayarlar, cihazlar ve erişime sahip oldukları kaynakları ve geçmişlerini tam derin Dalış araştırma için tasarlanmış sağlar. Profil sayfası gerçekleştirilen etkinlikler (en fazla bir dakika toplanan) bir grup bakın ve daha iyi anlamak gerçek etkinliklerini vermek için tek bir mantıksal etkinliğin gruplandırın yeni ATA mantıksal etkinliği Çeviricisi yararlanır, Kullanıcılar.

Bir varlık profili sayfasına erişmek için bir kullanıcı şüpheli etkinlik zaman çizelgesi gibi varlık adı tıklayın.

Soldaki menüden tüm Active Directory bilgileri varlıkta - e-posta adresi, etki alanı, ilk görülen tarihi sağlar. Varlık duyarlıysa bunu neden size bildirir. Örneğin, kullanıcının hassas veya gizli bir grubun üyesi olarak etiketlenir?
Kullanıcının hassas ise, kullanıcının adı altında simgesini görürsünüz.

## <a name="view-entity-activities"></a>Varlık faaliyetleri görüntüle

Kullanıcı tarafından gerçekleştirilen tüm etkinlikler görüntülemek veya bir varlık üzerinde gerçekleştirilen tıklayın **etkinlikleri** sekmesi. 

 ![Kullanıcı profili etkinlikleri](media/user-profile-activities.png)

Varsayılan olarak, varlık profili ana bölmede, ayrıca aşağı varlıklar, varlık erişen kullanıcılar için veya kullanıcı tarafından erişilen varlıklar ayrıntılarına geçebilir olan bir zaman çizelgesi varlığın etkinliklerin kadar 6 ayda geri geçmişini görüntüler.

En üstte, varlık hakkında bir bakışta anlamak ihtiyacınız olan hızlı bir genel bakış size Özet döşeme görüntüleyebilirsiniz. Ne varlığı, tür üzerinde değişiklik, bir kullanıcı için olan bu kutucuklar görürsünüz:
- Kaç kullanıcı için vardır kuşkulu etkinlikleri açın
- Kullanıcı oturum kaç bilgisayar
- Kullanıcı erişilen kaç tane kaynaklar
- Hangi konumlardan kullanıcı VPN oturum

Bilgisayarlar için görebilirsiniz:
- Kaç tane kuşkulu etkinlikler için makine vardır açın
- Makinede kaç kullanıcının oturum
- Bilgisayar erişilen kaç tane kaynaklar
- VPN erişilebilir bilgisayarda kaç konumları
- Hangi IP adresi bilgisayar listesini kullanılmış

![Varlık menüsü](media/entity-menu.png)

Kullanarak **göre filtre** düğmesi etkinlik zaman çizelgesi etkinlikleri etkinlik türüne göre filtreleyebilirsiniz. Ayrıca, belirli bir (gürültülü) türü etkinlik filtre uygulayabilirsiniz. Bir varlık ağ yaptıklarını temellerini anlamak istediğiniz zaman bu araştırma için gerçekten yardımcı olur. Belirli bir tarih de gidebilir ve etkinlikleri Excel'e filtre olarak dışa aktarabilirsiniz. Dışarı aktarılan dosyayı, Dizin Hizmetleri değişikliklerini (hesap için Active Directory içinde değiştirilen şeyler) için bir sayfa ve etkinlikler için ayrı bir sayfa sağlar. 

## <a name="view-directory-data"></a>Görünüm dizin verileri

**Dizin verilerini** sekmesi, etkin kullanıcı erişim denetimi güvenlik bayrakları dahil olmak üzere dizininden kullanılabilir statik bilgilerini sağlar. Böylece kullanıcı bir doğrudan üyelik veya bir özyinelemeli üyelik olup olmadığını söyleyebilir ATA kullanıcı için grup üyelikleri de görüntüler. Grupları için ATA grubunun üyeleri listeler.

 ![Kullanıcı profili dizin verileri](media/user-profile-dir-data.png)

İçinde **kullanıcı erişim denetimi** bölümü, ATA, attentions gerekebilir güvenlik ayarlarını ortaya çıkarır. Kullanıcı hakkındaki önemli bayrakları görebilirsiniz, kullanıcı sahip her zaman geçerli olsun parola vb., gibi kullanıcı tuşuna gibi parola atlamak için girin. 

## <a name="view-lateral-movement-paths"></a>Görünüm yanal hareket yolları

Tıklayarak **yanal hareket yolları** sekmesini yanal hareket yolları için ve ağınıza için kullanılan bu kullanıcı için görsel bir sunumdur sağlayan tam olarak dinamik ve tıklatılabilir bir harita görüntüleyebilirsiniz.

Harita, bilgisayarlar arasında kaç durağı listesini sağlar veya bu kullanıcı hassas hesap tehlikeye gelen ve kullanıcıların bir saldırgan sahip olabilir ve kullanıcı kendilerini sahip hassas hesap, kaç tane kaynaklar ve hesapları doğrudan olduğunu görebilirsiniz bağlı. Daha fazla bilgi için bkz: [yanal hareket yolları](use-case-lateral-movement-path.md). 

 ![Kullanıcı profili yanal hareket yolları](media/user-profile-lateral-movement-paths.png)


## <a name="see-also"></a>Ayrıca bkz:
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
