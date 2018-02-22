---
title: "Azure Gelişmiş tehdit koruması sistem durumu ve olayları izleyen | Microsoft Docs"
description: "Azure ATP hizmeti nasıl çalıştığını denetlemek için Azure ATP çalışma durumu Merkezi'ni kullanın ve olası sorunlarda uyarı almak ve Olay Görüntüleyicisi'nde sistem olayları görüntüleyin."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 1b7e72c3-a538-443f-981c-398ffafa5ab8
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 86eb90f452d5aee2504e525e64bfc62c22207880
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*


# <a name="working-with-azure-atp-workspace-health-and-events"></a>Azure ATP çalışma durumu ve olaylar ile çalışma

## <a name="azure-atp-workspace-health-center"></a>Azure ATP çalışma sistem durumu Merkezi 

Azure ATP çalışma sistem durumu Merkezi, Azure ATP çalışma alanınızı nasıl gerçekleştirmekte bilmenizi sağlar ve ilgili sorun olduğunda size verir.

## <a name="working-with-the-azure-atp-workspace-health-center"></a>Azure ATP çalışma sistem durumu Merkezi'yle çalışma

Azure ATP çalışma sistem durumu Merkezi, bir sorun olduğunu menü çubuğunda sistem durumu Merkezi simgesi üzerinde bir uyarı (kırmızı nokta) yükselterek bilmenizi sağlar.

![Azure ATP çalışma sistem durumu merkezi kırmızı nokta araç çubuğu](media/atp-health-bar.png)

### <a name="managing-azure-atp-workspace-health"></a>Azure ATP çalışma durumu yönetme
Çalışma alanınızı ait genel durumunu denetlemek için menü çubuğunda sistem durumu merkezi simgesine tıklayın ![Azure ATP çalışma sistem durumu Merkezi simgesi](media/atp-red-dot.png)

-   Tüm açık sorunlar ayarlanarak yönetilebilir **Kapat**, veya **bastır**, üç noktaya uyarı köşesindeki tıklatıp seçiminizden.

-   **Açık**: Tüm yeni şüpheli etkinlikler bu listede gösterilir.

-   **Kapat**: belirlediğiniz, Araştırdığınız ve düzeltip kuşkulu etkinlikleri izlemek için kullanılır.

    > [!NOTE]
    > Aynı etkinlik yeniden bir kısa süre içinde algılanırsa, azure ATP kapalı bir aktivite yeniden.
    > Her çalışma kendi sistem durumu merkezi sahiptir.

-   **Gösterme**: Bir etkinliği göstermemek, etkinliği o an için yoksaymak ve yalnızca yeni bir örnek ortaya çıkarsa uyarı almak istediğiniz anlamına gelir. Benzer bir uyarı varsa Azure ATP onu yeniden değil. Ancak uyarı yedi gün için durdurur ve daha sonra yeniden görülür, yeniden uyarı.

-   **Yeniden**: kapatın veya bir sorunu bastırmak, böylece açık görünür belgeyi yeniden açabilirsiniz yeniden çizelgesinde.
- 
- **Silme**: kuşkulu etkinlikler zaman çizelgesi içinde aynı zamanda bir sistem sorunu silmeye yönelik seçeneği vardır. Bir uyarı silerseniz, çalışma alanından silinir ve geri yüklemek mümkün olmaz. Sil’e tıkladıktan sonra aynı türdeki tüm şüpheli etkinlikleri silebilirsiniz.



![Azure ATP çalışma sistem durumu merkezi sorunları resmi](media/atp-health-issue.png)






## <a name="see-also"></a>Ayrıca bkz:

- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
