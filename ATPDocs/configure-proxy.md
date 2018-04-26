---
title: Proxy veya güvenlik duvarı ile algılayıcı Azure ATP iletişimi etkinleştirmek için yapılandırma | Microsoft Docs
description: Azure ATP algılayıcılar ve Azure ATP bulut hizmeti arasında iletişim sağlamak için güvenlik duvarı veya proxy ayarlamak açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 9c173d28-a944-491a-92c1-9690eb06b151
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: c52fa6d7cb42605f1809a40926e391bf39fe3eb2
ms.sourcegitcommit: d2d2750bfb0198c8488d538f1773fda6eda5e6f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="configure-endpoint-proxy-and-internet-connectivity-settings-for-your-azure-atp-sensor"></a>Uç nokta proxy ve Azure ATP algılayıcı için Internet bağlantı ayarlarını yapılandır

Her Azure Gelişmiş tehdit Koruması (ATP) algılayıcı başarılı biçimde çalışması için Azure ATP bulut hizmeti için Internet bağlantısı gerektirir. Bazı kuruluşlar etki alanı denetleyicileri doğrudan Internet'e bağlı olmayan, ancak bir web proxy bağlantısı üzerinden bağlanır. Her Azure ATP algılayıcı rapor algılayıcı verileri için Microsoft Windows Internet (WinINet) proxy conifguration kullanın ve Azure ATP hizmetiyle iletişim gerektirir. WinHTTP proxy yapılandırması için kullanırsanız, hala algılayıcı Azure ATP bulut hizmeti arasındaki iletişimi için Windows Internet (WinINet) tarayıcının proxy ayarlarını yapılandırmanız gerekir.


Proxy yapılandırırken, katıştırılmış Azure ATP algılayıcı hizmeti sistem bağlamı kullanarak çalıştığını bilmeniz gerekir **Yerelhizmet** hesabı ve Azure ATP algılayıcı güncelleştirici hizmetini çalıştıran kullanaraksistembağlamında**LocalSystem** hesabı. 

> [!NOTE]
> Ağ topolojinizi saydam proxy ya da WPAD kullanıyorsanız, WinINet, proxy için yapılandırma gerekmez.

## <a name="configure-the-proxy"></a>Proxy ayarlarını yapılandır 

El ile bir kayıt defteri tabanlı statik proxy'si, rapor Tanılama verileri için Azure ATP algılayıcı izin vermek ve bir bilgisayar Internet'e bağlanma izni yok, Azure ATP bulut hizmetiyle iletişim kurmak için kullanılan proxy sunucunuzu yapılandırın.

> [!NOTE]
> Kayıt defteri değişikliklerini yalnızca Yerelhizmet ve LocalSystem uygulanmalıdır.

Statik proxy kayıt defteri aracılığıyla yapılandırılabilir. Yerelhizmet ve localsystem kullanıcı bağlamında kullandığınız proxy yapılandırması kopyalamanız gerekir. Kullanıcı bağlamı proxy ayarlarınızı kopyalamak için:

1.   Bunları değiştirmeden önce kayıt defteri anahtarlarını yedeklemek emin olun.

2. Değeri kayıt defterinde arama `DefaultConnectionSetting` kayıt defteri anahtarı altındaki REG_BINARY olarak `HKCU\Software\Microsoft\Windows\CurrentVersion\InternetSetting\Connections\DefaultConnectionSetting` ve kopyalayın.
 
2.  LocalSystem doğru proxy ayarlarını yoksa (bunlar yapılandırılmamış veya Örnein Current_User ' farklıdır), proxy LocalSystem Örnein Current_User ayarını kopyalayın. Kayıt defteri anahtarı altında `HKU\S-1-5-18\Software\Microsoft\Windows\CurrentVersion\InternetSetting\Connections\DefaultConnectionSetting`.

3.  Örnein Current_user değerinden Yapıştır `DefaultConnectionSetting` REG_BINARY olarak.

4.  Yerelhizmet doğru proxy ayarlarını yoksa proxy Yerelhizmet Örnein Current_User ayarını kopyalayın. Kayıt defteri anahtarı altında `HKU\S-1-5-19\Software\Microsoft\Windows\CurrentVersion\InternetSetting\Connections\DefaultConnectionSetting`.

5.  Örnein Current_User değerinden Yapıştır `DefaultConnectionSetting` REG_BINARY olarak.

> [!NOTE]
> Bu, WinINet Yerelhizmet, LocalSytem bağlam kullanan Windows Hizmetleri dahil olmak üzere tüm uygulamaları etkileyecektir.


## <a name="enable-access-to-azure-atp-service-urls-in-the-proxy-server"></a>Azure ATP hizmeti URL'leri proxy sunucusu erişimi etkinleştir

Bir proxy veya Güvenlik Duvarı varsayılan ve yalnızca belirli etki alanlarında ilerlerken vererek göre tüm trafiği engelleyen veya HTTPS (SSL incelemesi) tarama etkin, aşağıdaki URL'ler beyaz-listelenen bağlantı noktası 443 Azure ATP hizmetiyle iletişim izin verecek biçimde olduğundan emin olun:

|Hizmet konumu|. Atp.Azure.com DNS kaydı|
|----|----|
|BİZE |triprd1wcusw1sensorapi.ATP.Azure.com<br>triprd1wcuswb1sensorapi.ATP.Azure.com<br>triprd1wcuse1sensorapi.ATP.Azure.com|
|Avrupa|triprd1wceun1sensorapi.ATP.Azure.com<br>triprd1wceuw1sensorapi.ATP.Azure.com|
|Asya|triprd1wcasse1sensorapi.ATP.Azure.com|

> [!NOTE]
> SSL denetlemesi Azure ATP arasındaki ağ trafiğini (algılayıcı Azure ATP hizmeti) gerçekleştirirken, SSL denetlemesi karşılıklı denetleme desteklemesi gerekir.


## <a name="see-also"></a>Ayrıca bkz:
- [Olay iletme özelliğini yapılandırma](configure-event-forwarding.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)