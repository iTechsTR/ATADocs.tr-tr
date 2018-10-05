---
title: Azure Gelişmiş tehdit koruması sistem durumu ve olaylarını izleme | Microsoft Docs
description: Azure ATP hizmetinin nasıl çalıştığını denetlemek için Azure ATP çalışma sistem durumu Merkezi'ni kullanın ve olası sorunlarda uyarı almak ve olay görüntüleyicisinde sistem olaylarını görüntüleyin.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 1b7e72c3-a538-443f-981c-398ffafa5ab8
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 8fdaa7311d39680ed8e9389f5dc9b7cdeca73197
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48782905"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="working-with-azure-atp-workspace-health-and-events"></a>Azure ATP çalışma durumu ve olayları ile çalışma

## <a name="azure-atp-workspace-health-center"></a>Azure ATP çalışma alanı sistem durumu Merkezi 

Azure ATP çalışma alanı sistem durumu Merkezi, Azure ATP çalışma alanınızı nasıl performans gösterdiğini bilmenizi sağlar ve sorunlar olduğunda sizi uyarır.

## <a name="working-with-the-azure-atp-workspace-health-center"></a>Azure ATP çalışma alanı sistem durumu Merkezi'yle çalışma

Azure ATP çalışma alanı sistem durumu Merkezi, ilgili bir sorun olduğunu menü çubuğunda sistem durumu Merkezi simgesi üzerinde bir uyarı (kırmızı nokta) yükselterek bilmenizi sağlar.

![Azure ATP çalışma alanı sistem durumu merkezi kırmızı nokta araç çubuğu](media/atp-health-bar.png)

### <a name="managing-azure-atp-workspace-health"></a>Azure ATP çalışma alanı sistem durumunu yönetme
Çalışma alanınızın genel durumunu denetlemek için menü çubuğunda sistem durumu merkezi simgesine tıklayın. ![Azure ATP çalışma alanı sistem durumu Merkezi simgesi](media/atp-red-dot.png)

-   Tüm açık sorunları ayarlanarak yönetilebilir **Kapat**, veya **bastır**, uyarı üst köşesindeki üç noktaya tıklayarak ve seçiminizi yapma.

-   **Açık**: Tüm yeni şüpheli etkinlikler bu listede gösterilir.

-   **Kapat**: belirlediğiniz, Araştırdığınız ve azalttığınız kuşkulu etkinlikleri izlemek için kullanılır.

    > [!NOTE]
    > Tekrar bir kısa süre içinde aynı etkinlik algılanırsa azure ATP kapalı bir etkinliği yeniden.
    
-   **Gösterme**: Bir etkinliği göstermemek, etkinliği o an için yoksaymak ve yalnızca yeni bir örnek ortaya çıkarsa uyarı almak istediğiniz anlamına gelir. Azure ATP benzer bir uyarı varsa yeniden değil. Ancak, bir uyarı yedi gün boyunca durdurur ve sonra tekrar görülürse ise, yeniden uyarılırsınız.

-   **Yeniden**: açık görünmesi kapalı veya gizlenen bir sorunu açabilirsiniz zaman çizelgesinde yeniden.

-   **Silme**: gelen kuşkulu etkinlikler zaman çizelgesi içinde bir sistem durumu sorunu silmek için seçeneğiniz de vardır. Bir uyarıyı silerseniz, bu çalışma alanından silinir ve geri yüklemek mümkün olmayacaktır. Sil’e tıkladıktan sonra aynı türdeki tüm şüpheli etkinlikleri silebilirsiniz.



![Azure ATP sistem durumu merkezi sorunları resmi](media/atp-health-issue.png)






## <a name="see-also"></a>Ayrıca Bkz.

- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
