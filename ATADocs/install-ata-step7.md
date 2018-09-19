---
title: Advanced Threat Analytics'i yükleme - 8. adım | Microsoft Docs
description: ATA’yı yükleme işleminin son adımında Honeytoken kullanıcısını yapılandırırsınız.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/14/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 8980e724-06a6-40b0-8477-27d4cc29fd2b
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: eacc3c2449e6fd7771c43b97b8ed08276ab130d2
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133571"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="install-ata---step-8"></a>Ata'yı adım 8 yükleme

>[!div class="step-by-step"]
[«7. adım](vpn-integration-install-step.md)
[9. adım»](install-ata-step9-samr.md)

## <a name="step-8-configure-ip-address-exclusions-and-honeytoken-user"></a>8. Adım IP adresi dışlamalarını ve Honeytoken kullanıcısını yapılandırma
ATA, belirli IP adreslerinin veya kullanıcıların birkaç algılama yönteminden dışlanmasına olanak verir. 

Örneğin, bir **DNS Keşfi dışlaması** DNS’i tarama mekanizması olarak kullanan bir güvenlik tarayıcısı olabilir. Bu dışlama işlemi ATA’nın böyle tarayıcıları yoksaymasına yardımcı olur. *Anahtar Geçişi* dışlama işlemine örnek olarak bir NAT aygıtı gösterilebilir.    

ATA ayrıca kötü amaçlı aktörler için tuzak olarak kullanılan bir Honeytoken kullanıcısının yapılandırılmasına sağlar - herhangi bir kimlik doğrulaması (normalde etkinliği olmayan) bu hesapla ilişkili bir uyarı tetikler.

Bunu yapılandırmak için aşağıdaki adımları izleyin:

1.  ATA Konsolu’ndan, ayarlar simgesine tıklayın ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları](media/ATA-config-icon.png)

2.  Altında **algılama**, tıklayın **varlık etiketleri**.

2. **Honeytoken hesapları** altında Honeytoken hesap adını girin. Honeytoken hesapları alanında arama yapılabilir ve otomatik olarak ağınızdaki varlıklar görüntüler.

   ![Honeytoken](media/honeytoken.png)

3. **Dışlamalar**’a tıklayın. Her bir tehdit türü için algılamadan dışlanacak bir kullanıcı hesabı veya IP adresi girin ve *artı* sembolüne tıklayın. **Varlık ekle** (kullanıcı veya bilgisayar) alanında arama yapılabilir ve bu alan, ağınızdaki varlıklarla otomatik olarak doldurulur. Daha fazla bilgi için bkz. [Varlıkları algılamalardan dışlama](excluding-entities-from-detections.md)

   ![Dışlamalar](media/exclusions.png)

4.  **Kaydet**'e tıklayın.


Tebrikler, Microsoft Advanced Threat Analytics dağıtımını başarıyla tamamladınız!

Algılanan kuşkulu etkinlikleri görüntülemek için saldırı zaman çizelgesini gözden geçirin ve kullanıcıları veya bilgisayarları arayın ve profillerini görüntüleyin.

ATA hemen şüpheli etkinlikler için tarama başlatılır. Bazı şüpheli davranış etkinlikleri gibi bazı etkinlikler kullanılamaz ATA, davranış profilleri (en az üç haftalık) oluşturmak için zaman bulana kadar.

ATA’nın çalışır durumda olduğunu ve ağınızdaki ihlalleri yakalayıp yakalamadığını denetlemek için [ATA saldırı simülasyonu senaryo kitabına](https://docs.microsoft.com/enterprise-mobility-security/solutions/ata-attack-simulation-playbook) bakabilirsiniz.


>[!div class="step-by-step"]
[«7. adım](vpn-integration-install-step.md)
[9. adım»](install-ata-step9-samr.md)


## <a name="related-videos"></a>İlgili videolar
- [ATA dağıtımı genel bakış](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)
- [ATA Gateway türü sağ seçme](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA POC Dağıtım Kılavuzu](http://aka.ms/atapoc)
- [ATA boyutlandırma aracı](http://aka.ms/atasizingtool)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)

