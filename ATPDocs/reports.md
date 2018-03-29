---
title: Azure ATP raporları ile çalışma | Microsoft Docs
description: Raporları ATP ağınızda izlemek için Azure nasıl oluşturabileceğiniz açıklanmaktadır.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/27/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 2c2d6b1a-fc8c-4ff7-b07d-64ce6159f84d
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 8d9c7f9208ce76e6c2ca915729b9c64f769ae7bd
ms.sourcegitcommit: 158bf048d549342f2d4689f98ab11f397d9525a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*


# <a name="azure-atp-reports"></a>Azure ATP raporları

Çalışma portal Azure ATP Raporlar bölümünde sistem durumu ve kuşkulu etkinliklerin bir raporu, ortamınızda algılanan sistem durumu bilgisi ile sağladığınız raporlar oluşturmanıza olanak sağlar.


Raporlar sayfasına erişmek için menü çubuğundaki rapor simgesine tıklayın: ![rapor simgesi](./media/atp-report-icon.png).
Kullanılabilir raporlar şunlardır: 

- **Özet raporu**: Özeti raporu sistem durumu Panosu sunar. -Biri için üç sekme görüntüleyebilirsiniz bir **Özet** ne ağınızdaki algılandı, **açmak kuşkulu etkinlikleri** , dikkatli olun, kuşkulu etkinlikleri listeler ve **açık sistem durumu sorunları** Azure ATP durumu sorunlarını listeler ilişkin halletmeniz emin. Şüpheli etkinlikler ve sistem durumu sorunları türlerine göre listelenmiştir. 

- **Hassas gruplara değiştirilmesini**: Bu rapor, bir değişiklik (örneğin, Yöneticiler veya el ile etiketlenmiş hesapları veya gruplar) hassas gruplara yapılan her zaman listeler. Hassas gruplarınızı hakkında tam bir rapor almak için Azure ATP tek başına algılayıcılar kullanıyorsanız, emin olmak gerekli olan [olayları tek başına algılayıcılar, etki alanı denetleyicilerinden iletildiği](configure-event-forwarding.md). 

- **Parolalar düz metinde gösterilen**: bazı hizmetler LDAP güvenli olmayan hesap kimlik bilgilerini düz metin olarak göndermek için protokolünü kullanır. Bu durum, hassas hesapları için bile oluşabilir. Ağ trafiğini izleme saldırganlar catch ve bu kimlik bilgileri kötü amaçlı olarak yeniden kullanabilirsiniz. Bu rapor, tüm kaynak bilgisayar ve düz metin olarak Azure olarak algılanan ATP gönderilen hesap parolalarını listeler. 

- **Yanal hareket yolları hassas hesaplarına**: Bu rapor, yanal hareket yolları sunulan hassas hesapları listeler. Daha fazla bilgi için bkz: [yanal hareket yolları](use-case-lateral-movement-path.md). Bu rapor, yalnızca iki gün temsil eden çalışma portalında görüntülenen bilgileri aksine son 60 gün içinde oluşturulan yolları toplar.

Bir rapor oluşturmak için iki yolu vardır: isteğe bağlı olarak veya e-postanıza düzenli aralıklarla gönderilmek üzere rapor zamanlayarak.

İsteğe bağlı bir rapor oluşturmak için:

1. Azure ATP çalışma portal menü çubuğunda, menü çubuğundaki rapor simgesine tıklayın: ![rapor simgesi](./media/atp-report-icon.png).

2. Altında seçilen rapor türünü ayarlayın **gelen** ve **için** tıklatın ve tarihleri **karşıdan**. 
 ![raporlar](./media/reports.png)

Zamanlanmış bir rapor ayarlamak için:
 
1. İçinde **raporları** sayfasında, **ayarlamak Zamanlanmış raporlar**, ya da Azure ATP çalışma portal yapılandırma sayfasında, bildirimler ve raporlar, altında tıklatın **zamanlanmış raporları**.

   ![Rapor zamanlama](./media/atp-sched-reports.png)
 
 > [!NOTE]
 > Günlük raporlar, kısa süre içinde gece yarısından sonra UTC gönderilmek üzere tasarlanmıştır.

2. Tıklatın **zamanlama** rapor teslimini sıklığı ve e-posta adresi ayarlayın ve bunları Ekle öğesini tıklatıp e-posta adresleri yanındaki artı işaretini tıklatın, seçilen rapor türü yanındaki **kaydetmek**.

   ![Rapor sıklığı ve e-postayı zamanlama](./media/sched-report1.png)


## <a name="see-also"></a>Ayrıca bkz:
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)