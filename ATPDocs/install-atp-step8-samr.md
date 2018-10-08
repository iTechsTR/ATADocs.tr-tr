---
title: Azure ATP yanal hareket yolu algılamasını etkinleştirmek için SAM-r'yi Yapılandır | Microsoft Docs
description: SAM uzak çağrı yapmak için Azure ATP yapılandırma açıklanmaktadır
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/07/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: b09adce3-0fbc-40e3-a53f-31f57fe79ca3
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 49372ce2432e90b04e0d10b2e8e102c1b05e9c9a
ms.sourcegitcommit: bbbe808c08ce703a314c82b46aedaae79ab256a3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48848482"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*

# <a name="configure-azure-atp-to-make-remote-calls-to-sam"></a>SAM uzak çağrı yapmak için Azure ATP yapılandırma
[Yanal hareket yolunun](use-case-lateral-movement-path.md) algılama özel makinelerde yerel yönetici tanımlamak sorgularını kullanır. Bu sorgular, Azure ATP yükleme işlemi sırasında oluşturulan Azure ATP hizmeti hesabını kullanarak SAM-R protokolü ile gerçekleştirilen [2. adım. AD'ye bağlanma](install-atp-step2.md).

## <a name="configure-sam-r-required-permissions"></a>SAM-R gerektiren izinleri yapılandırma
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



## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP ile yanal hareket yolu saldırılarını araştırma](use-case-lateral-movement-path.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)