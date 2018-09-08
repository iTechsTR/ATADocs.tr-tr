---
title: Azure Gelişmiş tehdit koruması şüpheli etkinliklerle çalışma | Microsoft Docs
description: Azure ATP tarafından belirlenen kuşkulu etkinliklerin nasıl gözden geçirileceğini açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: a06004bd-9f77-4e8e-a0e5-4727d6651a0f
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 2a254ca9cc81ed48e92b68079f59a99742b296c3
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44166842"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="working-with-suspicious-activities"></a>Kuşkulu Etkinliklerle Çalışma
Bu makalede, Azure Gelişmiş tehdit koruması ile çalışmaya ilişkin temel bilgileri açıklar.

## Saldırı zaman çizelgesine şüpheli etkinlikleri gözden geçirin <a name="review-suspicious-activities-on-the-attack-time-line"></a>
Azure ATP çalışma alanı portalda oturum açtıktan sonra açık olarak otomatik olarak alınır **kuşkulu etkinlikler zaman çizelgesi**. Kuşkulu etkinlikler, en yenileri zaman çizelgesinin en üstünde olacak şekilde kronolojik sırayla listelenir.
Her kuşkulu etkinliğin aşağıdaki bilgileri bulunur:

-   Katılan varlıklar; örneğin kullanıcılar, bilgisayarlar, sunucular, etki alanı denetleyicileri ve kaynaklar.

-   Kuşkulu etkinliklerin zamanı ve zaman çerçevesi.

-   Kuşkulu etkinliğin önem derecesi; Yüksek, Orta veya Düşük

-   Durum: Açık, kapalı veya baskılanmış.

-   Yapılabilecekler

    -   Kuşkulu etkinliği e-postayla kuruluşunuzdaki diğer kişilerle paylaşın.

    -   Kuşkulu etkinliği Excel’e aktarma.

> [!NOTE]
> -   Farenizi bir kullanıcı veya bilgisayarın üzerine getirdiğinizde, varlık hakkında ek bilgi sağlayan bir varlık mini profili görüntülenir ve varlığın bağlantılı olduğu kuşkulu etkinliklerin sayısını içerir.
> -   Varlığın üzerine tıkladığınızda, kullanıcının veya bilgisayarın varlık profiline alır.

![Azure ATP kuşkulu etkinlikler zaman çizelgesinin resmi](media/atp-sa-timeline.png)

## Önizleme algılamalar<a name="preview-detections"></a>

Azure ATP araştırma ekibi, yeni bulunan saldırıları için yeni algılamalar uygulama üzerinde sürekli olarak çalışır. Azure ATP bir bulut hizmeti olduğundan, yeni algılamalar Azure ATP müşterilerin yeni algılamalardan olabildiğince çabuk yararlanmak için hızlı bir şekilde serbest bırakılır.

Bu algılamaların amacı, yeni algılamalar tanımlamak ve üründe yenidir bilmeniz yardımcı olması için ek olarak, preview rozeti ile etiketlenir. Devre dışı Önizleme algılamalar kapatırsanız, bunlar Azure ATP Konsolu - Zaman Çizelgesi'nde veya varlık profilleri - görüntülenmez ve yeni uyarılar açılması gerekmez.

![Önizleme algılama vpn](./media/preview-detection-vpn.png) 

Varsayılan olarak, Önizleme algılamalar Azure ATP içinde etkinleştirilir. 

Önizleme algılamalar devre dışı bırakmak için:

1. Azure ATP konsolunda ayarlar dişlisine tıklayın.
2. Önizleme altında soldaki menüde tıklayın **Algılamalar**.
3. Önizleme algılamalar açıp kapatmak için kaydırıcıyı kullanın.
 
![Önizleme algılamalar](./media/preview-detections.png) 


## <a name="filter-suspicious-activities-list"></a>Kuşkulu etkinlikler listesini filtreleme
Kuşkulu etkinlikler listesini filtrelemek için:

