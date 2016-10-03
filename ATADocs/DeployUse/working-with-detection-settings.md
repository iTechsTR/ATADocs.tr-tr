---
title: "ATA Algılama Ayarlarıyla çalışma | Microsoft ATA"
description: "Alışılmışın dışında durumlarda olan ve ağınızdaki diğer varlıklardan farklı işlenmesi gereken IP adresleri ve alt ağlar listesinin nasıl yapılandırılacağı açıklanır."
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: f4f2ae30-4849-4a4f-8f6d-bfe99a32c746
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 28b6211599395317eb6336c37fd3461b8f5635f6
ms.openlocfilehash: 09248cdd5f8a66a164a5cd275f2765107f5c706d


---

*Uygulama hedefi: Advanced Threat Analytics sürüm 1.7*



# ATA Algılama Ayarlarıyla Çalışma
**Algılama** yapılandırma sayfası, alışılmışın dışında durumlarda olan ve ağınızdaki diğer varlıklardan farklı işlenmesi gereken IP adresleri ve alt ağlar listesini ayarlamanızı sağlar.

## Algılamayı ayarlama
**Algılama** bölümünde aşağıdaki öğeleri tanımlayabilirsiniz:

-   **Honeytoken hesabı SID’leri** – Bu, ağ etkinliği olmayan bir kullanıcı hesabı olmalıdır. Bu hesap, ATA Honeytoken kullanıcısı olarak yapılandırılır. Herhangi biri bu kullanıcı hesabını kullanma girişiminde bulunursa, ATA kuşkulu bir etkinlik oluşturur ve bu kötü amaçlı etkinliğin göstergesidir. Honeytoken kullanıcısını yapılandırmak için, kullanıcı adına değil kullanıcı hesabının SID değerine ihtiyacınız vardır.

>[!NOTE]
> Kullanıcının SID’sini ATA Konsolundaki kullanıcı profilinin *Hesap Bilgisi* sekmesinde bulabilirsiniz.


![ATA algılama ayarları honeytoken](media/ata-detection-settings-honeytoken-1.7.png)


**Algılama Dışlamaları** - Aşağıdaki algılamalarda IP adreslerini dışlayabilirsiniz. Bu listelerden birine bir IP adresi girerseniz, ATA bu IP adresini algılanan bu belirli etkinlik türünün dışında bırakır.

-   DNS Keşfi IP adresi dışlamaları

-   Anahtar Geçişi IP adresi dışlamaları

![ATA algılama ayarları dışlamaları](media/ata-detection-settings-exclusions-1.7.png)


## Ayrıca Bkz.
- [Kuşkulu etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATA yapılandırmasında değişiklik yapma](modifying-ata-configuration.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Aug16_HO5-->


