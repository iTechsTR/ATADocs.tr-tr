---
title: Azure Advanced Threat Protection kuşkulu etkinliklerle çalışma | Microsoft Docs
description: Azure ATP tarafından tanımlanan kuşkulu etkinlikleri gözden geçirmek açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/22/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: a06004bd-9f77-4e8e-a0e5-4727d6651a0f
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 1dccee094f4d6a8ec9bdc94a1d1314fa0675da9d
ms.sourcegitcommit: 324dc941282f2948366afa5a919bda0b029bd59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="working-with-suspicious-activities"></a>Kuşkulu Etkinliklerle Çalışma
Bu makalede Azure Gelişmiş tehdit koruması ile çalışmaya nasıl temelleri açıklanır.

## Saldırı zaman çizelgesini kuşkulu etkinlikleri gözden geçirin <a name="review-suspicious-activities-on-the-attack-time-line"></a>
Azure ATP çalışma portalına oturum açtıktan sonra açık olarak otomatik olarak alınır **kuşkulu etkinlikler zaman çizelgesi**. Kuşkulu etkinlikler, en yenileri zaman çizelgesinin en üstünde olacak şekilde kronolojik sırayla listelenir.
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
> -   Bir varlık üzerinde tıklatırsanız, kullanıcı veya bilgisayar varlık profili alır.

![Azure ATP kuşkulu etkinlikler zaman çizelgesinin resmi](media/atp-sa-timeline.png)

## <a name="filter-suspicious-activities-list"></a>Kuşkulu etkinlikler listesini filtreleme
Kuşkulu etkinlikler listesini filtrelemek için:

1.  İçinde **göre filtre** ekranın sol tarafındaki bölmesinde aşağıdaki seçeneklerden birini seçin: **tüm**, **açık**, **kapalı**, veya **Gizlenen**.

2.  Daha fazla listeyi filtrelemek için seçin **yüksek**, **orta**, veya **düşük**.

**Kuşkulu etkinliğin önem derecesi**

-   **Düşük**

    Kötü amaçlı kullanıcıların veya yazılımların kuruluş verilerine erişim kazanması için tasarlanmış saldırılara yol açabilecek kuşkulu etkinlikleri gösterir.

-   **Orta**

    Kimlik hırsızlığı veya ayrıcalık yükseltmeyle sonuçlanabilecek daha ciddi saldırılar için belirli kimlikleri riske atabilecek kuşkulu etkinlikleri gösterir.

-   **Yüksek**

    Kimlik hırsızlığı, ayrıcalık yükseltme veya diğer etkili saldırılara yol açabilecek kuşkulu etkinlikleri gösterir




## <a name="managing-suspicious-activities"></a>Kuşkulu etkinlikleri yönetme
Kuşkulu etkinliğin geçerli durumu tıklatarak ve aşağıdakilerden birini seçerek, kuşkulu etkinliğin durumunu değiştirebilirsiniz **açık**, **Suppressed**, **kapalı**, veya **silinmiş**.
Bir şüpheli etkinliğin sağ üst köşesindeki üç nokta simgesine tıklayarak ulaşacağınız kullanılabilir eylemler listesinden bunu yapabilirsiniz.

![Şüpheli etkinlikler için Azure ATP eylemleri](./media/atp-sa-actions.png)

**Kuşkulu etkinliğin durumu**

-   **Açık**: Tüm yeni şüpheli etkinlikler bu listede gösterilir.

-   **Kapat**: belirlediğiniz, Araştırdığınız ve düzeltip kuşkulu etkinlikleri izlemek için kullanılır.

    > [!NOTE]
    > Aynı etkinlik yeniden bir kısa süre içinde algılanırsa, Azure ATP kapalı bir aktivite yeniden.

-   **Gösterme**: Bir etkinliği göstermemek, etkinliği o an için yoksaymak ve yalnızca yeni bir örnek ortaya çıkarsa uyarı almak istediğiniz anlamına gelir. Başka bir deyişle, benzer bir uyarı Azure ATP ise, yeniden değil. Ancak uyarı yedi gün için durdurur ve daha sonra yeniden görülür, yeniden uyarı.

- **Silme**: uyarı silme sistemden veritabanından silinir ve geri yüklemek mümkün olmaz. Sil’e tıkladıktan sonra aynı türdeki tüm şüpheli etkinlikleri silebilirsiniz.

- **Dışla**: Bir varlığın belirli bir türdeki uyarıları göndermesini engelleme becerisi. Örneğin, belirli türde bir uzaktan kod çalıştıran belirli bir yönetici veya DNS keşfi yapan bir güvenlik tarayıcısı gibi şüpheli etkinlik yeniden uyarı gelen belirli bir varlık (kullanıcı veya bilgisayar) hariç tutulacak Azure ATP ayarlayabilirsiniz. Zaman çizelgesinde algılandığı zaman doğrudan Şüpheli etkinlik üzerinde dışlama yapabileceğiniz gibi, Yapılandırma sayfasında bulunan **Dışlamalar**’a gidip her bir şüpheli etkinlik için dışlanan varlık veya alt ağları (Pass-the-Ticket gibi) el ile ekleyebilir ve kaldırabilirsiniz. 

> [!NOTE]
> Yapılandırma sayfaları yalnızca Azure ATP yöneticiler tarafından değiştirilebilir.


## <a name="see-also"></a>Ayrıca bkz:

- [Azure ATP çalışma alanı portalıyla çalışma](workspace-portal.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)