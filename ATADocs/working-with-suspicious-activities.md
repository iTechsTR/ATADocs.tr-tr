---
title: "Advanced Threat Analytics’te şüpheli etkinliklerle çalışma | Microsoft Docs"
description: "ATA tarafından belirlenen kuşkulu etkinliklerin nasıl gözden geçirileceğini açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 08/28/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 44d7c899-816c-4f7f-91d3-84a09d291a24
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 62ce117423a189a1c2ce00b862f323db6ed328cb
ms.sourcegitcommit: 46dd0e695f16a0dd23bbfa140eba15ea6a34d7af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="working-with-suspicious-activities"></a>Kuşkulu Etkinliklerle Çalışma
Bu konu başlığı altında, Advanced Threat Analytics ile çalışmanın temelleri açıklanır.

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

    -   Kuşkulu etkinliğe bir not ekleme.

    -   Kuşkulu etkinlik için giriş sağlama.

-   Kuşkulu etkinliğin nasıl yanıtlanacağına ilişkin öneriler sağlar.

> [!NOTE]
> -   Farenizi bir kullanıcı veya bilgisayarın üzerine getirdiğinizde, varlık hakkında ek bilgi sağlayan bir varlık mini profili görüntülenir ve varlığın bağlantılı olduğu kuşkulu etkinliklerin sayısını içerir.
> -   Varlığın üzerine tıkladığınızda, kullanıcının veya bilgisayarın varlık profiline gidersiniz.

![ATA kuşkulu etkinlikler zaman çizelgesinin resmi](media/ATA-Suspicious-Activity-Timeline.JPG)

## <a name="filter-suspicious-activities-list"></a>Kuşkulu etkinlikler listesini filtreleme
Kuşkulu etkinlikler listesini filtrelemek için:

1.  İçinde **göre filtre** ekranın sol tarafındaki bölmesinde aşağıdakilerden birini seçin: **tüm**, **açık**, **kapalı**, veya  **Gizlenen**.

2.  Listeyi daha fazla filtrelemek için, **Yüksek**, **Orta** veya **Düşük** ayarını seçin.

**Kuşkulu etkinliğin önem derecesi**

-   **Düşük**

    Kötü amaçlı kullanıcıların veya yazılımların kuruluş verilerine erişim kazanması için tasarlanmış saldırılara yol açabilecek kuşkulu etkinlikleri gösterir.

-   **Orta**

    Kimlik hırsızlığı veya ayrıcalık yükseltmeyle sonuçlanabilecek daha ciddi saldırılar için belirli kimlikleri riske atabilecek kuşkulu etkinlikleri gösterir.

-   **Yüksek**

    Kimlik hırsızlığı, ayrıcalık yükseltme ve diğer etkili saldırılara yol açabilecek kuşkulu etkinlikleri gösterir




## <a name="remediating-suspicious-activities"></a>Şüpheli etkinlikleri düzeltme
Şüpheli etkinliğin geçerli durumuna tıklayıp **Açık**, **Gösterilmeyen**, **Kapalı** veya **Silinmiş** seçeneklerinden birini belirleyerek durumu değiştirebilirsiniz.
Bir şüpheli etkinliğin sağ üst köşesindeki üç nokta simgesine tıklayarak ulaşacağınız kullanılabilir eylemler listesinden bunu yapabilirsiniz.

![Şüpheli etkinlikler için ATA Eylemleri](./media/sa-actions.png)

**Kuşkulu etkinliğin durumu**

-   **Açık**: Tüm yeni şüpheli etkinlikler bu listede gösterilir.

-   **Kapalı**: Belirlediğiniz, araştırdığınız ve düzeltip riskini azalttığınız şüpheli etkinlikleri izlemek için kullanılır.

    > [!NOTE]
    > Aynı etkinlik ise, ATA kapalı bir etkinliği yeniden açabilir yeniden bir kısa süre içinde algılandı.

-   **Gösterme**: Bir etkinliği göstermemek, etkinliği o an için yoksaymak ve yalnızca yeni bir örnek ortaya çıkarsa uyarı almak istediğiniz anlamına gelir. Yani benzer bir uyarı olduğunda ATA bunu tekrardan açmayacaktır. Ancak uyarı 7 gün sonra tekrar görülürse yeniden uyarılırsınız.

- **Sil**: Bir uyarıyı silerseniz uyarı sistemden ve veritabanından silinir ve geri YÜKLEYEMEZSİNİZ. Sil’e tıkladıktan sonra aynı türdeki tüm şüpheli etkinlikleri silebilirsiniz.

- **Dışla**: Bir varlığın belirli bir türdeki uyarıları göndermesini engelleme becerisi. Örneğin ATA’yı, belirli bir varlığı (kullanıcı veya bilgisayar) dışlamak üzere ayarlayabilirsiniz, böylece uzak kod çalıştıran belirli bir yönetici veya DNS keşfi yapan bir güvenlik tarayıcısı gibi belirli türdeki şüpheli etkinlikler hakkında bu varlıktan tekrar uyarı almazsınız. Zaman çizelgesinde algılandığı zaman doğrudan Şüpheli etkinlik üzerinde dışlama yapabileceğiniz gibi, Yapılandırma sayfasında bulunan **Dışlamalar**’a gidip her bir şüpheli etkinlik için dışlanan varlık veya alt ağları (Pass-the-Ticket gibi) el ile ekleyebilir ve kaldırabilirsiniz. 
> [!NOTE]
> Yapılandırma sayfaları yalnızca ATA yöneticileri tarafından değiştirilebilir.


## <a name="related-videos"></a>İlgili videolar
- [Güvenlik topluluğu birleştirme](https://channel9.msdn.com/Shows/Microsoft-Security/Join-the-Security-Community)


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA kuşkulu etkinlik playbook](http://aka.ms/ataplaybook)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [ATA yapılandırmasında değişiklik yapma](modifying-ata-center-configuration.md)
