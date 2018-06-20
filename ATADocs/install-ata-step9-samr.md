---
title: Advanced Threat Analytics yanal hareket yolu algılamayı etkinleştirmek için SAM-R yapılandırma | Microsoft Docs
description: Yanal hareket yolu algılamayı Advanced Threat Analytics (ATA) içinde etkinleştirmek için SAM-R yapılandırmayı açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/25/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 7597ed25-87f5-472c-a496-d5f205c9c391
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 6e32f3ce59b049d0ced68a1330eefca7315bf49d
ms.sourcegitcommit: 5c0f914b44bfb8e03485f12658bfa9a7cd3d8bbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
ms.locfileid: "32298376"
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*

# <a name="install-ata---step-9"></a>Ata'yı - 9. adım yükleme

>[!div class="step-by-step"]
[«8. adım](install-ata-step7.md)

## <a name="step-9-configure-sam-r-required-permissions"></a>9. Adım SAM-R gerekli izinleri yapılandırma

[Yanal hareket yolu](use-case-lateral-movement-path.md) algılama belirli makinelerde yerel Yöneticiler tanımlamak sorgularını kullanır. Bu sorguları aracılığıyla oluşturulan ATA hizmet hesabı SAM-R protokolü kullanılarak gerçekleştirilen [2. adım. AD'ye bağlanma](install-ata-step2.md).
 
Windows istemcileri ve sunucuları bu SAM-R işlemi, bir değişiklik yapmak ATA hizmet hesabı olanak sağlamak için **Grup İlkesi** yapılmalıdır listelenen yapılandırılmış hesapları yanı sıra ATA hizmet hesabı ekler içinde **ağ erişimi** ilkesi.

1. İlkesi'ni bulun:

 - İlke adı: ağ erişimi - SAM uzak çağrı yapmak için izin verilen istemciler kısıtla
 - Konumu: Bilgisayar yapılandırma, Windows ayarları, güvenlik ayarları, yerel ilkeler, güvenlik seçenekleri
  
  ![İlkesi'ni bulun](./media/samr-policy-location.png)

2. ATA hizmeti modern Windows sistemleriniz üzerinde bu eylemi gerçekleştirmek için onaylanmış hesaplar listesine ekleyin.
 
  ![Hizmet Ekle](./media/samr-add-service.png)

3. **ATA hizmeti** (ATA hizmeti yükleme işlemi sırasında oluşturulan) artık ortama yapılan gerçekleştirmek için uygun ayrıcalıklara sahip.

SAM-R ve bu Grup İlkesi hakkında daha fazla bilgi için bkz: [ağ erişimi: SAM uzak çağrı yapmak için izin verilen istemciler kısıtlamak](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls).


>[!div class="step-by-step"]
[«8. adım](install-ata-step7.md)

## <a name="see-also"></a>Ayrıca bkz:
- [ATA POC Dağıtım Kılavuzu](http://aka.ms/atapoc)
- [ATA boyutlandırma aracı](http://aka.ms/atasizingtool)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)
