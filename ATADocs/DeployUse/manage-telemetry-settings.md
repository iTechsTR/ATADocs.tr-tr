---
# required metadata

title: Telemetri Ayarlarını Yönetme | Microsoft Advanced Threat Analytics
description: ATA tarafından toplanan veriler açıklanır ve veri toplamayı kapatma adımları sağlanır.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 8c1c7a1b-a3de-4105-9fd0-08a061952172

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Telemetri Ayarlarını Yönetme
Advanced Threat Analytics (ATA), ATA hakkında anonim telemetri verileri toplar ve bu verileri HTTPS bağlantısı üzerinden Microsoft sunucularına iletir.  Bu veriler Microsoft tarafından ATA’nın gelecek sürümlerini geliştirmeye yardımcı olmak için kullanılır.

## Toplanan veriler
Şu veriler toplanır:

-   Hem ATA Center’dan hem de ATA Gateway’den performans sayaçları

-   ATA’nın lisanslı kopyalarından Ürün Kimliği

-   ATA Center’ın dağıtım tarihi

-   Dağıtılan ATA Gateway bileşenlerinin sayısı

-   Aşağıdaki Active Directory bilgileri:

    -   Alfabetik sıralamada adı en başta yer alan etki alanının Etki Alanı Kimliği

    -   Etki alanı denetleyicilerinin sayısı

    -   ATA tarafından bağlantı noktası yansıtma yoluyla izlenen etki alanı denetleyicilerinin sayısı

    -   Site sayısı

    -   Bilgisayar sayısı

    -   Grup sayısı

    -   Kullanıcı sayısı

-   Kuşkulu Etkinlikler – Her kuşkulu etkinlik için aşağıdaki veriler toplanır:

    (Bilgisayar adları, kullanıcı adları ve IP adresleri **toplanmaz**)

    -   Kuşkulu etkinliğin türü

    -   Kuşkulu etkinliğin kimliği

    -   Durum

    -   Başlangıç ve Bitiş Zamanı

    -   Sağlanan giriş

### Veri toplamayı devre dışı bırakma
Telemetri verilerinin toplanmasını ve Microsoft’a gönderilmesini durdurmak için aşağıdaki adımları izleyin:

1.  ATA Konsolu’nda oturum açın, araç çubuğundaki üç noktaya tıklayın ve **Hakkında**’yı seçin..

2.  **Gelecekte müşteri deneyiminizi geliştirmeye yardımcı olmak için bize kullanım bilgilerini gönderin** kutusunun işaretini kaldırın..

## Ayrıca Bkz.
- [Sürüm 1.5’teki yenilikler](whats-new-version-1.5.md)
- [Sürüm 1.4’teki yenilikler](whats-new-version-1.4.md)
- [Destek için forumumuzu gözden geçirin!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=Apr16_HO4-->


