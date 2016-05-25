---
# required metadata

title: ATA günlüklerini kullanarak ATA sorunlarını giderme | Microsoft Advanced Threat Analytics
description: Sorunları gidermek için ATA günlüklerini nasıl kullanabileceğiniz açıklanır
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: b8ad5511-8893-4d1d-81ee-b9a86e378347

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ATA günlüklerini kullanarak ATA sorunlarını giderme
ATA günlükleri, ATA’nın her bileşeninin belirli bir anda neler yaptığı konusunda fikir edinmenizi sağlar.

## ATA Gateway günlükleri
ATA Gateway günlükleri, **Logs** adlı alt klasörde yer alır. Varsayılan yükleme konumunda, şu yolda bulunabilir: **C:\Program Files\Microsoft Advanced Threat Analytics\Gateway\Logs**.

ATA Gateway’in günlükleri şunlardır:

-   **Microsoft.Tri.Gateway.log** – Bu günlük, ATA Gateway’de gerçekleşen her şeyi (çözüm ve hatalar da dahil) içerir. Ana kullanım alanı, gerçekleşen tüm işlemlerin tarih sırasına göre genel durumunu elde etmektir.

-   **Microsoft.Tri.Gateway-Resolution.log** – Bu günlük ATA Gateway tarafından trafikte görülen varlıkların çözüm ayrıntılarını içerir. Ana kullanım alanı, varlıkların çözüm sorunlarını incelemektir.

-   **Microsoft.Tri.Gateway-Errors.log** – Bu günlük yalnızca ATA Gateway tarafından yakalanan hataları içerir. Ana kullanım alanı, sistem durumu denetimleri yapmak ve belirli zamanlarla ilintili olması gereken sorunları incelemektir.

-   **Microsoft.Tri.Gateway-ExceptionStatistics.log** – Bu günlük tüm benzer hataları ve özel durumları gruplandırır ve bunların sayısını sayar.
    ATA Gateway hizmeti her başlatıldığında bu dosya boş olur ve dakikada bir güncelleştirilir. Ana kullanım alanı, ATA Gateway’de yeni hatalar veya sorunlar olup olmadığını anlamaktır. Hatalar gruplandırıldığından, daha kolay okunabilir ve yeni bir tür hata veya sorun olup olmadığı görülebilir.

> [!NOTE]
> İlk üç günlük dosyasının boyut üst sınırı 50 MB’dir. Bu boyuta ulaşıldığında, yeni günlük dosyası açılır ve önceki dosya "&lt;özgün dosya adı&gt;-Arşivlendi-00000" olarak yeniden adlandırılır; buradaki sayı her yeniden adlandırmada artar.

### ATA Center günlükleri
ATA Center günlükleri, **Logs** adlı alt klasörde yer alır. Varsayılan yükleme konumunda, şu yolda bulunabilir: **C:\Program Files\Microsoft Advanced Threat Analytics\Center\Logs**".

ATA Center’ın günlükleri şunlardır:

-   **Microsoft.Tri.Center.log** – Bu günlük, ATA Center’da gerçekleşen her şeyi (algılamalar ve hatalar da dahil) içerir. Ana kullanım alanı, gerçekleşen tüm işlemlerin tarih sırasına göre genel durumunu elde etmektir.

-   **Microsoft.Tri.Center Detection.log** – Bu günlük yalnızca ATA Center’ın algılama ayrıntılarını içerir. Ana kullanım alanı, algılama sorunları incelemektir.

-   **Microsoft.Tri.Center-Errors.log** – Bu günlük yalnızca ATA Center tarafından yakalanan hataları içerir. Ana kullanım alanı, sistem durumu denetimleri yapmak ve belirli zamanlarla ilintili olması gereken sorunları incelemektir.

-   **Microsoft.Tri.Center-ExceptionStatistics.log** – Bu günlük tüm benzer hataları ve özel durumları gruplandırır ve bunların sayısını sayar.
    ATA Center hizmeti her başlatıldığında bu dosya boş olur ve dakikada bir güncelleştirilir. Ana kullanım alanı, ATA Center’da yeni hatalar veya sorunlar olup olmadığını anlamaktır. Hatalar gruplandırıldığından, daha kolay okunabilir ve yeni bir tür hata veya sorun olup olmadığı görülebilir.

