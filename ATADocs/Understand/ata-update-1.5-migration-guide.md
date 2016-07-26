---
title: "ATA’yı 1.5 sürümüne güncelleştirme geçiş kılavuzu | Microsoft ATA"
description: "ATA’yı sürüm 1.5’e güncelleştirme yordamları"
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: fb65eb41-b215-4530-93a2-0b8991f4e980
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5c7163bc7b1989672e587bfb4fa6a65cd4e3751
ms.openlocfilehash: 4c82467c8830b1e602edbe720cd6107664e433b9


---

# ATA’yı 1.5’e güncelleştirme geçiş kılavuzu
ATA 1.5 güncelleştirmesi aşağıdaki alanlarda geliştirmeler sağlar:

-   Daha hızlı algılama süreleri

-   NAT (ağ adresi çevirisi) cihazları için iyileştirilmiş otomatik algılama algoritması

-   Etki alanına katılmayan cihazlar için iyileştirilmiş ad çözümleme işlemi

-   Ürün güncelleştirmeleri sırasında veri geçiş desteği

-   Binlerce varlığın katıldığı kuşkulu etkinliklerde kullanıcı arabirimi yanıt sürelerinde gelişme

-   İzleme uyarılarının geliştirilmiş otomatik çözümlemesi

-   İzleme ve sorun gidermeyi iyileştirmek için ek performans sayaçları

## ATA’yı sürüm 1.5’e güncelleştirme
> [!NOTE]
> ATA ortamınızda yüklü değilse, ATA’nın sürüm 1.5’i de içeren tam sürümünü indirin ve [ATA’yı Yükleme](/advanced-threat-analytics/deploy-use/install-ata) başlığı altında açıklanan standart yükleme yordamını izleyin.

ATA sürüm 1.4’ü önceden dağıttıysanız, bu yordam yüklemenizi güncelleştirmek için gereken adımlarda size yol gösterir.

ATA sürüm 1.5’e güncelleştirmek için bu adımları izleyin:

1.  [Sürüm 1.5 güncelleştirmesini indirme](http://aka.ms/ata1_5update)
      > [!NOTE]
         Sürüm 1.5’e güncelleştirmek için, ATA’nın güncelleştirilmiş tam sürümünü de kullanabilirsiniz.


2.  ATA Center’ı güncelleştirme

3.  Güncelleştirilmiş ATA Gateway paketini indirme

4.  ATA Gateway’leri güncelleştirme

    > [!IMPORTANT]
    > ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.

### 1. Adım: ATA Center’ı güncelleştirme

1.  Veritabanınızı yedekleyin: (isteğe bağlı)

    -   ATA Center sanal makinede çalışıyorsa ve bir denetim noktası almak istiyorsanız, önce sanal makineyi kapatın.

    -   ATA Center fiziksel sunucuda çalışıyorsa, [MongoDB’yi yapılandırmak](https://docs.mongodb.org/manual/core/backups/) için önerilen yordamı izleyin.

2.  Microsoft ATA Center Update.exe güncelleştirme dosyasını çalıştırın ve ekrandaki yönergeleri izleyerek güncelleştirmeyi yükleyin.

    1.  **Hoş Geldiniz** sayfasında dilinizi seçin ve **İleri**’ye tıklayın.

    2.  Son Kullanıcı Lisans Sözleşmesi’ni okuyun ve koşulları kabul ediyorsanız, onay kutusuna tıklayın ve ardından **İleri**’ye tıklayın.

    3.  Tam (varsayılan) geçişi mi yoksa kısmı geçişi mi çalıştırmak istediğinizi seçin.

        ![Tam veya kısmi geçişi seçme](media/ATA-center-fullpartial.png)

        -   **Kısmi** geçişi seçerseniz, ATA’nın çözümlediği tüm toplanan ağ trafiği ve iletilen Windows olayları silinir ve kullanıcı davranış profillerinin yeniden öğrenilmesi gerekir; bu işlem en az üç hafta sürer. Disk alanınız yetersizse, **Kısmi** geçiş çalıştırmak yararlı olabilir.

        -   **Tam** geçişi çalıştırırsanız, yükseltme sayfasında sizin için hesaplanan ek disk alanına ihtiyacınız olur ve ağ trafiğine bağlı olarak geçiş daha uzun sürebilir. Tam geçişte, daha önce toplanmış olan tüm verileri ve kullanıcı davranış profilleri korunur. Bu da, ATA’nın davranış profillerini öğrenmesi için ek süre gerekmemesi ve anormal davranışların güncelleştirmeden hemen sonra algılanabilmesi anlamına gelir.

3.  **Güncelleştir**’e tıklayın. Güncelleştir'i tıkladığınızda, güncelleştirme yordamı tamamlanana kadar ATA çevrimdışı kalır.

4.  ATA Center’ı güncelleştirdikten sonra, ATA Gateway bileşenleri artık tarihi geçmiş olduklarını bildirirler.

    ![Tarihi geçmiş Gateway bileşenlerinin resmi](media/ATA-center-outdated.png)

> [!IMPORTANT]
> - ATA’nın düzgün çalıştığından emin olmak için tüm ATA Gateway bileşenlerini güncelleştirin.

### 2. Adım ATA Gateway kurulum paketini indirme
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

### 3. Adım: ATA Gateway bileşenlerini yapılandırma

1.  ATA Gateway bileşenlerinden her birinde, ATA Gateway paketinden dosyaları ayıklayın ve Microsoft ATA Gateway Kurulumu dosyasını çalıştırın.

    > [!NOTE]
    > Bu ATA Gateway paketini, yeni ATA Gateway bileşenleri yüklemek için de kullanabilirsiniz.

2.  Önceki ayarlarınız korunur, ancak hizmetin yeniden başlatılması birkaç dakika sürebilir.

3.  Dağıtılan tüm diğer ATA Gateway bileşenleri için bu adımı yineleyin.

> [!NOTE]
> ATA Gateway’i başarıyla güncelleştirdikten sonra, bu ATA Gateway’in eski bildirimi kaybolur.

Tüm ATA Gateway bileşenleri başarıyla eşitlendiklerini bildirdiklerinde ve güncelleştirilmiş bir ATA Gateway paketi bulunduğuna ilişkin ileti artık görüntülenmediğinde, tüm ATA Gateway bileşenlerinin başarıyla güncelleştirildiğini anlarsınız.

![Güncelleştirilmiş Gateway bileşenlerinin resmi](media/ATA-gw-updated.png)

## Ayrıca Bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jul16_HO3-->


