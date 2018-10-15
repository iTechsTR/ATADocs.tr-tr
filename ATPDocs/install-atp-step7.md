---
title: Azure Gelişmiş tehdit koruması yapılandırma algılama dışlamalarını ve honeytoken hesapları | Microsoft Docs
description: Algılama dışlamalarını ve honeytoken hesaplar yapılandırması.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 1ad5e923-9bbd-4f56-839a-b11a9f387d4b
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 9202ba7c2519de0c7cd2eb3103578159dc437e83
ms.sourcegitcommit: 58c75026e5ec4dcab3b0852a41f9f0a0ad6f22eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2018
ms.locfileid: "49315753"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="configure-detection-exclusions-and-honeytoken-accounts"></a>Algılama dışlamalarını ve honeytoken hesapları yapılandırma

Azure ATP çıkarma algılama sayısı, belirli IP adresleri veya kullanıcılarının sağlar. 

Örneğin, bir **DNS Keşfi dışlaması** DNS’i tarama mekanizması olarak kullanan bir güvenlik tarayıcısı olabilir. Dışlama Azure ATP böyle tarayıcıları yoksaymasına yardımcı olur.  

Azure ATP ayrıca kötü amaçlı aktörler - bu honeytoken hesaplar (normalde etkinliği olmayan) ilişkili herhangi bir kimlik doğrulaması için tuzak kullanılan, bir uyarı tetikler honeytoken hesapları yapılandırmasını sağlar.

Yapılandırmak için aşağıdaki adımları izleyin:

1.  Azure ATP portalında ayarlar simgesine tıklayın ve seçin **yapılandırma**.

    ![Azure ATP yapılandırma ayarları](media/atp-config-menu.png)

2.  Altında **algılama**, tıklayın **varlık etiketleri**.

3. Altında **Honeytoken hesapları**Honeytoken hesap adını girin ve tıklatın **+** oturum. Honeytoken hesapları alanında arama yapılabilir ve otomatik olarak ağınızdaki varlıklar görüntüler. **Kaydet**'e tıklayın.

   ![Honeytoken](media/honeytoken-sensitive.png)

4. **Dışlamalar**’a tıklayın. Bir kullanıcı hesabı veya her tür tehdit algılama dışlanacak IP adresi girin. 
5. Tıklayın *artı* oturum. **Varlık ekle** (kullanıcı veya bilgisayar) alanında arama yapılabilir ve bu alan, ağınızdaki varlıklarla otomatik olarak doldurulur. Daha fazla bilgi için [varlıkları algılamalardan dışlama](excluding-entities-from-detections.md) ve [şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md).

   ![Dışlamalar](media/exclusions.png)

6.  **Kaydet**'e tıklayın.


Tebrikler, Azure Gelişmiş tehdit koruması başarıyla dağıttığınız!

Algılanan kuşkulu etkinlikleri görüntülemek için saldırı zaman çizelgesini gözden geçirin ve kullanıcıları veya bilgisayarları arayın ve profillerini görüntüleyin.

Azure ATP şüpheli etkinlikler için tarama hemen başlar. Olağan dışı Grup değişiklikleri gibi bazı algılamalar bir öğrenme dönemi gerekir ve Azure ATP dağıtımdan hemen sonra kullanılamaz.


## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Zure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
