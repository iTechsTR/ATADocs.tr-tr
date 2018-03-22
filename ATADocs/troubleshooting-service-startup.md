---
title: "Advanced Threat Analytics hizmeti başlatma sorunlarını giderme | Microsoft Docs"
description: "ATA başlatma sorunları nasıl giderebileceğinizi açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 5a65285c-d1de-4025-9bb4-ef9c20b13cfa
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 87d3f1de8167c1198e6b334826f90df83cc96780
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*



# <a name="troubleshooting-service-startup"></a>Hizmet başlatma sorunlarını giderme

## <a name="troubleshooting-ata-center-service-startup"></a>ATA Center hizmet başlatma sorunlarını giderme

ATA Center bileşeninizin başlamazsa, aşağıdaki sorun giderme yordamı uygulayın:

1.  Aşağıdaki Windows PowerShell komutunu çalıştırın: `Get-Service Pla | Select Status` performans sayacı hizmetinin çalıştığından emin olmak için. Çalışmıyorsa bu bir platform sorunudur ve bu hizmeti yeniden çalışır hale getirmeniz gerekir.
2.  Çalışıyorsa, yeniden başlatmak ve sorunu çözdüğünü görmek deneyin: `Restart-Service Pla`
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

## <a name="troubleshooting-ata-lightweight-gateway-startup"></a>ATA Lightweight Gateway başlatma sorunlarını giderme

**Belirti**

ATA Gateway başlatılmaz ve bu hatayı alırsınız:<br></br>
*System.Net.Http.HttpRequestException: Response status code does not indicate success: 500 (Internal Server Error)*

**Açıklama**

Basit Ağ Geçidi yükleme işleminin bir parçası olarak, ATA Lightweight Gateway CPU % 15 arabellekle kullanmasına izin verir CPU eşiği ayırdığından meydana gelir. Kayıt defteri anahtarını kullanarak bir eşik bağımsız olarak ayarladıysanız: Bu çakışma Lightweight Gateway başlamasını engeller. 

**Çözümleme**

1. Kayıt defteri altında DWORD değerini ise, anahtar adı verilen **performans sayaçları devre dışı** ayarlanmış olmasına dikkat edin **0**:  `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\PerfOS\Performance\` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\PerfProc\Performance`
 
2. Pla hizmetini durdurup yeniden başlatın. ATA Lightweight Gateway otomatik olarak değişikliği algılar ve hizmeti yeniden başlatın.


## <a name="see-also"></a>Ayrıca bkz:
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
