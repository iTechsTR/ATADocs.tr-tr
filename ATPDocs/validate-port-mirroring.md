---
title: Azure Gelişmiş tehdit koruması bağlantı noktası yansıtmayı doğrulama | Microsoft Docs
description: Bağlantı noktası yansıtma ATA'daki doğru yapılandırılmış olduğunu doğrulamak açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/22/2018
ms.topic: conceptual
ms.service: ''
ms.technology: ''
ms.assetid: 0a56cf27-9eaa-4ad0-ae6c-9d0484c69094
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 15e53ef145b9d7bbbc980730acec6c3b92c1a0fa
ms.sourcegitcommit: e0b9252c770b3a3695af1642b76e3304f3df15d4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46566613"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="validate-port-mirroring"></a>Bağlantı Noktası Yansıtmayı Doğrulama
> [!NOTE] 
> Bu makalede yalnızca ilgili dağıtırsanız Azure ATP algılayıcısını yerine Azure ATP tek başına algılayıcı dağıtın. Azure ATP algılayıcısını kullanmanız gerekip gerekmediğini belirlemek için bkz: [dağıtımınız için doğru algılayıcı seçme](atp-capacity-planning.md#choosing-the-right-sensor-type-for-your-deployment).
 
Aşağıdaki adımlar, bağlantı noktası yansıtmanın düzgün yapılandırıldığını doğrulama işleminde size yol gösterir. Azure ATP'ın düzgün çalışması Azure ATP tek başına algılayıcı etki alanı denetleyicisi gelen ve giden trafiği görebilirsiniz olması gerekir. Azure ATP tarafından kullanılan ana veri kaynağı, etki alanı denetleyicilerinden gelen ve giden ağ trafiğinin derin paket incelemesi ' dir. Azure ATP'ın ağ trafiğini görebilmesi bağlantı noktası yansıtmayı yapılandırmanız gerekir. Bağlantı noktası yansıtma, bir bağlantı noktasındaki trafiği (kaynak bağlantı noktası) başka bir bağlantı noktasına (hedef bağlantı noktası) kopyalar.

## <a name="validate-port-mirroring-using-net-mon"></a>Net Mon kullanarak bağlantı noktası yansıtmayı doğrulama
1.  Yükleme [Microsoft Network Monitor 3.4](http://www.microsoft.com/download/details.aspx?id=4865) doğrulamak istediğiniz ATP tek başına algılayıcı üzerinde.

    > [!IMPORTANT]
    > Azure ATP tek başına algılayıcı hizmeti bağlantı noktası yansıtmayı doğrulama için Wireshark yüklemeyi seçerseniz, sonra doğrulama yeniden başlatın.

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
    

5.  Yalnızca bir yöndeki trafiği görüyorsanız, bağlantı noktası yansıtma yapılandırması gidermeye yardımcı olmak için ağ veya sanallaştırma ekiplerinizle birlikte çalışın.

## <a name="see-also"></a>Ayrıca Bkz.

- [Olay iletme'yi yapılandırma](configure-event-forwarding.md)
- [Bağlantı noktası yansıtmayı yapılandırma](configure-port-mirroring.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
