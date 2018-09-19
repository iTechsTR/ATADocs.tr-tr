---
title: Advanced Threat Analytics Sistem Durumu ve Olaylarını İzleme | Microsoft Docs
description: ATA hizmetinin nasıl çalıştığını denetlemek, olası sorunlarda uyarı almak ve Olay görüntüleyicisinde sistem olaylarını görüntülemek için ATA Sistem Durumu Merkezi’ni kullanın.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: d6c783b2-46c5-4211-b21a-d6b17f08d03d
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 12d1a3f10cc3b9d99a20a2562ae4f81425ec9578
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133503"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*


# <a name="working-with-ata-system-health-and-events"></a>ATA sistem durumu ve olayları ile çalışma

## <a name="ata-health-center"></a>ATA Sistem Durumu Merkezi
ATA Sistem Durumu Merkezi, ATA hizmetinizin nasıl performans gösterdiğini öğrenmenizi sağlar ve sorunlar olduğunda sizi uyarır.

## <a name="working-with-the-ata-health-center"></a>ATA Sistem Durumu Merkezi’yle çalışma
ATA Sistem Durumu Merkezi, menü çubuğundaki Sistem Durum Merkezi’nin üst kısmında bir uyarı (kırmızı nokta) göstererek sorun olduğunu bilmenizi sağlar.

![ATA Sistem Durumu Merkezi kırmızı nokta araç çubuğu](media/ATA-Health-Center-Alert-red-dot.png)

### <a name="managing-ata-health"></a>ATA sistem durumunu yönetme
Sisteminizin bir bütün olarak durumunu denetlemek için, menü çubuğunda Sistem Durumu Merkezi simgesine tıklayın. ![ATA Sistem Durumu Merkezi simgesi](media/ATA-red-dot.png)

-   Tüm açık uyarılar ayarlanarak yönetilebilir **Kapat**, **bastır**, veya **Sil** uyarı üst köşesindeki üç noktaya tıklayarak ve seçiminizi yapma.

-   **Açık**: Tüm yeni şüpheli etkinlikler bu listede gösterilir.

-   **Kapat**: belirlediğiniz, Araştırdığınız ve azalttığınız kuşkulu etkinlikleri izlemek için kullanılır.

    > [!NOTE]
    > Tekrar bir kısa süre içinde aynı etkinlik algılanırsa, ATA kapalı bir etkinlik yeniden.

-   **Gösterme**: Bir etkinliği göstermemek, etkinliği o an için yoksaymak ve yalnızca yeni bir örnek ortaya çıkarsa uyarı almak istediğiniz anlamına gelir. Benzer bir uyarı ATA ise yeniden değil. Ancak, bir uyarı yedi gün boyunca durdurur ve sonra tekrar görülürse ise, yeniden uyarılırsınız.

- **Silme**: bir uyarıyı silerseniz uyarı sistemden veritabanından silinir ve geri yüklemek mümkün olmayacaktır. Sil’e tıkladıktan sonra aynı türdeki tüm şüpheli etkinlikleri silebilirsiniz.



![ATA Sistem Durumu Merkezi sorunlarının resmi](media/ATA-Health-Issue.JPG)






## <a name="see-also"></a>Ayrıca Bkz.

- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
