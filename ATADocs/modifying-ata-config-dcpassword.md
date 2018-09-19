---
title: Advanced Threat Analytics yapılandırmasını değiştirme - etki alanı bağlantı parolası | Microsoft Docs
description: ATA Gateway’de Etki Alanı Bağlantı Parolası’nın nasıl değiştirileceği açıklanır.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 4a25561b-a5ed-44aa-9b72-366976b3c72a
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 5c84806dd12e516d1d7b61064906ed57bfd6db72
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133285"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="change-ata-configuration---domain-connectivity-password"></a>ATA yapılandırmasını değiştirme - etki alanı bağlantısı parolası



## <a name="change-the-domain-connectivity-password"></a>Etki alanı bağlantı parolasını değiştirme
Etki Alanı Bağlantısı Parolası’nı değiştirirseniz, girdiğiniz parolanın doğru olduğundan emin olun. Yüklü değilse, ATA Gateway hizmeti ATA Gateway bileşenleri üzerinde çalışmayı durdurur.

Bu, ATA Gateway'de gerçekleştiğini şüpheleniyorsanız kuşkulanırsanız Microsoft.Tri.Gateway-Errors.log dosyasında şu hatalar bakın: `The supplied credential is invalid.`

Bunu düzeltmek için, bu yordamı izleyerek ATA Center’da Etki Alanı Bağlantısı parolasını güncelleştirin:

1.  ATA Center’da ATA Konsolu’nu açın.

2.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.png)

3.  **Dizin Hizmetleri**’ni seçin.

    ![ATA Gateway parola değiştirme görüntüsü](media/ATA-GW-change-DC-password.png)

4.  **Parola** altında, parolayı değiştirin.

    ATA Center etki alanına bağlantısı varsa, kullanmak **Test Bağlantısı** kimlik doğrulamaya düğmesi

5.  **Kaydet**'e tıklayın.

6.  Parolayı değiştirdikten sonra, ATA Gateway sunucularında ATA Gateway hizmetinin çalıştığını el ile denetleyin.



## <a name="see-also"></a>Ayrıca Bkz.
- [ATA Konsolu ile çalışma](working-with-ata-console.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
