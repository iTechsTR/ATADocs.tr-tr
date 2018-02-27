---
title: "Azure Gelişmiş tehdit Koruması (ATP) nedir? | Microsoft Docs"
description: "Azure Gelişmiş tehdit Koruması (ATP) nedir ve ne tür kuşkulu etkinlikleri algılayabildiği açıklanır"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 2d14d0e9-1b03-4bcc-ae97-8fd41526ffc5
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 5ccac90a171c895ee8b4d5336a125ccd7fa66239
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*


# <a name="what-is-azure-advanced-threat-protection"></a>Azure Advanced Threat Protection nedir?
Azure Gelişmiş Tehdit Koruması (ATP), kurumsal hibrit ortamlarınızı birden fazla türdeki gelişmiş hedefli siber saldırı ve içeriden bilgi sızdırma tehditlerine karşı korumanıza yardımcı olan bir bulut hizmetidir.

## <a name="how-azure-atp-works"></a>Azure ATP nasıl çalışır?

Azure ATP (örneğin, Kerberos, DNS, RPC, NTLM ve diğerleri) birden çok protokollerin ağ trafiğini yakalamak ve altyapısı ayrıştırılırken özel bir ağ kimlik doğrulama, yetkilendirme ve bilgi toplama için yararlanır. Bu bilgileri Azure ATP tarafından toplanır:

-   Azure ATP algılayıcılar doğrudan etki alanı denetleyicilerinizde dağıtma
-   Etki alanı denetleyicileri ve DNS sunucularından Azure ATP tek başına algılayıcı yansıtma bağlantı noktası

Azure ATP birden çok veri kaynaklarından-, günlüklerini ve olayları kullanıcılar ve kuruluştaki diğer varlıklar davranışını öğrenmek ve bunlarla ilgili davranış profili oluşturmak için ağınızdaki gibi bilgilerini alır.
Azure ATP olayları ve günlükleri alabilirsiniz:

-   SIEM Tümleştirmesi
-   Windows Olay İletme (WEF)
-   Doğrudan Windows Olay Toplayıcısı (için algılayıcı)
-   RADIUS VPN hesaplaması


Azure ATP mimarisi hakkında daha fazla bilgi için bkz: [Azure ATP mimarisi](atp-architecture.md).

## <a name="what-does-azure-atp-do"></a>Azure ATP ne yapar?

Azure ATP teknolojisi siber saldırı sonlandırma zinciri de dahil olmak üzere çeşitli aşamaları odaklanan birden çok kuşkulu etkinlikleri algılar:

-   Keşif sırasında saldırganlar ortamı nasıl yapılandırıldığını bilgi toplamak, hangi farklı varlıkları içerir ve hangi varlık yoktur. Bunlar genellikle planlarına saldırı sonraki aşamaları için yapı oluşturma.
-   Yanal hareket döngüsü aşamasında saldırgan, ağınızdaki saldırı yüzeyini genişletmek için zaman ve çaba harcar.
-   Etki alanı hakimiyeti (kalıcı) sırasında bir saldırganın çeşitli ayarlar giriş noktaları, kimlik bilgileri ve teknikleri kullanarak kendi kampanya sürdürmeye vermeden bilgilerini yakalar. 

Bu siber saldırı aşamaları, hangi türde bir şirket saldırıya uğramış veya ne tür bilgiler hedeflenmiş olursa olsun birbirine benzer ve tahmin edilebilirdir.
Azure ATP üç ana saldırıları türlerinde arar: kötü amaçlı saldırıları, anormal davranış ve güvenlik sorunlarını ve riskleri.

**Kötü amaçlı saldırıları** algılanan belirleyici biçimde yanı sıra anormal davranışları analizi aracılığıyla. Bilinen saldırı türlerinin tam listesi içerir:

-   Anahtar Geçişi (PtT)
-   Karma Geçişi (PtH)
-   Karmayı Atlayarak Geçiş
-   Sahte PAC (MS14-068)
-   Altın Bilet
-   Kötü amaçlı çoğaltma
-   Dizin hizmeti numaralandırması
-   SMB Oturumu Listeleme
-   DNS Keşfi
-   Yatay deneme yanılma saldırısı 
-   Dikey deneme yanılma saldırısı
-   Maymuncuk
-   Olağan dışı protokol
-   Şifreleme indirgeme
-   Uzaktan yürütme
-   Kötü amaçlı hizmet oluşturma


Azure ATP bu kuşkulu etkinlikleri algılar ve kim, düz bir görünümünü de dahil olmak üzere Azure ATP çalışma portalında bilgileri de ortaya çıkarır, ne zaman ve nasıl. Bu basit, kullanımı kolay Pano izleyerek, gördüğünüz gibi Azure ATP geçişi anahtar saldırı, ağınızdaki istemci 1 ve 2 istemci bilgisayarlar üzerinde denendi şüphelendiği olduğunu uyarılırsınız.

 ![Örnek Azure ATP ekran geçişi anahtar](media/pass-the-ticket-sa.png)


Azure ATP de algılar **güvenlik sorunlarını ve riskleri**dahil:

-   Zayıf protokoller
-   Bilinen protokol güvenlik açıkları
-   [Yanal hareket yoluna hassas hesapları](use-case-lateral-movement-path.md)

# <a name="what-threats-does-azure-atp-look-for"></a>Hangi tehditleri Azure ATP arar?

Azure ATP Gelişmiş bir tehdidin çeşitli aşamaları için algılama sağlar: Keşif, kimlik bilgilerinin tehlikeye atılması, yanal hareket, ayrıcalık yükseltme, etki alanı hakimiyeti ve diğerleri. Bu algılamaların amacı, gelişmiş saldırıları ve içeriden gelen tehditleri kuruluşunuza zarar vermeden önce algılamaktır.

Her aşamadaki algılama, söz konusu aşamayla ilgili birkaç şüpheli etkinlikle sonuçlanır ve burada her şüpheli etkinlik farklı türde olası saldırılarla ilişkilidir.
Burada Azure ATP algılaması şu anda sağlar sonlandırma zinciri bu aşamada, aşağıdaki görüntüde vurgulanmıştır:

![Saldırı yanal etkinliğinde Azure ATP odaklanmak KILL zinciri](media/attack-kill-chain-small.jpg)


Daha fazla bilgi için bkz: [kuşkulu etkinliklerle çalışma](working-with-suspicious-activities.md) ve [Azure ATP şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md).

## <a name="whats-next"></a>Sırada ne var?

-   Azure ATP ağınıza nasıl uyum sağladığı hakkında daha fazla bilgi için: [Azure ATP mimarisi](atp-architecture.md)

-   ATP dağıtımına başlamak için: [ATP yükleyin](install-atp-step1.md)


## <a name="see-also"></a>Ayrıca bkz:
- [Azure ATP sık sorulan sorular](atp-technical-faq.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)