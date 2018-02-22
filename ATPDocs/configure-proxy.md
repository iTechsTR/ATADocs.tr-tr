---
title: "Proxy veya güvenlik duvarı ile algılayıcı Azure ATP iletişimi etkinleştirmek için yapılandırma | Microsoft Docs"
description: "Azure ATP algılayıcılar ve Azure ATP bulut hizmeti arasında iletişim sağlamak için güvenlik duvarı veya proxy ayarlamak açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: get-started-article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 9c173d28-a944-491a-92c1-9690eb06b151
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 47fa5ad5d6fb7800c7df4b878d16ec335e2b70e5
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="configure-your-proxy-to-allow-communication-between-azure-atp-sensors-and-the-azure-atp-cloud-service"></a>Azure ATP algılayıcılar ve Azure ATP bulut hizmeti arasında iletişim sağlamak için proxy yapılandırın

Etki alanı bulut hizmetiyle iletişim kurmak denetleyicileriniz için açmanız gerekir: *. güvenlik duvarı veya proxy atp.azure.com bağlantı noktası 443'tür. Yapılandırma (makine hesabı =) makine düzeyinde ve düzeyinde kullanıcı hesabı olması gerekir. Aşağıdaki adımları kullanarak yapılandırmanızı test edebilirsiniz:
 
1.  Onaylayın **geçerli kullanıcı** DC'den aşağıdaki URL'ye göz atarak IE kullanarak işlemci uç noktasını erişimi: https://triprd1wcuse1sensorapi.eastus.cloudapp.azure.com (ABD için) hata 503 almak:

 ![Hizmet kullanılamıyor](/media/service-unavailable.png)
 
2.  Bir hata 503 alamazsanız proxy yapılandırmasını gözden geçirin ve yeniden deneyin.

3.  Proxy yapılandırması için çalışıyorsa **Örnein CURRENT_USER** (diğer bir deyişle, 503 hatası gördüğünüz) ardından WinINet proxy ayarları için etkin olup olmadığını kontrol edin **LOCAL_SYSTEM** (algılayıcı güncelleştirici tarafından kullanılan hesap yükseltilmiş komut isteminde aşağıdaki komutu çalıştırarak hizmeti):
 
    reg compare "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\Connections" "HKU\S-1-5-18\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections" /v DefaultConnectionSettings

Hata alırsanız "hata: Sistem belirtilen kayıt defteri anahtarını veya değerini bulamadı." Bu proxy üzerinde ayarlamak anlamına gelir **LOCAL_SYSTEM** düzeyi
 
 ![Proxy yerel sistem hatası](/media/proxy-local-system-error.png)

Sonuç ise "sonucu ile karşılaştırıldığında: farklı" Bu proxy için ayarlandığı anlamına gelir **LOCAL_SYSTEM** , ancak aynı **Örnein CURRENT_USER**:
 
  ![Karşılaştırılan proxy sonuç](/media/proxy-result-compared.png)

5.  Varsa **LOCAL_SYSTEM** doğru proxy ayarlarını yok (yapılandırılmış değil veya farklı **Örnein CURRENT_USER**), proxy gelen ayarını kopyalamak gerekebilir sonra **CURRENT_ Kullanıcı** için **LOCAL_SYSTEM**. Değiştirmeden önce bu kayıt defteri anahtarını yedeklemek emin olun:

 Geçerli kullanıcı anahtarı: HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\Connections\DefaultConnectionSettings "Yerel Sistem anahtarı: HKU\S-1-5-18\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections\ DefaultConnectionSettings"

 
6.  4 ve 5. adımları tamamlamak**Local_Service** hesabı (aynı olan **Local_System** S-1-5-19 S-1-5-18 yerine olmalıdır, ancak.



## <a name="see-also"></a>Ayrıca bkz:
- [Olay iletme özelliğini yapılandırma](configure-event-forwarding.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)