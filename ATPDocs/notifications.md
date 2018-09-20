---
title: Azure Gelişmiş tehdit koruması bildirimlerini ayarlama | Microsoft Docs
description: Şüpheli etkinlikler algılandığında bildirim almak için Azure ATP uyarıları ayarlama işlemi açıklanmaktadır.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 4308f03e-b2a7-4e38-a750-540ff94faa81
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: c3fc5adbb700c4b8df66c243a655cf98aacc79af
ms.sourcegitcommit: 9f02f0f6669b25f39b616bb0885bb55b8c4f050b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46362434"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="set-azure-atp-notifications"></a>Azure ATP bildirimlerini ayarlama

Azure ATP, kuşkulu bir etkinlik veya sistem durumu uyarısı e-posta yoluyla algıladığında size bildirebilir. 

Belirli bir e-posta adresine bildirimleri almak için şu parametreleri ayarlayın:


1. Azure ATP çalışma alanı seçin ve araç çubuğunda ayarlar seçeneğini portalında **yapılandırma**.

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
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
