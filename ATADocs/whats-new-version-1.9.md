---
title: ATA sürüm 1.9 yenilikler | Microsoft Docs
description: Yenilikleri Ata sürümü 1.9 bilinen sorunları listeler
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 51de491c-49ba-4aff-aded-cc133a8ccf0b
ms.reviewer: ''
ms.suite: ems
ms.openlocfilehash: ddb93c2776dbb6e076314051068c4ca3544db756
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44166621"
---
# <a name="whats-new-in-ata-version-19"></a>ATA sürüm 1.9 yenilikler nelerdir?

[İndirme Merkezi’nden](https://www.microsoft.com/download/details.aspx?id=56725) ATA’nın son güncelleştirme sürümünü indirebilir veya [Değerlendirme merkezinden](http://www.microsoft.com/evalcenter/evaluate-microsoft-advanced-threat-analytics) tam sürümü indirebilirsiniz.

Bu sürüm notları, güncelleştirmeleri, yeni özellikler, hata düzeltmeleri ve, Advanced Threat Analytics'in bu sürümündeki bilinen sorunlar hakkında bilgi sağlar.

## <a name="new--updated-detections"></a>Yeni ve güncelleştirilmiş algılamalar

-  **Şüpheli hizmet oluşturma işlemi**: saldırganlar, ağınızdaki kuşkulu hizmet çalıştırma girişiminde. Birisi şüpheli görünüyorsa, yeni bir hizmet, bir etki alanı denetleyicisinde çalıştırıldığında belirlediğinde ATA artık bir uyarı başlatır. Daha fazla bilgi için bu algılama olayları (değil ağ trafiği), bağlı olduğu için bkz: [şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md#suspicious-service-creation).


## <a name="new-reports-to-help-you-investigate"></a>Araştırmanıza yardımcı olacak yeni raporlar 

-   [ **Parolalarını düz metin olarak ifşa** ](reports.md) hesapları, küçük harf duyarlı ve duyarlı olmayan, hesap kimlik bilgilerini düz metin olarak gönderdiğinizde algılamanıza olanak tanır. Bu, araştırmak ve ağ güvenlik düzeyinizi geliştirme ortamınızda LDAP basit bağlama kullanımını azaltmak sağlar. Bu rapor, hizmet ve hassas hesap düz metin olarak şüpheli etkinlik uyarılarını yerini alır.

- [ **Yana hareket yollarını hassas hesaplara yönelik** ](reports.md) yanal hareket yollarını sunulan hassas hesapları listeler. Bu, bu yollar azaltmak ve saldırı yüzeyi riski en aza indirmek için ağ sağlamlaştırma sağlar. Bu, böylece bunlar sanal güvenlik ikramiye isabet kadar saldırganlar ağınızdaki kullanıcılar ve bilgisayarlar arasında taşıyamazsınız yanal hareket önlemenize olanak sağlar: küçük harf duyarlı yönetici hesabı kimlik bilgilerinizle.

## <a name="improved-investigation"></a>Gelişmiş araştırma

-  Ata'yı 1.9 içeren yeni ve geliştirilmiş [varlık profili](entity-profiles.md). Varlık profili, kullanıcıların, bunların eriştiği kaynaklara ve geçmişlerini tam derinlemesine araştırma için tasarlanmış bir Pano sağlar. Varlık profili yanal hareket yollarını erişilebilir olan gizli kullanıcılar tanımlamanızı sağlar. 

-   Ata'yı 1.9 olanak tanır [el ile grupları etiket](tag-sensitive-accounts.md) veya algılamalar geliştirmek gibi hassas hesapları. Gizli Grup değişikliği algılama ve yanal hareket yolunun gibi birçok ATA algılamaları hangi gruplar ve hesaplar hassas kabul edilir üzerinde kullanan bu etiketleme etkiler.

## <a name="performance-improvements"></a>Performans iyileştirmeleri

- ATA Center altyapı performans için İyileştirildi: Toplu trafik görünümünü CPU ve paket işlem hattının etkinleştirir ve SSL oturumlarını DC'ye en aza indirmek için etki alanı denetleyicilerine yuva kullanır.



## <a name="additional-changes"></a>Ek değişiklikler

- Ata'nın yeni bir sürümünü yükledikten sonra [ **yenilikler** ](working-with-ata-console.md) simgesi, en son sürümde nelerin değiştiğini bilmeniz izin vermek için araç çubuğunda görünür. Ayrıca, ayrıntılı sürüm changelog bağlantısını içeren sağlar.


## <a name="removed-and-deprecated-features"></a>Kaldırılan ve kullanım dışı bırakılan özellikler

- **Bozuk güven şüpheli etkinlik** uyarı kaldırıldı.
- Parolaları düz metin şüpheli bir etkinliği kullanıma sunulan kaldırıldı. Tarafından değiştirildi [ **parolalarını düz metin raporda ifşa**](reports.md).



## <a name="see-also"></a>Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

[ATA sürüm 1.9 - Geçiş Kılavuzu güncelleştirme](ata-update-1.9-migration-guide.md)

