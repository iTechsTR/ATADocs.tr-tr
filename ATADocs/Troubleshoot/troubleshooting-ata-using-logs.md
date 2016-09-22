---
title: "ATA günlüklerini kullanarak ATA sorunlarını giderme | Microsoft ATA"
description: "Sorunları gidermek için ATA günlüklerini nasıl kullanabileceğiniz açıklanır"
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: b8ad5511-8893-4d1d-81ee-b9a86e378347
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ee5f60e43f50562e7a7309eafa3b52cf946b0d3b
ms.openlocfilehash: 493f255ae09b51d27079a186bb802f0f3f9706bc


---

*Uygulama hedefi: Advanced Threat Analytics sürüm 1.7*



# ATA günlüklerini kullanarak ATA sorunlarını giderme
ATA günlükleri, ATA’nın her bileşeninin belirli bir anda neler yaptığı konusunda fikir edinmenizi sağlar.

## ATA Gateway günlükleri
Bu bölümde, ATA Gateway’e yapılan her gönderme aynı zamanda ATA Lightweight Gateway için de uygundur. 

ATA Gateway günlükleri ATA’nın yüklendiği konumda, **Logs** adlı bir alt klasörde yer alır; varsayılan konum şu şekildedir:  . Varsayılan yükleme konumunda, şu yolda bulunabilir: **C:\Program Files\Microsoft Advanced Threat Analytics\Gateway\Logs**.

ATA Gateway’in günlükleri şunlardır:

-   **Microsoft.Tri.Gateway.log** – Bu günlük, ATA Gateway’de gerçekleşen her şeyi (çözüm ve hatalar da dahil) içerir. Ana kullanım alanı, gerçekleşen tüm işlemlerin tarih sırasına göre genel durumunu elde etmektir.

-   **Microsoft.Tri.Gateway-Resolution.log** – Bu günlük ATA Gateway tarafından trafikte görülen varlıkların çözüm ayrıntılarını içerir. Ana kullanım alanı, varlıkların çözüm sorunlarını incelemektir.

-   **Microsoft.Tri.Gateway-Errors.log** – Bu günlük yalnızca ATA Gateway tarafından yakalanan hataları içerir. Ana kullanım alanı, sistem durumu denetimleri yapmak ve belirli zamanlarla ilintili olması gereken sorunları incelemektir.

-   **Microsoft.Tri.Gateway-ExceptionStatistics.log** – Bu günlük tüm benzer hataları ve özel durumları gruplandırır ve bunların sayısını sayar.
    Bu dosya ATA Gateway hizmeti her başladığında boş olarak başlar ve dakikada bir kere güncelleştirilir. Asıl amacı ATA Gateway’de herhangi bir yeni hata veya sorun olup olmadığını anlamaktır (hatalar gruplandığından dosyayı okumak ve yeni bir sorun olup olmadığını anlamak kolaydır).
-   **Microsoft.Tri.Gateway.Updater.log** - Bu günlük, otomatik olarak güncelleştirilecek şekilde yapılandırıldıysa, ağ geçidini güncelleştirmekten sorumlu ağ geçidi güncelleştiricisi işlemi için kullanılır. ATA Lightweight Gateway’de ağ geçidi güncelleştiricisi işlemi ayrıca ATA Lightweight Gateway’in kaynak sınırlamalarından da sorumludur.
-   **Microsoft.Tri.Gateway.Updater-ExceptionStatistics.log** - Bu günlük tüm benzer hataları ve özel durumları gruplandırır ve bunların sayısını sayar. ATA Updater hizmeti her başlatıldığında bu dosya boş olur ve dakikada bir güncelleştirilir. ATA Updater ile ilgili herhangi yeni bir hata veya sorun olup olmadığını anlamanıza olanak tanır. Yeni hata veya sorun olup olmadığını hızlıca anlamayı kolaylaştırmak için hatalar gruplandırılır.

> [!NOTE]
> İlk üç günlük dosyasının boyut üst sınırı 50 MB’dir. Bu boyuta ulaşıldığında, yeni günlük dosyası açılır ve önceki dosya "&lt;özgün dosya adı&gt;-Arşivlendi-00000" olarak yeniden adlandırılır; buradaki sayı her yeniden adlandırmada artar. Aynı türden 10’dan fazla dosya zaten varsa, varsayılan olarak en eskisi silinir.

