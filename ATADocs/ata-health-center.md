---
title: "Advanced Threat Analytics Sistem Durumu ve Olaylarını İzleme | Microsoft Docs"
description: "ATA hizmetinin nasıl çalıştığını denetlemek, olası sorunlarda uyarı almak ve Olay görüntüleyicisinde sistem olaylarını görüntülemek için ATA Sistem Durumu Merkezi’ni kullanın."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/7/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: d6c783b2-46c5-4211-b21a-d6b17f08d03d
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: e5009d126f3c1b9d73f064787049068b071c5319
ms.sourcegitcommit: 4d2ac5b02c682840703edb0661be09055d57d728
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*


# <a name="working-with-ata-system-health-and-events"></a>ATA sistem durumu ve olayları ile çalışma

## <a name="ata-health-center"></a>ATA Sistem Durumu Merkezi
ATA Sistem Durumu Merkezi, ATA hizmetinizin nasıl performans gösterdiğini öğrenmenizi sağlar ve sorunlar olduğunda sizi uyarır.

## <a name="working-with-the-ata-health-center"></a>ATA Sistem Durumu Merkezi’yle çalışma
ATA Sistem Durumu Merkezi, menü çubuğundaki Sistem Durum Merkezi’nin üst kısmında bir uyarı (kırmızı nokta) göstererek sorun olduğunu bilmenizi sağlar.

![ATA Sistem Durumu Merkezi kırmızı nokta araç çubuğu](media/ATA-Health-Center-Alert-red-dot.png)

### <a name="managing-ata-health"></a>ATA sistem durumunu yönetme
Sisteminizin bir bütün olarak durumunu denetlemek için, menü çubuğunda Sistem Durumu Merkezi simgesine tıklayın. ![ATA Sistem Durumu Merkezi simgesi](media/ATA-red-dot.png)

-   Tüm açık uyarılar ayarlanarak yönetilebilir **Kapat**, **bastır**, veya **silmek** uyarı köşesindeki üç noktaya tıklatıp seçiminizden.

-   **Açık**: Tüm yeni şüpheli etkinlikler bu listede gösterilir.

-   **Kapat**: belirlediğiniz, Araştırdığınız ve düzeltip kuşkulu etkinlikleri izlemek için kullanılır.

    > [!NOTE]
    > Aynı etkinlik yeniden bir kısa süre içinde algılanırsa, ATA kapalı bir aktivite yeniden.

-   **Gösterme**: Bir etkinliği göstermemek, etkinliği o an için yoksaymak ve yalnızca yeni bir örnek ortaya çıkarsa uyarı almak istediğiniz anlamına gelir. Benzer bir uyarı ATA ise yeniden değil. Ancak uyarı yedi gün için durdurur ve daha sonra yeniden görülür, yeniden uyarı.

- **Silme**: uyarı silme sistemden veritabanından silinir ve geri yüklemek mümkün olmaz. Sil’e tıkladıktan sonra aynı türdeki tüm şüpheli etkinlikleri silebilirsiniz.



![ATA Sistem Durumu Merkezi sorunlarının resmi](media/ATA-Health-Issue.JPG)






## <a name="see-also"></a>Ayrıca Bkz.

- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
