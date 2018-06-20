---
title: Azure Advanced Threat Protection bildirimlerini ayarlama | Microsoft Docs
description: Şüpheli etkinlikler algılandığında bildirim almak için Azure ATP uyarıları ayarlamak açıklar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 4308f03e-b2a7-4e38-a750-540ff94faa81
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 85fe887df373d8132df932cdb3d1eaf5ab954a1d
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
ms.locfileid: "29445983"
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*


# <a name="set-azure-atp-notifications"></a>Azure ATP Bildirimleri Ayarla

Azure ATP kuşkulu bir etkinlik veya e-posta yoluyla bir sistem durumu uyarısı algıladığında size bildirebilir. 

Belirli bir e-posta adresine bildirimleri almak için aşağıdaki parametreleri ayarlayın:


1. Azure ATP çalışma Portalı'nda seçin ve araç çubuğunda ayarlar seçeneğini seçin **yapılandırma**.

![Azure ATP yapılandırma ayarları simgesi](media/atp-config-menu.png)

2. Tıklatın **bildirimleri**.
3. Altında **posta bildirimleri**, hangi bildirimleri e-posta ile gönderilmesi gerektiğini belirtin - yeni uyarılar (kuşkulu etkinlikleri) ve yeni sistem durumu sorunları için gönderilebilir. 
 
 >  [!NOTE]
 >   Kuşkulu etkinlikler için e-posta uyarıları, yalnızca kuşkulu etkinlik oluşturulduğunda gönderilir.

5. **Kaydet**'e tıklayın.

 ![Azure ATP bildirimleri](media/atp-notifications.png)



## <a name="see-also"></a>Ayrıca bkz:

- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)

- [Syslog ayarlarını belirleme](setting-syslog.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)