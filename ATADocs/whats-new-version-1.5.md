---
title: "Advanced Threat Analytics sürüm 1.5’teki yenilikler | Microsoft Docs"
description: "ATA sürüm 1.5’teki yenilikleri ve bilinen sorunları listeler"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: a0d64aff-ca9e-4300-b3f8-eb3c8b8ae045
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 08da33114bc3f0c9aafb9914b9d77a88fac009f4
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2017
---
# <a name="whats-new-in-ata-version-15"></a>ATA sürüm 1.5’teki yenilikler
Bu sürüm notları, Advanced Threat Analytics’in bu sürümündeki bilinen sorunlar hakkında bilgi sağlar.

## <a name="whats-new-in-the-ata-15-update"></a>ATA 1.5 güncelleştirmesindeki yenilikler
ATA 1.5 güncelleştirmesi aşağıdaki alanlarda geliştirmeler sağlar:

-   Daha hızlı algılama süreleri

-   NAT (ağ adresi çevirisi) cihazları için iyileştirilmiş otomatik algılama algoritması

-   Etki alanına katılmayan cihazlar için iyileştirilmiş ad çözümleme işlemi

-   Ürün güncelleştirmeleri sırasında veri geçiş desteği

-   Binlerce varlığın katıldığı kuşkulu etkinliklerde kullanıcı arabirimi yanıt sürelerinde gelişme

-   İzleme uyarılarının geliştirilmiş otomatik çözümlemesi

-   İzleme ve sorun gidermeyi iyileştirmek için ek performans sayaçları

## <a name="known-issues"></a>Bilinen sorunlar
Bu sürümün bilinen sorunları şunlardır:

### <a name="new-ata-gateway-installation-fails"></a>Yeni ATA Gateway yüklemesi başarısız oldu
ATA dağıtımınızı ATA sürüm 1.5’e güncelleştirdikten sonra, yeni ATA Gateway’i yüklerken aşağıdaki hatayı alıyorsunuz: Microsoft Advanced Threat Analytics Gateway yüklü değil

![ATA GW hatası](media/ata-install-error.png)

<b>Geçici çözüm:</b> Geçici çözüm adımlarını istemek için <ataeval@microsoft.com> adresine bir e-posta gönderin.
### <a name="deployment"></a>Dağıtım
"Veritabanı veri yolu" ve "Veritabanı günlük yolu" için belirtilen klasörün boş olması gerekir (hiçbir dosya veya alt klasör olmamalıdır).
Boş değilse, dağıtım devam etmez.

### <a name="installation-from-zip-file"></a>Zip dosyasından yükleme
ATA Gateway’i yüklerken, dosyaları zip dosyasından bir yerel dizine ayıkladığınızdan emin olun ve bileşeni o dizinden yükleyin. ATA Gateway’i doğrudan zip dosyasının içinden yüklemeyin; yoksa yükleme başarısız olur.

### <a name="configuration"></a>Yapılandırma
ATA Gateway’in yapılandırması ayarlandıktan sonra ATA Gateway ilk kez başlatıldığında, hizmet tümüyle başlatılana kadar "Eşitlenmedi" etiketi görüntülenir; hizmetin ilk kez başlatılması 10 dakika kadar sürebilir.

### <a name="network-capture-software"></a>Ağ Yakalama Yazılımı
ATA Gateway’de, yükleyebileceğiniz desteklenen tek ağ yakalama yazılımı [Microsoft Network Monitor 3.4](http://www.microsoft.com/download/details.aspx?id=4865)’tür. Microsoft Message Analyzer’ı veya başka bir ağ yakalama yazılımını yüklemeyin. Başka bir yazılımın yüklenmesi ATA Gateway’in düzgün çalışmayı durdurmasına neden olur.

### <a name="kb-on-virtualization-host"></a>Sanallaştırma ana bilgisayarında KB
Sanallaştırma ana bilgisayarına KB 3047154’ü yüklemeyin. Bu, bağlantı noktası yansıtma işleminin düzgün çalışmayı durdurmasına neden olur.

## <a name="see-also"></a>Ayrıca bkz.

[ATA’yı 1.5 sürümüne güncelleştirme: geçiş kılavuzu](ata-update-1.5-migration-guide.md)

[ATA’yı 1.6 sürümüne güncelleştirme: geçiş kılavuzu](ata-update-1.6-migration-guide.md)

[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
