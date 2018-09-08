---
title: Advanced Threat Analytics’i Yükleme - 3. Adım | Microsoft Docs
description: ATA yükleme işleminin üçüncü adımı, ATA Gateway kurulum paketini indirmenize yardımcı olur.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 7fb024e6-297a-4ad9-b962-481bb75a0ba3
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: f48360b1760ecdd9be8565f869af50bc83d7add8
ms.sourcegitcommit: 7f3ded32af35a433d4b407009f87cfa6099f8edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44126255"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="install-ata---step-3"></a>ATA’yı Yükleme - 3. Adım

>[!div class="step-by-step"]
[« 2. Adım](install-ata-step2.md)
[4. Adım »](install-ata-step4.md)

## <a name="step-3-download-the-ata-gateway-setup-package"></a>3. Adım. ATA Gateway kurulum paketini indirme
Etki alanı bağlantı ayarlarını yapılandırdıktan sonra, ATA Gateway kurulum paketini indirebilirsiniz. ATA Gateway ayrılmış bir sunucuya veya bir etki alanı denetleyicisine yüklenebilir. Bir etki alanı denetleyicisine yüklerseniz, bir ATA Lightweight Gateway yüklenir. ATA Lightweight Gateway hakkında daha fazla bilgi için bkz. [ATA Mimarisi](ata-architecture.md). 

Tıklayın **ağ geçidi kurulumunu indir** gitmek için sayfanın üst kısmındaki adımları listesinde **ağ geçitleri** sayfası.

![ATA Gateway yapılandırma ayarları](media/ATA_1.7-welcome-download-gateway.PNG)

> [!NOTE] 
> Ağ Geçidi yapılandırma ekranına daha sonra ulaşmak için sağ üst köşedeki **ayarlar simgesine** tıklayıp **Yapılandırma**’yı seçin ve sonra **Sistem**’in altında bulunan **Ağ Geçitleri**’ne tıklayın.  

1.  **Ağ Geçidi Kurulumu**’na tıklayın.
  ![ATA Gateway Kurulumunu indirme](media/download-gateway-setup.png)
2.  Paketi yerel olarak kaydedin.
3.  Paketi, ATA Gateway yükleyeceğiniz ayrılmış sunucuya veya etki alanı denetleyicisine kopyalayın. Alternatif olarak, ATA Konsolu’nu ayrılmış sunucudan veya etki alanı denetleyicisinden açabilir ve bu adımı atlayabilirsiniz.

Zip dosyası aşağıdaki dosyaları içerir:

-   ATA Gateway yükleyicisi

-   ATA Center’a bağlanmak için gereken bilgilerin bulunduğu yapılandırma ayarı dosyası


>[!div class="step-by-step"]
[« 2. Adım](install-ata-step2.md)
[4. Adım »](install-ata-step4.md)


## <a name="related-videos"></a>İlgili videolar
- [ATA dağıtımı genel bakış](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)
- [ATA Gateway türü sağ seçme](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)

## <a name="see-also"></a>Ayrıca Bkz.
- [ATA POC Dağıtım Kılavuzu](http://aka.ms/atapoc)
- [ATA boyutlandırma aracı](http://aka.ms/atasizingtool)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)
