---
title: Yükleme Azure Gelişmiş tehdit koruması - 4. adım | Microsoft Docs
description: Azure ATP yükleme işleminin dördüncü adımı Azure ATP tek başına algılayıcı yüklemek için yardımcı olur.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 51911e39-76c7-4dcd-bc0b-ec6235d0403f
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 9eaa6b37d56c3d8b18c3f5d015581cf7975d6e93
ms.sourcegitcommit: 7f3ded32af35a433d4b407009f87cfa6099f8edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44126340"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="install-azure-atp---step-4"></a>Azure ATP - 4. Adım'ı yükleme

>[!div class="step-by-step"]
[« 3. Adım](install-atp-step3.md)
[5. Adım »](install-atp-step5.md)

## <a name="step-4-install-the-azure-atp-sensor"></a>Adım 4. Azure ATP algılayıcısını yükleme

Azure ATP tek başına algılayıcı adanmış bir sunucuda yüklemeden önce bağlantı noktası yansıtmanın düzgün yapılandırıldığını ve Azure ATP tek başına algılayıcı etki alanı denetleyicilerinden gelen ve giden trafiği görebildiğini doğrulayın. 


> [!IMPORTANT]
>Olun emin .net Framework 4.7 makinede yüklü. .NET Framework 4.7 ise, yüklü Azure ATP algılayıcısı Kurulum paketini, sunucunun yeniden başlatılmasını gerektiren yükler.

Azure ATP algılayıcısı sunucu veya etki alanı denetleyicisi üzerinde aşağıdaki adımları gerçekleştirin.

1. Makine ilgili Azure ATP bulut Hizmeti uç noktasına bağlanabildiğini doğrulayın:
  - https://triprd1wceuw1sensorapi.atp.azure.com (Avrupa için)  
  - https://triprd1wcuse1sensorapi.atp.azure.com (ABD)
  - https://triprd1wcasse1sensorapi.atp.azure.com (Asya için)

2. Zip dosyasından yükleme dosyalarını ayıklayın. 
> [!NOTE] 
> Doğrudan zip dosyasından yükleme başarısız olur.

3.  Çalıştırma **Azure ATP algılayıcısı setup.exe** ve Kurulum sihirbazını izleyin.

4.  **Hoş Geldiniz** sayfasında dilinizi seçin ve **İleri**’ye tıklayın.

     ![Azure ATP tek başına algılayıcı yükleme dili](media/sensor-install-language.png)


5.  Yükleme Sihirbazı otomatik olarak sunucunun bir etki alanı denetleyicisi veya adanmış bir sunucu olup olmadığını denetler. Azure ATP algılayıcısını yüklü etki alanı denetleyicisiyse, Azure ATP tek başına algılayıcı adanmış bir sunucu ise, yüklü. 
    
    Örneğin, bir Azure ATP tek başına algılayıcı için bir Azure ATP tek başına algılayıcı adanmış sunucunuza yüklediğiniz bildiren aşağıdaki ekranı görüntülenir:
    
    ![Azure ATP tek başına algılayıcı yükleme](media/sensor-install-deployment-type.png)

    **İleri**'ye tıklayın.

    > [!NOTE] 
    > Etki alanı denetleyicisi veya adanmış sunucu yüklemesi için en düşük donanım gereksinimlerini karşılamıyorsa bir uyarı alırsınız. Bu, **İleri**’ye tıklamanızı ve yükleme işlemine devam etmenizi engellemez. Bu, veri depolama için fazla yere gereksinim duymadığınız küçük Laboratuvar testi ortamında Azure ATP yüklemesi için doğru seçenek olabilir. Üretim ortamları için Azure ATP'nin ile çalışmak için önerilir [kapasite planlaması](atp-capacity-planning.md) Kılavuzu, etki alanı denetleyicilerinizin veya adanmış sunucularınızın gereksinimleri karşıladığından emin olun.

6.  Altında **algılayıcıyı Yapılandır**, yükleme yolu ve ortamınıza bağlı olarak ve önceki adımda kopyaladığınız erişim anahtarını girin:

    ![Azure ATP tek başına algılayıcı yapılandırmasının resmi](media/sensor-install-config.png)

      - Yükleme yolu: Bu Azure ATP tek başına algılayıcı yüklendiği konumdur. Varsayılan olarak %programfiles%\Azure Gelişmiş tehdit koruması algılayıcı budur. Varsayılan değeri olduğu gibi bırakın.

      - Erişim anahtarı: Bu önceki adımda çalışma alanı portalından alınır.
    
7. **Yükle**’ye tıklayın. Aşağıdaki bileşenler yüklenir ve Azure ATP algılayıcısını yükleme sırasında yapılandırılır:

    -   KB 3047154 (Yalnızca Windows Server 2012 R2 için)

        > [!IMPORTANT]
        > -   KB 3047154’ü bir sanallaştırma konağına yüklemeyin (sanallaştırmayı çalıştıran konak; sanal makinede çalıştırılmasında sorun yoktur). Bu, bağlantı noktası yansıtma işleminin düzgün çalışmayı durdurmasına neden olur. 
        > -   Wireshark çalıştırdıktan sonra Wireshark ATP algılayıcısı makinede yüklüyse, aynı sürücüleri kullandığından, ATP algılayıcısını yeniden başlatmanız gerekir.

    -   Azure ATP algılayıcı hizmeti ve Azure ATP algılayıcı updater hizmeti
    -   Microsoft Visual C++ 2013 Yeniden Dağıtılabilir

8.  Yükleme tamamlandıktan sonra tıklayın **başlatma** tarayıcınızı açın ve Azure ATP çalışma alanı portalında oturum açın.


>[!div class="step-by-step"]
[« 3. Adım](install-atp-step3.md)
[5. Adım »](install-atp-step5.md)


## <a name="see-also"></a>Ayrıca Bkz.

- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)

- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)

- [Azure ATP önkoşulları](atp-prerequisites.md)

- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
