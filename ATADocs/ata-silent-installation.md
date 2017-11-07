---
title: "Advanced Threat Analytics’i Sessiz Yükleme | Microsoft Docs"
description: "Burada ATA’nın sessizce yüklenmesi açıklanmaktadır."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: b3cceb18-0f3c-42ac-8630-bdc6b310f1d6
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 16a8eb868448cc43244d3cf3c933e2e539b08d07
ms.sourcegitcommit: e2cb3af9c1dbb0b75946dc70cc439b19d654541c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*


# <a name="ata-silent-installation"></a>ATA’yı Sessiz Yükleme
Bu makalede ATA’yı sessizce yüklemeye dair yönergeler mevcuttur.

## <a name="prerequisites"></a>Önkoşullar

ATA sürüm 1.8 için Microsoft .NET Framework 4.6.1’in yüklü olması gerekir. 

ATA’yı yüklediğiniz veya güncelleştirdiğiniz zaman, .Net Framework 4.6.1, Microsoft ATA dağıtımının parçası olarak otomatik yüklenir.

> [!Note] 
> .Net Framework 4.6.1 yüklemesi için sunucunun yeniden başlatılması gerekebilir. Etki Alanı Denetleyicilerinde ATA Gateway’i yüklerken, bu Etki Alanı Denetleyicileri için bir bakım penceresi zamanlamayı dikkate alın.
ATA’yı sessiz yükleme yöntemini kullanırken, yükleyici yükleme sonunda sunucuyu (gerekirse) otomatik olarak yeniden başlatmak üzere yapılandırılır. Bir Windows Installer hatası yüzünden sunucunun yeniden başlatılmasını önlemek için norestart bayrağını kullanmak sağlıklı değildir, bu nedenle sessiz yüklemeyi sadece bir bakım penceresi esnasında çalıştırdığınızdan emin olun.

Dağıtımın ilerleme durumunu izlemek için, **%AppData%\Local\Temp** konumunda bulunan ATA yükleyici günlüklerine bakın.


## <a name="install-the-ata-center"></a>ATA Center’ı yükleme

ATA Center’ı yüklemek için aşağıdaki komutu kullanın:

**Söz dizimi**:

    "Microsoft ATA Center Setup.exe" [/quiet] [/Help] [--LicenseAccepted] [NetFrameworkCommandLineArguments="/q"] [InstallationPath="<InstallPath>"] [DatabaseDataPath= "<DBPath>"] [CenterIpAddress=<CenterIPAddress>] [CenterPort=<CenterPort>] [CenterCertificateThumbprint="<CertThumbprint>"] 
    [ConsoleIpAddress=<ConsoleIPAddress>] [ConsoleCertificateThumbprint="<CertThumbprint >"]
    
**Yükleme seçenekleri**:

> [!div class="mx-tableFixed"]
|Ad|Sözdizimi|Sessiz yükleme için zorunlu mu?|Açıklama|
|-------------|----------|---------|---------|
|Quiet|istemci bilgisayarlara|Evet|Kullanıcı arabirimi ve istem göstermeden yükleyiciyi çalıştırır.|
|Yardım|/help|Hayır|Yardım ve hızlı başvuru sağlar. Tüm seçenek ve davranışların bir listesi dahil olmak üzere kurulum komutunun doğru kullanımını gösterir.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Evet|.Net Framework yüklemesi için parametreleri belirtir. .Net Framework sessiz yüklemesini zorunlu kılmak üzere ayarlanmalıdır.|
|LicenseAccepted|--LicenseAccepted|Evet|Lisansın okunup onaylanmış olduğunu gösterir. Sessiz yüklemede ayarlanması gerekir.|

**Yükleme parametreleri**:

