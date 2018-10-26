---
title: Advanced Threat Analytics ATA Center yapılandırmasını değiştirme | Microsoft Docs
description: ATA Center’ınızın IP adresi, bağlantı noktası, konsol URL’si veya sertifikasını nasıl değiştireceğinizi açıklar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: b1b8b1fb9c1bf5a11c8a05daf3567f4a25c35c3f
ms.sourcegitcommit: 2916d6f8d6e6f754d7fb8a5d31b255a46aa35ecd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50132699"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="modifying-the-ata-center-configuration"></a>ATA Center yapılandırmasını değiştirme


İlk dağıtımdan sonra, ATA Center’da değişiklik yaparken dikkatli olmak gerekir. Konsol URL'si ve sertifikasını güncelleştirirken aşağıdaki yordamları kullanın.

## <a name="the-ata-console-url"></a>ATA Konsolu URL'si

URL aşağıdaki senaryolarda kullanılır:

-   Bu, ATA Gateway'ler tarafından ATA Center ile iletişim kurmak için kullanılan URL'dir.

- ATA Gateway bileşenleri yüklemesi – ATA Gateway yüklenirken, kendini ATA Center’a kaydeder. Bu kayıt işlemi ATA Konsolu’na bağlantı kurularak gerçekleştirilir. ATA Konsolu URL'si için bir FQDN girerseniz, ATA Gateway FQDN'yi ATA Konsolu'nda bağlı IP adresine çözümleyebileceğinden emin olun.

-   Uyarılar – ATA bir SIEM veya e-posta uyarısı gönderdiğinde, kuşkulu etkinliğin bağlantısını içerir. Bağlantının ana bilgisayar bölümü, ATA Konsolu URL ayarıdır.

-   Kendi iç sertifika yetkilisi (CA) bir sertifika yüklediyseniz, sertifika konu adında URL'sine eşleştirin. Bu, kullanıcıların ATA Konsolu'na bağlanırken uyarı iletisi almalarını önler.

-   ATA Konsolu URL'si için bir FQDN kullanmak, önceki uyarıları kesmeden veya ATA Gateway paketini karşıdan yüklemeyi yeniden ATA Konsolu tarafından kullanılan IP adresini değiştirebilmenizi sağlar. DNS’yi yeni IP adresiyle güncelleştirmeniz yeterli olur.

1. Kullanmak istediğiniz yeni URL ATA Konsolu'nun IP adresine çözümlenen emin olun.

2. ATA ayarlarında altında **Merkezi**, yeni URL'yi girin. Bu noktada, ATA Center hizmeti hala özgün URL'yi kullanır. 

 ![ATA yapılandırmasını değiştirme](media/change-center-config.png)

  > [!NOTE]
  > Özel bir IP adresi girdiyseniz tıklayamazsınız **etkinleştirme** IP adresini ATA Center'a yükleyene kadar.
    
3. ATA Gateway eşitleme bekleyin. Şimdi, ATA konsoluna erişmek iki olası URL sahiptirler. ATA Gateway özgün URL'yi kullanarak bağlantı kurabilir sürece, yeni bir tane denemez.

4. Merkezi yapılandırma sayfasında, güncelleştirilmiş yapılandırma ile eşitlenen tüm ATA Gateway'ler tıkladıktan sonra **etkinleştirme** yeni URL'sini etkinleştirmek için düğme. Yeni URL etkinleştirdiğinizde, ATA Gateway bileşenlerinin ATA Center erişmek için artık yeni URL'yi kullanır. ATA Center hizmetine bağlandıktan sonra ATA Gateway en yeni yapılandırmayı çeker ve ATA Konsolu için yalnızca yeni URL'ye sahiptir. 

5. 
 ![Sertifikayı etkinleştirin](media/center-activation.png)

> [!NOTE]
> -   Yeni URL etkinleştirildi ve güncelleştirilmiş yapılandırmayı hiç var ancak bir ATA Gateway çevrimdışıysa, ATA Gateway'de yapılandırma JSON dosyasını el ile güncelleştirin.
> -   Yeni URL etkinleştirdikten sonra yeni bir ATA Gateway dağıtımı yapmanız gerekirse, ATA Gateway Kurulum paketini yeniden indirmeniz gerekir.


## <a name="the-ata-center-certificate"></a>ATA Center Sertifikası

> [!WARNING]
> - Mevcut bir sertifikayı yenileme işlemi desteklenmiyor. Bir sertifikayı yenilemek için tek yolu, yeni bir sertifika oluşturmak ve yeni sertifikayı kullanmak için Ata'yı yapılandırma ' dir.


Bu işlemi yaparak sertifikayı değiştirin:

1. Geçerli bir sertifikanın süresi dolmadan önce yeni bir sertifika oluşturmalı ve ATA Center sunucusunda yüklü olduğundan emin olun. <br></br>Bir iç sertifika yetkilisinden bir sertifika seçmeniz, ancak yeni bir otomatik olarak imzalanan sertifika oluşturmak mümkündür önerilir. Daha fazla bilgi için [New-SelfSignedCertificate](https://technet.microsoft.com/itpro/powershell/windows/pkiclient/new-selfsignedcertificate).

2. ATA ayarlarında altında **Merkezi**, bu yeni oluşturulan sertifikayı seçin. Bu noktada, ATA Center hizmeti hala özgün sertifikaya bağlıdır. 

 ![ATA yapılandırmasını değiştirme](media/change-center-config.png)

3. ATA Gateway eşitleme bekleyin. Artık karşılıklı kimlik doğrulaması için geçerli olan iki olası sertifikaları sahiptirler. ATA Gateway özgün sertifikayı kullanarak bağlantı kurabilir sürece, yeni bir tane denemez.

4. Tüm ATA güncelleştirilmiş yapılandırmayla Gateway'ler eşitlendikten sonra ATA Center hizmetine bağlı olduğu yeni sertifikayı etkinleştirin. Yeni sertifika etkinleştirdiğinizde, ATA Center hizmeti için yeni sertifika bağlar. ATA Gateway'ler artık ATA Center'a kimlik doğrulaması için yeni sertifikayı kullanın. ATA Center hizmetine bağlandıktan sonra ATA Gateway en yeni yapılandırmayı çeker ve yalnızca yeni sertifikayı ATA Center için gerekir. 

> [!NOTE]
> -   Yeni sertifikayı etkin ve güncelleştirilmiş yapılandırmayı hiç aldı ancak bir ATA Gateway çevrimdışıysa, ATA Gateway'de yapılandırma JSON dosyasını el ile güncelleştirin.
> -   Kullandığınız sertifikaya ATA Gateway bileşenleri tarafından güveniliyor olmalıdır.
> -   Bu tarayıcı uyarılarını önlemek için ATA Konsolu adresiyle de eşleşmesi gerekir sertifika ATA Konsolu için de kullanılır.
> -   Yeni sertifikayı etkinleştirdikten sonra yeni bir ATA Gateway dağıtımı yapmanız gerekirse, ATA Gateway Kurulum paketini yeniden indirmelisiniz.



 
## <a name="see-also"></a>Ayrıca Bkz.
- [ATA Konsolu ile çalışma](working-with-ata-console.md)
- [ATA forumuna bakın!](https://aka.ms/ata-forum)
