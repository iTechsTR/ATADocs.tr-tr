---
# required metadata

title: ATA’yı Yükleme | Microsoft Advanced Threat Analytics
description: ATA’yı yükleme işleminin son adımında, kısa süreli kiralık alt ağları ve Honeytoken kullanıcısını yapılandırırsınız.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 8980e724-06a6-40b0-8477-27d4cc29fd2b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ATA’yı Yükleme - 6. Adım

>[!div class="step-by-step"]
[« 5. Adım](install-ata-step5.md)

## 6. Adım. Kısa süreli kiralık alt ağları ve Honeytoken kullanıcısını yapılandırma
Kısa süreli kiralık alt ağlar, IP adresi atamasının çok hızlı, saniyeler veya dakikalar içinde değiştiği alt ağlardır. Örneğin, VPN’leriniz için kullanılan IP adresleri ve Wi-Fi IP adresleri böyledir. Kuruluşunuzda kullanılan kısa süreli kiralık alt ağların listesi girmek için, şu adımları izleyin:

1.  ATA Gateway makinesindeki ATA Konsolu’nda ayarlar simgesine tıklayın ve **Yapılandırma**’yı seçin..

    ![ATA yapılandırma ayarları](media/ATA-config-icon.JPG)

2.  **Algılama**’nın altında kısa vadeli kiralık alt ağlar için şunları girin. Eğik çizgili gösterim biçimini kullanarak kısa süreli kiralık alt ağları girin (örneğin, `192.168.0.0/24`) ve artı işaretine tıklayın.

3.  Honeytoken hesabı SID’leri için, ağ etkinliği olmayacak kullanıcı hesabının SID değerini girin ve artı işaretine tıklayın. Örneğin: `S-1-5-21-72081277-1610778489-2625714895-10511`.

    > [!NOTE]
    > Bir kullanıcının SID’ini bulmak için, ATA Konsolu’nda kullanıcıyı arayın ve **Hesap Bilgileri** sekmesine tıklayın. 

4.  Özel durumları yapılandırın: Belirli kuşkulu etkinliklerden dışlanmak üzere IP adresleri yapılandırabilirsiniz. Daha fazla bilgi için bkz. [ATA algılama ayarlarıyla çalışma](working-with-detection-settings.md).

5.  **Kaydet**'e tıklayın..

![Değişiklikleri kaydedin.](media/ATA-VPN-Subnets.JPG)

Tebrikler, Microsoft Advanced Threat Analytics dağıtımını başarıyla tamamladınız!

Algılanan kuşkulu etkinlikleri görüntülemek için saldırı zaman çizelgesini gözden geçirin ve kullanıcıları veya bilgisayarları arayın ve profillerini görüntüleyin.

ATA hemen şüpheli etkinlikler için tarama yapmaya başlar. ATA, davranış profilleri (en az üç haftalık) oluşturmak için zaman bulana kadar, bazı şüpheli davranış etkinlikleri gibi bazı etkinlikler kullanılamaz.


>[!div class="step-by-step"]
[« 5. Adım](install-ata-step5.md)


## Ayrıca Bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)



<!--HONumber=May16_HO1-->


