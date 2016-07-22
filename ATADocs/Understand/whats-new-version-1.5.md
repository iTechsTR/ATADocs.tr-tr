---
title: "ATA sürüm 1.5’teki yenilikler | Microsoft Advanced Threat Analytics"
description: "ATA sürüm 1.5’teki yenilikleri ve bilinen sorunları listeler"
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: a0d64aff-ca9e-4300-b3f8-eb3c8b8ae045
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8d1dedaf86031e8585cca23241aead58f7f3db4e
ms.openlocfilehash: 5836792bcfadb2585d05d4a195979bd6003c84cf


---

# ATA sürüm 1.5’teki yenilikler
Bu sürüm notları, Advanced Threat Analytics’in bu sürümündeki bilinen sorunlar hakkında bilgi sağlar.

## ATA 1.5 güncelleştirmesindeki yenilikler
ATA 1.5 güncelleştirmesi aşağıdaki alanlarda geliştirmeler sağlar:

-   Daha hızlı algılama süreleri

-   NAT (ağ adresi çevirisi) cihazları için iyileştirilmiş otomatik algılama algoritması

-   Etki alanına katılmayan cihazlar için iyileştirilmiş ad çözümleme işlemi

-   Ürün güncelleştirmeleri sırasında veri geçiş desteği

-   Binlerce varlığın katıldığı kuşkulu etkinliklerde kullanıcı arabirimi yanıt sürelerinde gelişme

-   İzleme uyarılarının geliştirilmiş otomatik çözümlemesi

-   İzleme ve sorun gidermeyi iyileştirmek için ek performans sayaçları

## Bilinen sorunlar
Bu sürümün bilinen sorunları şunlardır:

### Yeni ATA Gateway yüklemesi başarısız oldu
ATA dağıtımınızı ATA sürüm 1.5’e güncelleştirdikten sonra, yeni ATA Gateway’i yüklerken aşağıdaki hatayı alıyorsunuz: Microsoft Advanced Threat Analytics Gateway yüklü değil

![ATA GW hatası](media/ata-install-error.png)

<b>Geçici çözüm:</b> Geçici çözüm adımlarını istemek için <ataeval@microsoft.com> adresine bir e-posta gönderin.
### Dağıtım
"Veritabanı veri yolu" ve "Veritabanı günlük yolu" için belirtilen klasörün boş olması gerekir (hiçbir dosya veya alt klasör olmamalıdır).
Boş değilse, dağıtım devam etmez.

### Zip dosyasından yükleme
ATA Gateway’i yüklerken, dosyaları zip dosyasından bir yerel dizine ayıkladığınızdan emin olun ve bileşeni o dizinden yükleyin. ATA Gateway’i doğrudan zip dosyasının içinden yüklemeyin; yoksa yükleme başarısız olur.

### Yapılandırma
ATA Gateway’in yapılandırması ayarlandıktan sonra ATA Gateway ilk kez başlatıldığında, hizmet tümüyle başlatılana kadar "Eşitlenmedi" etiketi görüntülenir; hizmetin ilk kez başlatılması 10 dakika kadar sürebilir.

### Ağ Yakalama Yazılımı
ATA Gateway’de, yükleyebileceğiniz desteklenen tek ağ yakalama yazılımı [Microsoft Network Monitor 3.4](http://www.microsoft.com/download/details.aspx?id=4865)’tür. Microsoft Message Analyzer’ı veya başka bir ağ yakalama yazılımını yüklemeyin. Başka bir yazılımın yüklenmesi ATA Gateway’in düzgün çalışmayı durdurmasına neden olur.

### Sanallaştırma ana bilgisayarında KB
Sanallaştırma ana bilgisayarına KB 3047154’ü yüklemeyin. Bu, bağlantı noktası yansıtma işleminin düzgün çalışmayı durdurmasına neden olur.

## Ayrıca Bkz.

[ATA’yı 1.5 sürümüne güncelleştirme - geçiş kılavuzu](ata-update-1.5-migration-guide.md)

[ATA’yı 1.6 sürümüne güncelleştirme - geçiş kılavuzu](ata-update-1.6-migration-guide.md)

[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jun16_HO4-->


