---
title: Yükleme Azure Gelişmiş tehdit koruması sessizce | Microsoft Docs
description: Bu, Azure ATP sessizce yüklemek nasıl açıklar.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/7/2017
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 24eca4c6-c949-42ea-97b9-41ef0fb611f1
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 363400531fe2b4e2634fa80ec1f65ad80923606f
ms.sourcegitcommit: 7f3ded32af35a433d4b407009f87cfa6099f8edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44125796"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="azure-atp-switches-and-silent-installation"></a>Azure ATP anahtarları ve sessiz yükleme
Bu makalede, rehberlik ve Azure ATP anahtarları ve sessiz yükleme için yönergeler sağlar.

## <a name="prerequisites"></a>Önkoşullar

Azure ATP Microsoft .NET Framework 4.7 yüklemesi gerektirir. 

Azure ATP yükleme sırasında .net Framework 4.7 otomatik olarak olan Azure ATP dağıtımının bir parçası olarak yüklenir.

> [!IMPORTANT] 
> .Net en son sürümüne sahip olduğunuzdan emin olun Framework yüklü. .Net önceki bir sürümünü yüklediyseniz, Azure ATP sessiz yükleme bir döngüde takılı kalarak ve yüklenemedi. 

> [!NOTE] 
> .Net Framework 4.7 yüklemesi için sunucunun yeniden başlatılması gerekebilir. Azure ATP algılayıcısını etki alanı denetleyicilerinize yüklerken, etki alanı denetleyicileri için bir bakım penceresi zamanlamayı düşünün.
Azure ATP sessiz yüklemeyi kullanarak, yükleyici otomatik olarak (gerekirse) yükleme sonunda sunucuyu yeniden yapılandırılır. Sessiz yüklemeyi sadece bir bakım penceresi sırasında çalıştırdığınızdan emin olun. Bir Windows Installer hatası nedeniyle *norestart* bayrağı güvenilir bir şekilde sunucuyu yeniden başlatma emin olmak için kullanılamaz.

Bulunan Azure ATP yükleyici günlükleri, dağıtım ilerlemesini izlemek için izleme **%AppData%\Local\Temp**.



## <a name="azure-atp-sensor-silent-installation"></a>Azure ATP algılayıcısı sessiz yükleme

