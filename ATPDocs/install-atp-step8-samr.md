---
title: Azure ATP yanal hareket yolu algılamayı etkinleştirmek için SAM-R yapılandırma | Microsoft Docs
description: Azure ATP yanal hareket yolu algılamayı etkinleştirmek için SAM-R yapılandırmayı açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/29/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: b09adce3-0fbc-40e3-a53f-31f57fe79ca3
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 24b42c5425933d8931a85e0ba454a69e0ca94a21
ms.sourcegitcommit: 5c0f914b44bfb8e03485f12658bfa9a7cd3d8bbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
ms.locfileid: "32298301"
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*

# <a name="install-azure-atp---step-8"></a>Azure ATP - adım 8 yükleme

>[!div class="step-by-step"]
[«Adım 7](install-atp-step7.md)

## <a name="step-8-configure-sam-r-required-permissions"></a>8. Adım SAM-R gerekli izinleri yapılandırma

[Yanal hareket yolu](use-case-lateral-movement-path.md) algılama belirli makinelerde yerel Yöneticiler tanımlamak sorgularını kullanır. Bu sorguları aracılığıyla oluşturulan Azure ATP hizmet hesabı SAM-R protokolü kullanılarak gerçekleştirilen [2. adım. AD'ye bağlanma](install-atp-step2.md).
 
Windows emin olmak için istemciler ve sunucular bu SAM-R işlemi, bir değişiklik yapmak Azure ATP hesabına izin ver **Grup İlkesi** listelenenyapılandırılmışhesaplarıyanısıraAzureATPhizmethesabıeklemekiçinyapılmasıgerekir **Ağ erişimi** ilkesi.

1. İlkesi'ni bulun:

 - İlke adı: ağ erişimi - SAM uzak çağrı yapmak için izin verilen istemciler kısıtla
 - Konumu: Bilgisayar yapılandırma, Windows ayarları, güvenlik ayarları, yerel ilkeler, güvenlik seçenekleri
  
  ![İlkesi'ni bulun](./media/samr-policy-location.png)

2. Azure ATP hizmet modern Windows sistemleriniz üzerinde bu eylemi gerçekleştirmek için onaylanmış hesaplar listesine ekleyin.
 
  ![Hizmet Ekle](./media/samr-add-service.png)

3. **AATP hizmet** (yükleme işlemi sırasında oluşturulan Azure ATP hizmeti) artık ortama yapılan gerçekleştirmek için uygun ayrıcalıklara sahip.

SAM-R ve bu Grup İlkesi hakkında daha fazla bilgi için bkz: [ağ erişimi: SAM uzak çağrı yapmak için izin verilen istemciler kısıtlamak](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls).


>[!div class="step-by-step"]
[«Adım 7](install-atp-step7.md)



## <a name="see-also"></a>Ayrıca bkz:
- [Yanal hareket yolu saldırılarına Azure ATP araştırma](use-case-lateral-movement-path.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)