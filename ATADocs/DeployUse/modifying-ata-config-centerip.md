---
title: "Advanced Threat Analytics yapılandırmasını değiştirme - ATA Center IP adresi | Microsoft Docs"
description: "ATA Center bileşeninizin IP adresini, bağlantı noktasını veya sertifikasını nasıl değiştireceğiniz açıklanır."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 93b27f15-f7e5-49bb-870a-d81d09dfe9fc
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: c90f34b0567df43d977ca23e38319eafe01c51e3
ms.sourcegitcommit: 49e892a82275efa5146998764e850959f20d3216
translationtype: HT
---
*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*



# <a name="change-ata-configuration---ata-center-ip-address"></a>Ata yapılandırmasını değiştirme - ATA Center IP adresi

>[!div class="step-by-step"]
[ATA Center sertifikası »](modifying-ata-config-centercert.md)

İlk dağıtımdan sonra, ATA Center’da değişiklik yaparken dikkatli olmak gerekir. IP adresini ve bağlantı noktasını veya sertifikayı güncelleştirirken aşağıdaki yordamları kullanın.

## <a name="change-the-ip-address-used-by-the-ata-center-server"></a>ATA Center sunucusunda kullanılan IP adresini değiştirme
ATA Center IP adresini ve bağlantı noktasını veya sertifikasını değiştirmeniz gerekiyorsa, aşağıdaki noktaları dikkate alın.

ATA Gateway bileşenleri bağlanmaları gereken ATA Center’ın IP adresini yerel olarak depolar. Düzenli aralıklarla ATA Center’a bağlanır ve yapılandırma değişikliklerini alırlar. ATA Gateway bileşenlerinin ATA Center’a bağlanma şeklinde yapılacak değişiklikler iki aşamada yapılır.

-   Birinci aşama – IP adresini ve bağlantı noktasını ATA Center hizmeti tarafından kullanılmasını istediğiniz gibi güncelleştirin. Bu noktada ATA Center özgün IP adresinde dinlemeye devam eder ve ATA Gateway’in yapılandırmasını bir sonraki eşitleyişinde ATA Center için iki IP adresi olur. ATA Gateway özgün (ilk) IP adresini kullanarak bağlanabildiği sürece, yeni IP adresini ve bağlantı noktasını denemez.

-   İkinci aşama – Tüm ATA Gateway bileşenleri güncelleştirilmiş yapılandırmayla eşitlendiğinde, ATA Center’ın dinlemesi için yeni IP adresini ve bağlantı noktasını etkinleştirin. Yeni IP adresini etkinleştirdiğinizde, ATA Center hizmeti yeni IP adresine bağlanır. ATA Gateway bileşenleri özgün adrese bağlanamaz ve şimdi ATA Center için var olan ikinci (yeni) IP adresiyle bağlanmayı dener. Yeni IP adresiyle ATA Center’a bağlandıktan sonra, ATA Gateway en yeni yapılandırmayı alır ve ATA Center için tek bir IP adresine sahip olur. (İşlemi yeniden başlatmadığınız sürece bu durum geçerli olur.)

> [!NOTE]
> -   İlk aşamada ATA Gateway çevrimdışıysa ve güncelleştirilmiş yapılandırmayı hiç almadıysa, ATA Gateway’de yapılandırma JSON dosyasını el ile güncelleştirmeniz gerekir.
> -   Yeni IP adresi ATA Center sunucusuna yüklendiyse, değişikliği yaparken bu adresi IP adresleri listesinden seçebilirsiniz. Öte yandan, herhangi bir nedenle IP adresini ATA Center sunucusuna yükleyemediyseniz, özel IP adresini seçebilir ve bu adresi el ile ekleyebilirsiniz. Yeni IP adresini etkinleştirebilmeniz için bu IP adresinin sunucuya yüklenmesi gerekir.
> -   Yeni IP adresini etkinleştirdikten sonra yeni bir ATA Gateway dağıtımı yapmanız gerekirse, ATA Gateway Kurulum paketini yeniden indirmelisiniz.

1.  ATA Konsolu’nu açın.

2.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

3.  **Center**’ı seçin.

4.  **Center hizmeti IP adresi: bağlantı noktası**’nın altında, mevcut IP adreslerinden birini seçin veya **Özel IP adresi ekle**’yi seçip bir IP adresi girin.

5.  **Kaydet**'e tıklayın.

6.  Kaç ATA Gateway’in en son yapılandırmayla eşitlendiğine ilişkin bir bildirim görürsünüz.

    ![ATA Center ile eşitlenen Gateway bileşenlerinin resmi](media/ATA-chge-IP-after-clicking-save.png)

    >[!IMPORTANT]
    >Yeni yapılandırmayı etkinleştirmeden önce, tüm ATA Gateway bileşenlerinin en son yapılandırmayla eşitlendiğini doğrulayın. Tüm ATA Gateway bileşenleri eşitlenmeden yeni yapılandırmayı etkinleştirmek, ATA Gateway’in beklendiği şekilde çalışmaya son vermesine neden olabilir. ATA Gateway bileşenlerinden herhangi biri eşitlenmemişse, Etkinleştir’e tıkladığınızda şu hatayla karşılaşırsınız:
    >
    >    ![ATA Gateway eşitleme hatası](media/ataGW-not-synced.png)


7.  Tüm ATA Gateway’ler eşitlendikten sonra, yeni IP adresini etkinleştirmek için **Etkinleştir**’e tıklayın.

    > [!NOTE]
    > Özel bir IP adresi girdiyseniz, IP adresini ATA Center’a yükleyene kadar **Etkinleştir**’e tıklayamazsınız.

8.  Değişiklikler etkinleştirildikten sonra tüm ATA Gateway bileşenlerinin yapılandırmalarını eşitleyebildiklerinden emin olun. Kaç ATA Gateway bileşeninin yapılandırmasını başarıyla eşitlediği, bildirim çubuğunda gösterilir.

>[!div class="step-by-step"]
[ATA Center sertifikasını değiştirme »](modifying-ata-config-centercert.md)


## <a name="see-also"></a>Ayrıca bkz.
- [ATA Konsolu ile çalışma](working-with-ata-console.md)
- [ATA forumuna bakın!](https://aka.ms/ata-forum)
