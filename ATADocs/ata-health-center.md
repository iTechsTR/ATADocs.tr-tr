---
title: Advanced Threat Analytics Sistem Durumu ve Olaylarını İzleme | Microsoft Docs
description: ATA hizmetinin nasıl çalıştığını denetlemek, olası sorunlarda uyarı almak ve Olay görüntüleyicisinde sistem olaylarını görüntülemek için ATA Sistem Durumu Merkezi’ni kullanın.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: d6c783b2-46c5-4211-b21a-d6b17f08d03d
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 0c8eb2c368a81a64e62f79b9fb606b9fc04efd8b
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
ms.locfileid: "30009794"
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*


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






## <a name="see-also"></a>Ayrıca bkz:

- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
