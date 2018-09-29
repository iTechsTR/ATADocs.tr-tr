---
title: Yükleme Azure Gelişmiş tehdit koruması - 7. adım | Microsoft Docs
description: Azure ATP yükleme son adımında Honeytoken kullanıcısını yapılandırın.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/2/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 1ad5e923-9bbd-4f56-839a-b11a9f387d4b
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 9252e47978a4adc0e2059a3111b362ff2b042daf
ms.sourcegitcommit: b283bf66e63d76e6dba4564a229e804792794c6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453808"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="install-azure-atp---step-7"></a>Azure ATP - 7. Adım'ı yükleme

> [!div class="step-by-step"]
> [«6. Adım](install-atp-step6-vpn.md)
> [8. Adım»](install-atp-step8-samr.md)

## <a name="step-7-configure-detection-exclusions-and-honeytoken-accounts"></a>7. Adım Algılama dışlamalarını ve honeytoken hesapları yapılandırma

Azure ATP çıkarma algılama sayısı, belirli IP adresleri veya kullanıcılarının sağlar. 

Örneğin, bir **DNS Keşfi dışlaması** DNS’i tarama mekanizması olarak kullanan bir güvenlik tarayıcısı olabilir. Dışlama Azure ATP böyle tarayıcıları yoksaymasına yardımcı olur.  

Azure ATP ayrıca kötü amaçlı aktörler - bu honeytoken hesaplar (normalde etkinliği olmayan) ilişkili herhangi bir kimlik doğrulaması için tuzak kullanılan, bir uyarı tetikler honeytoken hesapları yapılandırmasını sağlar.

Yapılandırmak için aşağıdaki adımları izleyin:

1.  Azure ATP çalışma alanı portalından, ayarlar simgesine tıklayın ve seçin **yapılandırma**.

    ![Azure ATP yapılandırma ayarları](media/atp-config-menu.png)

2.  Altında **algılama**, tıklayın **varlık etiketleri**.

3. Altında **Honeytoken hesapları**Honeytoken hesap adını girin ve tıklatın **+** oturum. Honeytoken hesapları alanında arama yapılabilir ve otomatik olarak ağınızdaki varlıklar görüntüler. **Kaydet**'e tıklayın.

   ![Honeytoken](media/honeytoken-sensitive.png)

4. **Dışlamalar**’a tıklayın. Bir kullanıcı hesabı veya her tür tehdit algılama dışlanacak IP adresi girin. 
5. Tıklayın *artı* oturum. **Varlık ekle** (kullanıcı veya bilgisayar) alanında arama yapılabilir ve bu alan, ağınızdaki varlıklarla otomatik olarak doldurulur. Daha fazla bilgi için [varlıkları algılamalardan dışlama](excluding-entities-from-detections.md) ve [şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md).

   ![Dışlamalar](media/exclusions.png)

6.  **Kaydet**'e tıklayın.


Tebrikler, Azure Gelişmiş tehdit koruması başarıyla dağıttığınız!

Algılanan kuşkulu etkinlikleri görüntülemek için saldırı zaman çizelgesini gözden geçirin ve kullanıcıları veya bilgisayarları arayın ve profillerini görüntüleyin.

Azure ATP şüpheli etkinlikler için tarama hemen başlar. Olağan dışı Grup değişiklikleri gibi bazı algılamalar bir öğrenme dönemi gerekir ve Azure ATP dağıtımdan hemen sonra kullanılamaz.



> [!div class="step-by-step"]
> [«6. Adım](install-atp-step6-vpn.md)
> [8. Adım»](install-atp-step8-samr.md)

## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
