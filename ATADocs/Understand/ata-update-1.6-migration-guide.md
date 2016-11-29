---
title: "ATA’yı 1.6 sürümüne güncelleştirme geçiş kılavuzu | Microsoft Docs"
description: "ATA’yı sürüm 1.6’ya güncelleştirme yordamları"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 0756ef64-3aef-4a69-8981-24fa8f285c6a
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fca7f1b2b8260cad6e0ce32aad1c9e1b53fc0ad5
ms.openlocfilehash: e361c1b659210934b9fcd70c7c438a47030eeeba


---

# <a name="ata-update-to-16-migration-guide"></a>ATA’yı 1.6’ya güncelleştirme geçiş kılavuzu
ATA 1.6 güncelleştirmesi aşağıdaki alanlarda geliştirmeler sağlar:

-   Yeni algılamalar

-   Var olan algılamalarda geliştirmeler

-   ATA Lightweight Gateway

-   Otomatik güncelleştirmeler

-   Geliştirilmiş ATA Center performansı

-   Daha az depolama alanı gereksinimleri

-   IBM QRadar desteği

## <a name="updating-ata-to-version-16"></a>ATA’yı sürüm 1.6’e güncelleştirme
> [!NOTE] 
> ATA ortamınızda yüklü değilse, ATA’nın sürüm 1.6’yı da içeren tam sürümünü indirin ve [ATA’yı Yükleme](/advanced-threat-analytics/deploy-use/install-ata) başlığı altında açıklanan standart yükleme yordamını izleyin.

ATA sürüm 1.5’i önceden dağıttıysanız, bu yordam dağıtımınızı güncelleştirmek için gereken adımlarda size yol gösterir.

> [!NOTE] 
> ATA sürüm 1.6’yı doğrudan ATA sürüm 1.4’ün üzerine yükleyemezsiniz. Önce ATA sürüm 1.5’i yüklemeniz gerekir. Yanlışlıkla ATA 1.5 yüklemeden ATA 1.6 yüklemeye çalışırsanız, **Makinenizde zaten daha yeni bir sürüm yüklü** şeklinde bir hata iletisiyle karşılaşırsınız. ATA 1.5 sürümünü yüklemeden önce, yükleme başarısız olsa bile bilgisayarınızda kalacak olan ATA 1.6 sürümünden kalanları kaldırmanız gerekir.

ATA sürüm 1.6’ya güncelleştirmek için bu adımları izleyin:

