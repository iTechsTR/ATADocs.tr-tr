---
title: Azure ATP yanal hareket yolu algılamasını etkinleştirmek için SAM-r'yi Yapılandır | Microsoft Docs
description: Azure ATP yanal hareket yolu algılamasını etkinleştirmek için SAM-r'yi Yapılandır açıklar
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 7/31/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: b09adce3-0fbc-40e3-a53f-31f57fe79ca3
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 34ee1589d59b0740e9d3b05eb117991325619295
ms.sourcegitcommit: b283bf66e63d76e6dba4564a229e804792794c6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47454007"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*

# <a name="install-azure-atp---step-8"></a>Azure ATP - 8. Adım'ı yükleme

> [!div class="step-by-step"]
> [«7. adım](install-atp-step7.md)
> [9. adım»](atp-multi-forest.md)

## <a name="step-8-configure-sam-r-required-permissions"></a>8. Adım SAM-R gerektiren izinleri yapılandırma

[Yanal hareket yolunun](use-case-lateral-movement-path.md) algılama özel makinelerde yerel yönetici tanımlamak sorgularını kullanır. Bu sorgular SAM-R protokolü ile gerçekleştirilir, Azure ATP hizmeti ile hesap içinde oluşturulan [2. adım. AD'ye bağlanma](install-atp-step2.md).
 
Windows emin olmak için istemciler ve sunucular SAM-R, değişiklik gerçekleştirmek Azure ATP hesabınızı izin **Grup İlkesi** listelenen yapılandırılmış hesapların yanı sıra Azure ATP hizmet hesabını eklemek için yapılmalıdır  **Ağ erişimi** ilkesi.

1. İlke bulun:

 - İlke adı: ağ erişimi: SAM uzak çağrı yapmasına izin istemcileri kısıtlama
 - Konum: Bilgisayar yapılandırmasını, Windows ayarlarını, güvenlik ayarları, yerel ilkeler, güvenlik seçenekleri
  
  ![İlkeyi bulma](./media/samr-policy-location.png)

2. Azure ATP hizmeti modern Windows sistemlerinde bu eylemi gerçekleştirmek için onaylanmış hesaplar listesine ekleyin.
 
  ![Hizmet Ekle](./media/samr-add-service.png)

3. **AATP hizmet** (yükleme sırasında oluşturulan Azure ATP hizmeti) artık SAM-R ortamında gerçekleştirmek için gereken ayrıcalıklara sahiptir.

> [!NOTE]
> Yeni ilkeler uygulamadan önce etkinleştirmek ve Denetim modunda önerdiğiniz değişiklikleri doğrulama, uygulama uyumluluğu etkilemeden ortamınızı güvenli kaldığından emin olun.

SAM-R ve bu Grup İlkesi hakkında daha fazla bilgi için bkz. [ağ erişimi: SAM uzak çağrı yapmasına izin istemcileri kısıtlama](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls).


> [!div class="step-by-step"]
> [«7. adım](install-atp-step7.md)
> [9. adım»](atp-multi-forest.md)



## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP ile yanal hareket yolu saldırılarını araştırma](use-case-lateral-movement-path.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)