## ATA Center günlükleri
ATA Center günlükleri, **Logs** adlı alt klasörde yer alır. Varsayılan yükleme konumunda, şu yolda bulunabilir: **C:\Program Files\Microsoft Advanced Threat Analytics\Center\Logs**".
> [!Note]
> Daha önce IIS günlükleri altında bulunan ATA konsolu günlükleri artık ATA Center günlükleri altında bulunmaktadır.

ATA Center’ın günlükleri şunlardır:

-   **Microsoft.Tri.Center.log** – Bu günlük, ATA Center’da gerçekleşen her şeyi (algılamalar ve hatalar da dahil) içerir. Ana kullanım alanı, gerçekleşen tüm işlemlerin tarih sırasına göre genel durumunu elde etmektir.

-   **Microsoft.Tri.Center Detection.log** – Bu günlük yalnızca ATA Center’ın algılama ayrıntılarını içerir. Ana kullanım alanı, algılama sorunları incelemektir.

-   **Microsoft.Tri.Center-Errors.log** – Bu günlük yalnızca ATA Center tarafından yakalanan hataları içerir. Ana kullanım alanı, sistem durumu denetimleri yapmak ve belirli zamanlarla ilintili olması gereken sorunları incelemektir.

-   **Microsoft.Tri.Center-ExceptionStatistics.log** – Bu günlük tüm benzer hataları ve özel durumları gruplandırır ve bunların sayısını sayar.
    ATA Center hizmeti her başlatıldığında bu dosya boş olur ve dakikada bir güncelleştirilir. Ana kullanım alanı, ATA Center’da yeni hatalar veya sorunlar olup olmadığını anlamaktır. Hatalar gruplandırıldığından, yeni hata veya sorunlar olup olmadığı kolayca anlaşılabilir.

> [!NOTE]
> İlk üç günlük dosyasının boyut üst sınırı 50 MB’dir. Bu boyuta ulaşıldığında, yeni günlük dosyası açılır ve önceki dosya "&lt;özgün dosya adı&gt;-Arşivlendi-00000" olarak yeniden adlandırılır; buradaki sayı her yeniden adlandırmada artar. Aynı türden 10’dan fazla dosya zaten varsa, varsayılan olarak en eskisi silinir.


## ATA Dağıtım günlükleri
ATA dağıtım günlükleri, ürünü yükleyen kullanıcının Temp dizininde yer alır. Varsayılan yükleme konumunda, şu yolda bulunabilir: **C:\Users\Administrator\AppData\Local\Temp** (veya %temp% dizininden bir dizin yukarıda).

ATA Center dağıtım günlükleri:

-   **Microsoft Advanced Threat Analytics Center_20150601104213.log** - Bu günlük, ATA Center’ın dağıtım işlemindeki adımları listeler. Ana kullanım alanı, ATA Center dağıtım işlemini izlemektir.

-   **Microsoft Advanced Threat Analytics Center_20150601104213_0_MongoDBPackage.log** - Bu günlük, ATA Center’da MongoDB dağıtım işleminin adımlarını listeler. Ana kullanım alanı, MongoDB dağıtım işlemini izlemektir.

-   **Microsoft Advanced Threat Analytics Center_20150601104213_1_MsiPackage.log** - Bu günlük dosyası, ATA Center ikili dosyalarının dağıtım işlemindeki adımları listeler. Ana kullanım alanı, ATA Center ikili dosyalarının dağıtımını izlemektir.

ATA Gateway ve ATA Lightweight Gateway dağıtım günlükleri:

-   **Microsoft Advanced Threat Analytics Gateway_20151214014801.log** - Bu günlük, ATA Gateway’in dağıtım işlemindeki adımları listeler. Ana kullanım alanı, ATA Gateway dağıtım işlemini izlemektir.

-   **Microsoft Advanced Threat Analytics Gateway_20151214014801_001_MsiPackage.log** - Bu günlük dosyası, ATA Gateway ikili dosyalarının dağıtım işlemindeki adımları listeler. Ana kullanım alanı, ATA Gateway ikili dosyalarının dağıtımını izlemektir.


## Ayrıca Bkz.
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [ATA kapasite planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [Olay koleksiyonunu yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [Windows olay iletme özelliğini yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Aug16_HO5-->


