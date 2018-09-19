---
title: ATA olay kimliği başvurusu | Microsoft Docs
description: ATA olay kimlikleri listesi ve açıklamalarının sağlar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 5d639e84-2e37-43a9-9667-49be6c4fa8b7
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: 38610c6b8f94dbe1a31e218e064750bf2bde2c49
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133149"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*


# <a name="ata-event-id-reference"></a>ATA olay kimliği başvuru

ATA Center Olay Görüntüleyicisi'ni, Ata'nın olayları günlüğe kaydeder. Bu makalede, olay kimliklerinin bir listesini sağlar ve her bir açıklaması verilmiştir.

Olayları burada bulunabilir:

![Olay Kimliği konumu](./media/event-id-location.png)

## <a name="ata-health-events"></a>ATA sistem durumu olayları

1001 – ATA Center veritabanı veri sürücü boş alan sistem durumu Uyarısı 

1003 – ATA Center aşırı yüklenmiş bir sistem durumu Uyarısı 

1004 – sertifika sona erme durumu Uyarısı 

1005: merkezi veritabanı bağlantısı kesilmiş bir sistem durumu Uyarısı 

1006: ATA Gateway Dizin Hizmetleri istemci hesabı parola sona erme durumu Uyarısı 

1007 – ATA Gateway etki alanı Eşitleyicisi atanmadı durumu Uyarısı 

1008 – ATA Gateway yakalama ağ bağdaştırıcısı hatalı sistem durumu Uyarısı 

1009 – ATA Gateway yakalama ağ bağdaştırıcısı eksik sistem durumu Uyarısı 

1010 – ATA Gateway Dizin Hizmetleri istemci bağlantı durumu Uyarısı 

1011 değerinin kodunu – sistem durumu uyarısı ATA Gateway bağlantısı kesildi 

1012 – olay etkinlikleri durumu uyarısı ATA Gateway aşırı 

1013 – ATA Gateway aşırı ağ etkinlikleri durumu Uyarısı 

1014 – merkezi posta sistem durumu Uyarısı 

1015 – merkezi Syslog durumu Uyarısı 

1016 – ATA Gateway bileşenleri güncel durumu Uyarısı 

1017: Merkezi sistem durumu uyarısı trafiği almıyor 

1018 – ATA Gateway start-başarısızlık durumu Uyarısı 

1019 – ATA Gateway düşük bellek durumu Uyarısı 

1020 – ATA Gateway RADIUS olay dinleyicisi durumu Uyarısı 

1021 – ATA Gateway Syslog olay dinleyicisi durumu Uyarısı 

1022 – ATA Center dış IP adresi çözüm hatası Sistem Durumu Uyarısı 
 
## <a name="ata-suspicious-activity-events"></a>ATA şüpheli etkinlik olayları

2001-şüpheli etkinlik anormal davranış 

2002: olağan dışı protokol şüpheli etkinlik 

2003: hesap numaralandırma şüpheli etkinliği 

2004: LDAP deneme yanılma şüpheli etkinlik zorla 

2006-çoğaltma şüpheli etkinlik Dizin Hizmetleri 

2007 – DNS keşfi şüpheli etkinliğini 

2008 – şifreleme düşürme şüpheli etkinliği 

2012 – şüpheli etkinlik oturumları listeleme 

2013 – sahte PAC şüpheli etkinliği 

2014 – Honeytoken etkinliği şüpheli etkinlik 

2016 – büyük çaplı nesne silme şüpheli etkinliği 

2017 – geçişi karma şüpheli etkinlik 

2018 – geçişi anahtar şüpheli etkinliği 

2019 – şüpheli etkinlik uzaktan yürütme 

2020 – data protection yedek anahtar şüpheli etkinlik alma 

2021 – SAMR keşfi şüpheli etkinliğini 

2022 – altın bilet şüpheli etkinlik 

2023 – yanılma şüpheli etkinlik 

2024 - anormal gizli grup üyeliği değişiklik şüpheli etkinliği  

## <a name="ata-auditing-events"></a>ATA denetim olayları

3001 – ATA yapılandırmasını değiştirme 

3002 – eklenen ATA Gateway

3003 – ATA Gateway silindi

3004 - ATA lisans etkinleştirildi

3005 – ATA Konsolu'nda oturum açma

3006: el ile etkinlik durumu değişikliği 

3007 – kuşkulu etkinliğin durumu el ile değişiklik 


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
