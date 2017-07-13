---
title: "Advanced Threat Analytics’i Yükleme - 4. Adım | Microsoft Docs"
description: "ATA’yı yükleme işleminin dördüncü adımı ATA Gateway’i yüklemenize yardımcı olur."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 06/18/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 6bbc50c3-bfa8-41db-a2f9-56eed68ef5d2
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 2713f6939c8756d0ecb438e866e6649f13d3c490
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# ATA’yı Yükleme - 4. Adım
<a id="install-ata---step-4" class="xliff"></a>

>[!div class="step-by-step"]
[« 3. Adım](install-ata-step3.md)
[5. Adım »](install-ata-step5.md)

## Adım 4. ATA Gateway’i yükleme
<a id="step-4-install-the-ata-gateway" class="xliff"></a>

Ayrılmış bir sunucuya ATA Gateway’i yüklemeden önce, bağlantı noktası yansıtmanın düzgün yapılandırıldığını ve ATA Gateway’i etki alanı denetleyicilerinden gelen ve giden trafiği görebildiğini doğrulayın. Daha fazla bilgi için bkz. [Bağlantı noktası yansıtmayı doğrulama](validate-port-mirroring.md).


> [!IMPORTANT]
> [KB2919355](http://support.microsoft.com/kb/2919355/)’in yüklendiğinden emin olun.  Düzeltmenin yüklenip yüklenmediğini denetlemek için aşağıdaki PowerShell cmdlet’ini çalıştırın:
>
> `Get-HotFix -Id kb2919355`

ATA Gateway sunucusunda aşağıdaki adımları gerçekleştirin.

1.  Zip dosyasından dosyaları ayıklayın. 
> [!NOTE] 
> Doğrudan zip dosyasından yükleme başarısız olur.

2.  **Microsoft ATA Gateway Setup.exe**’yi çalıştırın ve kurulum sihirbazını izleyin.

3.  **Hoş Geldiniz** sayfasında dilinizi seçin ve **İleri**’ye tıklayın.

4.  Yükleme sihirbazı sunucunun bir etki alanı denetleyicisi veya adanmış bir sunucu olup olmadığını otomatik olarak denetler. Etki alanı denetleyicisi ise ATA Lightweight Gateway, adanmış bir sunucu ise ATA Gateway yüklenir. 
    
    Örneğin, adanmış sunucunuza ATA Gateway yükleneceği zaman bunu size bildirmek için aşağıdaki ekran görüntülenecektir:
    
    ![ATA Gateway yüklemesi](media/ata-gw-install.png) **İleri**’ye tıklayın.

    > [!NOTE] 
    > Etki alanı denetleyicisi veya adanmış sunucu, yükleme işlemi için en düşük donanım gereksinimlerini karşılamıyorsa bir uyarı görürsünüz. Bu, **İleri**’ye tıklamanızı ve yükleme işlemine devam etmenizi engellemez. Bu, veri depolama için fazla yere gereksinim duymayacağınız küçük bir laboratuvar testi ortamında ATA yüklemesi için doğru seçenek olabilir. Üretim ortamlarında etki alanı denetleyicilerinizin veya adanmış sunucularınızın gereksinimleri karşıladığından emin olmak için ATA’nın [kapasite planlaması](ata-capacity-planning.md) kılavuzuyla çalışmanız önerilir.

4.  **Ağ Geçidini Yapılandırma** altında, ortamınıza bağlı olarak aşağıdaki bilgileri girin:

    ![ATA Gateway yapılandırmasının resmi](media/ata-gw-configure.png)

    > [!NOTE]
    > ATA Gateway’i dağıttığınızda kimlik bilgileri sağlamanız gerekmeyecektir. ATA Gateway çoklu oturum açma yoluyla kimlik bilgilerinizi almakta başarısız olursa (bu durum örneğin ATA Center, etki alanında olmadığında ortaya çıkabilir. ATA Gateway, etki alanında değilse ATA yönetici kimlik bilgilerine sahip değilsinizdir) aşağıdaki ekranda belirtildiği gibi kimlik bilgilerinizi sağlamanız istenir. 

  ![ATA gateway kimlik bilgileri sağlama](media/ata-install-credentials.png)

   - Yükleme Yolu: Bu, ATA Gateway’in yükleneceği konumdur. Bu yol varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Gateway’dir. Varsayılan değeri olduğu gibi bırakın.
    
5. **Yükle**’ye tıklayın. ATA Gateway’in yüklemesi sırasında aşağıdaki bileşenler yüklenir ve yapılandırılır:

    -   KB 3047154 (Yalnızca Windows Server 2012 R2 için)

        > [!IMPORTANT]
        > -   KB 3047154’ü bir sanallaştırma konağına yüklemeyin (sanallaştırmayı çalıştıran konak; sanal makinede çalıştırılmasında sorun yoktur). Bu, bağlantı noktası yansıtma işleminin düzgün çalışmayı durdurmasına neden olur. 
        > -   ATA Gateway’e Message Analyzer, Wireshark veya başka bir ağ yakalama yazılımı yüklemeyin. Ağ trafiğini yakalamanız gerekiyorsa, Microsoft Network Monitor 3.4’ü yükleyin ve kullanın.

    -   ATA Gateway hizmeti
    -   Microsoft Visual C++ 2013 Yeniden Dağıtılabilir
    -   Özel Performans İzleyicisi veri koleksiyonu kümesi

5.  Yükleme tamamlandıktan sonra, ATA Gateway için **Başlat**’a tıklayarak tarayıcınızı açın ve ATA Konsolu’nda oturum açın; ATA Lightweight Gateway için **Son**’a tıklayın.


>[!div class="step-by-step"]
[« 3. Adım](install-ata-step3.md)
[5. Adım »](install-ata-step5.md)

## Ayrıca bkz.
<a id="see-also" class="xliff"></a>

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)

