---
title: Azure Gelişmiş tehdit koruması bildirimlerini ayarlama | Microsoft Docs
description: Şüpheli etkinlikler algılandığında bildirim almak için Azure ATP güvenlik uyarıları ayarlama işlemi açıklanmaktadır.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 4308f03e-b2a7-4e38-a750-540ff94faa81
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: e6f3647ecaab82a32950fadd0a101385a2cc0051
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48783058"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="set-azure-atp-notifications"></a>Azure ATP bildirimlerini ayarlama

Azure ATP kuşkulu bir etkinlik algılar ve bir güvenlik uyarısı veya bir sistem durumu uyarı e-posta yoluyla sorunları size bildirebilir. 

Belirli bir e-posta adresine bildirimleri almak için şu parametreleri ayarlayın:


1. Azure ATP portalında seçin ve araç çubuğunda ayarlar seçeneğini **yapılandırma**.

![Azure ATP yapılandırma ayarları simgesi](media/atp-config-menu.png)

2. Tıklayın **bildirimleri**.
3. Altında **posta bildirimleri**, e-posta aracılığıyla hangi bildirimlerin gönderilmesi gerektiğini belirtin - yeni uyarılar (şüpheli etkinlikler) ve yeni sistem durumu sorunları için gönderilebilir. 
 
 >  [!NOTE]
 >   Kuşkulu etkinlikler için e-posta uyarıları, yalnızca kuşkulu etkinlik oluşturulduğunda gönderilir.
 
4. **Kaydet**'e tıklayın.

 ![Azure ATP bildirimlerini](media/atp-notifications.png)



## <a name="see-also"></a>Ayrıca Bkz.

- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)

- [Syslog ayarlarını belirleme](setting-syslog.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
