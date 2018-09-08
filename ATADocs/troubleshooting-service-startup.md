---
title: Advanced Threat Analytics Hizmet başlatma sorunlarını giderme | Microsoft Docs
description: Ata'yı başlatma sorunlarını nasıl giderebileceğinizi açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 5a65285c-d1de-4025-9bb4-ef9c20b13cfa
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 637f26736a520def329ba8599c3927079fdf354d
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44165924"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="troubleshooting-service-startup"></a>Hizmet başlatma sorunlarını giderme

## <a name="troubleshooting-ata-center-service-startup"></a>ATA Center hizmet başlatma sorunlarını giderme

ATA Center hizmetiniz başlamıyorsa aşağıdaki sorun giderme yordamını uygulayın:

1.  Aşağıdaki Windows PowerShell komutunu çalıştırın: `Get-Service Pla | Select Status`
    emin olmak için performans sayacı hizmetinin çalışıyor. Çalışmıyorsa bu bir platform sorunudur ve bu hizmeti yeniden çalışır hale getirmeniz gerekir.
2.  Çalışıyorsa, onu yeniden başlatabilir ve sorunun çözülüp çözülmediğine bakın deneyin: `Restart-Service Pla`
3.  El ile yeni bir veri toplayıcı oluşturmayı deneyin (herhangi biri yeterli olacaktır, örneğin bir toplama makinesi CPU’su bile).
Başlatabiliyorsanız, büyük olasılıkla iyi bir platformdur. Aksi durumda, hala bir platform sorunu vardır.

4.  Bu komutları çalıştırdıktan yükseltilmiş bir istek kullanarak ATA veri toplayıcısını el ile yeniden deneyin:

        sc stop ATACenter
        logman stop "Microsoft ATA Center"
        logman export "Microsoft ATA Center" -xml c:\center.xml
        logman delete "Microsoft ATA Center"
        logman import "Microsoft ATA Center" -xml c:\center.xml
        logman start "Microsoft ATA Center"
        sc start ATACenter

## <a name="troubleshooting-ata-lightweight-gateway-startup"></a>ATA Lightweight Gateway başlatma sorunlarını giderme

**Belirti**

ATA geçidinizin başlatılmaz ve bu hatayı alırsınız:<br></br>
*System.Net.Http.HttpRequestException: Yanıt durum kodu başarı anlamına gelmez: 500 (iç sunucu hatası)*

**Açıklama**

Lightweight Gateway yükleme işleminin bir parçası, ATA Lightweight Gateway CPU % 15'bir arabellek ile kullanmak sağlayan bir CPU eşiği ayırdığı için meydana gelir. Kayıt defteri anahtarını kullanarak bir eşik bağımsız olarak ayarladıysanız: Bu çakışma Lightweight Gateway başlatılmasını engelleyecek. 

**Çözümleme**

1. Kayıt defteri anahtarları, bir DWORD değeri ise adlı **performans sayaçları devre dışı** ayarlanmış olduğundan emin olmak **0**: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\PerfOS\Performance\`
    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\PerfProc\Performance`
 
2. Pla hizmetini durdurup yeniden başlatın. ATA Lightweight Gateway otomatik olarak değişikliği algılar ve hizmeti yeniden başlatın.


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
