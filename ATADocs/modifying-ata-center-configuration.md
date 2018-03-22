---
title: "Advanced Threat Analytics ATA Center yapılandırmasını değiştirme | Microsoft Docs"
description: "ATA Center’ınızın IP adresi, bağlantı noktası, konsol URL’si veya sertifikasını nasıl değiştireceğinizi açıklar."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 93b27f15-f7e5-49bb-870a-d81d09dfe9fc
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 294b9204f9ca6a40a835e5360a7011947e3255b4
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*



# <a name="modifying-the-ata-center-configuration"></a>ATA Center yapılandırmasını değiştirme


İlk dağıtımdan sonra, ATA Center’da değişiklik yaparken dikkatli olmak gerekir. Konsol URL'yi ve sertifikayı güncelleştirirken aşağıdaki yordamları kullanın.

## <a name="the-ata-console-url"></a>ATA Konsolu URL'si

URL aşağıdaki senaryolarda kullanılır:

-   Bu, ATA Center ile iletişim kurmak için ATA Gateway bileşenleri tarafından kullanılan URL'dir.

- ATA Gateway bileşenleri yüklemesi – ATA Gateway yüklenirken, kendini ATA Center’a kaydeder. Bu kayıt işlemi ATA Konsolu’na bağlantı kurularak gerçekleştirilir. ATA Konsolu URL'si için bir FQDN girerseniz, ATA Gateway FQDN'yi ATA Konsolu'nun bağlı IP adresine çözümleyebildiğinden emin olun.

-   Uyarılar – ATA bir SIEM veya e-posta uyarısı gönderdiğinde, kuşkulu etkinliğin bağlantısını içerir. Bağlantının ana bilgisayar bölümü, ATA Konsolu URL ayarıdır.

-   İç sertifika yetkilisi (CA) bir sertifika yüklü değilse, sertifikadaki konu adı için URL ile aynı. Bu, kullanıcıların ATA Konsolu'na bağlanırken uyarı iletisi almalarını önler.

-   ATA Konsolu URL'si için bir FQDN kullanarak, önceki uyarıları kesmeden veya ATA Gateway paketini karşıdan yüklemeyi yeniden ATA Konsolu tarafından kullanılan IP adresi değiştirmenizi sağlar. DNS’yi yeni IP adresiyle güncelleştirmeniz yeterli olur.

1. Kullanmak istediğiniz yeni URL ATA Konsolu IP adresine çözümler emin olun.

2. ATA ayarlarında altında **Center**, yeni URL girin. Bu noktada, ATA Center hizmeti hala özgün URL'yi kullanır. 

 ![ATA yapılandırmasını değiştirme](media/change-center-config.png)

  > [!NOTE]
  > Özel bir IP adresi girdiyseniz tıklatın olamaz **etkinleştirme** IP adresini ATA Center'a yükleyene kadar.
    
3. ATA Gateway eşitleme bekleyin. Şimdi içinden ATA Konsolu'na erişmek iki olası URL'leri sahiptirler. ATA Gateway özgün URL'yi kullanarak bağlanabildiği sürece, yeni bir denemez.

4. Tüm ATA Center yapılandırma sayfasında, güncelleştirilmiş yapılandırmayla eşitlendiğini tıklattıktan sonra **etkinleştirme** yeni URL etkinleştirmeyi düğmesi. Yeni URL etkinleştirdiğinizde, ATA Gateway bileşenlerinin ATA Center erişmek için artık yeni URL kullanır. ATA Center hizmetine bağlandıktan sonra ATA Gateway en yeni yapılandırmayı alır ve ATA Konsolu için yalnızca yeni URL gerekir. 
5. 
 ![Sertifika etkinleştir](media/center-activation.png)

> [!NOTE]
> -   Yeni URL etkinleştirilir ve güncelleştirilmiş yapılandırmayı hiç var ancak bir ATA Gateway çevrimdışıysa, ATA Gateway'de yapılandırma JSON dosyasını el ile güncelleştirin.
> -   Yeni URL etkinleştirdikten sonra yeni bir ATA Gateway dağıtımı yapmanız gerekirse ATA Gateway Kurulum paketini yeniden indirmelisiniz gerekir.


## <a name="the-ata-center-certificate"></a>ATA Center Sertifikası

> [!WARNING]
> - Varolan bir sertifikayı yenileme işlemi desteklenmiyor. Bir sertifikayı yenilemek için yalnızca yeni bir sertifika oluşturma ve yeni sertifikayı kullanmak üzere ATA yapılandırma yoludur.


Bu işlemi yaparak sertifikayı değiştirin:

1. Geçerli sertifikanın süresi dolmadan önce yeni bir sertifika oluşturmak ve ATA Center sunucusunda yüklü olduğundan emin olun. <br></br>Bir iç sertifika yetkilisinden bir sertifika seçin, ancak yeni bir otomatik olarak imzalanan sertifika oluşturmak mümkündür önerilir. Daha fazla bilgi için bkz: [yeni SelfSignedCertificate](https://technet.microsoft.com/itpro/powershell/windows/pkiclient/new-selfsignedcertificate).

2. ATA ayarlarında altında **Center**, bu yeni oluşturulan sertifikayı seçin. Bu noktada, ATA Center hizmeti hala özgün sertifikaya bağlıdır. 

 ![ATA yapılandırmasını değiştirme](media/change-center-config.png)

3. ATA Gateway eşitleme bekleyin. Karşılıklı kimlik doğrulaması için geçerli olan iki olası sertifikaları şimdi sahiptirler. ATA Gateway özgün sertifikayı kullanarak bağlanabildiği sürece, yeni bir denemez.

4. Tüm ATA güncelleştirilmiş gateway'ler eşitlendikten sonra ATA Center'ın bağlı olduğu yeni sertifikayı etkinleştirin. Yeni sertifika etkinleştirdiğinizde, ATA Center hizmeti için yeni sertifika bağlar. ATA Gateway yeni sertifikayı ATA Center ile kimlik doğrulaması için şimdi kullanın. ATA Center hizmetine bağlandıktan sonra ATA Gateway en yeni yapılandırmayı alır ve ATA Center için yalnızca yeni sertifika gerekir. 

> [!NOTE]
> -   Yeni sertifika etkinleştirilir ve güncelleştirilmiş yapılandırmayı hiç var ancak bir ATA Gateway çevrimdışıysa, ATA Gateway'de yapılandırma JSON dosyasını el ile güncelleştirin.
> -   Kullandığınız sertifikaya ATA Gateway bileşenleri tarafından güveniliyor olmalıdır.
> -   Tarayıcı uyarılarını önlemek amacıyla ATA Konsolu adresi eşleşmesi gereken şekilde sertifikayı ATA Konsolu için de kullanılır.
> -   Yeni sertifikayı etkinleştirdikten sonra yeni bir ATA Gateway dağıtımı yapmanız gerekirse, ATA Gateway Kurulum paketini yeniden indirmelisiniz.



 
## <a name="see-also"></a>Ayrıca bkz:
- [ATA Konsolu ile çalışma](working-with-ata-console.md)
- [ATA forumuna bakın!](https://aka.ms/ata-forum)
