---
title: "Günlükleri kullanarak Advanced Threat Analytics sorunlarını giderme | Microsoft Docs"
description: "Sorunları gidermek için ATA günlüklerini nasıl kullanabileceğiniz açıklanır"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 5a65285c-d1de-4025-9bb4-ef9c20b13cfa
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 760e03e764ddb502a2b11cdd3a2570b548837dc4
ms.sourcegitcommit: e2cb3af9c1dbb0b75946dc70cc439b19d654541c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="troubleshooting-ata-center-service-startup"></a>ATA Center hizmet başlatma sorunlarını giderme

ATA Center hizmetiniz başlamıyorsa aşağıdaki sorun giderme yordamını uygulayın:

1.  Şu Windows PowerShell komutunu çalıştırarak Performans sayacı hizmetinin çalıştığından emin olun: Get-Service Pla | Select Status. Çalışmıyorsa bu bir platform sorunudur ve bu hizmeti yeniden çalışır hale getirmeniz gerekir.
2.  Çalışıyorsa yeniden başlatmayı deneyin ve sorunun çözülüp çözülmediğine bakın: Restart-Service Pla
3.  El ile yeni bir veri toplayıcı oluşturmayı deneyin (herhangi biri yeterli olacaktır, örneğin bir toplama makinesi CPU’su bile).
Başlayabiliyorsa platformda büyük olasılıkla bir sorun yoktur, başlamıyorsa hala bir platform sorunu vardır.

4.  Yükseltilmiş bir istek kullanarak ve şu komutları çalıştırarak ATA veri toplayıcısını el ile yeniden oluşturmayı deneyin: sc stop ATACenter logman stop "Microsoft ATA Center" logman export "Microsoft ATA Center" -xml c:\center.xml logman delete "Microsoft ATA Center" logman import "Microsoft ATA Center" -xml c:\center.xml logman start "Microsoft ATA Center" sc start ATACenter



## <a name="see-also"></a>Ayrıca Bkz.
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
