---
title: ATA Raporları ile çalışma | Microsoft Docs
description: Ağınızı izlemek için ATA’da nasıl rapor oluşturabileceğinizi açıklar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 38ea49b5-cd5e-43e5-bc39-5071f759633b
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 9a113d8d090c5a90a07043a0ef75e1be0fc840c3
ms.sourcegitcommit: 158bf048d549342f2d4689f98ab11f397d9525a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
ms.locfileid: "30202264"
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*


# <a name="ata-reports"></a>ATA Raporları

Konsoldaki ATA raporları bölümü, size sistem durumu bilgileri (sistem durumu ve ortamınızda algılanan şüpheli etkinlikler) sağlayan raporlar oluşturmanıza imkan tanır.

Raporlar sayfasına erişmek için menü çubuğundaki rapor simgesine tıklayın: ![rapor simgesi](./media/ata-report-icon.png).
Kullanılabilir raporlar şunlardır: 

- **Özet raporu**: Özeti raporu sistem durumu Panosu sunar. Üç sekme görüntüleyebilirsiniz: Ağınızda algılananlar için bir **Özet** sekmesi, ilgilenmeniz gereken şüpheli etkinlikleri listeleyen **Şüpheli etkinlikleri aç** sekmesi ve ilgilenmeniz gereken ATA sistem durumu sorunlarını listeleyen **Sistem durumu sorunlarını aç** sekmesi. Şüpheli etkinlikler ve sistem durumu sorunları türlerine göre listelenmiştir. 

- **Hassas gruplara değiştirilmesini**: Bu rapor, bir değişiklik (örneğin, Yöneticiler) hassas gruplara yapılan her zaman listeler.

- **Parolalar düz metinde gösterilen**: bazı hizmetler LDAP güvenli olmayan hesap kimlik bilgilerini düz metin olarak göndermek için protokolünü kullanır. Bu durum, hassas hesapları için bile oluşabilir. Ağ trafiğini izleme saldırganlar catch ve bu kimlik bilgileri kötü amaçlı olarak yeniden kullanabilirsiniz. Bu rapor, düz metin olarak olarak algılanan ATA gönderilen tüm kaynak bilgisayarı ve hesap parolalarını listeler. 

- **Yanal hareket yolları hassas hesaplarına**: Bu rapor, yanal hareket yolları sunulan hassas hesapları listeler. Daha fazla bilgi için bkz: [yanal hareket yolları](use-case-lateral-movement-path.md)

Bir rapor oluşturmak için iki yolu vardır: isteğe bağlı olarak veya e-postanıza düzenli aralıklarla gönderilmek üzere rapor zamanlayarak.

İsteğe bağlı bir rapor oluşturmak için:

1. ATA konsolu menü çubuğundaki rapor simgesine tıklayın: ![rapor simgesi](./media/ata-report-icon.png).

2. Altında seçilen rapor türünü ayarlayın **gelen** ve **için** tıklatın ve tarihleri **karşıdan**. 
 ![raporlar](./media/reports.png)

Zamanlanmış bir rapor ayarlamak için:
 
1. **Raporlar** sayfasında **Zamanlanmış rapor ayarla**’ya tıklayın veya ATA Konsolu yapılandırma sayfasında bulunan Bildirimler ve Raporlar altında **Zamanlanmış raporlar**’a tıklayın.

   ![Rapor zamanlama](./media/ata-sched-reports.png)

  > [!NOTE]
  > Günlük raporlar, kısa süre içinde gece yarısından sonra UTC gönderilmek üzere tasarlanmıştır.

2. Tıklatın **zamanlama** rapor teslimini sıklığı ve e-posta adresi ayarlayın ve bunları Ekle öğesini tıklatıp e-posta adresleri yanındaki artı işaretini tıklatın, seçilen rapor türü yanındaki **kaydetmek**.

   ![Rapor sıklığı ve e-postayı zamanlama](./media/sched-report1.png)


> [!NOTE]
> Zamanlanan raporlar e-postayla teslim edilir ve yalnızca bir e-posta sunucusu altında zaten yapılandırdıysanız gönderilebilir **yapılandırma** ve ardından, **bildirimler ve raporlar**seçin **posta Sunucu**.


## <a name="see-also"></a>Ayrıca bkz:
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
