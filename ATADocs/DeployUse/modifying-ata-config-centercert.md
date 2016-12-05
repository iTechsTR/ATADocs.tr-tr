---
title: "ATA yapılandırmasını değiştirme: ATA Center sertifikası | Microsoft Docs"
description: "ATA Center sunucusundaki yerel bilgisayar deposunda yer alan sertifikayı yenileme veya değiştirmeye yönelik iki aşamalı işlem açıklanır."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/24/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: c8855287-de3b-4cdd-be8f-2128f48a6f27
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bc7af91a925928183d179391f15d3a24cda2b576
ms.openlocfilehash: 534b5f476e580919b11327ddbf9a35edad130515


---

*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*



# <a name="change-ata-configuration---ata-center-certificate"></a>Ata yapılandırmasını değiştirme - ATA Center sertifikası

>[!div class="step-by-step"]
[« ATA Center sunucusu IP adresi](modifying-ata-config-centerip.md)
[ATA Konsolu URL’si »](modifying-ata-config-consoleurl.md)

## <a name="change-the-ata-center-certificate"></a>ATA Center sertifikasını değiştirme
Sertifikalarınızın süresi sona ermek üzereyse ve ATA Center sunucusundaki yerel bilgisayar deposuna yeni sertifika yüklendikten sonra yenilenmesi veya değiştirilmesi gerekiyorsa, şu iki aşamalı işlemi yaparak sertifikayı değiştirin:

-   Birinci aşama – ATA Center hizmetinin kullanmasını istediğiniz sertifikayı güncelleştirin. Bu noktada, ATA Center hizmeti hala özgün sertifikaya bağlıdır. ATA Gateway bileşenleri yapılandırmalarını eşitlediğinde, karşılıklı kimlik doğrulaması için geçerli olan iki olası sertifikaları olur. ATA Gateway özgün sertifikayı kullanarak bağlanabildiği sürece, yeni sertifikayı denemez.

-   İkinci aşama – Tüm ATA Gateway bileşenleri güncelleştirilmiş yapılandırmayla eşitlendiğinde, ATA Center’ın bağlı olduğu yeni sertifikayı etkinleştirebilirsiniz. Yeni sertifika etkinleştirdiğinizde, ATA Center hizmeti bu sertifikaya bağlanır. ATA Gateway bileşenleri, ATA Center hizmetiyle düzgün bir şekilde karşılıklı kimlik doğrulaması yapamaz ve ikinci sertifikayla kimlik doğrulamasını dener. ATA Center hizmetine bağlandıktan sonra, ATA Gateway en yeni yapılandırmayı alır ve ATA Center için tek bir sertifikaya sahip olur. (İşlemi yeniden başlatmadığınız sürece bu durum geçerli olur.)

> [!NOTE]
> -   İlk aşamada ATA Gateway çevrimdışıysa ve güncelleştirilmiş yapılandırmayı hiç almadıysa, ATA Gateway’de yapılandırma JSON dosyasını el ile güncelleştirmeniz gerekir.
> -   Kullandığınız sertifikaya ATA Gateway bileşenleri tarafından güveniliyor olmalıdır.
> -   Sertifika ATA Konsolu için de kullanıldığından, tarayıcı uyarılarını önlemek için ATA Konsolu adresiyle de eşleşmesi gerekir
> -   Yeni sertifikayı etkinleştirdikten sonra yeni bir ATA Gateway dağıtımı yapmanız gerekirse, ATA Gateway Kurulum paketini yeniden indirmelisiniz.

1.  ATA Konsolu’nu açın.

2.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

3.  **Center**’ı seçin.

4.  **Sertifika**’nın altında, listedeki sertifikalardan birini seçin.

5.  **Kaydet**'e tıklayın.

6.  Kaç ATA Gateway’in en son yapılandırmayla eşitlendiğini gösteren bir bildirim görürsünüz.

7.  Tüm ATA Gateway’ler eşitlendikten sonra, yeni sertifikayı etkinleştirmek için **Etkinleştir**’e tıklayın.
    >[!IMPORTANT]
    >Yeni yapılandırmayı etkinleştirmeden önce, tüm ATA Gateway bileşenlerinin en son yapılandırmayla eşitlendiğini doğrulayın. Tüm ATA Gateway bileşenleri eşitlenmeden yeni yapılandırmayı etkinleştirmek, ATA Gateway’in beklendiği şekilde çalışmaya son vermesine neden olabilir. ATA Gateway bileşenlerinden herhangi biri eşitlenmemişse, Etkinleştir’e tıkladığınızda şu hatayla karşılaşırsınız:
    >
    >    ![ATA Gateway eşitleme hatası](media/ataGW-not-synced.png)

8.  Değişiklikler etkinleştirildikten sonra tüm ATA Gateway bileşenlerinin yapılandırmalarını eşitleyebildiklerinden emin olun.

>[!div class="step-by-step"]
[« ATA Center sunucusu IP adresi](modifying-ata-config-centerip.md)
[ATA Konsolu URL’si »](modifying-ata-config-consoleurl.md)

## <a name="see-also"></a>Ayrıca bkz.
- [ATA Konsolu ile çalışma](working-with-ata-console.md)
- [ATA forumuna bakın!](https://aka.ms/ata-forum)



<!--HONumber=Nov16_HO5-->