1.  İçinde **filtre** ekranın sol tarafındaki bölmede aşağıdaki seçeneklerden birini seçin: **tüm**, **açık**, **kapalı**, veya **Gizlenen**.

2.  Daha fazla listeyi filtrelemek için seçin **yüksek**, **orta**, veya **düşük**.

**Kuşkulu etkinliğin önem derecesi**

-   **Düşük**

    Kötü amaçlı kullanıcıların veya yazılımların kuruluş verilerine erişim kazanması için tasarlanmış saldırılara yol açabilecek kuşkulu etkinlikleri gösterir.

-   **Orta**

    Kimlik hırsızlığı veya ayrıcalık yükseltmeyle sonuçlanabilecek daha ciddi saldırılar için belirli kimlikleri riske atabilecek kuşkulu etkinlikleri gösterir.

-   **Yüksek**

    Kimlik hırsızlığı, ayrıcalık yükseltme saldırısı veya diğer etkili saldırılara yol açabilecek kuşkulu etkinlikleri gösterir




## <a name="managing-suspicious-activities"></a>Şüpheli etkinlikleri yönetme
Tıklayarak kuşkulu etkinliğin geçerli durumu ve aşağıdakilerden birini seçerek, kuşkulu bir etkinlik durumunu değiştirebilirsiniz **açık**, **gizlenen**, **kapalı**, veya **silinmiş**.
Bir şüpheli etkinliğin sağ üst köşesindeki üç nokta simgesine tıklayarak ulaşacağınız kullanılabilir eylemler listesinden bunu yapabilirsiniz.

![Şüpheli etkinlikler için Azure ATP eylemleri](./media/atp-sa-actions.png)

**Kuşkulu etkinliğin durumu**

-   **Açık**: Tüm yeni şüpheli etkinlikler bu listede gösterilir.

-   **Kapat**: belirlediğiniz, Araştırdığınız ve azalttığınız kuşkulu etkinlikleri izlemek için kullanılır.

    > [!NOTE]
    > Azure ATP, yeniden bir kısa süre içinde aynı etkinlik algılanırsa, kapalı bir etkinliği yeniden.

-   **Gösterme**: Bir etkinliği göstermemek, etkinliği o an için yoksaymak ve yalnızca yeni bir örnek ortaya çıkarsa uyarı almak istediğiniz anlamına gelir. Başka bir deyişle, benzer bir uyarı Azure ATP ise, yeniden değil. Ancak, bir uyarı yedi gün boyunca durdurur ve sonra tekrar görülürse ise, yeniden uyarılırsınız.

- **Silme**: bir uyarıyı silerseniz uyarı sistemden veritabanından silinir ve geri yüklemek mümkün olmayacaktır. Sil’e tıkladıktan sonra aynı türdeki tüm şüpheli etkinlikleri silebilirsiniz.

- **Dışla**: Bir varlığın belirli bir türdeki uyarıları göndermesini engelleme becerisi. Örneğin, belirli türde bir uzak kod çalıştıran belirli bir yönetici veya DNS keşfi yapan bir güvenlik tarayıcısı gibi şüpheli etkinlik için tekrar uyarmadan gelen belirli bir varlık (kullanıcı veya bilgisayar) dışlamak için Azure ATP ayarlayabilirsiniz. Zaman çizelgesinde algılandığı zaman doğrudan Şüpheli etkinlik üzerinde dışlama yapabileceğiniz gibi, Yapılandırma sayfasında bulunan **Dışlamalar**’a gidip her bir şüpheli etkinlik için dışlanan varlık veya alt ağları (Pass-the-Ticket gibi) el ile ekleyebilir ve kaldırabilirsiniz. 

> [!NOTE]
> Yapılandırma sayfaları yalnızca Azure ATP yöneticileri tarafından değiştirilebilir.


## <a name="see-also"></a>Ayrıca Bkz.

- [Azure ATP çalışma alanı portalıyla çalışma](workspace-portal.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)