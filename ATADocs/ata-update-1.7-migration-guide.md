---
title: Advanced Threat Analytics’i 1.7’ye güncelleştirme geçiş kılavuzu | Microsoft Docs
description: ATA’yı 1.7 sürümüne güncelleştirme yordamları
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 8eefcd45-7a4b-4074-ac5b-1ffc48e6654a
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: b8190552b91aa240b303bbe1a81e68086d19ded7
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44166415"
---
# <a name="ata-update-to-17-migration-guide"></a>ATA’yı 1.7 sürümüne güncelleştirme geçiş kılavuzu
ATA 1.7 güncelleştirmesi aşağıdaki alanlarda geliştirmeler sağlar:

-   Yeni algılamalar

-   Var olan algılamalarda geliştirmeler
  

## <a name="updating-ata-to-version-17"></a>ATA’yı 1.7 sürümüne güncelleştirme

> [!NOTE] 
> ATA ortamınızda yüklü değilse, sürüm 1.7 içerir ve açıklanan standart yükleme yordamını izleyin, ATA'ın tam sürümünü indirin [Ata'yı yükleme](install-ata-step1.md).

ATA sürüm 1. 6 dağıtılan zaten varsa, bu yordam dağıtımınızı güncelleştirmek gereken adımlarda size yol gösterir.

> [!NOTE] 
> ATA sürüm 1.7’yı doğrudan ATA sürüm 1.4 veya 1.5’in üzerine yükleyemezsiniz. Önce ATA sürüm 1.6’yı yüklemeniz gerekir. 

ATA’yı 1.7 sürümüne güncelleştirmek için bu adımları izleyin:

1.  [Sürüm 1.7 güncelleştirmesini indirme](http://www.microsoft.com/evalcenter/evaluate-microsoft-advanced-threat-analytics)<br>
Uygulamanın bu sürümünde, yeni bir ATA dağıtımı yüklemek ve var olan dağıtımları yükseltmek için aynı yükleme dosyası (Microsoft ATA Center Setup.exe) kullanılır.

2.  ATA Center’ı güncelleştirme

4.  ATA Gateway’leri güncelleştirme

    > [!IMPORTANT]
    > ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.

### <a name="step-1-update-the-ata-center"></a>1. Adım: ATA Center’ı güncelleştirme

1.  Veritabanınızı yedekleyin: (isteğe bağlı)

    -   ATA Center bir sanal makinede çalışıyorsa ve bir denetim noktası almak istiyorsanız, sanal makineyi önce kapatın.

    -   ATA Center fiziksel sunucuda çalışıyorsa, [MongoDB’yi yapılandırmak](https://docs.mongodb.org/manual/core/backups/) için önerilen yordamı izleyin.

2.  **Microsoft ATA Center Setup.exe** adlı yükleme dosyasını çalıştırın ve ekrandaki yönergeleri izleyerek güncelleştirmeyi yükleyin.

    -  **Hoş Geldiniz** sayfasında dilinizi seçin ve **İleri**’ye tıklayın.

    -  Sürüm 1. 6'da otomatik güncelleştirmeleri etkinleştirmediyseniz, Ata'yı güncel kalması için Ata'yı Microsoft Update kullanacak şekilde ayarlamanız istenir.  Microsoft Update sayfasında, **Güncelleştirmeleri denetlediğimde Microsoft Update'i kullan (önerilir)** öğesini seçin.
    ![ATA güncel resmi tutmak](media/ata_ms_update.png) bu Windows ayarları, burada görüldüğü gibi diğer Microsoft ürünleri (ATA dahil) için güncelleştirmeleri etkinleştirecek şekilde ayarlar. 
     ![Windows otomatik güncelleştirme resmi](media/ata_installupdatesautomatically.png)

    -  **Veri geçişi** ekranında, verilerin tümünü veya bir kısmını geçirmek istediğinizi seçin. Verilerin yalnızca bir kısmını taşımak isterseniz, daha önceden yakalanan ağ trafiğiniz ve davranış profilleriniz geçirilmez. Bu, anormal davranış algılama anormal etkinlik algılamayı etkinleştirmek için tam bir profil oluşturmasının üç hafta sürdüğünü anlamına gelir. Bu üç hafta boyunca diğer tüm ATA algılamaları düzgün. **Kısmi** veri geçişinin yüklenmesi çok daha kısa sürer. **Tam** veri geçişini seçerseniz, yüklemenin tamamlanması oldukça uzun sürebilir. **Veri Geçişi** ekranında belirtilen tahmini süre ve gerekli disk alanı, ATA’nın eski sürümlerinde kaydettiğiniz önceden yakalanan ağ trafiği miktarına bağlıdır. **Kısmi** veya **Tam** seçimini yapmadan önce bu gereksinimleri kontrol ettiğinizden emin olun.  
    
    ![ATA veri geçişi](media/migration-data-migration17.png)

    -  **Güncelleştir**’e tıklayın. Güncelleştir'e tıkladıktan sonra, güncelleştirme yordamı tamamlanana kadar ATA çevrimdışı kalır.

4.  ATA Center güncelleştirmesi başarıyla tamamlandıktan sonra, ATA Gateway’ler için ATA konsolundaki **Güncelleştirme** ekranını açmak üzere **Başlat**’a tıklayın.
    ![Güncelleştirme başarılı ekranı](media/migration-center-success17.png)

5.  İçinde **güncelleştirmeleri** ekranında, otomatik olarak güncelleştirmek için ATA Gateway zaten ayarlanmışsa kullanıcılar bu noktada güncelleştirilir, aksi halde tıklayın **güncelleştirme** her ATA Gateway'in yanındaki.
  ![Ağ geçitlerini güncelleştirme resmi](media/migration-update-gw-17.png)

  
> [!IMPORTANT] 
> ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.
> Tüm Gateway’ler üzerinde yapılandırılan Syslog dinleyicisi bağlantı noktası 514 olarak değiştirilecektir.
 
> [!NOTE] 
> Yeni ATA Gateways yüklemek amacıyla ATA 1.7 yükleme paketini edinmek ve [4. Adımda açıklanan yeni Ağ Geçidi yükleme yönergelerini takip etmek için **Ağ Geçitleri** ekranına gidip **Ağ Geçidi Kurulumunu İndir** seçeneğine tıklayın. ATA Gateway’i yükleyin](install-ata-step4.md).



## <a name="see-also"></a>Ayrıca Bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