> [!NOTE]
> System Center Configuration Manager veya başka bir yazılım dağıtım sistem aracılığıyla Azure ATP algılayıcısını sessizce dağıtırken, iki dağıtım paketi oluşturmak için önerilir:</br>-Net Framework 4.7 etki alanı denetleyicisini yeniden başlatma da dahil olmak üzere</br>-Azure ATP algılayıcısını. </br>Azure ATP algılayıcı paketini, .net dağıtımı bağımlı hale Framework paketi dağıtımı. </br>Alma [.Net Framework 4.7 çevrimdışı dağıtım paketi](https://www.microsoft.com/download/details.aspx?id=49982). 


Yükleyin Azure ATP algılayıcısını tamamen sessiz gerçekleştirmek için aşağıdaki komutu kullanın:


**Söz dizimi**:

    Azure ATP sensor Setup.exe /AccessKey=<Access Key> /quiet NetFrameworkCommandLineArguments ="/q" 
   

> [!NOTE]
> Altında çalışma alanı portalından erişim tuşunu kopyalamak **yapılandırma** ardından **algılayıcı**.


**Yükleme seçenekleri**:

> [!div class="mx-tableFixed"]
|Ad|Sözdizimi|Sessiz yükleme için zorunlu mu?|Description|
|-------------|----------|---------|---------|
|Quiet|istemci bilgisayarlara|Evet|Kullanıcı arabirimi ve istem göstermeden yükleyiciyi çalıştırır.|
|Yardım|/help|Hayır|Yardım ve hızlı başvuru sağlar. Tüm seçenek ve davranışların bir listesi dahil olmak üzere kurulum komutunun doğru kullanımını gösterir.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Evet|.Net Framework yüklemesi için parametreleri belirtir. .Net Framework sessiz yüklemesini zorunlu kılmak üzere ayarlanmalıdır.|

**Yükleme parametreleri**:

> [!div class="mx-tableFixed"]
|Ad|Sözdizimi|Sessiz yükleme için zorunlu mu?|Description|
|-------------|----------|---------|---------|
|accessKey|AccessKey = "\*\*"|Evet|Azure ATP algılayıcısını Azure ATP çalışma alanı ile kaydetmek için kullanılan erişim anahtarı ayarlar.|

**Örnekler**: yüklemesinin bir parçası kimlik bilgilerini belirtmek gerekmez, Azure ATP algılayıcısını sessizce yüklemek için etki alanında oturum bilgisayar yönetici kimlik bilgilerinizle Azure ATP alanına katıldı. Aksi takdirde, belirtilen kimlik bilgilerini kullanarak Azure ATP bulut hizmetiyle kaydedin:

    "Azure ATP sensor Setup.exe" /quiet NetFrameworkCommandLineArguments="/q" 
    AccessKey="3WlO0uKW7lY6Lk0+dfkfkJQ0qZV6aSq5WxLf71+fuBhggCl/BMs9JxfAwi7oy9vYGviazUS1EPpzte7z8s4grw==" 
    

## <a name="update-the-azure-atp-sensor"></a>Azure ATP algılayıcısını güncelleştir

Azure ATP algılayıcısını'ı sessizce güncelleştirmek için aşağıdaki komutu kullanın:

**Söz dizimi**:

    Azure ATP sensor Setup.exe [/quiet] [/Help] [NetFrameworkCommandLineArguments="/q"]


**Yükleme seçenekleri**:

> [!div class="mx-tableFixed"]
|Ad|Sözdizimi|Sessiz yükleme için zorunlu mu?|Description|
|-------------|----------|---------|---------|
|Quiet|istemci bilgisayarlara|Evet|Kullanıcı arabirimi ve istem göstermeden yükleyiciyi çalıştırır.|
|Yardım|/help|Hayır|Yardım ve hızlı başvuru sağlar. Tüm seçenek ve davranışların bir listesi dahil olmak üzere kurulum komutunun doğru kullanımını gösterir.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Evet|.Net Framework yüklemesi için parametreleri belirtir. .Net Framework sessiz yüklemesini zorunlu kılmak üzere ayarlanmalıdır.|


**Örnekler**: Azure ATP algılayıcısını'ı sessizce güncelleştirmek için:

    Azure ATP sensor Setup.exe /quiet NetFrameworkCommandLineArguments="/q"

## <a name="uninstall-the-azure-atp-sensor-silently"></a>Azure ATP algılayıcısını sessizce kaldırma

Sessizce kaldırma işlemini Azure ATP algılayıcısını gerçekleştirmek için aşağıdaki komutu kullanın: **söz dizimi**:

    Azure ATP sensor Setup.exe [/quiet] [/Uninstall] [/Help]
    
**Yükleme seçenekleri**:

> [!div class="mx-tableFixed"]
|Ad|Sözdizimi|Sessiz kaldırma için zorunlu mu?|Description|
|-------------|----------|---------|---------|
|Quiet|istemci bilgisayarlara|Evet|Kullanıcı arabirimi ve istem göstermeden kaldırıcıyı çalıştırır.|
|Kaldır|/uninstall|Evet|Azure ATP algılayıcısını sessiz kaldırma işlemi, sunucudan çalıştırır.|
|Yardım|/help|Hayır|Yardım ve hızlı başvuru sağlar. Tüm seçenek ve davranışların bir listesi dahil olmak üzere kurulum komutunun doğru kullanımını gösterir.|

**Örnekler**: Azure ATP algılayıcısını sunucudan sessizce kaldırmak için:


    Azure ATP sensor Setup.exe /quiet /uninstall
    



## <a name="see-also"></a>Ayrıca Bkz.

- [Olay iletme'yi yapılandırma](configure-event-forwarding.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
