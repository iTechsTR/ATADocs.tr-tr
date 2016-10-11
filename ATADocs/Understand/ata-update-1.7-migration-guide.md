---
title: "ATA’yı 1.7 sürümüne güncelleştirme geçiş kılavuzu | Microsoft ATA"
description: "ATA’yı 1.7 sürümüne güncelleştirme yordamları"
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: fb65eb41-b215-4530-93a2-0b8991f4e980
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e3b690767e5c6f5561a97a73eccfbf50ddb04148
ms.openlocfilehash: 5c20c41c3fe587f18087d64f4f84c1df65072fde


---

# ATA’yı 1.7 sürümüne güncelleştirme geçiş kılavuzu
ATA 1.7 güncelleştirmesi aşağıdaki alanlarda geliştirmeler sağlar:

-   Yeni algılamalar

-   Var olan algılamalarda geliştirmeler
  

## ATA’yı 1.7 sürümüne güncelleştirme
> [!NOTE] 
> ATA ortamınızda yüklü değilse, ATA’nın sürüm 1.7’yi da içeren tam sürümünü indirin ve [ATA’yı Yükleme](/advanced-threat-analytics/deploy-use/install-ata) başlığı altında açıklanan standart yükleme yordamını izleyin.

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

### 1. Adım: ATA Center’ı güncelleştirme

1.  Veritabanınızı yedekleyin: (isteğe bağlı)

    -   ATA Center sanal makinede çalışıyorsa ve bir denetim noktası almak istiyorsanız, önce sanal makineyi kapatın.

    -   ATA Center fiziksel sunucuda çalışıyorsa, [MongoDB’yi yapılandırmak](https://docs.mongodb.org/manual/core/backups/) için önerilen yordamı izleyin.

2.  **Microsoft ATA Center Setup.exe** adlı yükleme dosyasını çalıştırın ve ekrandaki yönergeleri izleyerek güncelleştirmeyi yükleyin.

    -  **Hoş Geldiniz** sayfasında dilinizi seçin ve **İleri**’ye tıklayın.

    -  Sürüm 1.6’da otomatik güncelleştirmeleri etkinleştirmediyseniz, ATA’nın güncel kalması için ATA’yı Microsoft Update kullanacak şekilde ayarlamanız istenir.  Microsoft Update sayfasında, **Güncelleştirmeleri denetlediğimde Microsoft Update'i kullan (önerilir)** öğesini seçin.
    ![ATA’yı güncel tutma resmi](media/ata_ms_update.png) Bu, burada görüldüğü gibi, Windows ayarlarını diğer Microsoft ürünleri (ATA dahil) için güncelleştirmeleri etkinleştirecek şekilde ayarlar. 
     ![Windows otomatik güncelleştirme resmi](media/ata_installupdatesautomatically.png)

    -  **Veri geçişi** ekranında, verilerin tümünü veya bir kısmını geçirmek istediğinizi seçin. Verilerin yalnızca bir kısmını taşımak isterseniz, daha önceden yakalanan ağ trafiğiniz ve davranış profilleriniz geçirilmez. Bu, anormal davranış algılama özelliğinin olağan dışı etkinlik algılamayı etkinleştirmek için tam bir profil oluşturmasının üç hafta süreceği anlamına gelir. Bu üç hafta boyunca diğer tüm ATA algılamaları düzgün çalışır. **Kısmi** veri geçişinin yüklenmesi çok daha kısa sürer. **Tam** veri geçişini seçerseniz, yüklemenin tamamlanması oldukça uzun sürebilir. **Veri Geçişi** ekranında belirtilen tahmini süre ve gerekli disk alanı, ATA’nın eski sürümlerinde kaydettiğiniz önceden yakalanan ağ trafiği miktarına bağlıdır. **Kısmi** veya **Tam** seçimini yapmadan önce bu gereksinimleri kontrol ettiğinizden emin olun.  
    
    ![ATA veri geçişi](media/migration data migration.png)

    -  **Güncelleştir**’e tıklayın. Güncelleştir'e tıkladıktan sonra, güncelleştirme yordamı tamamlanana kadar ATA çevrimdışı kalır.

4.  ATA Center güncelleştirmesi başarıyla tamamlandıktan sonra, ATA Gateway’ler için ATA konsolundaki **Güncelleştirme** ekranını açmak üzere **Başlat**’a tıklayın.
    ![Güncelleştirme başarılı ekranı](media/migration center success.png)

5.  **Güncelleştirmeler** ekranında, otomatik olarak güncelleştirilecek şekilde yapılandırdıysanız, ATA Gateway’leriniz bu noktada güncelleştirilir. Bu şekilde yapılandırmadıysanız her ATA Gateway’in yanındaki **Güncelleştir**’e tıklayın.
  ![Ağ geçitlerini güncelleştirme resmi](media/migration update gw.png)

  
> [!IMPORTANT] 
> ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.
> Tüm Gateway’ler üzerinde yapılandırılan Syslog dinleyicisi bağlantı noktası 514 olarak değiştirilecektir.
 
    > [!NOTE] 
    > To install new ATA Gateways, go the **Gateways** screen and click **Download Gateway Setup** to get the ATA 1.7 installation package and follow the instructions for new Gateway installation as described in [Step 4. Install the ATA Gateway](/advanced-threat-analytics/deploy-use/install-ata-step4) .



## Ayrıca Bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Oct16_HO1-->


