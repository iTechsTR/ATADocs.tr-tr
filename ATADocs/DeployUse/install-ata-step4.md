---
title: "ATA’yı Yükleme - 4. Adım | Microsoft Advanced Threat Analytics"
description: "ATA’yı yükleme işleminin dördüncü adımı ATA Gateway’i yüklemenize yardımcı olur."
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 6bbc50c3-bfa8-41db-a2f9-56eed68ef5d2
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d6e7d7bef97bfc4ffde07959dd9256f0319d685f
ms.openlocfilehash: f12e43a6918c0c02bb59e4a093720a805b7dbcfc


---

# ATA’yı Yükleme - 4. Adım

>[!div class="step-by-step"]
[« 3. Adım](install-ata-step3.md)
[5. Adım »](install-ata-step5.md)

## Adım 4. ATA Gateway’i yükleme

Ayrılmış bir sunucuya ATA Gateway’i yüklemeden önce, bağlantı noktası yansıtmanın düzgün yapılandırıldığını ve ATA Gateway’i etki alanı denetleyicilerinden gelen ve giden trafiği görebildiğini doğrulayın. Daha fazla bilgi için bkz. [Bağlantı noktası yansıtmayı doğrulama](validate-port-mirroring.md).


> [!IMPORTANT]
> [KB2919355](http://support.microsoft.com/kb/2919355/)’in yüklendiğinden emin olun.  Düzeltmenin yüklenip yüklenmediğini denetlemek için aşağıdaki PowerShell cmdlet’ini çalıştırın:
>
> `Get-HotFix -Id kb2919355`

ATA Gateway sunucusunda aşağıdaki adımları gerçekleştirin.

1.  Zip dosyasından dosyaları ayıklayın. 
> [!NOTE] 
> Doğrudan zip dosyasından yükleme başarısız olur.

2.  Yükseltilmiş bir komut isteminde **Microsoft ATA Gateway Setup.exe**’yi çalıştırın ve kurulum sihirbazını izleyin.

3.  **Hoş Geldiniz** sayfasında dilinizi seçin ve **İleri**’ye tıklayın.

4.  **ATA Gateway Yapılandırması**’nın altında, ortamınıza bağlı olarak aşağıdaki bilgileri girin:

    ![ATA Gateway yapılandırmasının resmi](media/ATA-Gateway-Configuration.JPG)

    |Alan|Açıklama|Açıklamalar|
    |---------|---------------|------------|
    |Yükleme Yolu|Bu, ATA Gateway’in yükleneceği konumdur. Varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Gateway yoludur.|Varsayılan değeri olduğu gibi bırakın.|
    |ATA Gateway Hizmeti SSL sertifikası|Bu, ATA Gateway tarafından kullanılacak olan sertifikadır.|Yalnızca laboratuvar ortamları için otomatik olarak imzalanan bir sertifika kullanın.|
    |ATA Gateway Kaydı|ATA yöneticisinin Kullanıcı Adı ve Parola değerlerini girin.|ATA Gateway’in ATA Center’a kaydolması için, ATA Center’ı yükleyen kullanıcının kullanıcı adını ve parolasını girin. Bu kullanıcı, ATA Center’da aşağıdaki yerel gruplardan birinin üyesi olmalıdır.<br /><br />-   Administrators<br />-   Microsoft Advanced Threat Analytics Administrators **Not:** Bu kimlik bilgileri yalnızca kayıt için kullanılır ve ATA’da depolanmaz.|
    ATA Gateway’in yüklemesi sırasında aşağıdaki bileşenler yüklenir ve yapılandırılır:

    -   KB 3047154

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

## Ayrıca Bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)




<!--HONumber=Jun16_HO4-->