1. Yükseltme sorunlarını önlemek için, **ATA sürüm 1.6’daki yenilikler** başlığı altında açıklanan [ATA sürüm 1.6’ya güncelleştirirken geçiş hatası](whats-new-version-1.6.md) bölümündeki 8 - 10 arası adımları izlediğinizden emin olun.
2. Yükseltmeyi tamamlamak için gerekli miktarda boş yeriniz olduğundan emin olun. Ne kadar boş alan olması gerektiğini kestirmek için, yüklemeyi hazırlık denetimine kadar gerçekleştirebilir ve ardından gerekli disk alanını ayırdıktan sonra yükseltme işlemini yeniden başlatabilirsiniz.
1.  [Sürüm 1.6 güncelleştirmesini indirme](http://www.microsoft.com/evalcenter/evaluate-microsoft-advanced-threat-analytics)<br>
Uygulamanın bu sürümünde, yeni bir ATA dağıtımı yüklemek ve var olan dağıtımları yükseltmek için aynı yükleme dosyası (Microsoft ATA Center Setup.exe) kullanılır.

2.  ATA Center’ı güncelleştirme

3.  Güncelleştirilmiş ATA Gateway paketini indirme

4.  ATA Gateway’leri güncelleştirme

    > [!IMPORTANT]
    > ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.

### <a name="step-1-update-the-ata-center"></a>1. Adım: ATA Center’ı güncelleştirme

1.  Veritabanınızı yedekleyin: (isteğe bağlı)

    -   ATA Center sanal makinede çalışıyorsa ve bir denetim noktası almak istiyorsanız, önce sanal makineyi kapatın.

    -   ATA Center fiziksel sunucuda çalışıyorsa, [MongoDB’yi yapılandırmak](https://docs.mongodb.org/manual/core/backups/) için önerilen yordamı izleyin.

2.  Microsoft ATA Center Setup.exe adlı yükleme dosyasını çalıştırın ve ekrandaki yönergeleri izleyerek güncelleştirmeyi yükleyin.

    1.  ATA 1.6 için .Net Framework 4.6.1 yüklü olması gerekir. Zaten yüklü değilse, ATA kendi yüklemesi kapsamında .Net Framework 4.6.1’i de yükler.
    
        > [!NOTE] 
        > .Net Framework 4.6.1 yüklemesi için sunucunun yeniden başlatılması gerekebilir. ATA yüklemesi ancak, sunucu yeniden başlatıldıktan sonra devam eder.
    
    2.  **Hoş Geldiniz** sayfasında dilinizi seçin ve **İleri**’ye tıklayın.

    3.  Son Kullanıcı Lisans Sözleşmesi’ni okuyun ve koşulları kabul ediyorsanız **İleri**’ye tıklayın.

    4.  Artık ATA’nın güncel kalması için, Microsoft Update'i kullanmak da mümkündür.  Microsoft Update sayfasında, **Güncelleştirmeleri denetlediğimde Microsoft Update'i kullan (önerilir)** öğesini seçin.
    ![ATA’yı güncel tutma resmi](media/ata_ms_update.png) Görüldüğü gibi, bu işlem Windows ayarlarını diğer Microsoft ürünleri (ATA dahil) için güncelleştirmeleri etkinleştirecek şekilde ayarlar. 
     ![Windows otomatik güncelleştirme resmi](media/ata_installupdatesautomatically.png)

    5.  Yükleme başlamadan önce ATA bir hazırlık denetimi gerçekleştirir. Ön koşulların başarılı şekilde yapılandırıldığından ve az en azından minimum disk alanına sahip olduğunuzdan emin olmak için denetimin sonuçlarını gözden geçirin. 
    ![ATA hazırlık denetimi resmi](media/ata_install_readinesschecks.png)

    6.  **Güncelleştir**’e tıklayın. Güncelleştir'e tıkladıktan sonra, güncelleştirme yordamı tamamlanana kadar ATA çevrimdışı kalır.

3.  ATA Center’ı güncelleştirdikten sonra, ATA Gateway bileşenleri artık tarihi geçmiş olduklarını bildirirler.

    ![Tarihi geçmiş Gateway bileşenlerinin resmi](media/ATA-center-outdated.png)

> [!IMPORTANT] 
> ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.

### <a name="step-2-download-the-ata-gateway-setup-package"></a>2. Adım ATA Gateway kurulum paketini indirme
Etki alanı bağlantı ayarlarını yapılandırdıktan sonra, ATA Gateway kurulum paketini indirebilirsiniz.

ATA Gateway paketini indirmek için:

1.  ATA Gateway paketinin daha önce indirmiş olduğunuz tüm önceki sürümlerini silin.

2.  ATA Gateway makinesinde, bir tarayıcı açın ve ATA Center’da ATA Konsolu için yapılandırdığınız IP adresini girin. ATA Konsolu açıldığında, ayarlar simgesine tıklayın ve **Yapılandırma**’yı seçin.

    ![Yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

3.  **ATA Gateway Bileşenleri** sekmesinde **ATA Gateway Kurulumunu İndir**’e tıklayın.

4.  Paketi yerel olarak kaydedin.

Zip dosyası şunları içerir:

-   ATA Gateway yükleyicisi

-   ATA Center’a bağlanmak için gereken bilgilerin bulunduğu yapılandırma ayarı dosyası

### <a name="step-3-update-the-ata-gateways"></a>3. Adım: ATA Gateway bileşenlerini yapılandırma

1.  ATA Gateway bileşenlerinden her birinde, ATA Gateway paketinden dosyaları ayıklayın ve **Microsoft ATA Gateway Setup.exe** dosyasını çalıştırın.

    > [!NOTE] 
    > Bu ATA Gateway paketini, yeni ATA Gateway bileşenleri yüklemek için de kullanabilirsiniz.

2.  Önceki ayarlarınız korunur, ancak hizmetin yeniden başlatılması birkaç dakika sürebilir.

3.  Dağıtılan tüm diğer ATA Gateway bileşenleri için bu adımı yineleyin.

> [!NOTE] 
> ATA Gateway’i başarıyla güncelleştirdikten sonra, bu ATA Gateway’in eski bildirimi çözülür.

Tüm ATA Gateway bileşenleri başarıyla eşitlendiklerini bildirdiklerinde ve güncelleştirilmiş bir ATA Gateway paketi bulunduğuna ilişkin ileti artık görüntülenmediğinde, tüm ATA Gateway bileşenlerinin başarıyla güncelleştirildiğini anlarsınız.

![Güncelleştirilmiş Gateway bileşenlerinin resmi](media/ATA-gw-updated.png)


## <a name="see-also"></a>Ayrıca bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Nov16_HO3-->


