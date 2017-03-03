---
title: "Advanced Threat Analytics telemetri ayarlarını yönetme | Microsoft Docs"
description: "ATA tarafından toplanan veriler açıklanır ve veri toplamayı kapatma adımları sağlanır."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 8c1c7a1b-a3de-4105-9fd0-08a061952172
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b28cb3a0da844b7c460c03726222bc775a9e47da
ms.openlocfilehash: 1b6da432e81bc42b772b2146213d2f24bee6231a


---

*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*



# <a name="manage-telemetry-settings"></a>Telemetri Ayarlarını Yönetme
Advanced Threat Analytics (ATA), ATA hakkında anonim telemetri verileri toplar ve bu verileri HTTPS bağlantısı üzerinden Microsoft sunucularına iletir.  Bu veriler Microsoft tarafından ATA’nın gelecek sürümlerini geliştirmeye yardımcı olmak için kullanılır.

## <a name="data-collected"></a>Toplanan veriler
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


### <a name="disable-data-collection"></a>Veri toplamayı devre dışı bırakma
Telemetri verilerinin toplanmasını ve Microsoft’a gönderilmesini durdurmak için aşağıdaki adımları izleyin:

1.  ATA Konsolu’nda oturum açın, araç çubuğundaki üç noktaya tıklayın ve **Hakkında**’yı seçin.

2.  **Gelecekte müşteri deneyiminizi geliştirmeye yardımcı olmak için bize kullanım bilgilerini gönderin** kutusunun işaretini kaldırın.

## <a name="see-also"></a>Ayrıca bkz.
- [Sürüm 1.6’daki yenilikler](/advanced-threat-analytics/understand-explore/whats-new-version-1.6)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Feb17_HO1-->


