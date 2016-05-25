---
# required metadata

title: ATA yapılandırmasını değiştirme - ATA Center IP adresi | Microsoft Advanced Threat Analytics
description: ATA Center bileşeninizin IP adresini, bağlantı noktasını veya sertifikasını nasıl değiştireceğiniz açıklanır.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 93b27f15-f7e5-49bb-870a-d81d09dfe9fc

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Ata yapılandırmasını değiştirme - ATA Center IP adresi

>[!div class="step-by-step"]
[ATA Center sertifikası »](modifying-ata-config-centercert.md)

İlk dağıtımdan sonra, ATA Center’da değişiklik yaparken dikkatli olmak gerekir. IP adresini ve bağlantı noktasını veya sertifikayı güncelleştirirken aşağıdaki yordamları kullanın.

## ATA Center sunucusunda kullanılan IP adresini değiştirme
ATA Center IP adresini ve bağlantı noktasını veya sertifikasını değiştirmeniz gerekiyorsa, aşağıdaki noktaları dikkate alın.

ATA Gateway bileşenleri bağlanmaları gereken ATA Center’ın IP adresini yerel olarak depolar. Düzenli aralıklarla ATA Center’a bağlanır ve yapılandırma değişikliklerini alırlar. ATA Gateway bileşenlerinin ATA Center’a bağlanma şeklinde yapılacak değişiklikler iki aşamada yapılır.

-   Birinci aşama – ATA Center hizmetinin IP adresini ve bağlantı noktasını ATA Center hizmeti tarafından kullanılmasını istediğiniz gibi güncelleştirin. Bu noktada ATA Center özgün IP adresinde dinlemeye devam eder ve ATA Gateway’in yapılandırmasını bir sonraki eşitleyişinde ATA Center için iki IP adresi olur. ATA Gateway özgün (ilk) IP adresini kullanarak bağlanabildiği sürece, yeni IP adresini ve bağlantı noktasını denemez.

-   İkinci aşama – Tüm ATA Gateway bileşenleri güncelleştirilmiş yapılandırmayla eşitlendiğinde, ATA Center’ın dinlemesi için yeni IP adresini ve bağlantı noktasını etkinleştirin. Yeni IP adresini etkinleştirdiğinizde, ATA Center hizmeti yeni IP adresine bağlanır. ATA Gateway bileşenleri özgün adrese bağlanamaz ve şimdi ATA Center için var olan ikinci (yeni) IP adresiyle bağlanmayı dener. Yeni IP adresiyle ATA Center’a bağlandıktan sonra, ATA Gateway en yeni yapılandırmayı alır ve ATA Center için tek bir IP adresine sahip olur. (İşlemi yeniden başlatmadığınız sürece bu durum geçerli olur.)

> [!NOTE]
> -   İlk aşamada ATA Gateway çevrimdışıysa ve güncelleştirilmiş yapılandırmayı hiç almadıysa, ATA Gateway’de yapılandırma JSON dosyasını el ile güncelleştirmeniz gerekir.
> -   Yeni IP adresi ATA Center sunucusuna yüklendiyse, değişikliği yaparken bu adresi IP adresleri listesinden seçebilirsiniz. Öte yandan, herhangi bir nedenle IP adresini ATA Center sunucusuna yükleyemediyseniz, özel IP adresini seçebilir ve bu adresi el ile ekleyebilirsiniz. Yeni IP adresini etkinleştirebilmeniz için bu IP adresinin sunucuya yüklenmesi gerekir.
> -   Yeni IP adresini etkinleştirdikten sonra yeni bir ATA Gateway dağıtımı yapmanız gerekirse, ATA Gateway Kurulum paketini yeniden indirmelisiniz.

1.  ATA Konsolu’nu açın.

2.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin..

    ![ATA yapılandırma ayarları simgesi](media/ATA-config-icon.JPG)

3.  **ATA Center**’ı seçin..

4.  **ATA Center Service IP adresi: bağlantı noktası**’nın altında, var olan IP adreslerinden birini seçin veya **Özel IP adresi ekle**’yi seçip bir IP adresi girin.

5.  **Kaydet**'e tıklayın..

6.  Kaç ATA Gateway’in en son yapılandırmayla eşitlendiğine ilişkin bir bildirim görürsünüz.

    ![ATA Center ile eşitlenen Gateway bileşenlerinin resmi](media/ATA-chge-IP-after-clicking-save.png)

7.  Tüm ATA Gateway’ler eşitlendikten sonra, yeni IP adresini etkinleştirmek için **Etkinleştir**’e tıklayın.

    > [!NOTE]
    > Özel bir IP adresi girdiyseniz, IP adresini ATA Center’a yükleyene kadar **Etkinleştir**’e tıklayamazsınız.

8.  Değişiklikler etkinleştirildikten sonra tüm ATA Gateway bileşenlerinin yapılandırmalarını eşitleyebildiklerinden emin olun. Kaç ATA Gateway bileşeninin yapılandırmasını başarıyla eşitlediği, bildirim çubuğunda gösterilir.

>[!div class="step-by-step"]
[ATA Center sertifikasını değiştirme »](modifying-ata-config-centercert.md)


## Ayrıca Bkz.
- [ATA Konsolu’yla çalışma](/advanced-threat-analytics/understand-explore/working-with-ata-console)
- [ATA’yı yükleme](install-ata.md)
- [Destek için forumumuzu gözden geçirin!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=Apr16_HO4-->


