---
title: Azure ATP raporları ile çalışma | Microsoft Docs
description: Ağınızı izlemek için Azure ATP'de raporları nasıl oluşturabileceğiniz açıklanır.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 2c2d6b1a-fc8c-4ff7-b07d-64ce6159f84d
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 367ad07bd1d0be80486bfc10c2b70546d360805c
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48783194"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="azure-atp-reports"></a>Azure ATP raporları

Azure ATP portalı Azure ATP Raporlar bölümünde, sistem durumu ve şüpheli etkinlikler, bir raporu kullanarak ortamınızda algılanan sistem durumu bilgileri sağlayan raporlar oluşturmanıza olanak sağlar.


Raporlar sayfasına erişmek için menü çubuğundaki rapor simgesine tıklayın: ![rapor simgesi](./media/atp-report-icon.png).
Kullanılabilir raporlar şunlardır: 

- **Özet raporu**: Özeti raporu, sistemde bir durumu Panosu sunar. İçin üç sekme görüntüleyebilirsiniz bir **özeti** ağınızda algılandı ' ın **şüpheli etkinlikleri Aç** , ölçeklendirilmesini, şüpheli etkinlikleri listeler ve **açık sistem durumu sorunları** Azure ATP sistem durumu sorunlarını listeleyen algılananlar. Şüpheli etkinlikler ve sistem durumu sorunları türlerine göre listelenmiştir. 

- **Gizli gruplarda değişiklikler**: değişiklik (örneğin, Yöneticiler, veya el ile etiketlenmiş hesapları veya gruplar) hassas gruplara yapılan tüm değişiklikler Bu raporda listelenir. Azure ATP tek başına algılayıcı, hassas gruplarınızı hakkında tam bir rapor almak için kullanıyorsanız, emin olmak gerekli [olayları, tek başına algılayıcı için etki alanı denetleyicilerinizden iletildiği](configure-event-forwarding.md). 

- **Düz metin olarak ifşa edilen parolalar**: bazı hizmetleri hesabı kimlik bilgilerini düz metin olarak gönderilecek güvenli olmayan LDAP protokolünü kullanır. Bu durum, hassas hesaplar için bile oluşabilir. Saldırganların ağ trafiğini izleme, catch ve daha sonra bu kimlik bilgilerini kötü amaçlar için yeniden kullanabilirsiniz. Bu rapor, tüm kaynak bilgisayarı ve Azure ATP olarak algılanan düz metin olarak gönderilen hesap parolalarını listeler. 

- **Yana hareket yollarını hassas hesaplara yönelik**: Bu rapor, yanal hareket yollarını sunulan hassas hesapları listeler. Daha fazla bilgi için [yana hareket yollarını](use-case-lateral-movement-path.md). Bu rapor, yalnızca iki gün temsil eden çalışma portalında görüntülenen bilgileri aksine son 60 gün içinde oluşturulan yolları toplar.

Bir rapor oluşturmak için iki yolu vardır: isteğe bağlı olarak veya e-postanıza düzenli aralıklarla gönderilmek üzere rapor zamanlayarak.

İsteğe bağlı bir rapor oluşturmak için:

1. Azure ATP portal menü çubuğunda, menü çubuğundaki rapor simgesine tıklayın: ![rapor simgesi](./media/atp-report-icon.png).

2. Seçilen rapor türü, altında ayarlanan **gelen** ve **için** tarihleri ve tıklatın **indirme**. 
 ![raporlar](./media/reports.png)

Zamanlanmış bir rapor ayarlamak için:
 
1. İçinde **raporları** sayfasında **zamanlanan raporları Ayarla**, ya da Azure ATP çalışma alanı portal Yapılandırması sayfasında, bildirimler ve raporlar, altında tıklayın **zamanlanmış raporları**.

   ![Rapor zamanlama](./media/atp-sched-reports.png)
 
 > [!NOTE]
 > Günlük raporlar, kısa süre içinde gece yarısından sonra UTC gönderilmek üzere tasarlanmıştır.

2. Tıklayın **zamanlama** rapor sıklığı ve e-posta adresini ayarlayın ve bunları ekleyin ve e-posta adreslerinin yanındaki artı işaretine tıklayın, seçilen rapor türü yanındaki **Kaydet**.

   ![Rapor sıklığı ve e-postayı zamanlama](./media/sched-report1.png)


## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)