---
title: "Advanced Threat Analytics’i yükleme - 7. Adım | Microsoft Docs"
description: "ATA’yı yükleme işleminin son adımında Honeytoken kullanıcısını yapılandırırsınız."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 07/2/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 8980e724-06a6-40b0-8477-27d4cc29fd2b
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: d261273adfa23392a9c0b8408483aa02708f1eee
ms.sourcegitcommit: fa50f37b134d7579d7c310852dff60e5f1996eaa
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# ATA’yı Yükleme - 7. Adım
<a id="install-ata---step-7" class="xliff"></a>

>[!div class="step-by-step"]
[« 6. Adım](install-ata-step6.md)

## 7. Adım IP adresi dışlamalarını ve Honeytoken kullanıcısını yapılandırma
<a id="step-7-configure-ip-address-exclusions-and-honeytoken-user" class="xliff"></a>
ATA, belirli IP adreslerinin veya kullanıcıların birkaç algılama yönteminden dışlanmasına olanak verir. 

Örneğin, bir **DNS Keşfi dışlaması** DNS’i tarama mekanizması olarak kullanan bir güvenlik tarayıcısı olabilir. Bu dışlama işlemi ATA’nın böyle tarayıcıları yoksaymasına yardımcı olur. *Anahtar Geçişi* dışlama işlemine örnek olarak bir NAT aygıtı gösterilebilir.    

ATA ayrıca, kötü amaçlı aktörler için tuzak olarak kullanılan bir Honeytoken kullanıcısının yapılandırılmasına olanak tanır. Bu hesapla (normalde etkinliği yoktur) ilişkilendirilen herhangi bir kimlik doğrulaması bir uyarının tetiklenmesine neden olur.

Yukarıdakileri yapılandırmak için şu adımları izleyin:

1.  ATA Konsolu’ndan, ayarlar simgesine tıklayın ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları](media/ATA-config-icon.png)

2.  **Algılama** altında bulunan **Genel**’e tıklayın.

2. **Honeytoken hesapları** altında Honeytoken hesap adını girin. Honeytoken hesapları alanında arama yapılabilir ve ağınızdaki varlıklar otomatik olarak görüntülenir.

   ![Honeytoken](media/honeytoken.png)

3. **Dışlamalar**’a tıklayın. Her bir tehdit türü için algılamadan dışlanacak bir kullanıcı hesabı veya IP adresi girin ve *artı* sembolüne tıklayın. Varlık ekle (kullanıcı veya bilgisayar) alanında arama yapılabilir ve otomatik olarak ağınızdaki varlıklarla doldurulur.

   ![Dışlamalar](media/exclusions.png)


  > [!NOTE]
  > Bir kullanıcının SID’ini bulmak için, ATA Konsolu’nda kullanıcıyı arayın ve **Hesap Bilgileri** sekmesine tıklayın. 

4.  **Kaydet**'e tıklayın.


Tebrikler, Microsoft Advanced Threat Analytics dağıtımını başarıyla tamamladınız!

Algılanan kuşkulu etkinlikleri görüntülemek için saldırı zaman çizelgesini gözden geçirin ve kullanıcıları veya bilgisayarları arayın ve profillerini görüntüleyin.

ATA hemen şüpheli etkinlikler için tarama yapmaya başlar. ATA, davranış profilleri (en az üç haftalık) oluşturmak için zaman bulana kadar, bazı şüpheli davranış etkinlikleri gibi bazı etkinlikler kullanılamaz.

ATA’nın çalışır durumda olduğunu ve ağınızdaki ihlalleri yakalayıp yakalamadığını denetlemek için [ATA saldırı simülasyonu senaryo kitabına](https://docs.microsoft.com/enterprise-mobility-security/solutions/ata-attack-simulation-playbook) bakabilirsiniz.


>[!div class="step-by-step"]
[« 6. Adım](install-ata-step6.md)


## Ayrıca Bkz.
<a id="see-also" class="xliff"></a>

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)

