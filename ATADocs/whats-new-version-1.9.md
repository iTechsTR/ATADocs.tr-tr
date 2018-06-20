---
title: ATA sürüm 1.9 yenilikler | Microsoft Docs
description: Yenilikleri ve ATA sürüm 1.9 bilinen sorunları listeler
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/25/2018
ms.topic: article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 51de491c-49ba-4aff-aded-cc133a8ccf0b
ms.reviewer: ''
ms.suite: ems
ms.openlocfilehash: f4a0776d52a69ba519e5cfdd0befb6bbd39d73c3
ms.sourcegitcommit: 158bf048d549342f2d4689f98ab11f397d9525a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
ms.locfileid: "30202400"
---
# <a name="whats-new-in-ata-version-19"></a>ATA sürüm 1.9 yenilikler nelerdir?

[İndirme Merkezi’nden](https://www.microsoft.com/download/details.aspx?id=56725) ATA’nın son güncelleştirme sürümünü indirebilir veya [Değerlendirme merkezinden](http://www.microsoft.com/evalcenter/evaluate-microsoft-advanced-threat-analytics) tam sürümü indirebilirsiniz.

Bu sürüm notları güncelleştirmeleri, yeni özellikler, hata düzeltmeleri ve Advanced Threat Analytics bu sürümündeki bilinen sorunlar hakkında bilgi sağlar.

## <a name="new--updated-detections"></a>Yeni ve güncelleştirilmiş algılamalar

-  **Şüpheli hizmet oluşturma**: saldırganlar ağınızdaki kuşkulu hizmet çalıştırmak dener. Birisi şüpheli görünüyorsa, yeni bir hizmet, bir etki alanı denetleyicisinde çalıştırıldığında belirlediğinde, ATA artık bir uyarı başlatır. Bu algılama (olmayan ağ trafiği), olaylar hakkında daha fazla bilgi için bağlı olduğu için bkz: [şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md#suspicious-service-creation).


## <a name="new-reports-to-help-you-investigate"></a>Araştırmanıza yardımcı olacak yeni raporlar 

-   [ **Parolaların temiz metin olarak sunulan** ](reports.md) hesapları, gizli ve hassas olmayan, hesap kimlik bilgilerini düz metin olarak göndermek algılayabilir olanak tanır. Bu, araştırın ve ağ güvenlik düzeyini artırma ortamınızda LDAP basit bağlama kullanımını azaltmak sağlar. Bu rapor, hizmet ve hassas hesap doğrulamaya şüpheli etkinlik uyarıları yerini alır.

- [ **Yanal hareket yolları hassas hesaplarına** ](reports.md) yanal hareket yolları sunulan hassas hesaplarını listeler. Bu, bu yollar azaltmak ve saldırı yüzeyini riski en aza indirmek için ağınızı sağlamlaştırmak olanak sağlar. Bu, böylece sanal güvenlik ikramiye isabet kadar saldırganların ağınızda kullanıcıları ve bilgisayarları arasında taşınamıyor yanal hareket engellemenizi sağlar: hassas yönetici hesabı kimlik bilgilerinizi.

## <a name="improved-investigation"></a>Geliştirilmiş araştırma

-  ATA 1.9 içeren yeni ve geliştirilmiş [varlık profili](entity-profiles.md). Varlık profili, kullanıcılar, bunlar erişilen kaynaklar ve geçmişlerini tam derin Dalış araştırma için tasarlanmış bir Pano sağlar. Varlık profili yanal hareket yolları erişilebilir hassas kullanıcıları belirlemek sağlar. 

-   ATA 1.9 olanak tanır [manuel olarak grupları etiketleme](tag-sensitive-accounts.md) veya algılamaların geliştirmek gibi hassas hesapları. Hangi gruplar ve hesaplar hassas kabul edilir üzerinde hassas grubu değişikliği algılama ve yanal hareket yolu gibi birçok ATA algılamaları kullanan bu etiketleme etkiler.

## <a name="performance-improvements"></a>Performans iyileştirmeleri

- ATA Center altyapı için performansı geliştirildi: trafiğin toplanan görünümünü iyileştirme CPU ve paket ardışık sağlar ve SSL oturumları DC'ye en aza indirmek için etki alanı denetleyicilerine yuva yeniden kullanır.



## <a name="additional-changes"></a>Ek değişiklikler

- ATA'ın yeni bir sürüm yüklendikten sonra [ **yenilikler** ](working-with-ata-console.md) simgesi bildiğiniz en son sürümde değiştirildi izin vermek için araç çubuğunda görünür. Ayrıca, ayrıntılı sürüm değişim günlüğü bağlantı sağlar.


## <a name="removed-and-deprecated-features"></a>Kaldırılan ve kullanım dışı özellikler

- **Bozuk güven şüpheli etkinlik** uyarı kaldırıldı.
- Düz metin kuşkulu etkinliğinde sunulan parolaları kaldırıldı. Tarafından değiştirildi [ **parolaları düz metin raporda gösterilen**](reports.md).



## <a name="see-also"></a>Ayrıca bkz:
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

[Ata'yı sürüm 1.9 - Geçiş Kılavuzu güncelleştirme](ata-update-1.9-migration-guide.md)

