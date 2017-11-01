---
title: "ATA olay kimliği başvurusu | Microsoft Docs"
description: "ATA olay kimliklerinin bir listesi ve açıklamalarının sağlar."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/25/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 5d639e84-2e37-43a9-9667-49be6c4fa8b7
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: 7bd0f90acbb6a2d8eb84fd09bc4d859fff082273
ms.sourcegitcommit: 5563c6861bb5db5cb73e058e5a51b4938b9a7d46
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*


# <a name="ata-event-id-reference"></a>ATA olay kimliği başvurusu

ATA Center Olay Görüntüleyicisi'ni, ATA'ın olayları günlüğe kaydeder. Bu makalede, olay kimliklerinin bir listesini sağlar ve her bir açıklaması verilmiştir.

Olayları şurada bulunabilir:

![Olay Kimliği konumu](./media/event-id-location.png)

## <a name="ata-health-events"></a>ATA sistem durumu olayları

1001 – boş alan sistem durumu uyarısı ATA Center veritabanı veri sürücüsü 

1003 – ATA Center aşırı yüklenmiş sistem durumu Uyarısı 

1004 – sertifikası süre sonu sistem durumu Uyarısı 

1005 – merkezi veritabanı bağlantısı kesilmiş sistem durumu Uyarısı 

1006 – ATA Gateway Dizin Hizmetleri istemci hesabı parola süre sonu sistem durumu Uyarısı 

1007 – ATA Gateway etki alanı Eşitleyici atanmamıştır sistem durumu Uyarısı 

1008 – ATA Gateway yakalama ağ bağdaştırıcısı hatalı sistem durumu Uyarısı 

1009 – ATA Gateway yakalama ağ bağdaştırıcısı eksik sistem durumu Uyarısı 

1010 – ATA Gateway Dizin Hizmetleri istemci bağlantısı sistem durumu Uyarısı 

1011 – ATA Gateway bağlantısı kesilmiş sistem durumu Uyarısı 

1012 – olay etkinlikleri sistem durumu uyarısı ATA Gateway aşırı yüklenmiş 

1013 – ATA Gateway aşırı ağ etkinlikleri sistem durumu Uyarısı 

1014 – merkezi posta sistem durumu Uyarısı 

1015 – merkezi Syslog sistem durumu Uyarısı 

1016 – ATA Gateway bileşenleri güncel sistem durumu Uyarısı 

1017 – merkezi trafiği sistem durumu uyarısı almıyor 

1018 – ATA Gateway başlatma hatası Sistem Durumu Uyarısı 

1019 – ATA Gateway düşük bellek sistem durumu Uyarısı 

1020 – ATA Gateway RADIUS olay dinleyicisi sistem durumu Uyarısı 

1021 – ATA Gateway Syslog olay dinleyicisi sistem durumu Uyarısı 

1022 – ATA Center dış IP adresi çözüm hatası Sistem Durumu Uyarısı 
 
## <a name="ata-suspicious-ctivity-events"></a>ATA kuşkulu ctivity olayları

2001 – anormal davranışları şüpheli etkinlik 

2002 – olağan dışı protokol şüpheli etkinlik 

2003 – hesap numaralandırma kuşkulu etkinliği 

2004 – LDAP deneme yanılma zorla şüpheli etkinlik 

2005 – şüpheli etkinlik bilgisayar ön kimlik doğrulaması başarısız oldu 

2006 – çoğaltma şüpheli etkinlik Dizin Hizmetleri 

2007 – DNS keşif şüpheli etkinlik 

2008 – şifreleme indirgeme şüpheli etkinlik 

2012 – oturumları şüpheli etkinlik listeleme 

2013 – sahte PAC şüpheli etkinlik 

2014 – Honeytoken aktivite şüpheli etkinlik 

2015 – LDAP doğrulamaya parola şüpheli etkinlik 

2016 – büyük nesne silme şüpheli etkinlik 

2017 – geçişi karma şüpheli etkinlik 

2018 – geçişi bilet şüpheli etkinlik 

2019 – uzaktan yürütme şüpheli etkinlik 

2020 – veri koruma yedek anahtar şüpheli etkinlik alma 

2021 – yapılan keşif şüpheli etkinlik 

2022 – altın anahtar şüpheli etkinlik 

2023 – anormal hassas grubu üyeliği değişikliği şüpheli etkinlik 

2023 – deneme yanılma saldırısı şüpheli etkinlik 

## <a name="ata-auditing-events"></a>ATA denetim olayları

3001 – ATA yapılandırmasını değiştirme 

3002 – ATA Gateway eklendi

3003 – ATA Gateway silindi

3004 - ATA lisans etkinleştirildi

3005 – ATA Konsolu'nda oturum açma

3006 – etkinlik durumu el ile değişiklik 

3007 – el ile değişiklik şüpheli etkinlik durumu 


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
