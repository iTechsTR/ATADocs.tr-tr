---
title: "ATA yapılandırmasını değiştirme - IIS sertifikası | Microsoft ATA"
description: "IIS tarafından ATA Center için kullanılan sertifikanın nasıl değiştirileceği açıklanır."
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: e58a0390-57ef-4c68-a987-2e75e5f3d6b3
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f13750f9cdff98aadcd59346bfbbb73c2f3a26f0
ms.openlocfilehash: 18d3dfdc2262765d71d82f395273e2972118cbfb


---

# Ata yapılandırmasını değiştirme - IIS sertifikası

>[!div class="step-by-step"]
[« ATA Konsolu IP adresi](modifying-ata-config-consoleip.md)
[Etki alanı bağlantı parolası »](modifying-ata-config-dcpassword.md)

## IIS sertifikasını değiştirme
Konsolda, ATA Center hizmeti için sertifikayı seçebilir ve değiştirebilirsiniz ancak IIS tarafından kullanılan sertifikayı değiştiremezsiniz.

Bunu değiştirmek istiyorsanız aşağıdaki yordamı kullanın:

> [!NOTE]
> IIS Sertifikası değiştirdikten sonra, yeni ATA Gateway bileşenlerini yüklemeden ATA Gateway Kurulum paketini indirmelisiniz.

IIS tarafından ATA Center için kullanılan sertifikayı değiştirmeniz gerekirse, ATA Center sunucusunda şu adımları izleyin.

1.  Yeni sertifikayı ATA Center sunucusuna yükleyin.

2.  Internet Information Services (IIS) Yöneticisi'ni açın.

3.  Sunucunun adını genişletin ve **Siteler**’i genişletin.

4.  Microsoft ATA Konsolu sitesini seçin ve **Eylemler** bölmesinde **Bağlamalar**’a tıklayın.

    ![ATA Konsolu bağlamalar eylemi](media/ATA-console-change-IP-bindings.jpg)

5.  **HTTPS**’yi seçin ve **Düzenle**’ye tıklayın.

6.  **SSL sertifikası**’nın altında, yeni sertifikayı seçin.

7.  Yeni bir ATA Gateway yüklemeden önce ATA Gateway Kurulum paketini indirin.

>[!div class="step-by-step"]
[« ATA Konsolu IP adresi](modifying-ata-config-consoleip.md)
[Etki alanı bağlantı parolası »](modifying-ata-config-dcpassword.md)

## Ayrıca Bkz.
- [ATA Konsolu’yla çalışma](working-with-ata-console.md)
- [ATA’yı yükleme](install-ata.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jul16_HO4-->


