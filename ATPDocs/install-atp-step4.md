---
title: "Yükleme Azure Gelişmiş tehdit koruması - 4. adım | Microsoft Docs"
description: "Azure ATP yükleme dört adım Azure ATP tek başına algılayıcı yüklemenize yardımcı olur."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2017
ms.topic: get-started-article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 51911e39-76c7-4dcd-bc0b-ec6235d0403f
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 7b003882f21f22b3427fb95534ca2bde255b14e6
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="install-azure-atp---step-4"></a>Azure ATP - 4. adım yükleme

>[!div class="step-by-step"]
[« 3. Adım](install-atp-step3.md)
[5. Adım »](install-atp-step5.md)

## <a name="step-4-install-the-azure-atp-sensor"></a>Adım 4. Azure ATP algılayıcı yükleyin

Özel bir sunucu üzerinde Azure ATP tek başına algılayıcı yüklemeden önce bağlantı noktası yansıtmanın düzgün yapılandırıldığını ve Azure ATP tek başına algılayıcı etki alanı denetleyicilerinden gelen ve giden trafiği görebildiğini doğrulayın. 


> [!IMPORTANT]
>Olun emin .net Framework 4.7 makineye yüklenir. .NET Framework 4.7 ise yüklenmemiş Azure ATP algılayıcı kurulum paketi, sunucunun yeniden başlatılmasını gerektiren yükler. Makinenin Azure ATP bulut Hizmeti uç noktası bağlantısı olduğunu doğrulayın: https://triprd1wceuw1sensorapi.atp.azure.com (için Avrupa) veya https://triprd1wcuse1sensorapi.atp.azure.com (ABD için).

Azure ATP algılayıcı sunucu veya etki alanı denetleyicisinde aşağıdaki adımları gerçekleştirin.

1.  Zip dosyasından dosyaları ayıklayın. 
> [!NOTE] 
> Doğrudan zip dosyasından yükleme başarısız olur.

2.  Çalıştırma **Azure ATP algılayıcı setup.exe** ve Kurulum sihirbazını izleyin.

3.  **Hoş Geldiniz** sayfasında dilinizi seçin ve **İleri**’ye tıklayın.

     ![Azure ATP tek başına algılayıcı yükleme dili](media/sensor-install-language.png)


4.  Yükleme Sihirbazı'nı otomatik olarak sunucunun bir etki alanı denetleyicisi veya ayrılmış bir sunucuya olup olmadığını denetler. Bir etki alanı denetleyicisi ise, Azure ATP algılayıcı yüklenir, ayrılmış bir sunucu ise, Azure ATP tek başına algılayıcı yüklenir. 
    
    Örneğin, bir Azure ATP tek başına algılayıcı için bir Azure ATP tek başına algılayıcı adanmış sunucunuz üzerinde yüklendiğini size bildirmek için aşağıdaki ekran görüntülenir:
    
    ![Azure ATP tek başına algılayıcı yükleme](media/sensor-install-deployment-type.png)

    **İleri**'ye tıklayın.

    > [!NOTE] 
    > Etki alanı denetleyicisi veya adanmış sunucu yüklemesi için en düşük donanım gereksinimlerini karşılamıyorsa, bir uyarı alırsınız. Bu, **İleri**’ye tıklamanızı ve yükleme işlemine devam etmenizi engellemez. Bu veri depolama için gerektiği kadar yeri gerekmeyen küçük Laboratuvar test ortamında Azure ATP yüklemesi için doğru seçeneği olabilir. Üretim ortamları için Azure ATP ile 's çalışmaya önerilir [kapasite planlaması](atp-capacity-planning.md) Kılavuzu etki alanı denetleyicileri veya adanmış sunucular gerekli gereksinimlerini karşıladığından emin olun.

4.  Altında **algılayıcı yapılandırma**, ortamınıza bağlı olarak önceki adımda kopyalanan erişim anahtar ve yükleme yolu girin:

    ![Azure ATP tek başına algılayıcı yapılandırma resmi](media/sensor-install-config.png)

      - : Yükleme bu Azure ATP tek başına algılayıcı yüklendiği konumun yoludur. Varsayılan olarak %programfiles%\Azure Advanced Threat Protection algılayıcı budur. Varsayılan değeri olduğu gibi bırakın.

      - Erişim anahtarı: Bu önceki adımda çalışma portalından alınır.
    
5. **Yükle**’ye tıklayın. Aşağıdaki bileşenler yüklenir ve Azure ATP algılayıcı yüklenmesi sırasında yapılandırılır:

    -   KB 3047154 (Yalnızca Windows Server 2012 R2 için)

        > [!IMPORTANT]
        > -   KB 3047154’ü bir sanallaştırma konağına yüklemeyin (sanallaştırmayı çalıştıran konak; sanal makinede çalıştırılmasında sorun yoktur). Bu, bağlantı noktası yansıtma işleminin düzgün çalışmayı durdurmasına neden olur. 
        > -   Wireshark çalıştırdıktan sonra Wireshark ATP algılayıcı makinede yüklü aynı sürücüleri kullandığından, ATP algılayıcı yeniden başlatmanız gerekir.

    -   Azure ATP algılayıcı hizmeti ve Azure ATP algılayıcı güncelleştirici hizmetini
    -   Microsoft Visual C++ 2013 Yeniden Dağıtılabilir

5.  Yükleme tamamlandıktan sonra **başlatma** tarayıcınızı açın ve Azure ATP çalışma portalında oturum açın.


>[!div class="step-by-step"]
[« 3. Adım](install-atp-step3.md)
[5. Adım »](install-atp-step5.md)


## <a name="see-also"></a>Ayrıca bkz:

- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)

- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)

- [Azure ATP önkoşulları](atp-prerequisites.md)

- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)