---
title: "Advanced Threat Analytics telemetri ayarlarını yönetme | Microsoft Docs"
description: "ATA tarafından toplanan veriler açıklanır ve veri toplamayı kapatma adımları sağlanır."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 07/3/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 8c1c7a1b-a3de-4105-9fd0-08a061952172
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: b0e94ca7d817d6d5735921fefd7c9f4cf2cbd866
ms.sourcegitcommit: fa50f37b134d7579d7c310852dff60e5f1996eaa
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# Telemetri Ayarlarını Yönetme
<a id="manage-telemetry-settings" class="xliff"></a>
Advanced Threat Analytics (ATA), ATA hakkında anonim telemetri verileri toplar ve bu verileri HTTPS bağlantısı üzerinden Microsoft sunucularına iletir.  Bu veriler Microsoft tarafından ATA’nın gelecek sürümlerini geliştirmeye yardımcı olmak için kullanılır.

## Toplanan veriler
<a id="data-collected" class="xliff"></a>
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

- Sistem durumu sorunları - Aşağıdaki anonimleştirilmiş veriler her sistem durumu sorunu için toplanır:

    (Bilgisayar adları, kullanıcı adları ve IP adresleri toplanmaz)

    -   Sistem durumu sorunu türü

    -   Sistem durumu sorunu kimliği

    -   Durum

    -   Başlangıç ve Bitiş Zamanı

- ATA Konsolu URL adresleri - ATA Konsolu ile kullanılan (ATA Konsolu içinde ziyaret edilen) sayfaların URL adresleri.


### Veri toplamayı devre dışı bırakma
<a id="disable-data-collection" class="xliff"></a>
Telemetri verilerinin toplanmasını ve Microsoft’a gönderilmesini durdurmak için aşağıdaki adımları izleyin:

1.  ATA Konsolu’nda oturum açın, araç çubuğundaki üç noktaya tıklayın ve **Hakkında**’yı seçin.

2.  **Gelecekte müşteri deneyiminizi geliştirmeye yardımcı olmak için bize kullanım bilgilerini gönderin** kutusunun işaretini kaldırın.

## Ayrıca Bkz.
<a id="see-also" class="xliff"></a>
- [Olay günlüğünü kullanarak ATA sorunlarını giderme](troubleshooting-ata-using-logs.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
