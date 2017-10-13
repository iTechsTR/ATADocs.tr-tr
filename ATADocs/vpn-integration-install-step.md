---
title: "Advanced Threat Analytics’i yükleme - 7. Adım | Microsoft Docs"
description: "Ata'yı yükleme Bu adımda, VPN tümleştirin."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/9/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: e0aed853-ba52-46e1-9c55-b336271a68e7
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: c02649a6acb6a083145ba81b3b9c1647e7f8ea2a
ms.sourcegitcommit: e9f2bfd610b7354ea3fef749275f16819d60c186
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="install-ata---step-7"></a>ATA’yı Yükleme - 7. Adım

>[!div class="step-by-step"]
[«5. adım](install-ata-step5.md)
[8. adım»](install-ata-step7.md)

## <a name="step-7-integrate-vpn"></a>7. Adım VPN tümleştirme

### <a name="configuring-vpn"></a>VPN’i yapılandırma

ATA hangi bilgisayarların konumlardan ağ ve anormal VPN bağlantıları algılayabilir bağlanmasını profili yardımcı olan VPN verileri toplar.

ATA VPN verileri yapılandırmak için:

1. Git **yapılandırma** ve ardından **VPN** sekmesi.

2. Girin **hesap paylaşılan gizliliği** RADIUS sunucunuzun. Paylaşılan gizliliği almak için VPN belgelerinize bakın.

 ![ATA VPN bağlantısını yapılandırma](media/vpn.png)

3.  Bu etkinleştirildikten sonra tüm ATA Gateway ve Lightweight Gateway RADIUS hesaplama olayları 1813 numaralı bağlantı noktasında dinler. 

4.  Bu yapılandırıldıktan sonra VPN'nin RADIUS hesap olaylarını herhangi bir ATA Gateway veya ATA Lightweight Gateway iletilen.

5.  ATA Gateway VPN olaylarını alır ve ATA Center işleme için gönderir sonra ATA Center HTTPS bağlantı noktası 443 VPN olayları dış IP adresleriyle bunların coğrafi konuma çözümleyebilmesi için Internet bağlantısı gerekir.

Dış IP adresini bir konuma çözümlemek için anonim çağrıdır. Hiçbir kişisel tanımlayıcı bu çağrısında gönderilir.

Desteklenen VPN satıcıları şunlardır:
- Microsoft
- F5
- Check Point
- Cisco ASA




>[!div class="step-by-step"]
[«6. Adım](install-ata-step5.md)
[8. Adım»](install-ata-step7.md)



## <a name="related-videos"></a>İlgili videolar
- [ATA dağıtımına genel bakış](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)
- [ATA Gateway türü sağ seçme](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA POC Dağıtım Kılavuzu](http://aka.ms/atapoc)
- [ATA boyutlandırma aracı](http://aka.ms/atasizingtool)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)

