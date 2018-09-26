---
title: Ara sunucunuzda veya güvenlik duvarı ile algılayıcı Azure ATP iletişimi etkinleştirmek için yapılandırma | Microsoft Docs
description: Azure ATP bulut hizmeti ve Azure ATP algılayıcı arasında iletişime izin vermek için güvenlik duvarınızın veya Ara sunucu ayarlama işlemi açıklanmaktadır
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 9/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 9c173d28-a944-491a-92c1-9690eb06b151
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: fa6bb10b029649a158d7733b10fec51c52acb9f7
ms.sourcegitcommit: 8e80f59409c65e7d8d60ec7de8b96b621795699a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47168561"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="configure-endpoint-proxy-and-internet-connectivity-settings-for-your-azure-atp-sensor"></a>Uç nokta proxy ve Internet bağlantısı ayarlarını, Azure ATP algılayıcısını yapılandırma

Her Azure Gelişmiş tehdit Koruması (ATP) algılayıcı başarılı biçimde çalışması için Azure ATP bulut hizmeti için Internet bağlantısı olmasını gerektirir. Bazı kuruluşlarda, etki alanı denetleyicileri doğrudan Internet'e bağlı olmayan, ancak bir web proxy bağlantısı üzerinden. Her Azure ATP algılayıcısını sensör verilerini raporlamaya Microsoft Windows Internet (WinINet) Ara sunucu yapılandırmasını kullanır ve Azure ATP hizmeti ile iletişim gerektirir. WinHTTP proxy yapılandırması için kullanıyorsanız, hala algılayıcı Azure ATP bulut hizmeti arasında iletişim için Windows Internet (WinINet) Tarayıcı proxy ayarlarını yapılandırmanız gerekir.


Proxy yapılandırırken, katıştırılmış Azure ATP algılayıcı hizmetinin sistemi bağlamını kullanarak içinde çalıştığını bilmeniz gerekir **LocalService** kullanaraksistembağlamındahesabıveAzureATPalgılayıcısıUpdaterhizmetiniçalıştıran**LocalSystem** hesabı. 

> [!NOTE]
> Ağ topolojinizi saydam proxy ya da WPAD kullanıyorsanız, WinINET proxy için yapılandırma gerekmez.

## <a name="configure-the-proxy"></a>Proxy yapılandırma 

Azure ATP algılayıcısını tanılama verilerini raporlamaya izin vermek ve bir bilgisayar Internet'e bağlanmasına izin verilmez, Azure ATP bulut hizmetiyle iletişim kurmak için bir kayıt defteri tabanlı statik proxy kullanarak el ile proxy sunucunuzu yapılandırın.

> [!NOTE]
> Kayıt defteri değişiklikleri yalnızca LocalService ve LocalSystem uygulanmalıdır.

Statik proxy kayıt defteri aracılığıyla yapılandırılabilir. Yerelhizmet ve localsystem kullanıcı bağlamında, kullandığınız proxy yapılandırmasını kopyalamanız gerekir. Kullanıcı bağlamı proxy ayarlarınızı kopyalamak için:

1.   Bunları değiştirmeden önce kayıt defteri anahtarlarını yedeklemek emin olun.

2. Değerini kayıt defterine arama `DefaultConnectionSettings` REG_BINARY kayıt defteri anahtarı altında olarak `HKCU\Software\Microsoft\Windows\CurrentVersion\InternetSetting\Connections\DefaultConnectionSettings` ve kopyalayın.
 
2.  LocalSystem doğru ara sunucu ayarları yoksa (bunlar yapılandırılmamış veya Örnein Current_User ' farklıdır), ardından proxy Örnein Current_User LocalSystem ayarı kopyalayın. Kayıt defteri anahtarı altında `HKU\S-1-5-18\Software\Microsoft\Windows\CurrentVersion\InternetSetting\Connections\DefaultConnectionSettings`.

3.  Örnein Current_user değerini yapıştırın `DefaultConnectionSettings` REG_BINARY olarak.

4.  Doğru ara sunucu ayarları LocalService sahip değilse, proxy için LocalService Örnein Current_User ayarı'ni kopyalayın. Kayıt defteri anahtarı altında `HKU\S-1-5-19\Software\Microsoft\Windows\CurrentVersion\InternetSetting\Connections\DefaultConnectionSettings`.

5.  Örnein Current_User değerini yapıştırın `DefaultConnectionSettings` REG_BINARY olarak.

> [!NOTE]
> Bu WinINet LocalService, LocalSytem bağlamı kullanan Windows Hizmetleri dahil olmak üzere tüm uygulamaları etkiler.


## <a name="enable-access-to-azure-atp-service-urls-in-the-proxy-server"></a>Azure ATP hizmeti URL'leri proxy sunucusu erişimi etkinleştirme

Bir proxy veya Güvenlik Duvarı varsayılan ve yalnızca belirli etki alanları aracılığıyla izin vererek tüm trafiği engelleyen veya HTTPS (SSL incelemesi) tarama etkinleştirildi, beyaz-listelenen bağlantı noktası 443'deki Azure ATP hizmeti ile iletişimi izin vermek için aşağıdaki URL'ler olduğundan emin olun:

|Hizmet konumu|. Atp.Azure.com DNS kaydı|
|----|----|
|ABD |triprd1wcusw1sensorapi.ATP.Azure.com<br>triprd1wcuswb1sensorapi.ATP.Azure.com<br>triprd1wcuse1sensorapi.ATP.Azure.com|
|Avrupa|triprd1wceun1sensorapi.ATP.Azure.com<br>triprd1wceuw1sensorapi.ATP.Azure.com|
|Asya|triprd1wcasse1sensorapi.ATP.Azure.com|


Ayrıca, bir kural için aşağıdaki DNS kayıtlarını oluşturma tarafından oluşturulan güvenlik duvarı veya proxy kuralları belirli bir çalışma alanı için sağlamlaştırmak:
- \<uygulamanızın çalışma alanı-adı >. atp.azure.com – konsol bağlantısı için. Örneğin, "Contoso-corp.atp.azure.com"
- \<uygulamanızın çalışma alanı-adı > sensorapi.atp.azure.com – algılayıcılar bağlantı. Örneğin, "contoso-corpsensorapi.atp.azure.com"

 
> [!NOTE]
> Azure ATP arasındaki ağ trafiğini (algılayıcı Azure ATP hizmeti) SSL denetimi gerçekleştirirken, SSL denetimi karşılıklı İnceleme desteklemesi gerekir.


## <a name="see-also"></a>Ayrıca Bkz.
- [Olay iletme'yi yapılandırma](configure-event-forwarding.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)