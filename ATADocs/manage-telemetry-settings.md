---
title: Advanced Threat Analytics sistem tarafından oluşturulan günlükleri yönetme | Microsoft Docs
description: ATA tarafından toplanan veriler açıklanır ve veri toplamayı kapatma adımları sağlanır.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/26/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 8c1c7a1b-a3de-4105-9fd0-08a061952172
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 0db1054f47d462251577a4d5251c07e8cd6283e8
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133421"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="manage-system-generated-logs-note"></a>Sistem tarafından oluşturulan günlükleri Yönet > [!NOTE]

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

Gelişmiş Threat Analytics (ATA), ATA hakkında anonim sistem tarafından oluşturulan günlük verileri toplar ve Microsoft sunucuları için bir HTTPS bağlantısı üzerinden veri iletir.  Bu veriler Microsoft tarafından ATA’nın gelecek sürümlerini geliştirmeye yardımcı olmak için kullanılır.

## <a name="data-collected"></a>Toplanan veriler
Anonim veriler toplanır, aşağıdaki parametreleri içerir:

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

- Ziyaret edilen sayfalar ATA Konsolu'nda ATA Konsolu URL adresleri - diğer bir deyişle, ATA Konsolu URL adresleri.


### <a name="disable-data-collection"></a>Veri toplamayı devre dışı bırakma
Telemetri verilerinin toplanmasını ve Microsoft’a gönderilmesini durdurmak için aşağıdaki adımları izleyin:

1.  ATA Konsolu’nda oturum açın, araç çubuğundaki üç noktaya tıklayın ve **Hakkında**’yı seçin.

2.  **Gelecekte müşteri deneyiminizi geliştirmeye yardımcı olmak için bize kullanım bilgilerini gönderin** kutusunun işaretini kaldırın.

## <a name="see-also"></a>Ayrıca Bkz.
- [Olay günlüğünü kullanarak ATA sorunlarını giderme](troubleshooting-ata-using-logs.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
