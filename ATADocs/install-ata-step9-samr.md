---
title: Advanced Threat analytics'te yanal hareket yolu algılamayı etkinleştirmek için SAM-r'yi Yapılandır | Microsoft Docs
description: Yanal hareket yolu algılama Advanced Threat Analytics (ATA) içinde etkinleştirmek için SAM-r'yi Yapılandır açıklar
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 7/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 7597ed25-87f5-472c-a496-d5f205c9c391
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 8a1de6e0f3d5234eb96d710b54ded8c8a894f440
ms.sourcegitcommit: 7f3ded32af35a433d4b407009f87cfa6099f8edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44125746"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*

# <a name="install-ata---step-9"></a>Ata'yı 9. adım yükleme

>[!div class="step-by-step"]
[«8. adım](install-ata-step7.md)

## <a name="step-9-configure-sam-r-required-permissions"></a>9. Adım SAM-R gerektiren izinleri yapılandırma

[Yanal hareket yolunun](use-case-lateral-movement-path.md) algılama özel makinelerde yerel yönetici tanımlamak sorgularını kullanır. Bu sorguları aracılığıyla oluşturulan ATA hizmet hesabı SAM-R protokolünü kullanarak gerçekleştirilir [2. adım. AD'ye bağlanma](install-ata-step2.md).
 
Windows istemcileri ve sunucuları bu SAM-R işlemi, değişiklik gerçekleştirmek ATA hizmeti hesabına izin ver emin olmak için **Grup İlkesi** yapılmalıdır listelenen yapılandırılmış hesapları ek olarak ATA hizmet hesabı ekler içinde **ağ erişimi** ilkesi.

1. İlke bulun:

 - İlke adı: ağ erişimi: SAM uzak çağrı yapmasına izin istemcileri kısıtlama
 - Konum: Bilgisayar yapılandırmasını, Windows ayarlarını, güvenlik ayarları, yerel ilkeler, güvenlik seçenekleri
  
  ![İlkeyi bulma](./media/samr-policy-location.png)

2. ATA hizmetinin modern Windows sistemlerinde bu eylemi gerçekleştirmek için onaylanmış hesaplar listesine ekleyin.
 
  ![Hizmet Ekle](./media/samr-add-service.png)

3. **ATA hizmeti** (yükleme sırasında oluşturulan ATA hizmeti) artık SAM-R ortamında gerçekleştirmek için uygun ayrıcalıklara sahiptir.

> [!NOTE]
> Yeni ilkeler uygulamadan önce etkinleştirmek ve Denetim modunda önerdiğiniz değişiklikleri doğrulama tarafından uygulama uyumluluğu etkilemeden ortamınızı güvenli kaldığından emin olun. 

 SAM-R ve Grup İlkesi hakkında daha fazla bilgi için bkz. [ağ erişimi: SAM uzak çağrı yapmasına izin istemcileri kısıtlama](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls).


>[!div class="step-by-step"]
[«8. adım](install-ata-step7.md)

## <a name="see-also"></a>Ayrıca Bkz.
- [ATA POC Dağıtım Kılavuzu](http://aka.ms/atapoc)
- [ATA boyutlandırma aracı](http://aka.ms/atasizingtool)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)
