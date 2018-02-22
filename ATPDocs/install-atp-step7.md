---
title: "Yükleme Azure Gelişmiş tehdit koruması - 7. adım | Microsoft Docs"
description: "Azure ATP yükleme son adım, Honeytoken kullanıcısını yapılandırın."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2017
ms.topic: get-started-article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 1ad5e923-9bbd-4f56-839a-b11a9f387d4b
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: bef13d0f4799a4483eda6604a8ed96befaa13508
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="install-azure-atp---step-7"></a>Azure ATP - 7. adım yükleme

>[!div class="step-by-step"]
[«6. Adım](install-atp-step6-vpn.md)
[8. Adım»](install-atp-step8-samr.md)

## <a name="step-7-configure-detection-exclusions-and-honeytoken-user"></a>7. Adım Algılama Dışlamalar ve honeytoken kullanıcısını yapılandırma

Azure ATP belirli IP adresleri veya kullanıcı dışlama algılama numarasından sağlar. 

Örneğin, bir **DNS Keşfi dışlaması** DNS’i tarama mekanizması olarak kullanan bir güvenlik tarayıcısı olabilir. Dışlama Azure böyle tarayıcılar yoksay ATP yardımcı olur.  

Azure ATP ayrıca bir yakalama kötü amaçlı aktörler için kullanılan bir Honeytoken kullanıcısını yapılandırma sağlar - bir uyarı (normalde etkinliği olmayan) bu hesapla ilişkili herhangi bir kimlik doğrulamasını tetikler.

Bunu yapılandırmak için aşağıdaki adımları izleyin:

1.  Azure ATP çalışma portalı, ayarlar simgesine tıklayın ve seçin **yapılandırma**.

    ![Azure ATP yapılandırma ayarları](media/atp-config-menu.png)

2.  Altında **algılama**, tıklatın **varlık etiketleri**.

3. Altında **Honeytoken hesapları** Honeytoken hesabı adı girin ve tıklayın  **+**  oturum. Honeytoken hesapları alanını aranabilir ve otomatik olarak, ağınızdaki varlıkların görüntüler. **Kaydet**'e tıklayın.

   ![Honeytoken](media/honeytoken-sensitive.png)

4. **Dışlamalar**’a tıklayın. Her bir tehdit türü için algılamadan dışlanacak bir kullanıcı hesabı veya IP adresi girin ve *artı* sembolüne tıklayın. **Varlık ekle** (kullanıcı veya bilgisayar) alanında arama yapılabilir ve bu alan, ağınızdaki varlıklarla otomatik olarak doldurulur. Daha fazla bilgi için bkz: [varlıklar algılamaların dışında hariç](excluding-entities-from-detections.md) ve [şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md).

   ![Dışlamalar](media/exclusions.png)

5.  **Kaydet**'e tıklayın.


Tebrikler, Azure Advanced Threat Protection başarıyla dağıtıldı.

Algılanan kuşkulu etkinlikleri görüntülemek için saldırı zaman çizelgesini gözden geçirin ve kullanıcıları veya bilgisayarları arayın ve profillerini görüntüleyin.

Azure ATP şüpheli etkinlikler için hemen taramaya başlar. Olağan dışı grubu değişiklikleri gibi bazı algılamaların öğrenme süresi gerektirir ve Azure ATP dağıtımdan hemen sonra kullanılabilir değil.



>[!div class="step-by-step"]
[«6. Adım](install-atp-step6-vpn.md)
[8. Adım»](install-atp-step8-samr.md)

## <a name="see-also"></a>Ayrıca bkz:
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
