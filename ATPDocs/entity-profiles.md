---
title: Azure Gelişmiş tehdit koruması çalışma Portalı'nda kullanıcı profilleri ile çalışma | Microsoft Docs
description: Kullanıcılara Azure ATP çalışma alanı Portalı'nda kullanıcı profilleri ekranından araştırmaya açıklar
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/06/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 17458706-79fb-4c23-aa42-66979164a45f
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: b4353de9d004358ddcdc929271fd96665e1c7322
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44165856"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="understanding-entity-profiles"></a>Varlık profilleri anlama

Varlık profili kapsamlı varlık sayfasıyla kullanıcılar, bilgisayarlar, cihazlar, erişime sahip oldukları kaynakları ve geçmişlerini tam derinlemesine araştırma için tasarlanmış sağlar. Profil sayfasında, bir grup etkinlik (bir dakikaya kadar toplanmış) gerçekleşen bakın ve daha iyi anlamak gerçek etkinliklerini vermek için tek bir mantıksal etkinliğini gruplamak yeni Azure ATP mantıksal etkinliği Çeviricisi yararlanır Kullanıcılarınızın.

Bir varlık profili sayfasına erişmek için şüpheli etkinlik zaman çizelgesinde bir kullanıcı adı gibi varlık adını tıklayın.

Soldaki menü Active Directory sunulan tüm bilgileri varlıkta - e-posta adresi, etki alanı, ilk görülen tarihi sağlar. Varlığın büyük/küçük harfe duyarlıdır, bunu size neden bildirir. Örneğin, kullanıcının hassas veya gizli bir grubun üyesi olarak etiketlendiğinden?
Hassas kullanıcı ise, kullanıcının adını bölümündeki simgeye bakın.

## <a name="view-entity-activities"></a>Varlık etkinlikleri görüntüleyin

Kullanıcı tarafından gerçekleştirilen tüm etkinlikleri görüntülemek veya bir varlık üzerinde gerçekleştirilen tıklayarak **etkinlikleri** sekmesi. 

 ![Kullanıcı profili etkinlikleri](media/user-profile-activities.png)

Varsayılan olarak, varlık profili ana bölmede, ayrıca kullanıcı tarafından veya varlıklar, varlık erişen kullanıcılar için erişim varlıklardan detaya gidebilirsiniz bir zaman çizelgesi varlığın etkinliklerin en fazla altı ay geri geçmişini görüntüler.

Üst kısmında, varlık - kaç makineler ne kadar kaynak erişildiğini için kullanıcının oturum açtığı ve konumları, VPN (yapılandırılmışsa) oturum açmış kullanıcı hakkında bir bakışta anlamak ihtiyacınız olan hızlı bir genel bakış sunan Özet kutucuğunu görüntüleyebilirsiniz. . 

Kullanarak **filtre** düğmesi etkinliği zaman çizelgesi etkinlikleri etkinlik türüne göre filtre uygulayabilirsiniz. Ayrıca, belirli bir (gürültülü) türünün etkinlik filtreleyebilirsiniz. Bir varlık ağ ne yaptığını temellerini anlamak istediğinizde bu araştırma için yararlıdır. Ayrıca belirli bir tarihe gidebilirsiniz ve etkinlikler de filtrelenmiş Excel'e dışarı aktarabilirsiniz. Dışarı aktarılan dosyayı, Dizin Hizmetleri değişikliklerini (hesap için Active Directory içinde değiştirilen öğeleri) için bir sayfa ve etkinlikleri için ayrı bir sayfa sağlar. 

## <a name="view-directory-data"></a>Dizin verilerini görüntüle

**Dizin verilerini** sekmesi, etkin kullanıcı erişim denetimi güvenlik bayrakları içeren dizinden statik bilgileri sağlar. Böylece kullanıcı bir doğrudan üyelik veya bir özyinelemeli üyelik olup olmadığını söyleyebilir azure ATP kullanıcı grup üyelikleri de görüntüler. Gruplar için Azure ATP grubunun üyeleri listeler.

 ![Kullanıcı profili dizin verileri](media/user-profile-dir-data.png)

İçinde **kullanıcı erişimi denetimi** , attentions gerekebilir Azure ATP yüzeyleri güvenlik ayarları bölümü. Kullanıcı ile ilgili önemli bayrakları görebilirsiniz, kullanıcı sahip her zaman geçerli olsun, parola vb., gibi kullanıcı tuşuna gibi parolayı atlamak için girin. 

## <a name="view-lateral-movement-paths"></a>Yanal hareket yollarını görüntüleme

Yanal hareket yollarını sekmesine tıklayarak, yanal hareket yollarını ağınıza için kullanılan bu kullanıcı gelen ve görsel bir temsilini sağlayan tamamen dinamik ve tıklatılabilir bir harita görüntüleyebilirsiniz.

Harita, bilgisayarlar veya kullanıcılar arasında kaç atlama bir saldırganın hassas hesabının gizliliğini bozmak için bu kullanıcı gelen ve giden yoktur, bir liste sağlar ve kullanıcının hassas hesap varsa, kaç tane kaynaklar ve hesapları doğrudan bağlı görebilirsiniz.

Etkinlik Son iki güne ait graf artık görünür algılanmazsa, ancak [yana hareket yolu rapor](reports.md) son 60 güne yatay hareket yolları hakkında bilgi sağlamak kullanılabilir. 

Daha fazla bilgi için [yana hareket yollarını](use-case-lateral-movement-path.md). 

 ![Kullanıcı profili yatay hareket yolları](media/user-profile-lateral-movement-paths.png)


## <a name="see-also"></a>Ayrıca Bkz.

- [Azure ATP ile yanal hareket yollarını araştırma](use-case-lateral-movement-path.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)