---
title: Advanced Threat Analytics’te şüpheli etkinliklerle çalışma | Microsoft Docs
description: ATA tarafından belirlenen kuşkulu etkinliklerin nasıl gözden geçirileceğini açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/29/2018
ms.topic: article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 44d7c899-816c-4f7f-91d3-84a09d291a24
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: fdc83443c30db4278ccffde35e070e8b17b423bb
ms.sourcegitcommit: 5c0f914b44bfb8e03485f12658bfa9a7cd3d8bbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*



# <a name="working-with-suspicious-activities"></a>Kuşkulu Etkinliklerle Çalışma
Bu makalede, Advanced Threat Analytics ile çalışmaya nasıl temelleri açıklanır.

## <a name="review-suspicious-activities-on-the-attack-time-line"></a>Saldırı zaman çizelgesinde kuşkulu etkinlikleri gözden geçirme
ATA Konsolu’nda oturum açtıktan sonra, otomatik olarak açık **Kuşkulu Etkinlikler Zaman Çizelgesi**’ne gelirsiniz. Kuşkulu etkinlikler, en yenileri zaman çizelgesinin en üstünde olacak şekilde kronolojik sırayla listelenir.
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

![ATA kuşkulu etkinlikler zaman çizelgesinin resmi](media/ATA-Suspicious-Activity-Timeline.JPG)

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




## <a name="remediating-suspicious-activities"></a>Şüpheli etkinlikleri düzeltme
Kuşkulu etkinliğin geçerli durumu tıklatarak ve aşağıdakilerden birini seçerek, kuşkulu etkinliğin durumunu değiştirebilirsiniz **açık**, **Suppressed**, **kapalı**, veya **silinmiş**.
Bir şüpheli etkinliğin sağ üst köşesindeki üç nokta simgesine tıklayarak ulaşacağınız kullanılabilir eylemler listesinden bunu yapabilirsiniz.

![Şüpheli etkinlikler için ATA Eylemleri](./media/sa-actions.png)

**Kuşkulu etkinliğin durumu**

-   **Açık**: Tüm yeni şüpheli etkinlikler bu listede gösterilir.

-   **Kapat**: belirlediğiniz, Araştırdığınız ve düzeltip kuşkulu etkinlikleri izlemek için kullanılır.

    > [!NOTE]
    > Aynı etkinlik yeniden bir kısa süre içinde algılanırsa, ATA kapalı bir aktivite yeniden.

-   **Gösterme**: Bir etkinliği göstermemek, etkinliği o an için yoksaymak ve yalnızca yeni bir örnek ortaya çıkarsa uyarı almak istediğiniz anlamına gelir. Başka bir deyişle, benzer bir uyarı ATA ise, yeniden değil. Ancak uyarı yedi gün için durdurur ve daha sonra yeniden görülür, yeniden uyarı.

- **Silme**: uyarı silme sistemden veritabanından silinir ve geri yüklemek mümkün olmaz. Sil’e tıkladıktan sonra aynı türdeki tüm şüpheli etkinlikleri silebilirsiniz.

- **Dışla**: Bir varlığın belirli bir türdeki uyarıları göndermesini engelleme becerisi. Örneğin ATA’yı, belirli bir varlığı (kullanıcı veya bilgisayar) dışlamak üzere ayarlayabilirsiniz, böylece uzak kod çalıştıran belirli bir yönetici veya DNS keşfi yapan bir güvenlik tarayıcısı gibi belirli türdeki şüpheli etkinlikler hakkında bu varlıktan tekrar uyarı almazsınız. Zaman çizelgesinde algılandığı zaman doğrudan Şüpheli etkinlik üzerinde dışlama yapabileceğiniz gibi, Yapılandırma sayfasında bulunan **Dışlamalar**’a gidip her bir şüpheli etkinlik için dışlanan varlık veya alt ağları (Pass-the-Ticket gibi) el ile ekleyebilir ve kaldırabilirsiniz. 
> [!NOTE]
> Yapılandırma sayfaları yalnızca ATA yöneticileri tarafından değiştirilebilir.


## <a name="related-videos"></a>İlgili videolar
- [Güvenlik topluluğu birleştirme](https://channel9.msdn.com/Shows/Microsoft-Security/Join-the-Security-Community)


## <a name="see-also"></a>Ayrıca bkz:
- [ATA kuşkulu etkinlik playbook](http://aka.ms/ataplaybook)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [ATA yapılandırmasında değişiklik yapma](modifying-ata-center-configuration.md)
