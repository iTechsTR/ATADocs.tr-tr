---
title: "Advanced Threat Analytics Sistem Durumu Merkezi uyarılarını izleme | Microsoft Docs"
description: "ATA hizmetinin nasıl çalıştığını denetlemek ve olası sorunlarda uyarı almak için ATA Sistem Durumu Merkezi’ni kullanın."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: d6c783b2-46c5-4211-b21a-d6b17f08d03d
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b28cb3a0da844b7c460c03726222bc775a9e47da
ms.openlocfilehash: 25030dd40c7bbd9f036dbf0d228017f571d4ba71


---

*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*



# <a name="ata-health-center"></a>ATA Sistem Durumu Merkezi
ATA Sistem Durumu Merkezi, ATA hizmetinizin nasıl performans gösterdiğini öğrenmenizi sağlar ve sorunlar olduğunda sizi uyarır.

## <a name="working-with-the-ata-health-center"></a>ATA Sistem Durumu Merkezi’yle çalışma
ATA Sistem Durumu Merkezi, menü çubuğundaki Sistem Durum Merkezi’nin üst kısmında bir uyarı (kırmızı nokta) göstererek sorun olduğunu bilmenizi sağlar.

![ATA Sistem Durumu Merkezi kırmızı nokta araç çubuğu](media/ATA-Health-Center-Alert-red-dot.png)

### <a name="managing-ata-health"></a>ATA sistem durumunu yönetme
Sisteminizin bir bütün olarak durumunu denetlemek için, menü çubuğunda Sistem Durumu Merkezi simgesine tıklayın. ![ATA Sistem Durumu Merkezi simgesi](media/ATA-red-dot.png)

-   Tüm açık uyarılar, **Çözüldü** veya **Çıkarıldı** olarak ayarlanarak yönetilebilir. Uyarıda **Açık** seçeneğine tıklayın ve ekranı aşağı kaydırarak **Çözüldü** veya **Çıkarıldı** seçeneğine gelin.

-   Bir sorunu çözerseniz ve ATA sorunun kalıcı olduğunu algılarsa, sorun otomatik olarak **Açık** sorunlar listesine geri taşınır. ATA açık bir sorunun çözüldüğünü algılarsa, sorun otomatik olarak **Çözülen** sorunlar listesine taşınır.

-   **Çıkarılan** sorunlar, ATA’nın denetlemeye devam etmesini istemediğiniz sorunlardır. Örneğin, var olduğunu bildiğiniz ve çözmeyi planlamadığınız bir sorunla ilgili olarak uyarılırsanız ancak bu sorun hakkında bildirim almaya devam etmek ve artık bunu **Açık** sorunlar listesinde görmek istemiyorsanız, sorunu **Çıkarıldı** olarak ayarlayabilirsiniz.

![ATA Sistem Durumu Merkezi sorunlarının resmi](media/ATA-Health-Issue.JPG)

## <a name="see-also"></a>Ayrıca bkz.
- [ATA algılama ayarlarıyla çalışma](working-with-detection-settings.md)
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Feb17_HO1-->


