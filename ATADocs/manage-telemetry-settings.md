---
title: Advanced Threat Analytics sistem tarafından oluşturulan günlükleri yönetme | Microsoft Docs
description: ATA tarafından toplanan veriler açıklanır ve veri toplamayı kapatma adımları sağlanır.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 8c1c7a1b-a3de-4105-9fd0-08a061952172
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 7f1a0cb9a7e237259a9b77b96e16c6680336c2b0
ms.sourcegitcommit: 324dc941282f2948366afa5a919bda0b029bd59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2018
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*



# <a name="manage-system-generated-logs-note"></a>Sistem tarafından oluşturulan günlükleri Yönet > [!NOTE]
> Görüntüleme veya kişisel verileri silme düşünüyorsanız, lütfen Microsoft'un Kılavuzu gözden [Microsoft Uyumluluk Yöneticisi](https://servicetrust.microsoft.com/ComplianceManager) ve [Microsoft 365 Kurumsal uyumluluk sitesininGDPRbölümünü](https://docs.microsoft.com/en-us/microsoft-365/compliance/gdpr). GDPR hakkında genel bilgi arıyorsanız bkz [Hizmeti'ne güvenen portal GDPR bölümünü](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).


Advanced Threat Analytics (ATA), ATA hakkında anonim sistem tarafından oluşturulan günlük verilerini toplar ve Microsoft sunucularına bir HTTPS bağlantısı üzerinden verileri iletir.  Bu veriler Microsoft tarafından ATA’nın gelecek sürümlerini geliştirmeye yardımcı olmak için kullanılır.

## <a name="data-collected"></a>Toplanan veriler
Anonim veriler toplanır aşağıdaki parametreleri içerir:

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

- Ziyaret edilen sayfalar ATA Konsolu'nda ATA Konsolu URL'si adresleri - diğer bir deyişle, ATA konsolu kullanılırken URL adresi.


### <a name="disable-data-collection"></a>Veri toplamayı devre dışı bırakma
Telemetri verilerinin toplanmasını ve Microsoft’a gönderilmesini durdurmak için aşağıdaki adımları izleyin:

1.  ATA Konsolu’nda oturum açın, araç çubuğundaki üç noktaya tıklayın ve **Hakkında**’yı seçin.

2.  **Gelecekte müşteri deneyiminizi geliştirmeye yardımcı olmak için bize kullanım bilgilerini gönderin** kutusunun işaretini kaldırın.

## <a name="see-also"></a>Ayrıca bkz:
- [Olay günlüğünü kullanarak ATA sorunlarını giderme](troubleshooting-ata-using-logs.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
