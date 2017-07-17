---
title: "Advanced Threat Analytics 1.8 güncelleştirmesi geçiş kılavuzu| Microsoft Docs"
description: "ATA’yı sürüm 1.8’e güncelleştirme yordamları"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 07/9/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: e5a9718c-b22e-41f7-a614-f00fc4997682
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: ff61d12eefaf6fb0a6b3d92568ef8c25c9d4c49b
ms.sourcegitcommit: 3177d5894413fbd363b9aca8130f3f7a369223b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2017
---
# ATA’yı sürüm 1.8’e güncelleştirme
<a id="updating-ata-to-version-18" class="xliff"></a>

> [!NOTE] 
> Ortamınızda ATA yüklü değilse ATA’nın sürüm 1.8’i de içeren tam sürümünü indirin ve [ATA’yı Yükleme](install-ata-step1.md) başlığı altında açıklanan standart yükleme yordamını izleyin.

ATA sürüm 1.7’yi önceden dağıttıysanız bu yordam, dağıtımınızı güncelleştirmek için gereken adımlarda size yol gösterir.

> [!NOTE] 
>  Yalnızca ATA sürüm 1.7 Güncelleştirmesi 1 ve 1.7 Güncelleştirmesi 2, ATA sürüm 1.8’e güncelleştirilebilir, ATA’nın daha eski sürümleri doğrudan ATA sürüm 1.8’e güncelleştirilemez.

ATA’yı sürüm 1.8’e güncelleştirmek için bu adımları izleyin:

1.  [İndirme Merkezi’nden ATA 1.8’in güncelleştirme sürümünü](https://www.microsoft.com/download/details.aspx?id=55536) veya [Değerlendirme merkezinden](http://www.microsoft.com/evalcenter/evaluate-microsoft-advanced-threat-analytics) tam sürümü indirin.<br>
Geçiş sürümündeki dosya yalnızca ATA 1.7’yi güncelleştirmek için kullanılabilir. Değerlendirme merkezindeki sürümde ise yeni bir ATA dağıtımı yüklemek ve mevcut dağıtımları yükseltmek için aynı yükleme dosyası (Microsoft ATA Center Setup.exe) kullanılır.

2.  ATA Center’ı güncelleştirme

4.  ATA Gateway’leri güncelleştirme

    > [!IMPORTANT]
    > ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.

### 1. Adım: ATA Center’ı güncelleştirme
<a id="step-1-update-the-ata-center" class="xliff"></a>

1.  Veritabanınızı yedekleyin: (isteğe bağlı)

    -   ATA Center sanal makinede çalışıyorsa ve bir denetim noktası almak istiyorsanız, önce sanal makineyi kapatın.

    -   ATA Center fiziksel sunucuda çalışıyorsa veritabanını yedekleme hakkında bilgi için [Olağanüstü durum kurtarma](disaster-recovery.md) makalesine bakın.

2.  **Microsoft ATA Center Setup.exe** adlı yükleme dosyasını çalıştırın ve ekrandaki yönergeleri izleyerek güncelleştirmeyi yükleyin.

    -  **Hoş Geldiniz** sayfasında dilinizi seçin ve **İleri**’ye tıklayın.

    -  Sürüm 1.7’de otomatik güncelleştirmeleri etkinleştirmediyseniz ATA’nın güncel kalması için ATA’yı Microsoft Update kullanacak şekilde ayarlamanız istenir.  Microsoft Update sayfasında, **Güncelleştirmeleri denetlediğimde Microsoft Update'i kullan (önerilir)** öğesini seçin.
    ![ATA’yı güncel tutma resmi](media/ata_ms_update.png)
     
     Böylelikle Windows ayarlarını, ATA güncelleştirmelerini etkinleştirecek şekilde belirlemiş olursunuz. 
    
    -  **Veri geçişi** ekranında, verilerin tümünü veya bir kısmını geçirmek istediğinizi seçin. Verilerin yalnızca bir kısmını geçirmeyi seçerseniz profil oluşturma işleminin tamamlanması üç haftaya kadar sürebilen anormal davranış algılama hariç tüm algılamalar hemen çalışacaktır.  
    
    **Kısmi** veri geçişinin yüklenmesi çok daha kısa sürer. **Tam** veri geçişini seçerseniz, yüklemenin tamamlanması oldukça uzun sürebilir. **Veri Geçişi** ekranında listelenen tahmini süre ve gerekli disk alanı bilgilerine bakmayı unutmayın. Bu rakamlar, ATA’nın önceki sürümlerinde kaydettiğiniz yakalanan ağ trafiği miktarına bağlıdır. Örneğin aşağıdaki ekranda, çok büyük bir veritabanından veri geçişi işlemini görebilirsiniz:
         
    ![ATA veri geçişi](media/migration-data-migration.png)

    -  **Güncelleştir**’e tıklayın. Güncelleştir'e tıkladıktan sonra, güncelleştirme yordamı tamamlanana kadar ATA çevrimdışı kalır.

4.  ATA Center güncelleştirmesi başarıyla tamamlandıktan sonra, ATA Gateway’ler için ATA konsolundaki **Güncelleştirme** ekranını açmak üzere **Başlat**’a tıklayın.

    ![Güncelleştirme başarılı ekranı](media/migration-center-success.png)

5.  **Güncelleştirmeler** ekranında, otomatik olarak güncelleştirilecek şekilde yapılandırdıysanız, ATA Gateway’leriniz bu noktada güncelleştirilir. Bu şekilde yapılandırmadıysanız her ATA Gateway’in yanındaki **Güncelleştir**’e tıklayın.
  
![Ağ geçitlerini güncelleştirme resmi](media/migration-update-gw.png)

  
> [!IMPORTANT] 
> ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.
 
> [!NOTE] 
> Yeni ATA Gateway’ler yüklemek için **Ağ Geçitleri** ekranına gidin, ATA 1.8 Gateway kurulum paketini almak için **Ağ Geçidi Kurulumunu İndir**’e tıklayın ve yeni Ağ Geçidi yüklemesi için [4. Adım’da açıklanan yönergeleri izleyin. ATA Gateway’i yükleyin](install-ata-step4.md).


## Ayrıca bkz:
<a id="see-also" class="xliff"></a>

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
