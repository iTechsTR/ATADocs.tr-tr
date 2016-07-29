---
title: "Telemetri Ayarlarını yönetme | Microsoft ATA"
description: "ATA tarafından toplanan veriler açıklanır ve veri toplamayı kapatma adımları sağlanır."
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 8c1c7a1b-a3de-4105-9fd0-08a061952172
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f13750f9cdff98aadcd59346bfbbb73c2f3a26f0
ms.openlocfilehash: 7e849e9d902873cec7140a14b6f0709d3ef9ddd1


---

# Telemetri Ayarlarını Yönetme
Advanced Threat Analytics (ATA), ATA hakkında anonim telemetri verileri toplar ve bu verileri HTTPS bağlantısı üzerinden Microsoft sunucularına iletir.  Bu veriler Microsoft tarafından ATA’nın gelecek sürümlerini geliştirmeye yardımcı olmak için kullanılır.

## Toplanan veriler
Şu anonim veriler toplanır:

-   Hem ATA Center’dan hem de ATA Gateway’den performans sayaçları

-   ATA’nın lisanslı kopyalarından Ürün Kimliği

-   ATA Center’ın dağıtım tarihi

-   Dağıtılan ATA Gateway bileşenlerinin sayısı

-   Aşağıdaki anonim Active Directory bilgileri:

    -   Alfabetik sıralamada adı en başta yer alan etki alanının Etki Alanı Kimliği

    -   Etki alanı denetleyicilerinin sayısı

    -   ATA tarafından bağlantı noktası yansıtma yoluyla izlenen etki alanı denetleyicilerinin sayısı

    -   Site sayısı

    -   Bilgisayar sayısı

    -   Grup sayısı

    -   Kullanıcı sayısı

-   Kuşkulu Etkinlikler – Her kuşkulu etkinlik için aşağıdaki anonim veriler toplanır:

    (Bilgisayar adları, kullanıcı adları ve IP adresleri **toplanmaz**)

    -   Kuşkulu etkinliğin türü

    -   Kuşkulu etkinliğin kimliği

    -   Durum

    -   Başlangıç ve Bitiş Zamanı

    -   Sağlanan giriş

### Veri toplamayı devre dışı bırakma
Telemetri verilerinin toplanmasını ve Microsoft’a gönderilmesini durdurmak için aşağıdaki adımları izleyin:

1.  ATA Konsolu’nda oturum açın, araç çubuğundaki üç noktaya tıklayın ve **Hakkında**’yı seçin.

2.  **Gelecekte müşteri deneyiminizi geliştirmeye yardımcı olmak için bize kullanım bilgilerini gönderin** kutusunun işaretini kaldırın.

## Ayrıca Bkz.
- [Sürüm 1.6’daki yenilikler](/advanced-threat-analytics/understand-explore/whats-new-version-1.6)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jul16_HO4-->


