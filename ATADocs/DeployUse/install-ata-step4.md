---
title: "Advanced Threat Analytics’i Yükleme - 4. Adım | Microsoft Docs"
description: "ATA’yı yükleme işleminin dördüncü adımı ATA Gateway’i yüklemenize yardımcı olur."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 6bbc50c3-bfa8-41db-a2f9-56eed68ef5d2
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: a5a9b0672fa6a571e265ff5472cb7f7d1cfb034f
ms.sourcegitcommit: 49e892a82275efa5146998764e850959f20d3216
translationtype: HT
---
*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*



# <a name="install-ata---step-4"></a>ATA’yı Yükleme - 4. Adım

>[!div class="step-by-step"]
[« 3. Adım](install-ata-step3.md)
[5. Adım »](install-ata-step5.md)

## <a name="step-4-install-the-ata-gateway"></a>Adım 4. ATA Gateway’i yükleme

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
    
    Örneğin, ATA Lightweight Gateway söz konusuysa etki alanı denetleyicinize ATA Lightweight Gateway yükleneceğini bildiren aşağıdaki ekranı görürsünüz:
    
    ![ATA Lightweight Gateway yüklemesi](media/ATA-lightweight-gateway-install-selected.png) **İleri**’ye tıklayın.

    > [!NOTE] 
    > Etki alanı denetleyicisi veya adanmış sunucu, yükleme işlemi için en düşük donanım gereksinimlerini karşılamıyorsa bir uyarı görürsünüz. Bu, **İleri**’ye tıklamanızı ve yükleme işlemine devam etmenizi engellemez. Bu, veri depolama için fazla yere gereksinim duymayacağınız küçük bir laboratuvar testi ortamında ATA yüklemesi için doğru seçenek olabilir. Üretim ortamlarında etki alanı denetleyicilerinizin veya adanmış sunucularınızın gereksinimleri karşıladığından emin olmak için ATA’nın [kapasite planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning) kılavuzuyla çalışmanız önerilir.

4.  **ATA Gateway Yapılandırması** altında, ortamınıza bağlı olarak aşağıdaki bilgileri girin:

    ![ATA Gateway yapılandırmasının resmi](media/ATA-Gateway-Configuration.png)

    |Alan|Açıklama|Açıklamalar|
    |---------|---------------|------------|
    |Yükleme Yolu|Bu, ATA Gateway’in yükleneceği konumdur. Varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Gateway yoludur.|Varsayılan değeri olduğu gibi bırakın.|
    |Ağ Geçidi Hizmeti SSL sertifikası|Bu, ATA Gateway tarafından kullanılacak olan sertifikadır.|Yalnızca laboratuvar ortamları için otomatik olarak imzalanan bir sertifika kullanın.|
    |Ağ Geçidi Kaydı|ATA yöneticisinin Kullanıcı Adı ve Parola değerlerini girin.|ATA Gateway’in ATA Center’a kaydolması için, ATA Center’ı yükleyen kullanıcının kullanıcı adını ve parolasını girin. Bu kullanıcı, ATA Center’da aşağıdaki yerel gruplardan birinin üyesi olmalıdır.<br /><br />-   Administrators<br />-   Microsoft Advanced Threat Analytics Administrators **Not:** Bu kimlik bilgileri yalnızca kayıt için kullanılır ve ATA’da depolanmaz.|
    
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

## <a name="see-also"></a>Ayrıca bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)

