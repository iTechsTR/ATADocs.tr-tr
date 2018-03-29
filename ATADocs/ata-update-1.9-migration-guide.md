---
title: 1.9 Geçiş Kılavuzu'na tehdit analizi güncelleştirme Gelişmiş | Microsoft Docs
description: ATA sürüm 1.9 güncelleştirme yordamları
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 03/25/2018
ms.topic: article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 2946310a-8e4e-48fc-9450-fc9647efeb22
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 0bd4bca536facb9ad4b7fea627f2ef512949728e
ms.sourcegitcommit: 158bf048d549342f2d4689f98ab11f397d9525a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="updating-ata-to-version-19"></a>ATA sürüm 1.9 güncelleştiriliyor

> [!NOTE] 
> ATA ortamınızda yüklü değilse, açıklanan standart yükleme yordamını izleyin ve sürüm 1.9 içerir, ATA'ın tam sürümünü indirin [Ata'yı yükleme](install-ata-step1.md).

ATA sürüm dağıtılan 1.8 zaten varsa, bu yordam dağıtımınızı güncelleştirmek için gereken adımlarda size yol gösterir.

> [!NOTE] 
>  Yalnızca ATA sürüm 1,8 (1.8.6645) ve ATA 1.8 güncelleştirme 1 (1.8.6765) ATA sürüm 1.9 güncelleştirilebilir, ATA eski sürümlerini ATA sürüm 1.9 doğrudan güncelleştirilemez.

ATA sürüm 1.9 güncelleştirmek için aşağıdaki adımları izleyin:

1.  [ATA 1.9 güncelleştirme sürümü Yükleme Merkezi'nden](https://www.microsoft.com/download/details.aspx?id=56725) veya tam sürümünden [Eval Merkezi](http://www.microsoft.com/evalcenter/evaluate-microsoft-advanced-threat-analytics).<br>
Geçiş sürümünde dosyası yalnızca ATA 1.8 güncelleştirmek için kullanılabilir. Değerlendirme merkezindeki sürümde ise yeni bir ATA dağıtımı yüklemek ve mevcut dağıtımları yükseltmek için aynı yükleme dosyası (Microsoft ATA Center Setup.exe) kullanılır.

2.  ATA Center’ı güncelleştirme

4.  ATA Gateway’leri güncelleştirme

    > [!IMPORTANT]
    > ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.

### <a name="step-1-update-the-ata-center"></a>1. Adım: ATA Center’ı güncelleştirme

1.  Veritabanınızı yedekleyin: (isteğe bağlı)

    -   ATA Center bir sanal makinede çalışıyorsa ve bir denetim noktası almak istiyorsanız, önce sanal makineyi kapatın.

    -   ATA Center fiziksel sunucuda çalışıyorsa veritabanını yedekleme hakkında bilgi için [Olağanüstü durum kurtarma](disaster-recovery.md) makalesine bakın.

2.  **Microsoft ATA Center Setup.exe** adlı yükleme dosyasını çalıştırın ve ekrandaki yönergeleri izleyerek güncelleştirmeyi yükleyin.

    -  **Hoş Geldiniz** sayfasında dilinizi seçin ve **İleri**’ye tıklayın.

    -  Sürümünde 1.8 otomatik güncelleştirmeler etkinleştirirseniz alamadık, ATA'ın güncel kalması için ATA için Microsoft Update'i kullanmak için ayarlamanız istenir.  Microsoft Update sayfasında, **Güncelleştirmeleri denetlediğimde Microsoft Update'i kullan (önerilir)** öğesini seçin.
    ![ATA güncel resmi tutun](media/ata_ms_update.png)
     
     Bu, ATA'ın güncelleştirmeleri etkinleştirmek için Windows ayarlarını ayarlar. 
    
    -  **Kısmi veri geçişi** ekran, daha önce yakalanan ağ trafiğinin bilmenizi sağlar, olaylar, varlıkları ve algılama ilgili veriler silinir. Anormal davranışları algılama, anormal grubu değişiklik, Dizin Hizmetleri (SAM-R) ve sonra tam bir profili oluşturmak için üç hafta alması şifreleme indirgeme algılamaları kullanarak keşif hariç olmak üzere tüm algılamaların hemen çalışır gerekli öğrenme zamanı. 
     
      ![ATA kısmi geçiş](media/partial-migration.png)

    -  **Güncelleştir**’e tıklayın. Güncelleştir'e tıkladıktan sonra, güncelleştirme yordamı tamamlanana kadar ATA çevrimdışı kalır.

4.  ATA Center güncelleştirmesi başarıyla tamamlandıktan sonra, ATA Gateway’ler için ATA konsolundaki **Güncelleştirme** ekranını açmak üzere **Başlat**’a tıklayın.

     ![Güncelleştirme başarılı ekranı](media/migration-center-success.png)

5.  İçinde **güncelleştirmeleri** ekran, otomatik olarak güncelleştirmek için ATA Gateway zaten ayarladıysanız, bu noktada güncelleştirmek değilse, tıklatın **güncelleştirme** her ATA Gateway yanındaki.
  
     ![Ağ geçitlerini güncelleştirme resmi](media/migration-update-gw.png)

  
> [!IMPORTANT] 
> ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.
 
> [!NOTE] 
> Yeni ATA Gateway bileşenleri yüklemek için Git **ağ geçitleri** ekranında ve tıklatın **Gateway kurulumunu indir** ATA 1.9 ağ geçidi yükleme paketi alın ve olarak yeni ağ geçidi yüklemek için yönergeleri izleyin açıklanan [4. adım. ATA Gateway’i yükleyin](install-ata-step4.md).


## <a name="see-also"></a>Ayrıca bkz:

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
