---
title: "Advanced Threat Analytics’i 1.7’ye güncelleştirme geçiş kılavuzu | Microsoft Docs"
description: "ATA’yı 1.7 sürümüne güncelleştirme yordamları"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 8eefcd45-7a4b-4074-ac5b-1ffc48e6654a
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: a1494f0428593ee58c7e1da64192b45c6d006c15
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2017
---
# <a name="ata-update-to-17-migration-guide"></a>ATA’yı 1.7 sürümüne güncelleştirme geçiş kılavuzu
ATA 1.7 güncelleştirmesi aşağıdaki alanlarda geliştirmeler sağlar:

-   Yeni algılamalar

-   Var olan algılamalarda geliştirmeler
  

## <a name="updating-ata-to-version-17"></a>ATA’yı 1.7 sürümüne güncelleştirme

> [!NOTE] 
> ATA ortamınızda yüklü değilse, ATA’nın sürüm 1.7’yi da içeren tam sürümünü indirin ve [ATA’yı Yükleme](install-ata-step1.md) başlığı altında açıklanan standart yükleme yordamını izleyin.

ATA’nın 1.6 sürümünü önceden dağıttıysanız, bu yordam dağıtımınızı güncelleştirmek için gereken adımlarda size yol gösterir.

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

    -   ATA Center sanal makinede çalışıyorsa ve bir denetim noktası almak istiyorsanız, önce sanal makineyi kapatın.

    -   ATA Center fiziksel sunucuda çalışıyorsa, [MongoDB’yi yapılandırmak](https://docs.mongodb.org/manual/core/backups/) için önerilen yordamı izleyin.

2.  **Microsoft ATA Center Setup.exe** adlı yükleme dosyasını çalıştırın ve ekrandaki yönergeleri izleyerek güncelleştirmeyi yükleyin.

    -  **Hoş Geldiniz** sayfasında dilinizi seçin ve **İleri**’ye tıklayın.

    -  Sürüm 1.6’da otomatik güncelleştirmeleri etkinleştirmediyseniz, ATA’nın güncel kalması için ATA’yı Microsoft Update kullanacak şekilde ayarlamanız istenir.  Microsoft Update sayfasında, **Güncelleştirmeleri denetlediğimde Microsoft Update'i kullan (önerilir)** öğesini seçin.
    ![ATA’yı güncel tutma resmi](media/ata_ms_update.png) Görüldüğü gibi, bu işlem Windows ayarlarını diğer Microsoft ürünleri (ATA dahil) için güncelleştirmeleri etkinleştirecek şekilde ayarlar. 
     ![Windows otomatik güncelleştirme resmi](media/ata_installupdatesautomatically.png)

    -  **Veri geçişi** ekranında, verilerin tümünü veya bir kısmını geçirmek istediğinizi seçin. Verilerin yalnızca bir kısmını taşımak isterseniz, daha önceden yakalanan ağ trafiğiniz ve davranış profilleriniz geçirilmez. Bu, anormal davranış algılama özelliğinin olağan dışı etkinlik algılamayı etkinleştirmek için tam bir profil oluşturmasının üç hafta süreceği anlamına gelir. Bu üç hafta boyunca diğer tüm ATA algılamaları düzgün çalışır. **Kısmi** veri geçişinin yüklenmesi çok daha kısa sürer. **Tam** veri geçişini seçerseniz, yüklemenin tamamlanması oldukça uzun sürebilir. **Veri Geçişi** ekranında belirtilen tahmini süre ve gerekli disk alanı, ATA’nın eski sürümlerinde kaydettiğiniz önceden yakalanan ağ trafiği miktarına bağlıdır. **Kısmi** veya **Tam** seçimini yapmadan önce bu gereksinimleri kontrol ettiğinizden emin olun.  
    
    ![ATA veri geçişi](media/migration-data-migration17.png)

    -  **Güncelleştir**’e tıklayın. Güncelleştir'e tıkladıktan sonra, güncelleştirme yordamı tamamlanana kadar ATA çevrimdışı kalır.

4.  ATA Center güncelleştirmesi başarıyla tamamlandıktan sonra, ATA Gateway’ler için ATA konsolundaki **Güncelleştirme** ekranını açmak üzere **Başlat**’a tıklayın.
    ![Güncelleştirme başarılı ekranı](media/migration-center-success17.png)

5.  **Güncelleştirmeler** ekranında, otomatik olarak güncelleştirilecek şekilde yapılandırdıysanız, ATA Gateway’leriniz bu noktada güncelleştirilir. Bu şekilde yapılandırmadıysanız her ATA Gateway’in yanındaki **Güncelleştir**’e tıklayın.
  ![Ağ geçitlerini güncelleştirme resmi](media/migration-update-gw-17.png)

  
> [!IMPORTANT] 
> ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.
> Tüm Gateway’ler üzerinde yapılandırılan Syslog dinleyicisi bağlantı noktası 514 olarak değiştirilecektir.
 
> [!NOTE] 
> Yeni ATA Gateways yüklemek amacıyla ATA 1.7 yükleme paketini edinmek ve [4. Adımda açıklanan yeni Ağ Geçidi yükleme yönergelerini takip etmek için **Ağ Geçitleri** ekranına gidip **Ağ Geçidi Kurulumunu İndir** seçeneğine tıklayın. ATA Gateway](install-ata-step4.md)’i yükleyin.



## <a name="see-also"></a>Ayrıca bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
