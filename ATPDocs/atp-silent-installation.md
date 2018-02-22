---
title: "Yükleme Azure Gelişmiş tehdit koruması sessizce | Microsoft Docs"
description: "Bu Azure ATP gerek kalmadan sessiz yükleme açıklar."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2017
ms.topic: get-started-article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 24eca4c6-c949-42ea-97b9-41ef0fb611f1
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 862420fb6914dbf9ee57c36bc21103cc7dddf7af
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*


# <a name="azure-atp-silent-installation"></a>Azure ATP sessiz yükleme
Bu makalede Azure ATP sessizce yüklemek için yönergeler sağlar.

## <a name="prerequisites"></a>Önkoşullar

Azure ATP Microsoft .NET Framework 4.7 yüklenmesini gerektirir. 

Azure ATP yüklediğinizde, .net Framework 4.7 otomatik olarak Azure ATP dağıtımının bir parçası olarak yüklenir.

> [!Note] 
> .Net framework 4.7 yüklenmesi sunucunun yeniden başlatılması gerekebilir. Azure ATP algılayıcı etki alanı denetleyicilerinde yüklerken, bu etki alanı denetleyicileri için bir bakım penceresi zamanlamayı dikkate alın.
Azure ATP sessiz yükleme yöntemini kullanırken, yükleyici yükleme işleminin sonunda sunucuyu (gerekirse) otomatik olarak yeniden yapılandırılır. Bir Windows Installer hatası nedeniyle *norestart* bayrağı güvenilir sunucu yok yeniden, bu nedenle yalnızca sessiz yüklemeyi bir bakım penceresi sırasında çalıştırıldığından emin olun emin olmak için kullanılamaz.

Dağıtımın ilerleme durumunu izlemek için izleme bulunan Azure ATP yükleyici günlüklerini **%AppData%\Local\Temp**.



## <a name="azure-atp-sensor-silent-installation"></a>Azure ATP algılayıcı sessiz yükleme

> [!NOTE]
> System Center Configuration Manager veya diğer yazılım dağıtım sistemi aracılığıyla Azure ATP algılayıcı sessizce dağıtırken, iki dağıtım paketleri oluşturmak için önerilir:</br>-Net Framework 4.7 etki alanı denetleyicisini yeniden başlatma da dahil olmak üzere</br>-Azure ATP algılayıcı. </br>Azure ATP algılayıcı paketi .net dağıtımını bağımlı hale Framework paket dağıtımı. </br>Alma [.Net Framework 4.7 çevrimdışı dağıtım paketi](https://www.microsoft.com/download/details.aspx?id=49982). 


Azure ATP algılayıcı sessizce yüklemek için aşağıdaki komutu kullanın:

**Söz dizimi**:

    Azure ATP sensor Setup.exe [/AccessKey=<Access Key>] [/quiet] [/Help] [NetFrameworkCommandLineArguments ="/q"] 
   

> [!NOTE]
> Erişim anahtarı altında çalışma Portal'dan kopyalayın **yapılandırma** ve ardından **algılayıcı**.


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
|AccessKey|AccessKey="**"|Evet|Azure ATP algılayıcı Azure ATP çalışma alanıyla kaydetmek için kullanılan erişim tuşu ayarlar.|

**Örnekler**: böylece yüklemesinin bir parçası kimlik bilgilerini belirtmeniz gerekmez Azure ATP algılayıcı sessizce yüklemek için günlük etki alanına bilgisayar Azure ATP yönetici kimlik bilgilerinizle alanına katıldı. Aksi halde, belirtilen kimlik bilgilerini kullanarak Azure ATP bulut hizmetiyle kaydedin:

    "Azure ATP sensor Setup.exe" /quiet NetFrameworkCommandLineArguments="/q" 
    AccessKey="3WlO0uKW7lY6Lk0+dfkfkJQ0qZV6aSq5WxLf71+fuBhggCl/BMs9JxfAwi7oy9vYGviazUS1EPpzte7z8s4grw==" 
    

## <a name="update-the-azure-atp-sensor"></a>Güncelleştirme Azure ATP algılayıcısı

Azure ATP algılayıcı'ı sessizce güncelleştirmek için aşağıdaki komutu kullanın:

**Söz dizimi**:

    Azure ATP  sensor Setup.exe [/quiet] [/Help] [NetFrameworkCommandLineArguments="/q"]


**Yükleme seçenekleri**:

> [!div class="mx-tableFixed"]
|Ad|Sözdizimi|Sessiz yükleme için zorunlu mu?|Description|
|-------------|----------|---------|---------|
|Quiet|istemci bilgisayarlara|Evet|Kullanıcı arabirimi ve istem göstermeden yükleyiciyi çalıştırır.|
|Yardım|/help|Hayır|Yardım ve hızlı başvuru sağlar. Tüm seçenek ve davranışların bir listesi dahil olmak üzere kurulum komutunun doğru kullanımını gösterir.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Evet|.Net Framework yüklemesi için parametreleri belirtir. .Net Framework sessiz yüklemesini zorunlu kılmak üzere ayarlanmalıdır.|


**Örnekler**: Azure ATP algılayıcı sessizce güncelleştirmek için:

        Azure ATP sensor Setup.exe /quiet NetFrameworkCommandLineArguments="/q"

## <a name="uninstall-the-azure-atp-sensor-silently"></a>Azure ATP algılayıcı sessizce kaldırma

Sessiz kaldırma Azure ATP algılayıcı işlemini gerçekleştirmek için aşağıdaki komutu kullanın: **sözdizimi**:

    Azure ATP sensor Setup.exe [/quiet] [/Uninstall] [/Help]
    
**Yükleme seçenekleri**:

> [!div class="mx-tableFixed"]
|Ad|Sözdizimi|Sessiz kaldırma için zorunlu mu?|Description|
|-------------|----------|---------|---------|
|Quiet|istemci bilgisayarlara|Evet|Kullanıcı arabirimi ve istem göstermeden kaldırıcıyı çalıştırır.|
|Kaldır|/uninstall|Evet|Sessiz kaldırma Azure ATP algılayıcı sunucudan çalıştırır.|
|Yardım|/help|Hayır|Yardım ve hızlı başvuru sağlar. Tüm seçenek ve davranışların bir listesi dahil olmak üzere kurulum komutunun doğru kullanımını gösterir.|

**Örnekler**: Azure ATP algılayıcı sunucudan sessizce kaldırmak için:


    Azure ATP sensor Setup.exe /quiet /uninstall
    



## <a name="see-also"></a>Ayrıca bkz:

- [Olay iletme özelliğini yapılandırma](configure-event-forwarding.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)