> [!div class="mx-tableFixed"]
|Ad|Sözdizimi|Sessiz yükleme için zorunlu mu?|Açıklama|
|-------------|----------|---------|---------|
|InstallationPath|InstallationPath="<InstallPath>"|Hayır|ATA ikili dosyalarını yükleme yolunu ayarlar. Varsayılan yol: C:\Program Files\Microsoft Advanced Threat Analytics\Center|
|DatabaseDataPath|DatabaseDataPath= "<DBPath>"|Hayır|ATA Veritabanı veri klasörünün yolunu ayarlar. Varsayılan yol: C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\data|
|CenterIpAddress|CenterIpAddress=<CenterIPAddress>|Evet|ATA Center Hizmetinin IP adresini ayarlar|
|CenterPort|CenterPort=<CenterPort>|Evet|ATA Center Hizmetinin ağ bağlantı noktasını ayarlar|
|CenterCertificateThumbprint|CenterCertificateThumbprint="<CertThumbprint>"|Hayır|ATA Center Hizmeti için sertifika parmak izini ayarlar. Bu Sertifika ATA Center ile ATA Gateway arasındaki iletişimin güvenliğini sağlamak için kullanılır. Ayarlanmazsa, yükleme otomatik olarak imzalanan bir sertifika oluşturur.|
|ConsoleIpAddress|ConsoleIpAddress=<ConsoleIPAddress>|Evet|ATA Konsolunun IP adresini ayarlar|
|ConsoleCertificateThumbprint|ConsoleCertificateThumbprint="<CertThumbprint >"|Hayır|ATA Konsolu için sertifika parmak izini ayarlar. Bu Sertifika ATA Konsolu web sitesinin kimliğini doğrulamak için kullanılır. Belirtilmezse yükleme otomatik olarak imzalanan bir sertifika oluşturur|

**Örnekler**: ATA Center’ı varsayılan yükleme yolları ve tek bir IP adresi yüklemek için:

    "Microsoft ATA Center Setup.exe" /quiet --LicenseAccepted NetFrameworkCommandLineArguments="/q" CenterIpAddress=192.168.0.10
    CenterPort=444 ConsoleIpAddress=192.168.0.10

ATA Center’ı varsayılan yükleme yolları, iki IP adresi ve kullanıcı tanımlı sertifika parmak izleri ile yüklemek için:

    "Microsoft ATA Center Setup.exe" /quiet --LicenseAccepted NetFrameworkCommandLineArguments ="/q" CenterIpAddress=192.168.0.10 CenterPort=443 CenterCertificateThumbprint= ‎"1E2079739F624148ABDF502BF9C799FCB8C7212F"
    ConsoleIpAddress=192.168.0.11  ConsoleCertificateThumbprint="G9530253C976BFA9342FD1A716C0EC94207BFD5A"

## <a name="update-the-ata-center"></a>ATA Center’ı güncelleştirme

ATA Center’ı güncelleştirmek için aşağıdaki komutu kullanın:

**Söz dizimi**:

    "Microsoft ATA Center Setup.exe" [/quiet] [/Help] [NetFrameworkCommandLineArguments="/q"]


**Yükleme seçenekleri**:

> [!div class="mx-tableFixed"]
|Ad|Sözdizimi|Sessiz yükleme için zorunlu mu?|Açıklama|
|-------------|----------|---------|---------|
|Quiet|istemci bilgisayarlara|Evet|Kullanıcı arabirimi ve istem göstermeden yükleyiciyi çalıştırır.|
|Yardım|/help|Hayır|Yardım ve hızlı başvuru sağlar. Tüm seçenek ve davranışların bir listesi dahil olmak üzere kurulum komutunun doğru kullanımını gösterir.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Evet|.Net Framework yüklemesi için parametreleri belirtir. .Net Framework sessiz yüklemesini zorunlu kılmak üzere ayarlanmalıdır.|


ATA’yı güncelleştirirken, yükleyici ATA’nın sunucuda zaten yüklü olduğunu ve hiçbir güncelleştirme yükleme seçeneği gerekmediğini otomatik olarak algılar.

