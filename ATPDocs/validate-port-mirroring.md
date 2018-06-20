---
title: Azure Advanced Threat Protection içinde bağlantı noktası yansıtmayı doğrulama | Microsoft Docs
description: Bağlantı noktası yansıtma Azure ATP düzgün yapılandırılıp yapılandırılmadığını doğrulamak açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 0a56cf27-9eaa-4ad0-ae6c-9d0484c69094
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: b3d9d35d31eee7ae46800e0547f18330d66e90cc
ms.sourcegitcommit: 324dc941282f2948366afa5a919bda0b029bd59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34444612"
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="validate-port-mirroring"></a>Bağlantı Noktası Yansıtmayı Doğrulama
> [!NOTE] 
> Bu makalede yalnızca ilgili dağıtırsanız Azure ATP tek başına algılayıcı Azure ATP algılayıcı yerine dağıtın. Azure ATP algılayıcı kullanmanız gerekip gerekmediğini belirlemek için bkz: [dağıtımınız için doğru algılayıcı seçme](atp-capacity-planning.md#choosing-the-right-sensor-type-for-your-deployment).
 
Aşağıdaki adımlar, bağlantı noktası yansıtmanın düzgün yapılandırıldığını doğrulama işleminde size yol gösterir. Azure ATP'ın düzgün çalışması Azure ATP tek başına algılayıcı etki alanı denetleyicisi gelen ve giden trafiği görüyor olmanız gerekir. Azure ATP tarafından kullanılan ana veri kaynağı, etki alanı denetleyicilerinden gelen ve giden ağ trafiğinin derin paket incelemesi ' dir. Azure ATP'ın ağ trafiğini görebilmesi bağlantı noktası yansıtma yapılandırılması gerekir. Bağlantı noktası yansıtma, bir bağlantı noktasındaki trafiği (kaynak bağlantı noktası) başka bir bağlantı noktasına (hedef bağlantı noktası) kopyalar.

## <a name="validate-port-mirroring-using-net-mon"></a>Net Mon kullanarak bağlantı noktası yansıtmayı doğrulama
1.  Yükleme [Microsoft Network Monitor 3.4](http://www.microsoft.com/download/details.aspx?id=4865) doğrulamak istediğiniz ATP tek başına algılayıcı üzerinde.

    > [!IMPORTANT]
    > Bağlantı noktası yansıtmayı doğrulama için Wireshark yüklemeyi seçerseniz Azure ATP tek başına algılayıcı hizmetini doğrulama sonrasında yeniden başlatın.

2.  Ağ İzleyicisi'ni açın ve yeni bir yakalama sekmesi oluşturun.

    1.  Yalnızca **Yakalama** ağ bağdaştırıcısını veya bağlantı noktası yansıtma hedefi için yapılandırılmış anahtar bağlantı noktasına bağlı ağ bağdaştırıcısını seçin.

    2.  P-Modu’nun etkinleştirildiğinden emin olun.

    3.  **Yeni Yakalama**’ya tıklayın.

        ![Yeni yakalama sekmesi oluşturma resmi](media/atp-port-mirroring-capture.png)

3.  Görüntüleme Filtresi penceresinde **KerberosV5 VEYA LDAP** filtresini girin ve ardından **Uygula**’ya tıklayın.

    ![KerberosV5 veya LDAP filtresini uygulama resmi](media/atp-port-mirroring-filter-settings.png)

4.  Yakalama oturumunu başlatmak için **Başlat**’a tıklayın. Etki alanı denetleyicisinden gelen veya giden trafiği görmüyorsanız, bağlantı noktası yansıtma yapılandırmanızı gözden geçirin.

    ![Yakalama oturumunu başlatma resmi](media/atp-port-mirroring-capture-traffic.png)

    > [!NOTE]
    > Etki alanı denetleyicilerinden gelen ve giden trafiği gördüğünüzden emin olmanız önemlidir.
    

5.  Yalnızca bir yöndeki trafiği görüyorsanız, bağlantı noktası yansıtma yapılandırması gidermenize yardımcı olması için ağ veya sanallaştırma ekipleriniz ile çalışır.

## <a name="see-also"></a>Ayrıca bkz:

- [Olay iletme özelliğini yapılandırma](configure-event-forwarding.md)
- [Bağlantı noktası yansıtmayı yapılandırma](configure-port-mirroring.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
