---
title: "Günlükleri kullanarak Advanced Threat Analytics sorunlarını giderme | Microsoft Docs"
description: "Sorunları gidermek için ATA günlüklerini nasıl kullanabileceğiniz açıklanır"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/7/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 5a65285c-d1de-4025-9bb4-ef9c20b13cfa
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 125376b1e3530481a3b9f62c4661dd10dce13f22
ms.sourcegitcommit: 4d2ac5b02c682840703edb0661be09055d57d728
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="troubleshooting-ata-center-service-startup"></a>ATA Center hizmet başlatma sorunlarını giderme

ATA Center bileşeninizin başlamazsa, aşağıdaki sorun giderme yordamı uygulayın:

1.  Aşağıdaki Windows PowerShell komutunu çalıştırın: `Get-Service Pla | Select Status` performans sayacı hizmetinin çalıştığından emin olmak için. Çalışmıyorsa bu bir platform sorunudur ve bu hizmeti yeniden çalışır hale getirmeniz gerekir.
2.  Çalışıyorsa, yeniden başlatmak ve sorunu çözdüğünü görmek deneyin:`Restart-Service Pla`
3.  El ile yeni bir veri toplayıcı oluşturmayı deneyin (herhangi biri yeterli olacaktır, örneğin bir toplama makinesi CPU’su bile).
Başlatmak için büyük olasılıkla daha iyi bir platformdur. Aksi durumda, hala bir platform sorunu olduğunu.

4.  Bu komutlar çalıştırıldığında yükseltilmiş bir istemi kullanarak ATA Veri Toplayıcı, el ile yeniden deneyin:

        sc stop ATACenter
        logman stop "Microsoft ATA Center"
        logman export "Microsoft ATA Center" -xml c:\center.xml
        logman delete "Microsoft ATA Center"
        logman import "Microsoft ATA Center" -xml c:\center.xml
        logman start "Microsoft ATA Center"
        sc start ATACenter



## <a name="see-also"></a>Ayrıca Bkz.
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
