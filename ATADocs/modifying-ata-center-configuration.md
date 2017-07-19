---
title: "Advanced Threat Analytics ATA Center yapılandırmasını değiştirme | Microsoft Docs"
description: "ATA Center’ınızın IP adresi, bağlantı noktası, konsol URL’si veya sertifikasını nasıl değiştireceğinizi açıklar."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 93b27f15-f7e5-49bb-870a-d81d09dfe9fc
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 1e9fa2d104c52087746e7c03fea27e3cb596adf0
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="modifying-the-ata-center-configuration"></a>ATA Center yapılandırmasını değiştirme


İlk dağıtımdan sonra, ATA Center’da değişiklik yaparken dikkatli olmak gerekir. IP adresi, bağlantı noktası, konsol URL’si ve sertifikasını güncelleştirirken aşağıdaki yordamları kullanın.

## <a name="the-ata-center-ip-address"></a>ATA Center IP adresi

ATA Gateway bileşenleri bağlanmaları gereken ATA Center’ın IP adresini yerel olarak depolar. Düzenli aralıklarla ATA Center’a bağlanır ve yapılandırma değişikliklerini alırlar. ATA Gateway bileşenlerinin ATA Center’a bağlanma şeklinde yapılacak değişiklikler iki aşamada yapılır.

-   Birinci aşama – IP adresini ve bağlantı noktasını ATA Center hizmeti tarafından kullanılmasını istediğiniz gibi güncelleştirin. Bu noktada ATA Center özgün IP adresinde dinlemeye devam eder ve ATA Gateway’in yapılandırmasını bir sonraki eşitleyişinde ATA Center için iki IP adresi olur. ATA Gateway özgün (ilk) IP adresini kullanarak bağlanabildiği sürece, yeni IP adresini ve bağlantı noktasını denemez.

-   İkinci aşama – Tüm ATA Gateway bileşenleri güncelleştirilmiş yapılandırmayla eşitlendiğinde, ATA Center’ın dinlemesi için yeni IP adresini ve bağlantı noktasını etkinleştirin. Yeni IP adresini etkinleştirdiğinizde, ATA Center hizmeti yeni IP adresine bağlanır. ATA Gateway bileşenleri özgün adrese bağlanamaz ve şimdi ATA Center için var olan ikinci (yeni) IP adresiyle bağlanmayı dener. Yeni IP adresiyle ATA Center’a bağlandıktan sonra, ATA Gateway en yeni yapılandırmayı alır ve ATA Center için tek bir IP adresine sahip olur. (İşlemi yeniden başlatmadığınız sürece bu durum geçerli olur.)

> [!NOTE]
> -   İlk aşamada ATA Gateway çevrimdışıysa ve güncelleştirilmiş yapılandırmayı hiç almadıysa, ATA Gateway’de yapılandırma JSON dosyasını el ile güncelleştirmeniz gerekir.
> -   Yeni IP adresi ATA Center sunucusuna yüklendiyse, değişikliği yaparken bu adresi IP adresleri listesinden seçebilirsiniz. Öte yandan, herhangi bir nedenle IP adresini ATA Center sunucusuna yükleyemediyseniz, özel IP adresini seçebilir ve bu adresi el ile ekleyebilirsiniz. Yeni IP adresini etkinleştirebilmeniz için bu IP adresinin sunucuya yüklenmesi gerekir.
> -   Yeni IP adresini etkinleştirdikten sonra yeni bir ATA Gateway dağıtımı yapmanız gerekirse, ATA Gateway Kurulum paketini yeniden indirmelisiniz.

## <a name="the-console-url"></a>Konsol URL’si

URL aşağıdaki senaryolarda kullanılır:

-   ATA Gateway bileşenleri yüklemesi – ATA Gateway yüklenirken, kendini ATA Center’a kaydeder. Bu kayıt işlemi ATA Konsolu’na bağlantı kurularak gerçekleştirilir. ATA Konsolu URL’si için bir FQDN girerseniz, ATA Gateway’in FQDN’yi ATA Konsolu’nun bağlı olduğu IP adresine çözümleyebileceğinden emin olmanız gerekir.

-   Uyarılar – ATA bir SIEM veya e-posta uyarısı gönderdiğinde, kuşkulu etkinliğin bağlantısını içerir. Bağlantının ana bilgisayar bölümü, ATA Konsolu URL ayarıdır.

-   İç Sertifika Yetkilinizden (CA) bir sertifika yüklediyseniz, kullanıcıların ATA Konsolu’na bağlanırken uyarı iletisi almalarını önlemek için büyük olasılıkla URL’yi sertifikanın konu adıyla eşleştirmek istersiniz.

-   ATA Konsolu URL’si olarak bir FQDN kullanmak, geçmişte gönderilmiş olan uyarıları kesmeden veya ATA Gateway paketini yeniden indirmek zorunda kalmadan, ATA Konsolu için kullanılan IP adresini değiştirebilmenizi sağlar. DNS’yi yeni IP adresiyle güncelleştirmeniz yeterli olur.

