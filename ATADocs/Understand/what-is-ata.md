---
title: Microsoft Advanced Threat Analytics (ATA) nedir? | Microsoft ATA
description: "Microsoft Advanced Threat Analytics (ATA) çözümünün ne olduğu ve ne tür kuşkulu etkinlikleri algılayabildiği açıklanır"
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 283e7b4e-996a-4491-b7f6-ff06e73790d2
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e3b690767e5c6f5561a97a73eccfbf50ddb04148
ms.openlocfilehash: c2f8d642f5ab0927448730453873a5b6271b3d2b


---

*Uygulama hedefi: Advanced Threat Analytics sürüm 1.7*


## Advanced Threat Analytics nedir?
Advanced Threat Analytics (ATA), kuruluşunuzu çeşitli türlerdeki, gelişmiş ve hedefe yönelik siber saldırıların yanı sıra dahili tehditlerden de korumaya yardımcı olan şirket içi bir platformdur.

## ATA nasıl çalışır?
ATA, kuruluştaki kullanıcıların ve diğer varlıkların davranışlarını öğrenmek ve bunlar hakkında davranışsal bir profil oluşturmak için ağınızdaki günlükler ve olaylar gibi birden fazla veri kaynağından bilgiler alır.
ATA, olayları ve günlükleri şuralardan alabilir:

-   SIEM Tümleştirmesi
-   Windows Olay İletme (WEF)

ATA ayrıca, kimlik doğrulaması, yetkilendirme ve bilgi toplama için birden çok protokoldeki (Kerberos, DNS, RPC, NTLM vb.) ağ trafiğini yakalamak ve ayrıştırmak üzere özel bir ağ ayrıştırma altyapısından faydalanır. Bu bilgiler ATA tarafından şu yollarla toplanır:

-   Etki Alanı Denetleyicilerinden ve DNS sunucularından ATA Gateway’e bağlantı noktası yansıtma
-   Doğrudan Etki Alanı Denetleyicilerinde bir ATA Lightweight Gateway (LGW) dağıtma

ATA mimarisi hakkında daha fazla bilgi için bkz. [ATA Mimarisi](/advanced-threat-analytics/plan-design/ata-architecture).

ATA tanıtım videomuza göz atın!
<iframe width="560" height="315" src="https://www.youtube.com/embed/0nA9FeTRZFw" frameborder="0" allowfullscreen></iframe>

## ATA ne yapar?

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
ATA bu şüpheli etkinlikleri algılar ve Kim, Ne, Ne Zaman ve Nasıl sorularına yönelik net bir bakış sağlayarak bilgileri ATA konsolunda sunar. Burada, basit, kullanıcı dostu bir panoda, ATA’nın ağınızdaki İstemci 1 ve İstemci 2 bilgisayarları üzerinde Karma Geçişi saldırısı denendiğinden şüphelendiği konusundaki uyarısı görülüyor.

 ![Örnek ATA ekranı karma geçişi](media/sample screen pth.png)

ATA, aşağıda örnekleri verilen ve ağınızdaki kullanıcılarla cihazlarda görülen şüpheli etkinliklerle anormal davranışları ortaya çıkarmak için davranışsal analiz kullanarak ve Makine Öğrenimi özelliğinden faydalanarak **Anormal davranışları** algılar:

-   Anormal oturum açma işlemleri
-   Bilinmeyen tehditler
-   Parola paylaşımı
-   Yanal hareket


Bu tür şüpheli etkinlikleri ATA Panosunda görüntüleyebilirsiniz. Aşağıdaki örnekte, bir kullanıcı her zaman erişmediği 4 bilgisayara erişir ve bu bir uyarı nedeni olabileceğinden, ATA sizi uyarır.

 ![Örnek ATA ekranı anormal davranış](media/sample screen abnormal behavior.png) 

ATA ayrıca, aşağıdakiler gibi **güvenlik sorunlarını ve risklerini** de algılar:

-   Bozulmuş güven
-   Zayıf protokoller
-   Bilinen protokol güvenlik açıkları

Bu tür şüpheli etkinlikleri ATA Panosunda görüntüleyebilirsiniz. Aşağıdaki örnekte, ATA, ağınızdaki bir bilgisayar ve etki alanı arasında bir bozulmuş güven ilişkisi olduğunu size bildirir.

  ![Örnek ATA ekranı bozulmuş güven](media/sample screen broken trust.png)


## Sırada ne var?

-   ATA’nın ağınıza nasıl uyum sağladığı hakkında daha fazla bilgi için: [ATA mimarisi](/advanced-threat-analytics/plan-design/ata-architecture)

-   ATA’nın dağıtımına başlamak için: [ATA’yı yükleme](/advanced-threat-analytics/deploy-use/install-ata)

## Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Aug16_HO5-->