> [!NOTE]
> İlk üç günlük dosyasının boyut üst sınırı 50 MB’dir. Bu boyuta ulaşıldığında, yeni günlük dosyası açılır ve önceki dosya "&lt;özgün dosya adı&gt;-Arşivlendi-00000" olarak yeniden adlandırılır; buradaki sayı her yeniden adlandırmada artar.

### ATA Konsolu günlükleri
ATA Konsolu günlükleri (yönetim API’si günlükleri) **Logs** adlı alt klasörde yer alır. Varsayılan yükleme konumunda, şu yolda bulunabilir: **C:\Program Files\Microsoft Advanced Threat Analytics\Center\Management\Logs**.

ATA Konsolu’nun günlükleri şunlardır:

-   **w3wp.log** – Bu günlük yönetim işleminde (IIS) gerçekleşen her şeyi içerir.


-   **w3wp-Errors.log** – Bu günlük yalnızca yönetim işlemi (IIS) tarafından yakalanan hataları içerir.


-   **8e75f9f1-ExceptionStatistics.log** – Bu günlük tüm benzer hataları ve özel durumları gruplandırır ve bunların sayısını sayar.
    Gateway hizmeti her başlatıldığında bu dosya boş olur ve dakikada bir güncelleştirilir. Ana kullanım alanı, ATA Center’da yeni hatalar veya sorunlar olup olmadığını anlamaktır. Hatalar gruplandırıldığından, daha kolay okunabilir ve yeni bir tür hata veya sorun olup olmadığı görülebilir.

> [!NOTE]
> İlk iki günlük dosyasının boyut üst sınırı 50 MB’dir. Bu boyuta ulaşıldığında, yeni günlük dosyası açılır ve önceki dosya "&lt;özgün dosya adı&gt;-Arşivlendi-00000" olarak yeniden adlandırılır; buradaki sayı her yeniden adlandırmada artar.

### ATA Dağıtım günlükleri
ATA dağıtım günlükleri, ürünü yükleyen kullanıcının Temp dizininde yer alır. Varsayılan yükleme konumunda, şu yolda bulunabilir: **C:\Users\Administrator\AppData\Local\Temp** (veya %temp% dizininden bir dizin yukarıda).

ATA Center dağıtım günlükleri:

-   **Microsoft Advanced Threat Analytics Center_20150601104213.log** - Bu günlük, ATA Center’ın dağıtım işlemindeki adımları listeler. Ana kullanım alanı, ATA Center dağıtım işlemini izlemektir.

-   **Microsoft Advanced Threat Analytics Center_20150601104213_0_MongoDBPackage.log** - Bu günlük, ATA Center’da MongoDB dağıtım işleminin adımlarını listeler. Ana kullanım alanı, MongoDB dağıtım işlemini izlemektir.

-   **Microsoft Advanced Threat Analytics Center_20150601104213_1_MsiPackage.log** - Bu günlük dosyası, ATA Center ikili dosyalarının dağıtım işlemindeki adımları listeler. Ana kullanım alanı, ATA Center ikili dosyalarının dağıtımını izlemektir.

ATA Gateway dağıtım günlükleri:

-   **Microsoft Advanced Threat Analytics Gateway_20151214014801.log** - Bu günlük, ATA Gateway’in dağıtım işlemindeki adımları listeler. Ana kullanım alanı, ATA Gateway dağıtım işlemini izlemektir.

-   **Microsoft Advanced Threat Analytics Gateway_20151214014801_001_MsiPackage.log** - Bu günlük dosyası, ATA Gateway ikili dosyalarının dağıtım işlemindeki adımları listeler. Ana kullanım alanı, ATA Gateway ikili dosyalarının dağıtımını izlemektir.


<!--HONumber=Apr16_HO4-->


