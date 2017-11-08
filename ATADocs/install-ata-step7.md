---
title: "Yükleme Gelişmiş tehdit analizi - 8. adım | Microsoft Docs"
description: "ATA’yı yükleme işleminin son adımında Honeytoken kullanıcısını yapılandırırsınız."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/7/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 8980e724-06a6-40b0-8477-27d4cc29fd2b
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 0feb12a2e86adae124016c90431209ec33cdbcb5
ms.sourcegitcommit: 4d2ac5b02c682840703edb0661be09055d57d728
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="install-ata---step-8"></a>Ata'yı - adım 8 yükleme

>[!div class="step-by-step"]
[«Adım 7](vpn-integration-install-step.md)

## <a name="step-8-configure-ip-address-exclusions-and-honeytoken-user"></a>8. Adım IP adresi dışlamalarını ve Honeytoken kullanıcısını yapılandırma
ATA, belirli IP adreslerinin veya kullanıcıların birkaç algılama yönteminden dışlanmasına olanak verir. 

Örneğin, bir **DNS Keşfi dışlaması** DNS’i tarama mekanizması olarak kullanan bir güvenlik tarayıcısı olabilir. Bu dışlama işlemi ATA’nın böyle tarayıcıları yoksaymasına yardımcı olur. *Anahtar Geçişi* dışlama işlemine örnek olarak bir NAT aygıtı gösterilebilir.    

ATA ayrıca bir yakalama kötü amaçlı aktörler için kullanılan bir Honeytoken kullanıcısını yapılandırma sağlar - bir uyarı (normalde etkinliği olmayan) bu hesapla ilişkili herhangi bir kimlik doğrulamasını tetikler.

Bunu yapılandırmak için aşağıdaki adımları izleyin:

1.  ATA Konsolu’ndan, ayarlar simgesine tıklayın ve **Yapılandırma**’yı seçin.

    ![ATA yapılandırma ayarları](media/ATA-config-icon.png)

2.  **Algılama** altında bulunan **Genel**’e tıklayın.

2. **Honeytoken hesapları** altında Honeytoken hesap adını girin. Honeytoken hesapları alanını aranabilir ve otomatik olarak, ağınızdaki varlıkların görüntüler.

   ![Honeytoken](media/honeytoken.png)

3. **Dışlamalar**’a tıklayın. Her bir tehdit türü için algılamadan dışlanacak bir kullanıcı hesabı veya IP adresi girin ve *artı* sembolüne tıklayın. **Varlık ekle** (kullanıcı veya bilgisayar) alanında arama yapılabilir ve bu alan, ağınızdaki varlıklarla otomatik olarak doldurulur. Daha fazla bilgi için bkz. [Varlıkları algılamalardan dışlama](excluding-entities-from-detections.md)

   ![Dışlamalar](media/exclusions.png)

4.  **Kaydet**'e tıklayın.


Tebrikler, Microsoft Advanced Threat Analytics dağıtımını başarıyla tamamladınız!

Algılanan kuşkulu etkinlikleri görüntülemek için saldırı zaman çizelgesini gözden geçirin ve kullanıcıları veya bilgisayarları arayın ve profillerini görüntüleyin.

ATA hemen şüpheli etkinlikler için tarama başlatır. Bazı şüpheli davranış etkinlikleri gibi bazı etkinlikler kullanılamaz ATA davranış profilleri (en az üç hafta) oluşturmak için zaman bulana kadar.

ATA’nın çalışır durumda olduğunu ve ağınızdaki ihlalleri yakalayıp yakalamadığını denetlemek için [ATA saldırı simülasyonu senaryo kitabına](https://docs.microsoft.com/enterprise-mobility-security/solutions/ata-attack-simulation-playbook) bakabilirsiniz.


>[!div class="step-by-step"]
[«Adım 7](vpn-integration-install-step.md)



## <a name="related-videos"></a>İlgili videolar
- [ATA dağıtımına genel bakış](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)
- [ATA Gateway türü sağ seçme](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA POC Dağıtım Kılavuzu](http://aka.ms/atapoc)
- [ATA boyutlandırma aracı](http://aka.ms/atasizingtool)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)