> [!NOTE]
> ATA Konsolu URL’sini değiştirdikten sonra, yeni ATA Gateway bileşenlerini yüklemeden ATA Gateway Kurulum paketini indirmelisiniz.

## <a name="the-ata-center-certificate"></a>ATA Center Sertifikası
Sertifikalarınızın süresi sona ermek üzereyse ve ATA Center sunucusundaki yerel bilgisayar deposuna yeni sertifika yüklendikten sonra yenilenmesi veya değiştirilmesi gerekiyorsa, şu iki aşamalı işlemi yaparak sertifikayı değiştirin:

-   Birinci aşama – ATA Center hizmetinin kullanmasını istediğiniz sertifikayı güncelleştirin. Bu noktada, ATA Center hizmeti hala özgün sertifikaya bağlıdır. ATA Gateway bileşenleri yapılandırmalarını eşitlediğinde, karşılıklı kimlik doğrulaması için geçerli olan iki olası sertifikaları olur. ATA Gateway özgün sertifikayı kullanarak bağlanabildiği sürece, yeni sertifikayı denemez.

-   İkinci aşama – Tüm ATA Gateway bileşenleri güncelleştirilmiş yapılandırmayla eşitlendiğinde, ATA Center’ın bağlı olduğu yeni sertifikayı etkinleştirebilirsiniz. Yeni sertifika etkinleştirdiğinizde, ATA Center hizmeti bu sertifikaya bağlanır. ATA Gateway bileşenleri, ATA Center hizmetiyle düzgün bir şekilde karşılıklı kimlik doğrulaması yapamaz ve ikinci sertifikayla kimlik doğrulamasını dener. ATA Center hizmetine bağlandıktan sonra, ATA Gateway en yeni yapılandırmayı alır ve ATA Center için tek bir sertifikaya sahip olur. (İşlemi yeniden başlatmadığınız sürece bu durum geçerli olur.)

> [!NOTE]
> -   İlk aşamada ATA Gateway çevrimdışıysa ve güncelleştirilmiş yapılandırmayı hiç almadıysa, ATA Gateway’de yapılandırma JSON dosyasını el ile güncelleştirmeniz gerekir.
> -   Kullandığınız sertifikaya ATA Gateway bileşenleri tarafından güveniliyor olmalıdır.
> -   Sertifika ATA Konsolu için de kullanıldığından, tarayıcı uyarılarını önlemek için ATA Konsolu adresiyle de eşleşmesi gerekir
> -   Yeni sertifikayı etkinleştirdikten sonra yeni bir ATA Gateway dağıtımı yapmanız gerekirse, ATA Gateway Kurulum paketini yeniden indirmelisiniz.

## <a name="changing-the-ata-center-configuration"></a>ATA Center yapılandırmasını değiştirme

1.  ATA Konsolu’nu açın.

2.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.png)

3.  **Center**’ı seçin.

  ![ATA yapılandırmasını değiştirme](media/change-center-config.png)

4.  **URL** altında **Özel DNS adı/IP adresi ekle**’yi ve ardından yeni DNS veya IP adresini seçin ya da **Sertifika** altında yeni sertifikayı seçin.

5.  **Kaydet**'e tıklayın.

6.  Kaç ATA Gateway’in en son yapılandırmayla eşitlendiğine ilişkin bir bildirim görürsünüz.

    >[!IMPORTANT]
    >Yeni yapılandırmayı etkinleştirmeden önce, tüm ATA Gateway bileşenlerinin en son yapılandırmayla eşitlendiğini doğrulayın. Tüm ATA Gateway bileşenleri eşitlenmeden yeni yapılandırmayı etkinleştirmek, ATA Gateway’in beklendiği şekilde çalışmaya son vermesine neden olabilir. ATA Gateway bileşenlerinden herhangi biri eşitlenmemişse, Etkinleştir’e tıkladığınızda şu hatayla karşılaşırsınız:


7.  Tüm ATA Gateway’ler eşitlendikten sonra, yeni IP adresini veya sertifikayı etkinleştirmek için **Etkinleştir**’e tıklayın.

    > [!NOTE]
    > Özel bir IP adresi girdiyseniz, IP adresini ATA Center’a yükleyene kadar **Etkinleştir**’e tıklayamazsınız.

8.  Değişiklikler etkinleştirildikten sonra tüm ATA Gateway bileşenlerinin yapılandırmalarını eşitleyebildiklerinden emin olun. Kaç ATA Gateway bileşeninin yapılandırmasını başarıyla eşitlediği, bildirim çubuğunda gösterilir.




## <a name="see-also"></a>Ayrıca bkz:
- [ATA Konsolu ile çalışma](working-with-ata-console.md)
- [ATA forumuna bakın!](https://aka.ms/ata-forum)
