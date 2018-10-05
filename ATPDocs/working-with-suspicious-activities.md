---
title: Azure Gelişmiş tehdit koruması uyarıları güvenlik ile çalışma | Microsoft Docs
description: Azure ATP tarafından verilen güvenlik uyarıları gözden açıklar
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: a06004bd-9f77-4e8e-a0e5-4727d6651a0f
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 72ed08a941b5927599aa39b196634ffc21ac6395
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48783823"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="working-with-security-alerts"></a>Güvenlik Uyarıları ile çalışma
Bu makalede, Azure Gelişmiş tehdit koruması ile çalışmaya ilişkin temel bilgileri açıklar.

## Güvenlik uyarılarını saldırı zaman çizelgesini gözden geçirin <a name="review-suspicious-activities-on-the-attack-time-line"></a>
Azure ATP portalında oturum açtıktan sonra açık olarak otomatik olarak alınır **güvenlik uyarıları zaman çizelgesi**. Güvenlik Uyarıları yenileri zaman çizelgesinin en yeni uyarı şekilde kronolojik sırayla listelenir.
Her güvenlik uyarısı, aşağıdaki bilgileri içerir:

-   Katılan varlıklar; örneğin kullanıcılar, bilgisayarlar, sunucular, etki alanı denetleyicileri ve kaynaklar.

-   Ve güvenlik uyarısı başlatılan şüpheli etkinlik zaman çerçevesi.

-   Uyarının önem derecesi: yüksek, Orta veya düşük.

-   Durum: Açık, kapalı veya baskılanmış.

-   Yapılabilecekler

    -   Güvenlik Uyarısı, e-postayla kuruluşunuzdaki diğer kişilerle paylaşın.

    -   Güvenlik Uyarısı Excel'e aktarma.

> [!NOTE]
> -   Farenizi bir kullanıcı veya bilgisayarın üzerine getirdiğinizde, varlık hakkında ek bilgi sağlar ve varlığın bağlantılı olduğu güvenlik uyarıları sayısını içeren bir varlık Mini profili görüntülenir.
> -   Varlığın üzerine tıkladığınızda, kullanıcının veya bilgisayarın varlık profiline alır.

![Azure ATP güvenlik uyarıları zaman çizelgesinin resmi](media/atp-sa-timeline.png)

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


## <a name="filter-security-alerts-list"></a>Güvenlik Uyarıları listesi filtreleme
Güvenlik Uyarısı listesini filtrelemek için:

1.  İçinde **filtre** ekranın sol tarafındaki bölmede aşağıdaki seçeneklerden birini seçin: **tüm**, **açık**, **kapalı**, veya **Gizlenen**.

2.  Daha fazla listeyi filtrelemek için seçin **yüksek**, **orta**, veya **düşük**.

**Kuşkulu etkinliğin önem derecesi**

-   **Düşük**

    Kötü amaçlı kullanıcıların veya yazılımların kuruluş verilerine erişim kazanmak için tasarlanmış saldırılara yol açabilecek etkinlikleri gösterir.

-   **Orta**

    Risk kimlik hırsızlığı veya ayrıcalık yükseltmeyle sonuçlanabilecek daha ciddi saldırılar için belirli kimlikleri riske atabilir etkinlikleri gösterir

-   **Yüksek**

    Kimlik hırsızlığı, ayrıcalık yükseltme saldırısı veya diğer etkili saldırılara yol açabilecek etkinlikleri gösterir


## <a name="managing-security-alerts"></a>Güvenlik uyarılarını yönetme
Güvenlik Uyarısı geçerli durumuna tıklayıp ve aşağıdakilerden birini seçerek bir güvenlik uyarısı durumunu değiştirebilirsiniz **açık**, **gizlenen**, **kapalı**, veya **Silinmiş**.
Bunu yapmak için kullanılabilir eylemler listesinden açığa çıkarmak için belirli bir uyarı sağ üst köşesindeki üç noktaya tıklayın.

![Azure ATP eylemleri için güvenlik uyarıları](./media/atp-sa-actions.png)

**Güvenlik uyarı durumu**

-   **Açık**: tüm yeni güvenlik uyarılarını bu listede görünür.

-   **Kapat**: belirlediğiniz, Araştırdığınız ve azalttığınız güvenlik uyarıları izlemek için kullanılır.

    > [!NOTE]
    > Azure ATP, yeniden bir kısa süre içinde aynı etkinlik algılanırsa, kapatılan bir uyarıyı yeniden.

-   **Bastır**: bir aalert gizleme o an için yoksaymak ve yeni bir örneği ise yalnızca uyarı almak istediğiniz anlamına gelir. Başka bir deyişle, benzer bir uyarı Azure ATP ise, yeniden değil. Ancak, bir uyarı yedi gün boyunca durdurur ve sonra tekrar görülürse ise, yeniden uyarılırsınız.

- **Silme**: bir uyarıyı silerseniz uyarı sistemden veritabanından silinir ve geri yüklemek mümkün olmayacaktır. Sil'e tıkladıktan sonra aynı türdeki tüm güvenlik uyarıları silmek mümkün olacaktır.

- **Dışla**: Bir varlığın belirli bir türdeki uyarıları göndermesini engelleme becerisi. Örneğin, belirli türde bir uzak kod çalıştıran belirli bir yönetici veya DNS keşfi yapan bir güvenlik tarayıcısı gibi bir etkinlik için tekrar uyarmadan gelen belirli bir varlık (kullanıcı veya bilgisayar) dışlamak için Azure ATP ayarlayabilirsiniz. Zaman çizelgesinde algılandığı dışlamaları doğrudan güvenlik uyarısında ekleyebilmek için olmasının yanı sıra, ayrıca yapılandırma sayfasına giderek **dışlamaları**ve her güvenlik uyarısı el ile eklemek ve çıkarılan kaldırmak için varlık veya alt ağları (örneğin Pass--Ticket). 

> [!NOTE]
> Yapılandırma sayfaları yalnızca Azure ATP yöneticileri tarafından değiştirilebilir.


## <a name="see-also"></a>Ayrıca Bkz.

- [Azure ATP çalışma alanı portalıyla çalışma](workspace-portal.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)