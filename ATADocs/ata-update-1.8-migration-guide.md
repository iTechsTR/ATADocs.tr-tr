---
title: Advanced Threat Analytics 1.8 güncelleştirmesi geçiş kılavuzu| Microsoft Docs
description: ATA’yı sürüm 1.8’e güncelleştirme yordamları
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 07/20/2017
ms.topic: article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: e5a9718c-b22e-41f7-a614-f00fc4997682
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 540d1cb0754dc9191a985625a8f988cb44c9f000
ms.sourcegitcommit: 4d2ac5b02c682840703edb0661be09055d57d728
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2017
ms.locfileid: "24019009"
---
# <a name="updating-ata-to-version-18"></a>ATA’yı sürüm 1.8’e güncelleştirme

> [!NOTE] 
> ATA ortamınızda yüklü değilse, açıklanan standart yükleme yordamını izleyin ve sürüm 1,8 içerir, ATA'ın tam sürümünü indirin [Ata'yı yükleme](install-ata-step1.md).

ATA sürüm dağıtılan 1.7 zaten varsa, bu yordam dağıtımınızı güncelleştirmek için gereken adımlarda size yol gösterir.

> [!NOTE] 
>  Yalnızca ATA sürüm 1.7 Güncelleştirmesi 1 ve 1.7 Güncelleştirmesi 2, ATA sürüm 1.8’e güncelleştirilebilir, ATA’nın daha eski sürümleri doğrudan ATA sürüm 1.8’e güncelleştirilemez.

ATA’yı sürüm 1.8’e güncelleştirmek için bu adımları izleyin:

1.  [İndirme Merkezi’nden ATA 1.8’in güncelleştirme sürümünü](https://www.microsoft.com/download/details.aspx?id=55536) veya [Değerlendirme merkezinden](http://www.microsoft.com/evalcenter/evaluate-microsoft-advanced-threat-analytics) tam sürümü indirin.<br>
Geçiş sürümündeki dosya yalnızca ATA 1.7’yi güncelleştirmek için kullanılabilir. Değerlendirme merkezindeki sürümde ise yeni bir ATA dağıtımı yüklemek ve mevcut dağıtımları yükseltmek için aynı yükleme dosyası (Microsoft ATA Center Setup.exe) kullanılır.

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

    -  Sürüm 1.7 otomatik güncelleştirmeleri etkinleştirirseniz alamadık, ATA'ın güncel kalması için ATA için Microsoft Update'i kullanmak için ayarlamanız istenir.  Microsoft Update sayfasında, **Güncelleştirmeleri denetlediğimde Microsoft Update'i kullan (önerilir)** öğesini seçin.
    ![ATA güncel resmi tutun](media/ata_ms_update.png)
     
     Bu, ATA'ın güncelleştirmeleri etkinleştirmek için Windows ayarlarını ayarlar. 
    
    -  **Veri geçişi** ekranında, verilerin tümünü veya bir kısmını geçirmek istediğinizi seçin. Yalnızca kısmi veri geçirmeyi seçerseniz, tüm algılamaların tam bir profil oluşturmak için üç hafta sürer anormal davranışları algılama hariç olmak üzere, hemen çalışır.  
    
    **Kısmi** veri geçişinin yüklenmesi çok daha kısa sürer. **Tam** veri geçişini seçerseniz, yüklemenin tamamlanması oldukça uzun sürebilir. **Veri Geçişi** ekranında listelenen tahmini süre ve gerekli disk alanı bilgilerine bakmayı unutmayın. Bu rakamlar, ATA’nın önceki sürümlerinde kaydettiğiniz yakalanan ağ trafiği miktarına bağlıdır. Örneğin, aşağıdaki ekran büyük veritabanından veri geçişi görebilirsiniz:
         
    ![ATA veri geçişi](media/migration-data-migration.png)

    -  **Güncelleştir**’e tıklayın. Güncelleştir'e tıkladıktan sonra, güncelleştirme yordamı tamamlanana kadar ATA çevrimdışı kalır.

4.  ATA Center güncelleştirmesi başarıyla tamamlandıktan sonra, ATA Gateway’ler için ATA konsolundaki **Güncelleştirme** ekranını açmak üzere **Başlat**’a tıklayın.

    ![Güncelleştirme başarılı ekranı](media/migration-center-success.png)

5.  İçinde **güncelleştirmeleri** ekran, otomatik olarak güncelleştirmek için ATA Gateway zaten ayarladıysanız, bu noktada güncelleştirmek değilse, tıklatın **güncelleştirme** her ATA Gateway yanındaki.
  
![Ağ geçitlerini güncelleştirme resmi](media/migration-update-gw.png)

  
> [!IMPORTANT] 
> ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.
 
> [!NOTE] 
> Yeni ATA Gateway’ler yüklemek için **Ağ Geçitleri** ekranına gidin, ATA 1.8 Gateway kurulum paketini almak için **Ağ Geçidi Kurulumunu İndir**’e tıklayın ve yeni Ağ Geçidi yüklemesi için [4. Adım’da açıklanan yönergeleri izleyin. ATA Gateway’i yükleyin](install-ata-step4.md).


## <a name="see-also"></a>Ayrıca bkz:

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
