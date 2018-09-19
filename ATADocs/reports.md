---
title: ATA Raporları ile çalışma | Microsoft Docs
description: Ağınızı izlemek için ATA’da nasıl rapor oluşturabileceğinizi açıklar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/27/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 38ea49b5-cd5e-43e5-bc39-5071f759633b
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: eaa579a6b82bab27bba0ddb79b39f06bd495debc
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133234"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*


# <a name="ata-reports"></a>ATA Raporları

Konsoldaki ATA raporları bölümü, size sistem durumu bilgileri (sistem durumu ve ortamınızda algılanan şüpheli etkinlikler) sağlayan raporlar oluşturmanıza imkan tanır.

Raporlar sayfasına erişmek için menü çubuğundaki rapor simgesine tıklayın: ![rapor simgesi](./media/ata-report-icon.png).
Kullanılabilir raporlar şunlardır: 

- **Özet raporu**: Özeti raporu, sistemde bir durumu Panosu sunar. Üç sekme görüntüleyebilirsiniz: Ağınızda algılananlar için bir **Özet** sekmesi, ilgilenmeniz gereken şüpheli etkinlikleri listeleyen **Şüpheli etkinlikleri aç** sekmesi ve ilgilenmeniz gereken ATA sistem durumu sorunlarını listeleyen **Sistem durumu sorunlarını aç** sekmesi. Şüpheli etkinlikler ve sistem durumu sorunları türlerine göre listelenmiştir. 

- **Gizli gruplarda değişiklikler**: gizli gruplara (Yöneticiler gibi) değişiklik yapılan tüm değişiklikler Bu raporda listelenir.

- **Düz metin olarak ifşa edilen parolalar**: bazı hizmetleri hesabı kimlik bilgilerini düz metin olarak gönderilecek güvenli olmayan LDAP protokolünü kullanır. Bu durum, hassas hesaplar için bile oluşabilir. Saldırganların ağ trafiğini izleme, catch ve daha sonra bu kimlik bilgilerini kötü amaçlar için yeniden kullanabilirsiniz. Bu rapor düz metin olarak algılanan ATA gönderilen tüm kaynak bilgisayarınızın ve hesabınızın parolaları listeler. 

- **Yana hareket yollarını hassas hesaplara yönelik**: Bu rapor, yanal hareket yollarını sunulan hassas hesapları listeler. Daha fazla bilgi için [yana hareket yolları](use-case-lateral-movement-path.md)

Bir rapor oluşturmak için iki yolu vardır: isteğe bağlı olarak veya e-postanıza düzenli aralıklarla gönderilmek üzere rapor zamanlayarak.

İsteğe bağlı bir rapor oluşturmak için:

1. ATA konsolu menü çubuğundaki rapor simgesine tıklayın: ![rapor simgesi](./media/ata-report-icon.png).

2. Seçilen rapor türü, altında ayarlanan **gelen** ve **için** tarihleri ve tıklatın **indirme**. 
 ![raporlar](./media/reports.png)

Zamanlanmış bir rapor ayarlamak için:
 
1. **Raporlar** sayfasında **Zamanlanmış rapor ayarla**’ya tıklayın veya ATA Konsolu yapılandırma sayfasında bulunan Bildirimler ve Raporlar altında **Zamanlanmış raporlar**’a tıklayın.

   ![Rapor zamanlama](./media/ata-sched-reports.png)

  > [!NOTE]
  > Günlük raporlar, kısa süre içinde gece yarısından sonra UTC gönderilmek üzere tasarlanmıştır.

2. Tıklayın **zamanlama** rapor sıklığı ve e-posta adresini ayarlayın ve bunları ekleyin ve e-posta adreslerinin yanındaki artı işaretine tıklayın, seçilen rapor türü yanındaki **Kaydet**.

   ![Rapor sıklığı ve e-postayı zamanlama](./media/sched-report1.png)


> [!NOTE]
> Zamanlanan raporları e-posta ile teslim edilir ve yalnızca bir e-posta sunucusu altında zaten yapılandırdıysanız gönderilebilir **yapılandırma** ve sonra **bildirimler ve raporlar**seçin **posta Sunucu**.


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
