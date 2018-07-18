---
title: Azure ATP yanal hareket yolu algılamasını etkinleştirmek için SAM-r'yi Yapılandır | Microsoft Docs
description: Azure ATP yanal hareket yolu algılamasını etkinleştirmek için SAM-r'yi Yapılandır açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/17/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: b09adce3-0fbc-40e3-a53f-31f57fe79ca3
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: a529c9751fc993ec0913a54772d46161f39199f6
ms.sourcegitcommit: 8feb9b65dc0e1de0ace00aca11784e54f9852a15
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39098177"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*

# <a name="install-azure-atp---step-8"></a>Azure ATP - 8. Adım'ı yükleme

>[!div class="step-by-step"]
[«7. adım](install-atp-step7.md)
[9. adım»](atp-multi-forest.md)

## <a name="step-8-configure-sam-r-required-permissions"></a>8. Adım SAM-R gerektiren izinleri yapılandırma

[Yanal hareket yolunun](use-case-lateral-movement-path.md) algılama özel makinelerde yerel yönetici tanımlamak sorgularını kullanır. Bu sorguları aracılığıyla oluşturulan Azure ATP hizmet hesabı SAM-R protokolünü kullanarak gerçekleştirilir [2. adım. AD'ye bağlanma](install-atp-step2.md).
 
Windows emin olmak için istemciler ve sunucular için bir değişiklik bu SAM-R işlemi gerçekleştirmek Azure ATP hesabına izin ver **Grup İlkesi** içindelistelenenyapılandırılanhesaplaryanısıraAzureATPhizmethesabınıeklemekiçinyapılmasıgerekir **Ağ erişimi** ilkesi.

1. İlke bulun:

 - İlke adı: ağ erişimi: SAM uzak çağrı yapmasına izin istemcileri kısıtlama
 - Konum: Bilgisayar yapılandırmasını, Windows ayarlarını, güvenlik ayarları, yerel ilkeler, güvenlik seçenekleri
  
  ![İlkeyi bulma](./media/samr-policy-location.png)

2. Azure ATP hizmeti modern Windows sistemlerinde bu eylemi gerçekleştirmek için onaylanmış hesaplar listesine ekleyin.
 
  ![Hizmet Ekle](./media/samr-add-service.png)

3. **AATP hizmet** (yükleme sırasında oluşturulan Azure ATP hizmeti) artık SAMR ortamda gerçekleştirmek için uygun ayrıcalıklara sahiptir.

SAM-R ve bu Grup İlkesi hakkında daha fazla bilgi için bkz. [ağ erişimi: SAM uzak çağrı yapmasına izin istemcileri kısıtlama](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls).


>[!div class="step-by-step"]
[«7. adım](install-atp-step7.md)
[9. adım»](atp-multi-forest.md)



## <a name="see-also"></a>Ayrıca bkz:
- [Azure ATP ile yanal hareket yolu saldırılarını araştırma](use-case-lateral-movement-path.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)