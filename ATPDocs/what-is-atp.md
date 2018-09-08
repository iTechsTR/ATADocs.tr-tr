---
title: Azure Gelişmiş tehdit Koruması (ATP) nedir? | Microsoft Docs
description: Azure Gelişmiş tehdit Koruması (ATP) nedir ve ne tür kuşkulu etkinlikleri algılama açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 2d14d0e9-1b03-4bcc-ae97-8fd41526ffc5
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 7e78d5db2babc682de8eae50091193e1ccee8433
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44166150"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="what-is-azure-advanced-threat-protection"></a>Azure Gelişmiş tehdit Koruması nedir?
Azure Gelişmiş Tehdit Koruması (ATP), kurumsal hibrit ortamlarınızı birden fazla türdeki gelişmiş hedefli siber saldırı ve içeriden bilgi sızdırma tehditlerine karşı korumanıza yardımcı olan bir bulut hizmetidir.

## <a name="how-azure-atp-works"></a>Azure ATP nasıl çalışır?

Azure ATP özel bir ağ ayrıştırma altyapısından (Kerberos, DNS, RPC, NTLM ve diğerleri gibi) birden çok protokolün ağ trafiğini yakalamak ve ayrıştırmak için kimlik doğrulaması, yetkilendirme ve bilgi toplama yararlanır. Bu bilgiler Azure ATP tarafından yollardan biriyle toplanır:

-   Azure ATP algılayıcı doğrudan etki alanı denetleyicilerinizde dağıtma
-   Azure ATP tek başına algılayıcı için etki alanı denetleyicileri ve DNS sunucularından yansıtma bağlantı noktası

Azure ATP birden çok veri kaynağında, günlükler ve olaylar kullanıcıların ve kuruluştaki diğer varlıkların davranışlarını öğrenmek ve bunlar hakkında davranış profili oluşturmak için ağınızdaki gibi bilgileri alır.
Azure ATP olayları ve günlükleri şuralardan alabilir:

-   SIEM Tümleştirmesi
-   Windows Olay İletme (WEF)
-   Doğrudan Windows Olay Toplayıcısı'ndan (için algılayıcı)
-   RADIUS Vpn'lerden hesaplaması


Azure ATP mimarisi hakkında daha fazla bilgi için bkz. [Azure ATP mimarisi](atp-architecture.md).

## <a name="what-does-azure-atp-do"></a>Azure ATP ne yapar?

Azure ATP teknolojisi siber saldırı ölüm zincirinin, belirtilen çeşitli aşamalarına odaklanarak birden çok şüpheli etkinliği algılar:

-   Keşif aşamasında saldırganlar ortamın nasıl oluşturulduğunu bilgi toplamak, hangi farklı varlıklardır ve hangi varlık yoktur. Bunlar genellikle saldırının sonraki aşamaları için planlarına oluşturma.
-   Yanal hareket döngüsü aşamasında saldırgan, ağınızdaki saldırı yüzeyini genişletmek için zaman ve çaba harcar.
-   Etki alanı hakimiyeti (Kalıcılık) aşamasında saldırgan bunları çeşitli ayarlar giriş noktaları, kimlik bilgileri ve teknikler kullanarak sürdürmesine olanak sağlayan bilgileri yakalar. 

Bu siber saldırı aşamaları, hangi türde bir şirket saldırıya uğramış veya ne tür bilgiler hedeflenmiş olursa olsun birbirine benzer ve tahmin edilebilirdir.
Azure ATP saldırıları başlıca üç türdeki için arar: kötü amaçlı saldırılar, olağan dışı davranış ve güvenlik sorunlarını ve riskleri.

**Kötü amaçlı saldırıları** algılanan belirleyici yanı sıra anormal davranış analizi aracılığıyla. Bilinen saldırı türlerinin tam listesi içerir:

-   Anahtar Geçişi (PtT)
-   Karma Geçişi (PtH)
-   Karmayı Atlayarak Geçiş
-   Sahte PAC (MS14-068)
-   Altın Bilet
    -   zaman anomoly
    -   Varolmayan hesabı - yeni
-   Kötü amaçlı çoğaltma
-   Dizin hizmeti numaralandırması
-   SMB Oturumu Listeleme
-   DNS Keşfi
-   Yatay deneme yanılma 
-   Dikey deneme yanılma
-   Maymuncuk
-   Olağan dışı protokol
-   Şifrelemeyi düşürme
-   Uzaktan yürütme
-   Kötü amaçlı hizmeti oluşturma
-   Şüpheli etki alanı denetleyicisi yükseltme (olası DCShadow saldırı) - yeni
-   Şüpheli çoğaltma isteği (olası DCShadow saldırı) - yeni
-   VPN 


Azure ATP bu şüpheli etkinlikleri algılar ve kim, düz bir görünümünü de dahil olmak üzere Azure ATP çalışma alanı portalında bilgilerini ortaya çıkarır neyi, nasıl ve ne zaman. Bu basit, kullanımı kolay Panoda, gördüğünüz gibi Azure ATP ağınızdaki istemci 1 ve istemci 2 bilgisayarları üzerinde bir Pass--Ticket saldırısı girişiminde bulunuldu şüphelendiği uyarılırsınız.

 ![Örnek Azure ATP ekranı pass--ticket](media/pass-the-ticket-sa.png)


Azure ATP de algılar **güvenlik sorunlarını ve riskleri**de dahil olmak üzere:

-   Zayıf protokoller
-   Bilinen protokol güvenlik açıkları
-   [Hassas hesaplara yönelik yatay hareket yolu](use-case-lateral-movement-path.md)

# <a name="what-threats-does-azure-atp-look-for"></a>Hangi tehditleri Azure ATP arar?

Azure ATP Gelişmiş bir tehdidin çeşitli aşamaları için algılama sağlar: Keşif, kimlik bilgilerinin tehlikeye atılması, yanal hareket, ayrıcalık yükseltme, etki alanı hakimiyeti ve diğerleri. Bu algılamaların amacı, gelişmiş saldırıları ve içeriden gelen tehditleri kuruluşunuza zarar vermeden önce algılamaktır.

Her aşamadaki algılama, söz konusu aşamayla ilgili birkaç şüpheli etkinlikle sonuçlanır ve burada her şüpheli etkinlik farklı türde olası saldırılarla ilişkilidir.
Azure ATP şu anda algılayabildiği sonlandırma zinciri Bu aşamalar aşağıdaki resimde vurgulanmıştır:

![Ölüm zincirindeki yanal etkinliklere saldırı Azure ATP odaklanır](media/attack-kill-chain-small.jpg)


Daha fazla bilgi için [kuşkulu etkinliklerle çalışma](working-with-suspicious-activities.md) ve [Azure ATP şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md).

## <a name="whats-next"></a>Sırada ne var?

-   Azure ATP ağınıza nasıl uyguladığı hakkında daha fazla bilgi: [Azure ATP mimarisi](atp-architecture.md)

-   ATP dağıtımına başlamak için: [ATP yükleyin](install-atp-step1.md)


## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP sık sorulan sorular](atp-technical-faq.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)