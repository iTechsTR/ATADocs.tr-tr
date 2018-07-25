---
title: Microsoft Advanced Threat Analytics (ATA) nedir? | Microsoft Docs
description: Microsoft Advanced Threat Analytics (ATA) çözümünün ne olduğu ve ne tür kuşkulu etkinlikleri algılayabildiği açıklanır
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 7/24/2018
ms.topic: article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 283e7b4e-996a-4491-b7f6-ff06e73790d2
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: adca31a6767031fce19f1a14bf8031c911717c9c
ms.sourcegitcommit: 63a36cd96aec30e90dd77bee1d0bddb13d2c4c64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39227249"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*


# <a name="what-is-advanced-threat-analytics"></a>Advanced Threat Analytics nedir?
Advanced Threat Analytics (ATA), kuruluşunuzu çeşitli türlerdeki, gelişmiş ve hedefe yönelik siber saldırıların yanı sıra dahili tehditlerden de korumaya yardımcı olan şirket içi bir platformdur.

## <a name="how-ata-works"></a>ATA nasıl çalışır?

ATA, kimlik doğrulaması, yetkilendirme ve bilgi toplama için özel bir ağ ayrıştırma altyapısından (Kerberos, DNS, RPC, NTLM ve diğerleri gibi) birden çok protokolün ağ trafiğini yakalamak ve ayrıştırmak için yararlanır. Bu bilgiler ATA tarafından şu yollarla toplanır:

-   Etki Alanı Denetleyicileri ve DNS sunucularından ATA Gateway’e bağlantı noktası yansıtma ve/veya
-   Doğrudan Etki Alanı Denetleyicilerinde bir ATA Lightweight Gateway (LGW) dağıtma

ATA, birden çok veri kaynağında, günlükler ve olaylar kullanıcıların ve kuruluştaki diğer varlıkların davranışlarını öğrenmek için ağınızda gibi bilgileri alır ve bunlar hakkında davranışsal bir profil oluşturur.
ATA, olayları ve günlükleri şuralardan alabilir:

-   SIEM Tümleştirmesi
-   Windows Olay İletme (WEF)
-   Doğrudan Windows Olay Toplayıcısı’ndan (Lightweight Gateway için)


ATA mimarisi hakkında daha fazla bilgi için bkz. [ATA mimarisi](ata-architecture.md).

## <a name="what-does-ata-do"></a>ATA ne yapar?

ATA teknolojisi siber saldırı ölüm zincirinin aşağıda belirtilen çeşitli aşamalarına odaklanarak birden çok şüpheli etkinliği algılar:

-   Keşif aşamasında saldırganlar ortamın nasıl oluşturulduğunu bilgi toplamak, hangi farklı varlıklardır ve hangi varlık yoktur. Genellikle, burada saldırganlar, saldırının sonraki aşamaları için planlarını yapı budur.
-   Yanal hareket döngüsü aşamasında saldırgan, ağınızdaki saldırı yüzeyini genişletmek için zaman ve çaba harcar.
-   Etki alanı hakimiyeti (Kalıcılık) aşamasında saldırgan, çeşitli ayarlar giriş noktaları, kimlik bilgileri ve teknikler kullanarak sürdürmesine olanak veren bilgileri yakalar. 

Bu siber saldırı aşamaları, hangi türde bir şirket saldırıya uğramış veya ne tür bilgiler hedeflenmiş olursa olsun birbirine benzer ve tahmin edilebilirdir.
ATA başlıca üç türdeki saldırıları arar: kötü amaçlı saldırılar, olağan dışı davranış ve güvenlik sorunlarını ve riskleri.

**Kötü amaçlı saldırılar** aşağıdakiler gibi bilinen saldırı türlerinin tam listesine bakarak belirlenimci olarak belirlenir:

-   Anahtar Geçişi (PtT)
-   Karma Geçişi (PtH)
-   Karmayı Atlayarak Geçiş
-   Sahte PAC (MS14-068)
-   Altın Bilet
-   Kötü amaçlı çoğaltmalar
-   Keşif
-   Deneme Yanılma
-   Uzaktan yürütme

Algılamaların ve açıklamalarının tam listesi için bkz: [hangi şüpheli etkinlikleri olabilir ATA algılar?](ata-threats.md). 

ATA bu şüpheli etkinlikleri algılar ve Kim, Ne, Ne Zaman ve Nasıl sorularına yönelik net bir bakış sağlayarak bilgileri ATA konsolunda sunar. Bu basit, kullanımı kolay Panoda, gördüğünüz gibi ATA, ağınızdaki istemci 1 ve istemci 2 bilgisayarları üzerinde bir Pass--Ticket saldırısı girişiminde bulunuldu şüphelendiği uyarılırsınız.

 ![örnek ATA ekranı pass-the-ticket](media/pass_the_ticket_sa.png)

ATA, aşağıda örnekleri verilen ve ağınızdaki kullanıcılarla cihazlarda görülen şüpheli etkinliklerle anormal davranışları ortaya çıkarmak için davranışsal analiz kullanarak ve Makine Öğrenimi özelliğinden faydalanarak **Anormal davranışları** algılar:

-   Anormal oturum açma işlemleri
-   Bilinmeyen tehditler
-   Parola paylaşımı
-   Yanal hareket
-   Gizli grup değişiklikleri


Bu tür şüpheli etkinlikleri ATA Panosunda görüntüleyebilirsiniz. Bir kullanıcı, normalde bir uyarı nedeni olabilir bu kullanıcı tarafından erişilemeyen dört bilgisayar erişiyorsa aşağıdaki örnekte, ATA sizi uyarır.

 ![Örnek ATA ekranı anormal davranış](media/abnormal-behavior-sa.png) 

ATA ayrıca, aşağıdakiler gibi **güvenlik sorunlarını ve risklerini** de algılar:

-   Bozulmuş güven
-   Zayıf protokoller
-   Bilinen protokol güvenlik açıkları

Bu tür şüpheli etkinlikleri ATA Panosunda görüntüleyebilirsiniz. Aşağıdaki örnekte, ATA, ağınızdaki bir bilgisayar ve etki alanı arasında bir bozulmuş güven ilişkisi olduğunu size bildirir.

  ![Örnek ATA ekranı bozulmuş güven](media/broken-trust-sa.png)


## <a name="known-issues"></a>Bilinen sorunlar

- ATA 1.7 ve hemen ATA 1.8 için ATA Gateway bileşenleri güncelleştirmeden güncelleştirirseniz ATA 1.8 geçiremezsiniz. ATA Center’ı 1.8 sürümüne güncelleştirmeden önce tüm Gateway’leri sürüm 1.7.1 veya 1.7.2’ye güncelleştirmek zorunludur.

- Tam geçiş gerçekleştirme seçeneğini seçerseniz veritabanı boyutuna bağlı olarak, geçiş çok uzun zaman alabilir. Geçiş seçeneklerinizi belirlerken tahmini süre görüntülenir; hangisini seçeceğinizden karar vermeden önce buna dikkat edin. 


## <a name="whats-next"></a>Sırada ne var?

-   ATA’nın ağınıza nasıl uyum sağladığı hakkında daha fazla bilgi için: [ATA mimarisi](ata-architecture.md)

-   ATA’nın dağıtımına başlamak için: [ATA’yı yükleme](install-ata-step1.md)

## <a name="related-videos"></a>İlgili videolar
- [Güvenlik topluluğuna katılmak](https://channel9.msdn.com/Shows/Microsoft-Security/Join-the-Security-Community)
- [ATA dağıtımı genel bakış](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)


## <a name="see-also"></a>Ayrıca bkz:
[ATA şüpheli etkinlik playbook](http://aka.ms/ataplaybook)
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