**Örnekler**: ATA Center’ı sessizce güncelleştirmek için. Büyük ortamlarda, ATA Center güncelleştirmesinin tamamlanması biraz zaman alabilir. Güncelleştirmenin ilerleme durumunu izlemek için ATA günlüklerini takip edin.

        "Microsoft ATA Center Setup.exe" /quiet NetFrameworkCommandLineArguments="/q"

## <a name="uninstall-the-ata-center-silently"></a>ATA Center’ı sessizce kaldırma

ATA Center’ı sessizce kaldırma işlemini gerçekleştirmek için şu komutu kullanın: **Söz dizimi**:

    Microsoft ATA Center Setup.exe [/quiet] [/Uninstall] [/Help]
     [--DeleteExistingDatabaseData]

**Yükleme seçenekleri**:

> [!div class="mx-tableFixed"]
|Ad|Söz dizimi|Sessiz kaldırma için zorunlu mu?|Açıklama|
|-------------|----------|---------|---------|
|Quiet|istemci bilgisayarlara|Evet|Kullanıcı arabirimi ve istem göstermeden kaldırıcıyı çalıştırır.|
|Kaldır|/uninstall|Evet|Sunucudan ATA Center’ı sessizce kaldırma işlemini çalıştırır.|
|Yardım|/help|Hayır|Yardım ve hızlı başvuru sağlar. Tüm seçenek ve davranışların bir listesi dahil olmak üzere kurulum komutunun doğru kullanımını gösterir.|

**Yükleme parametreleri**:

> [!div class="mx-tableFixed"]
|Ad|Söz dizimi|Sessiz kaldırma için zorunlu mu?|Açıklama|
|-------------|----------|---------|---------|
|DeleteExistingDatabaseData|DeleteExistingDatabaseData|Hayır|Var olan veritabanındaki tüm dosyaları siler.|

**Örnekler**: Var olan tüm veritabanı verilerini kaldırarak sunucudan ATA Center’ı sessizce kaldırmak için:


    "Microsoft ATA Center Setup.exe" /quiet /uninstall --DeleteExistingDatabaseData

## <a name="ata-gateway-silent-installation"></a>ATA Gateway Sessiz Yüklemesi

