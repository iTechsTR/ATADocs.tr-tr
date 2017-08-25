---
title: Microsoft Advanced Threat Analytics (ATA) nedir? | Microsoft Docs
description: "Microsoft Advanced Threat Analytics (ATA) çözümünün ne olduğu ve ne tür kuşkulu etkinlikleri algılayabildiği açıklanır"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 08/20/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 283e7b4e-996a-4491-b7f6-ff06e73790d2
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: db2133e05fb7d2390f4b7e05dd219be71bf4e157
ms.sourcegitcommit: 129bee06ff89b72d21b64f9aa0d1a29f66bf9153
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*


# <a name="what-is-advanced-threat-analytics"></a>Advanced Threat Analytics nedir?
Advanced Threat Analytics (ATA), kuruluşunuzu çeşitli türlerdeki, gelişmiş ve hedefe yönelik siber saldırıların yanı sıra dahili tehditlerden de korumaya yardımcı olan şirket içi bir platformdur.

## <a name="how-ata-works"></a>ATA nasıl çalışır?

ATA; birden çok kimlik doğrulaması, yetkilendirme ve bilgi toplama protokolündeki (Kerberos, DNS, RPC, NTLM vb.) ağ trafiğini yakalamak ve ayrıştırmak üzere özel bir ağ ayrıştırma altyapısından faydalanır. Bu bilgiler ATA tarafından şu yollardan biriyle toplanır:

-   Etki Alanı Denetleyicileri ve DNS sunucularından ATA Gateway’e bağlantı noktası yansıtma ve/veya
-   Doğrudan Etki Alanı Denetleyicilerinde bir ATA Lightweight Gateway (LGW) dağıtma

ATA, kuruluştaki kullanıcıların ve diğer varlıkların davranışlarını öğrenmek ve bunlar hakkında davranış profili oluşturmak için ağınızdaki günlükler ve olaylar gibi birden çok veri kaynağından bilgiler alır.
ATA, olayları ve günlükleri şuralardan alabilir:

-   SIEM Tümleştirmesi
-   Windows Olay İletme (WEF)
-   Doğrudan Windows Olay Toplayıcısı’ndan (Lightweight Gateway için)


ATA mimarisi hakkında daha fazla bilgi için bkz. [ATA Mimarisi](ata-architecture.md).

## <a name="what-does-ata-do"></a>ATA ne yapar?

ATA teknolojisi siber saldırı ölüm zincirinin aşağıda belirtilen çeşitli aşamalarına odaklanarak birden çok şüpheli etkinliği algılar:

-   Keşif aşamasında saldırganlar ortamın yapılandırılma şekli ile ortamda bulunan çeşitli varlıklar hakkında bilgi toplar ve genellikle saldırının sonraki aşamaları için planlarını oluşturur.
-   Yanal hareket döngüsü aşamasında saldırgan, ağınızdaki saldırı yüzeyini genişletmek için zaman ve çaba harcar.
-   Etki alanı üzerinde egemenlik (kalıcılık) aşamasında saldırgan, çeşitli giriş noktaları, kimlik bilgileri ve teknikler kullanarak eylemlerini sürdürmesine olanak sağlayan bilgileri yakalar. 

Bu siber saldırı aşamaları, hangi türde bir şirket saldırıya uğramış veya ne tür bilgiler hedeflenmiş olursa olsun birbirine benzer ve tahmin edilebilirdir.
ATA, başlıca üç türdeki saldırıları arar: kötü amaçlı saldırılar, olağan dışı davranışlar ve güvenlik sorunlarıyla riskleri.

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

Algılamaların ve açıklamalarının tam listesi için lütfen bkz. [ATA Hangi Şüpheli Etkinlikleri Algılayabilir?](ata-threats.md)
ATA bu şüpheli etkinlikleri algılar ve Kim, Ne, Ne Zaman ve Nasıl sorularına yönelik net bir bakış sağlayarak bilgileri ATA konsolunda sunar. Burada basit, kullanımı kolay bir panoyu izleyerek ATA’nın ağınızdaki İstemci 1 ve İstemci 2 bilgisayarları üzerinde bir Pass-the-Ticket saldırısı denemesinden şüphelendiğine dair bir uyarı aldığınızı görüyorsunuz.

 ![örnek ATA ekranı pass-the-ticket](media/pass_the_ticket_sa.png)

ATA, aşağıda örnekleri verilen ve ağınızdaki kullanıcılarla cihazlarda görülen şüpheli etkinliklerle anormal davranışları ortaya çıkarmak için davranışsal analiz kullanarak ve Makine Öğrenimi özelliğinden faydalanarak **Anormal davranışları** algılar:

-   Anormal oturum açma işlemleri
-   Bilinmeyen tehditler
-   Parola paylaşımı
-   Yanal hareket
-   Gizli grup değişiklikleri


Bu tür şüpheli etkinlikleri ATA Panosunda görüntüleyebilirsiniz. Aşağıdaki örnekte, bir kullanıcı her zaman erişmediği 4 bilgisayara erişir ve bu bir uyarı nedeni olabileceğinden, ATA sizi uyarır.

 ![Örnek ATA ekranı anormal davranış](media/abnormal-behavior-sa.png) 

ATA ayrıca, aşağıdakiler gibi **güvenlik sorunlarını ve risklerini** de algılar:

-   Bozulmuş güven
-   Zayıf protokoller
-   Bilinen protokol güvenlik açıkları

Bu tür şüpheli etkinlikleri ATA Panosunda görüntüleyebilirsiniz. Aşağıdaki örnekte, ATA, ağınızdaki bir bilgisayar ve etki alanı arasında bir bozulmuş güven ilişkisi olduğunu size bildirir.

  ![Örnek ATA ekranı bozulmuş güven](media/broken-trust-sa.png)


## <a name="known-issues"></a>Bilinen sorunlar

- ATA 1.7’ye ve hemen ardından ATA Gateway’lerini güncelleştirmeden önce ATA 1.8’e güncelleştirirseniz ATA 1.8’e geçemezsiniz. ATA Center’ı 1.8 sürümüne güncelleştirmeden önce tüm Gateway’leri sürüm 1.7.1 veya 1.7.2’ye güncelleştirmek zorunludur.

- Tam geçiş gerçekleştirme seçeneğini seçerseniz veritabanı boyutuna bağlı olarak, geçiş çok uzun zaman alabilir. Geçiş seçeneklerinizi belirlerken tahmini süre görüntülenir, lütfen hangi seçeneği belirleyeceğinize karar verirken buna dikkat edin. 


## <a name="whats-next"></a>Sırada ne var?

-   ATA’nın ağınıza nasıl uyum sağladığı hakkında daha fazla bilgi için: [ATA mimarisi](ata-architecture.md)

-   ATA’nın dağıtımına başlamak için: [ATA’yı yükleme](install-ata-step1.md)

## <a name="related-videos"></a>İlgili videolar
- [Güvenlik topluluğu birleştirme](https://channel9.msdn.com/Shows/Microsoft-Security/Join-the-Security-Community)


## <a name="see-also"></a>Ayrıca Bkz.
[ATA kuşkulu etkinlik playbook](http://aka.ms/ataplaybook)
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
