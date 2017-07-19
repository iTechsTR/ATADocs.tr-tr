---
title: "ATA Raporları ile çalışma | Microsoft Docs"
description: "Ağınızı izlemek için ATA’da nasıl rapor oluşturabileceğinizi açıklar."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 38ea49b5-cd5e-43e5-bc39-5071f759633b
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 4f29dfcc8b18ff755f6c0dcdaa08eaa807b08072
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*


# <a name="ata-reports"></a>ATA Raporları

Konsoldaki ATA raporları bölümü, size sistem durumu bilgileri (sistem durumu ve ortamınızda algılanan şüpheli etkinlikler) sağlayan raporlar oluşturmanıza imkan tanır.

Raporlar sayfasına erişmek için menü çubuğundaki rapor simgesine tıklayın: ![rapor simgesi](./media/ata-report-icon.png).
Kullanılabilir raporlar şunlardır: 
- Özet raporu: Özeti raporu, bir sistem durumu panosu sunar. Üç sekme görüntüleyebilirsiniz: Ağınızda algılananlar için bir **Özet** sekmesi, ilgilenmeniz gereken şüpheli etkinlikleri listeleyen **Şüpheli etkinlikleri aç** sekmesi ve ilgilenmeniz gereken ATA sistem durumu sorunlarını listeleyen **Sistem durumu sorunlarını aç** sekmesi. Şüpheli etkinlikler ve sistem durumu sorunları türlerine göre listelenmiştir. 
- Gizli grup değişiklikleri: Gizli gruplara (yöneticiler gibi) yapılan tüm değişiklikler bu raporda listelenir.

Bir rapor oluşturmak için iki yolu vardır: isteğe bağlı olarak veya e-postanıza düzenli aralıklarla gönderilmek üzere rapor zamanlayarak.

İsteğe bağlı bir rapor oluşturmak için:

1. ATA konsolu menü çubuğundaki rapor simgesine tıklayın: ![rapor simgesi](./media/ata-report-icon.png).
2. **Özet** veya **Gizli grup değişiklikleri** altında **Şu tarihten** ve **Şu tarihe** kısımlarını ayarlayın ve **İndir**’e tıklayın. 
![raporlar](./media/reports.png)

Zamanlanmış bir rapor ayarlamak için:
 
1. **Raporlar** sayfasında **Zamanlanmış rapor ayarla**’ya tıklayın veya ATA Konsolu yapılandırma sayfasında bulunan Bildirimler ve Raporlar altında **Zamanlanmış raporlar**’a tıklayın.

   ![Rapor zamanlama](./media/ata-sched-reports.png)

2. **Özet** veya **Gizli grup değişiklikleri**’nin yanında bulunan **Zamanla**’ya tıklayarak raporların iletileceği sıklığı ve e-posta adresini ayarlayın, e-posta adreslerinin yanındaki artı işaretine tıklayarak adres ekleyin ve daha sonra **Kaydet**’e basın.

   ![Rapor sıklığı ve e-postayı zamanlama](./media/sched-report1.png)


> [!NOTE]
> Zamanlanmış raporlar, e-posta yoluyla ve yalnızca **Yapılandırma** bölümündeki Bildirimler ve Raporlar’dan **Posta sunucusu**’nu seçerek bir e-posta sunucusu yapılandırdıysanız gönderilebilir.


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
