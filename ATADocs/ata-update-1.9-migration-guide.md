---
title: Threat Analytics güncelleştirme Gelişmiş 1.9 Geçiş Kılavuzu | Microsoft Docs
description: Ata'yı 1.9 sürümüne güncelleştirme yordamları
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 03/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 2946310a-8e4e-48fc-9450-fc9647efeb22
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: bd96cf2b2048aa37e559649d15565c3244684e35
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44166008"
---
# <a name="updating-ata-to-version-19"></a>Ata'yı 1.9 sürümüne güncelleştirme

> [!NOTE] 
> ATA ortamınızda yüklü değilse, sürümü 1.9 içerir ve açıklanan standart yükleme yordamını izleyin, ATA'ın tam sürümünü indirin [Ata'yı yükleme](install-ata-step1.md).

ATA sürüm 1.8 dağıtılan zaten varsa, bu yordam dağıtımınızı güncelleştirmek gereken adımlarda size yol gösterir.

> [!NOTE] 
>  Yalnızca ATA sürüm 1.8 (1.8.6645) ve ATA 1.8 update 1 (1.8.6765) ATA sürüm 1.9 güncelleştirilebilir, ATA'ın daha eski sürümleri doğrudan ATA sürüm 1.9 güncelleştirilemez.

ATA sürüm 1.9 güncelleştirmek için aşağıdaki adımları izleyin:

1.  [Ata'yı 1.9 güncelleştirme sürümü İndirme Merkezi'nden](https://www.microsoft.com/download/details.aspx?id=56725) veya tam sürümü [değerlendirme merkezinden](http://www.microsoft.com/evalcenter/evaluate-microsoft-advanced-threat-analytics).<br>
Geçiş sürümündeki dosya yalnızca ATA 1.8 güncelleştirmek için kullanılabilir. Değerlendirme merkezindeki sürümde ise yeni bir ATA dağıtımı yüklemek ve mevcut dağıtımları yükseltmek için aynı yükleme dosyası (Microsoft ATA Center Setup.exe) kullanılır.

2.  ATA Center’ı güncelleştirme

4.  ATA Gateway’leri güncelleştirme

    > [!IMPORTANT]
    > ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.

### <a name="step-1-update-the-ata-center"></a>1. Adım: ATA Center’ı güncelleştirme

1.  Veritabanınızı yedekleyin: (isteğe bağlı)

    -   ATA Center bir sanal makinede çalışıyorsa ve bir denetim noktası almak istiyorsanız, sanal makineyi önce kapatın.

    -   ATA Center fiziksel sunucuda çalışıyorsa veritabanını yedekleme hakkında bilgi için [Olağanüstü durum kurtarma](disaster-recovery.md) makalesine bakın.

2.  **Microsoft ATA Center Setup.exe** adlı yükleme dosyasını çalıştırın ve ekrandaki yönergeleri izleyerek güncelleştirmeyi yükleyin.

    -  **Hoş Geldiniz** sayfasında dilinizi seçin ve **İleri**’ye tıklayın.

    -  Sürüm 1.8 otomatik güncelleştirmeleri etkinleştirmediyseniz, Ata'yı güncel kalması için Ata'yı Microsoft Update kullanacak şekilde ayarlamanız istenir.  Microsoft Update sayfasında, **Güncelleştirmeleri denetlediğimde Microsoft Update'i kullan (önerilir)** öğesini seçin.
    ![ATA güncel resmi tutun](media/ata_ms_update.png)
     
     Bu, Windows ayarlarını, ATA güncelleştirmelerini etkinleştirecek şekilde ayarlar. 
    
    -  **Kısmi veri geçişi** ekran, bu daha önceden yakalanan ağ trafiği bilmenizi sağlar, olaylar, varlıkları ve algılama ilgili veriler silinir. Anormal davranış algılama, olağan dışı bir grup değişikliği, Dizin Hizmetleri (SAM-R) ve sonra tam bir profil oluşturmak için üç hafta geçmesi, şifreleme düşürme algılamalar kullanarak keşif hariç tüm algılamalar hemen çalışır gerekli öğrenme zamanı. 
     
      ![ATA kısmi geçiş](media/partial-migration.png)

    -  **Güncelleştir**’e tıklayın. Güncelleştir'e tıkladıktan sonra, güncelleştirme yordamı tamamlanana kadar ATA çevrimdışı kalır.

4.  ATA Center güncelleştirmesi başarıyla tamamlandıktan sonra, ATA Gateway’ler için ATA konsolundaki **Güncelleştirme** ekranını açmak üzere **Başlat**’a tıklayın.

     ![Güncelleştirme başarılı ekranı](media/migration-center-success.png)

5.  İçinde **güncelleştirmeleri** ekranında, otomatik olarak güncelleştirmek için ATA Gateway zaten ayarlanmışsa kullanıcılar bu noktada güncelleştirilir, aksi halde tıklayın **güncelleştirme** her ATA Gateway'in yanındaki.
  
     ![Ağ geçitlerini güncelleştirme resmi](media/migration-update-gw.png)

  
> [!IMPORTANT] 
> ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.
 
> [!NOTE] 
> Yeni ATA Gateways yüklemek amacıyla go **ağ geçitleri** tıklayın ve ekranı **ağ geçidi kurulumunu indir** yeni bir ağ geçidi yükleme yönergelerini izleyin ve Ata'yı 1.9 Gateway Kurulum paketini almak için açıklanan [4. adım. ATA Gateway’i yükleyin](install-ata-step4.md).


## <a name="see-also"></a>Ayrıca Bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