> [!NOTE]
> System Center Configuration Manager veya diğer yazılım dağıtım sistemi aracılığıyla ATA Lightweight Gateway sessiz dağıtırken, iki dağıtım paketleri oluşturmak için önerilir:</br>-Net Framework 4.6.1 etki alanı denetleyicisini yeniden başlatma da dahil olmak üzere</br>-ATA Gateway. </br>ATA Gateway paketini .net dağıtımını bağımlı hale Framework paket dağıtımı. </br>Alma [.Net Framework 4.6.1 çevrimdışı dağıtım paketi](https://www.microsoft.com/download/details.aspx?id=49982). 


ATA Gateway’i sessizce yüklemek için aşağıdaki komutu kullanın:

**Söz dizimi**:

    Microsoft ATA Gateway Setup.exe [/quiet] [/Help] [NetFrameworkCommandLineArguments ="/q"] 
    [ConsoleAccountName="<AccountName>"] 
    [ConsoleAccountPassword="<AccountPassword>"]

> [!NOTE]
> Etki alanına katılmış bir bilgisayarda çalışıyorsanız ve ATA yönetici kullanıcı adı ve parolanızla oturum açtıysanız bu noktada kimlik bilgilerinizi sağlamanıza gerek yoktur.


**Yükleme seçenekleri**:

> [!div class="mx-tableFixed"]
|Ad|Sözdizimi|Sessiz yükleme için zorunlu mu?|Açıklama|
|-------------|----------|---------|---------|
|Quiet|istemci bilgisayarlara|Evet|Kullanıcı arabirimi ve istem göstermeden yükleyiciyi çalıştırır.|
|Yardım|/help|Hayır|Yardım ve hızlı başvuru sağlar. Tüm seçenek ve davranışların bir listesi dahil olmak üzere kurulum komutunun doğru kullanımını gösterir.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Evet|.Net Framework yüklemesi için parametreleri belirtir. .Net Framework sessiz yüklemesini zorunlu kılmak üzere ayarlanmalıdır.|

**Yükleme parametreleri**:

> [!div class="mx-tableFixed"]
|Ad|Sözdizimi|Sessiz yükleme için zorunlu mu?|Açıklama|
|-------------|----------|---------|---------|
|ConsoleAccountName|ConsoleAccountName="<AccountName>"|Evet|ATA Gateway’i ATA Center’a kaydetmek için kullanılan kullanıcı hesabının (user@domain.com) adını ayarlar.|
|ConsoleAccountPassword|ConsoleAccountPassword="<AccountPassword>"|Evet|ATA Gateway’i ATA Center’a kaydetmek için kullanılan kullanıcı hesabının (user@domain.com) parolasını ayarlar.|

**Örnekler**: ATA Gateway’i sessizce yüklemek için etki alanına katılmış bilgisayarda yönetici kimlik bilgilerinizle oturum açarsanız kimlik bilgisi belirtmeniz gerekmez. Aksi takdirde, belirtilen kimlik bilgilerini kullanarak ATA Center’a kaydedebilirsiniz:

    "Microsoft ATA Gateway Setup.exe" /quiet NetFrameworkCommandLineArguments="/q" 
    ConsoleAccountName="user@contoso.com" ConsoleAccountPassword="userpwd"
    

## <a name="update-the-ata-gateway"></a>ATA Gateway’i güncelleştirme

ATA Gateway’i sessizce güncelleştirmek için aşağıdaki komutu kullanın:

**Söz dizimi**:

    Microsoft ATA Gateway Setup.exe [/quiet] [/Help] [NetFrameworkCommandLineArguments="/q"]


**Yükleme seçenekleri**:

> [!div class="mx-tableFixed"]
|Ad|Sözdizimi|Sessiz yükleme için zorunlu mu?|Açıklama|
|-------------|----------|---------|---------|
|Quiet|istemci bilgisayarlara|Evet|Kullanıcı arabirimi ve istem göstermeden yükleyiciyi çalıştırır.|
|Yardım|/help|Hayır|Yardım ve hızlı başvuru sağlar. Tüm seçenek ve davranışların bir listesi dahil olmak üzere kurulum komutunun doğru kullanımını gösterir.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Evet|.Net Framework yüklemesi için parametreleri belirtir. .Net Framework sessiz yüklemesini zorunlu kılmak üzere ayarlanmalıdır.|


**Örnekler**: ATA Gateway’i sessizce güncelleştirmek için:

        Microsoft ATA Gateway Setup.exe /quiet NetFrameworkCommandLineArguments="/q"

## <a name="uninstall-the-ata-gateway-silently"></a>ATA Gateway’i sessizce kaldırma

ATA Gateway’i sessizce kaldırma işlemini gerçekleştirmek için şu komutu kullanın: **Söz dizimi**:

    Microsoft ATA Gateway Setup.exe [/quiet] [/Uninstall] [/Help]
    
**Yükleme seçenekleri**:

> [!div class="mx-tableFixed"]
|Ad|Söz dizimi|Sessiz kaldırma için zorunlu mu?|Açıklama|
|-------------|----------|---------|---------|
|Quiet|istemci bilgisayarlara|Evet|Kullanıcı arabirimi ve istem göstermeden kaldırıcıyı çalıştırır.|
|Kaldır|/uninstall|Evet|Sunucudan ATA Gateway’i sessizce kaldırma işlemini çalıştırır.|
|Yardım|/help|Hayır|Yardım ve hızlı başvuru sağlar. Tüm seçenek ve davranışların bir listesi dahil olmak üzere kurulum komutunun doğru kullanımını gösterir.|

**Örnekler**: Sunucudan ATA Gateway’i sessizce kaldırmak için:


    Microsoft ATA Gateway Setup.exe /quiet /uninstall
    









## <a name="see-also"></a>Ayrıca bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)