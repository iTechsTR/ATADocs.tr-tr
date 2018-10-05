---
title: Günlükleri kullanarak Azure Gelişmiş tehdit koruması sorunlarını giderme | Microsoft Docs
description: Sorunları gidermek için Azure ATP günlüklerini nasıl kullanabileceğiniz açıklanır
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: de796346-647d-48e1-970a-8f072e990f1e
ms.reviewer: ''
ms.suite: ''
ms.openlocfilehash: 2cd1d7b070818044e74838178b0fab5838ab46ef
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48783262"
---
*İçin geçerlidir: Gelişmiş tehdit koruması*



# <a name="troubleshooting-azure-advanced-threat-protection-atp-sensor-using-the-atp-logs"></a>ATP günlükleri kullanarak sorun giderme Azure Gelişmiş tehdit Koruması (ATP) algılayıcı
ATP günlükleri, hangi Azure ATP algılayıcısını'nın her bileşeninin belirli bir anda neler yaptığı konusunda fikir sağlar.


Azure ATP günlükler adlı alt klasörde bulunan **günlükleri** nerede ATP yüklenir; varsayılan konum: **C:\Program Files\Azure Gelişmiş tehdit koruması algılayıcı\\**. Varsayılan yükleme konumunda, şu anda bulunabilir: **C:\Program Files\Azure Gelişmiş tehdit koruması Sensor\version number\Logs**.

Azure ATP algılayıcısını günlükleri şunlardır:

-   **Microsoft.Tri.Sensor.log** – bu günlük (Çözüm ve hatalar dahil olmak üzere) Azure ATP algılayıcısını gerçekleşen her şeyi içerir. Ana kullanım alanı, gerçekleşen tüm işlemlerin tarih sırasına göre genel durumunu elde etmektir.

-   **Microsoft.Tri.Sensor-Resolution.log** – bu günlük ATP algılayıcı tarafından trafikte görülen varlıkların çözüm ayrıntılarını içerir. Ana kullanım alanı, varlıkların çözüm sorunlarını incelemektir.

-   **Microsoft.Tri.Sensor-Errors.log** – bu günlük yalnızca ATP algılayıcı tarafından yakalanan hataları içerir. Ana kullanım alanı, sistem durumu denetimleri yapmak ve belirli zamanlarla ilintili olması gereken sorunları incelemektir.

-   **Microsoft.Tri.Sensor.Updater.log** -bu günlük, otomatik olarak bunu yapmak için yapılandırılmışsa ATP algılayıcısını güncelleştirmekten sorumlu algılayıcı güncelleştiricisi işlemi için kullanılır. 


> [!NOTE]
> İlk üç günlük dosyasının boyut üst sınırı 50 MB’dir. Bu boyuta ulaşıldığında, yeni günlük dosyası açılır ve önceki dosya "&lt;özgün dosya adı&gt;-Arşivlendi-00000" olarak yeniden adlandırılır; buradaki sayı her yeniden adlandırmada artar. Aynı türden 10’dan fazla dosya zaten varsa, varsayılan olarak en eskisi silinir.

## <a name="azure-atp-deployment-logs"></a>Azure ATP dağıtım günlükleri
Azure ATP dağıtım günlükleri ürünü yükleyen kullanıcının temp dizininde yer alır. Varsayılan yükleme konumunda, şu yolda bulunabilir: **C:\Users\Administrator\AppData\Local\Temp** (veya %temp% dizininden bir dizin yukarıda).

Azure ATP algılayıcı dağıtım günlükleri:

-   **Azure Gelişmiş tehdit koruması Sensor_YYYYMMDDHHMMSS.log** -bu günlük dağıtım Azure ATP algılayıcısını sürecindeki adımları listeler. Ana kullanım Azure ATP algılayıcı dağıtım işlemini izlemektir.

-   **Azure Gelişmiş tehdit koruması Sensor_YYYYMMDDHHMMSS_001_MsiPackage.log** -bu günlük dosyası Azure ATP algılayıcısı ikili dosyalarının dağıtım sürecindeki adımları listeler. Ana kullanım Azure ATP algılayıcısı ikili dosyalarının dağıtımını izlemektir.


> [!NOTE] 
> Burada adı geçen dağıtım günlüklerine ek olarak, "Azure Gelişmiş tehdit koruması ile" ile başlayan diğer günlükler vardır, ayrıca sağlayabilir ek bilgi ve dağıtım süreciyle ilgili.


## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)