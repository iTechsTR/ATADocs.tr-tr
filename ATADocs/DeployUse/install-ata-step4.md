---
# required metadata

title: ATA’yı Yükleme - 4. Adım | Microsoft Advanced Threat Analytics
description: ATA’yı yükleme işleminin dördüncü adımı ATA Gateway’i yüklemenize yardımcı olur.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 6bbc50c3-bfa8-41db-a2f9-56eed68ef5d2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ATA’yı Yükleme - 4. Adım

>[!div class="step-by-step"]
[« 3. Adım](install-ata-step3.md)
[5. Adım »](install-ata-step5.md)

## 4. Adım ATA Gateway’i yükleme
ATA Gateway’i yüklemeden önce, bağlantı noktası yansıtmanın düzgün yapılandırıldığını ve ATA Gateway’i etki alanı denetleyicilerinden gelen ve giden trafiği görebildiğini doğrulayın. Daha fazla bilgi için bkz. [Bağlantı noktası yansıtmayı doğrulama](/advanced-threat-analytics/plan-design/validate-port-mirroring).

> [!IMPORTANT]
> [KB2919355](http://support.microsoft.com/kb/2919355/)’in yüklendiğinden emin olun.  Düzeltmenin yüklenip yüklenmediğini denetlemek için aşağıdaki PowerShell cmdlet’ini çalıştırın:
>
> `Get-HotFix -Id kb2919355`

ATA Gateway sunucusunda aşağıdaki adımları gerçekleştirin.

1.  Zip dosyasından dosyaları ayıklayın.

2.  Yükseltilmiş bir komut isteminde Microsoft ATA Gateway Setup.exe’yi çalıştırın ve kurulum sihirbazını izleyin.

3.  **Hoş Geldiniz** sayfasında dilinizi seçin ve **İleri**’ye tıklayın..

4.  **ATA Gateway Yapılandırması**’nın altında, ortamınıza bağlı olarak aşağıdaki bilgileri girin:

    ![ATA Gateway yapılandırmasının resmi](media/ATA-Gateway-Configuration.JPG)

    |Alan|Açıklama|Notlar|
    |---------|---------------|------------|
    |Yükleme Yolu|Bu, ATA Gateway’in yükleneceği konumdur. Varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Gateway yoludur.|Varsayılan değeri olduğu gibi bırakın.|
    |ATA Gateway Hizmeti SSL sertifikası|Bu, ATA Gateway tarafından kullanılacak olan sertifikadır.|Yalnızca laboratuvar ortamları için otomatik olarak imzalanan bir sertifika kullanın.|
    |ATA Gateway Kaydı|ATA yöneticisinin Kullanıcı Adı ve Parola değerlerini girin.|ATA Gateway’in ATA Center’a kaydolması için, ATA Center’ı yükleyen kullanıcının kullanıcı adını ve parolasını girin. Bu kullanıcı, ATA Center’da aşağıdaki yerel gruplardan birinin üyesi olmalıdır.<br /><br />-   Administrators<br />-   Microsoft Advanced Threat Analytics Administrators **Not:** Bu kimlik bilgileri yalnızca kayıt için kullanılır ve ATA’da depolanmaz.|
    ATA Gateway’in yüklemesi sırasında aşağıdaki bileşenler yüklenir ve yapılandırılır:

    -   KB 3047154

        > [!IMPORTANT]
        > -   KB 3047154’ü sanallaştırma ana bilgisayarına yüklemeyin. Bu, bağlantı noktası yansıtma işleminin düzgün çalışmayı durdurmasına neden olur.
        > -   ATA Gateway’e Message Analyzer, Wireshark veya başka bir ağ yakalama yazılımı yüklemeyin. Ağ trafiğini yakalamanız gerekiyorsa, Microsoft Network Monitor 3.4’ü yükleyin ve kullanın.

    -   ATA Gateway hizmeti

    -   Microsoft Visual C++ 2013 Yeniden Dağıtılabilir

    -   Özel Performans İzleyicisi veri koleksiyonu kümesi

5.  Yükleme tamamlandıktan sonra, tarayıcınızı açmak ve ATA Konsolu’nda oturum açmak için **Başlat**’a tıklayın.


>[!div class="step-by-step"]
[« 3. Adım](install-ata-step3.md)
[5. Adım »](install-ata-step5.md)

## Ayrıca Bkz.

- [Destek için forumumuzu gözden geçirin!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](/advanced-threat-analytics/plan-design/configure-event-collection)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)


<!--HONumber=Apr16_HO4-->


