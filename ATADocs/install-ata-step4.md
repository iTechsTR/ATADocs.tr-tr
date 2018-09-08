---
title: Advanced Threat Analytics’i Yükleme - 4. Adım | Microsoft Docs
description: ATA’yı yükleme işleminin dördüncü adımı ATA Gateway’i yüklemenize yardımcı olur.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 6bbc50c3-bfa8-41db-a2f9-56eed68ef5d2
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 5414539edca088b49d16dc03c17dfe0ee0a2bfc5
ms.sourcegitcommit: 7f3ded32af35a433d4b407009f87cfa6099f8edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44125881"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="install-ata---step-4"></a>ATA’yı Yükleme - 4. Adım

>[!div class="step-by-step"]
[« 3. Adım](install-ata-step3.md)
[5. Adım »](install-ata-step5.md)

## <a name="step-4-install-the-ata-gateway"></a>Adım 4. ATA Gateway’i yükleme

Ayrılmış bir sunucuya ATA Gateway’i yüklemeden önce, bağlantı noktası yansıtmanın düzgün yapılandırıldığını ve ATA Gateway’i etki alanı denetleyicilerinden gelen ve giden trafiği görebildiğini doğrulayın. Daha fazla bilgi için [bağlantı noktası yansıtmayı doğrulama](validate-port-mirroring.md).


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

4.  Yükleme Sihirbazı otomatik olarak sunucunun bir etki alanı denetleyicisi veya adanmış bir sunucu olup olmadığını denetler. Etki alanı denetleyicisiyse, ATA Lightweight Gateway yüklendikten, ayrılmış bir sunucu ise, ATA Gateway yüklenir. 
    
    Örneğin, bir ATA Gateway için adanmış sunucunuza ATA Gateway yükleneceğini bildiren aşağıdaki ekranı görüntülenir:
    
    ![ATA Gateway yüklemesi](media/ata-gw-install.png) **İleri**’ye tıklayın.

    > [!NOTE] 
    > Etki alanı denetleyicisi veya adanmış sunucu yüklemesi için en düşük donanım gereksinimlerini karşılamıyorsa bir uyarı alırsınız. Bu, **İleri**’ye tıklamanızı ve yükleme işlemine devam etmenizi engellemez. Bu, veri depolama için fazla yere gereksinim duymadığınız küçük Laboratuvar testi ortamında ATA yüklemesi için doğru seçenek olabilir. Üretim ortamlarında etki alanı denetleyicilerinizin veya adanmış sunucularınızın gereksinimleri karşıladığından emin olmak için ATA’nın [kapasite planlaması](ata-capacity-planning.md) kılavuzuyla çalışmanız önerilir.

4.  **Ağ Geçidini Yapılandırma** altında, ortamınıza bağlı olarak aşağıdaki bilgileri girin:

    ![ATA Gateway yapılandırmasının resmi](media/ata-gw-configure.png)

    > [!NOTE]
    > ATA Gateway'i dağıttığınızda kimlik bilgilerini sağlamanız gerekmez. Çoklu oturum açma kullanarak kimlik bilgilerinizi almak ATA Gateway yüklemesi başarısız olursa (ATA Center etki alanında değilse, örneğin, bu sorun oluşabilir ATA Gateway etki alanında değilse ATA yönetici kimlik bilgilerine sahip değil), sağlamanız istenir. Aşağıdaki ekranda gösterildiği gibi kimlik: 

  ![ATA gateway kimlik bilgilerini sağlayın](media/ata-install-credentials.png)

   - Yükleme yolu: ATA Gateway yüklendiği konumun budur. Bu yol varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Gateway’dir. Varsayılan değeri olduğu gibi bırakın.
    
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


## <a name="related-videos"></a>İlgili videolar
- [ATA dağıtımı genel bakış](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)
- [ATA Gateway türü sağ seçme](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)

## <a name="see-also"></a>Ayrıca Bkz.
- [ATA POC Dağıtım Kılavuzu](http://aka.ms/atapoc)
- [ATA boyutlandırma aracı](http://aka.ms/atasizingtool)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)

