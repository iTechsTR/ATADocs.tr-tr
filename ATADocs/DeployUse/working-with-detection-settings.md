---
# required metadata

title: ATA Algılama Ayarlarıyla Çalışma | Microsoft Advanced Threat Analytics
description: Alışılmışın dışında durumlarda olan ve ağınızdaki diğer varlıklardan farklı işlenmesi gereken IP adresleri ve alt ağlar listesinin nasıl yapılandırılacağı açıklanır.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: f4f2ae30-4849-4a4f-8f6d-bfe99a32c746

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ATA Algılama Ayarlarıyla Çalışma
**Algılama** yapılandırma sayfası, alışılmışın dışında durumlarda olan ve ağınızdaki diğer varlıklardan farklı işlenmesi gereken IP adresleri ve alt ağlar listesini ayarlamanızı sağlar.

## Algılamayı ayarlama
**Algılama** sayfasında aşağıdaki öğeleri tanımlayabilirsiniz:

-   **Kısa süreli kiralık alt ağlar** - Kuruluşunuzda VPN IP adresi alt ağları veya Wi-Fi alt ağları gibi IP adreslerinin çok kısa süreli olduğu alt ağlar varsa, bu IP adreslerini ve alt ağları ATA’ya giriş olarak sağlamak önemlidir. Çünkü böylelikle ATA, bir bilgisayarla bu aralıktaki bir IP adresi arasındaki ilişkiyi diğer IP adreslerinde olduğundan daha kısa bir süre için depolayacağını bilir.

-   **Honeytoken hesabı SID’leri** – Bu, ağ etkinliği olmayan bir kullanıcı hesabı olmalıdır. Bu hesap, ATA Honeytoken kullanıcısı olarak yapılandırılır. Herhangi biri bu kullanıcı hesabını kullanma girişiminde bulunursa, ATA kuşkulu bir etkinlik oluşturur ve bu kötü amaçlı etkinliğin göstergesidir. Honeytoken kullanıcısını yapılandırmak için, kullanıcı adına değil kullanıcı hesabının SID değerine ihtiyacınız vardır.

IP adreslerini aşağıdaki algılamaların dışında bırakabilirsiniz. Bu listelerden birine bir IP adresi girerseniz, ATA bu IP adresini algılanan bu belirli etkinlik türünün dışında bırakır.

-   DNS Keşfi IP adresi dışlamaları

-   Anahtar Geçişi IP adresi dışlamaları

## Ayrıca Bkz.
- [Kuşkulu etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATA yapılandırmasında değişiklik yapma](modifying-ata-configuration.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=May16_HO1-->


