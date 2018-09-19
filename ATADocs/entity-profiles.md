---
title: Advanced Threat Analytics konsolundaki varlık profilleri ile çalışma | Microsoft Docs
description: ATA konsolundaki kullanıcı profilleri ekranından varlıkları araştırma açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/25/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 581a3257-32dc-453f-b84e-b9f99186f5d3
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: a34d25e59183e496350216f5d3043430cd65bca6
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133472"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="investigating-entity-profiles"></a>Varlık profilleri araştırma

Varlık profili, bir pano ile kullanıcılar, bilgisayarlar, cihazlar ve erişime sahip oldukları kaynakları ve geçmişlerini tam derinlemesine araştırma için tasarlanan sağlar. Profil sayfasında gerçekleştirilen etkinlikler (bir dakikaya kadar toplu olarak) bir grup bakın ve daha iyi anlamak gerçek etkinliklerini vermek için tek bir mantıksal etkinliğini gruplamak yeni ATA mantıksal etkinliği Çeviricisi yararlanır, Kullanıcılar.

Bir varlık profili sayfasına erişmek için şüpheli etkinlik zaman çizelgesinde bir kullanıcı adı gibi varlık adını tıklayın.

Soldaki menü Active Directory sunulan tüm bilgileri varlıkta - e-posta adresi, etki alanı, ilk görülen tarihi sağlar. Varlık hassas ise bunu neden size bildirir. Örneğin, kullanıcının hassas veya gizli bir grubun üyesi olarak etiketlendiğinden?
Hassas kullanıcı ise kullanıcı adının altında simgesini görürsünüz.

## <a name="view-entity-activities"></a>Varlık etkinlikleri görüntüleyin

Kullanıcı tarafından gerçekleştirilen tüm etkinlikleri görüntülemek veya bir varlık üzerinde gerçekleştirilen tıklayarak **etkinlikleri** sekmesi. 

 ![Kullanıcı profili etkinlikleri](media/user-profile-activities.png)

Varsayılan olarak, varlık profili ana bölmede, ayrıca kullanıcı tarafından veya varlıklar, varlık erişen kullanıcılar için erişim varlıklardan detaya gidebilirsiniz bir zaman çizelgesi varlığın etkinliklerin en fazla 6 ay geri geçmişini görüntüler.

Üst kısmında, Kurumunuz hakkında bir bakışta anlamak için ihtiyacınız olanlar Hızlı Bakış size Özet kutucukları görüntüleyebilirsiniz. Ne varlığı, türünü bağlı olarak değişir, bir kullanıcı için olan bu kutucuklar görürsünüz:
- Kaç kullanıcıdan vardır şüpheli etkinlikleri açın
- Kullanıcı oturum kaç bilgisayar
- Kullanıcının eriştiği kaç kaynak
- Hangi konumlardan VPN kullanıcı oturumu

  ![Varlık menüsü](media/entity-menu.png)

Bilgisayarlar için görebilirsiniz:
- Kuşkulu etkinlikler vardır makine için kaç açın
- Kaç kullanıcının makinede oturum
- Erişilen bilgisayar kaç kaynak
- Kaç tane konumları VPN bilgisayarda erişildi
- Hangi bilgisayar IP adresleri listesi kullandı

  ![Varlık menü bilgisayar](media/entity-computer.png)

Kullanarak **filtre** düğmesi etkinliği zaman çizelgesi etkinlikleri etkinlik türüne göre filtre uygulayabilirsiniz. Ayrıca, belirli bir (gürültülü) türünün etkinlik filtreleyebilirsiniz. Bir varlık ağ ne yaptığını temellerini anlamak istediğinizde bu araştırma için gerçekten çok yardımcı budur. Ayrıca belirli bir tarihe gidebilirsiniz ve etkinlikler de filtrelenmiş Excel'e dışarı aktarabilirsiniz. Dışarı aktarılan dosyayı, Dizin Hizmetleri değişikliklerini (hesap için Active Directory içinde değiştirilen öğeleri) için bir sayfa ve etkinlikleri için ayrı bir sayfa sağlar. 

## <a name="view-directory-data"></a>Dizin verilerini görüntüle

**Dizin verilerini** sekmesi, etkin kullanıcı erişim denetimi güvenlik bayrakları içeren dizinden statik bilgileri sağlar. Kullanıcı bir doğrudan üyelik veya bir özyinelemeli üyelik olup olmadığını söyleyebilir. böylece ATA ayrıca kullanıcının grup üyeliklerini görüntüler. Grupları için ATA grubunun üyeleri listeler.

 ![Kullanıcı profili dizin verileri](media/user-profile-dir-data.png)

İçinde **kullanıcı erişimi denetimi** bölümde, ATA, attentions gerekebilir güvenlik ayarları ortaya çıkarır. Kullanıcı ile ilgili önemli bayrakları görebilirsiniz, kullanıcı sahip her zaman geçerli olsun, parola vb., gibi kullanıcı tuşuna gibi parolayı atlamak için girin. 

## <a name="view-lateral-movement-paths"></a>Yanal hareket yollarını görüntüleme

Tıklayarak **yana hareket yollarını** sekmesinde yanal hareket yollarını ağınıza için kullanılan bu kullanıcı gelen ve görsel bir temsilini sağlayan tamamen dinamik ve tıklatılabilir bir harita görüntüleyebilirsiniz.

Harita, bilgisayarlar arasında kaç durak listesi sağlar veya kullanıcıların bir saldırgan sahip gizli bir hesabın güvenliğini aşmak için bu kullanıcı gelen ve giden ve kullanıcı kendilerini sahip gizli bir hesabın, kaç kaynakları ve hesapları doğrudan olduğunu görebilirsiniz. bağlı. Daha fazla bilgi için [yana hareket yollarını](use-case-lateral-movement-path.md). 

 ![Kullanıcı profili yatay hareket yolları](media/user-profile-lateral-movement-paths.png)


## <a name="see-also"></a>Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
