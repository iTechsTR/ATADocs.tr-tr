---
title: Advanced Threat Analytics’te varlıkları algılamalardan dışlama | Microsoft Docs
description: ATA’nın belirli varlık etkinliklerini şüpheli olarak algılamasını nasıl engelleyeceğinizi açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 344c0f33-45e1-42e2-a051-f722a4504531
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: e15a4ab34b0389b2c69d8cdf2e5ac04771a24fc9
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44165788"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="excluding-entities-from-detections"></a>Varlıkları algılamalardan dışlama
Bu makalede, doğru zararsız pozitif sonuçları en aza indirmek, ancak aynı zamanda doğru pozitif sonuçları yakalamak emin olmak için uyarılar tetiklemesini önlemek varlıkları açıklanmaktadır. ATA, belirli kullanıcılar tarafından normal ritmi iş parçası olabilecek etkinlikleri hakkında gürültülü engellemek için quiet - edebilir veya hariç tutabilirsiniz - belirli varlıkların uyarılarını susturabilir.

Örneğin, kuruluşunuzdaki rutin BT işlemleri gereği DNS keşfi yapan bir güvenlik tarayıcınız veya etki alanı denetleyicisinde uzaktan betik çalıştıran bir yöneticiniz varsa (ve bunlar tasdikli eylemlerse) bu özelliğe ihtiyaç duyabilirsiniz.

Varlıkların ATA’da uyarı tetiklemesini engellemek için:

Varlıkları dışlamak için iki yol vardır: Doğrudan şüpheli etkinlik üzerinden veya **Yapılandırma** sayfasındaki **Dışlamalar** sekmesinden.

- **Şüpheli etkinlik**: bir kullanıcı veya bilgisayar veya belirli etkinlik gerçekleştirmesine izin verilen ve sık sık, bunu yapabilirsiniz, IP adresi için bir etkinlik hakkında uyarı aldığınızda, şüpheli etkinlik zaman çizelgesinde, üç noktaya sağ tıklayın Bu varlık ve select kuşkulu etkinlik için bir satır sonu **Kapat ve dışla**. <br></br>Bu kullanıcı, bilgisayar veya IP adresini bu şüpheli etkinliğin Dışlamalar listesine ekler. Şüpheli etkinlik kapatır ve artık listelenen **açık** olayları listeyi **şüpheli etkinlik zaman çizelgesi**.

    ![Varlık dışlama](./media/exclude-in-sa.png)

- **Yapılandırma sayfasından**: gözden geçirmek veya herhangi bir özel değiştirmek için: altında **yapılandırma**, tıklayın **dışlamaları** ve şüpheli etkinlik gibi ardından  **Gizli hesap kimlik bilgileri ifşa**.

    ![Dışlama yapılandırma](./media/exclusions-config-page.png)

Bir varlığı **Dışlamalar** yapılandırmasından kaldırmak için: Varlık adının yanındaki eksi işaretine tıklayın ve sayfanın sonundaki **Kaydet** düğmesine basın.

Algılama dışlamalarını yalnızca, aldığınız bir uyarı türünün doğru zararsız pozitif sonuç olduğunu belirlemeniz durumunda eklemeniz önerilir. 

> [!NOTE]
> Güvenliğiniz için, dışlama ayarlama seçeneği algılamaların tamamında sunulmaz. 

Bazı algılamalar, neleri dışlayabileceğinize karar vermeniz için ipuçları sağlar. 

Her dışlama bağlam üzerinde bağlıdır, diğerleri için bilgisayar veya IP adresleri ayarlayabilirsiniz ancak bazı durumlarda kullanıcılar ayarlayabilirsiniz. 

Birini veya diğerini - hariç tutabilirsiniz bir IP adresi veya bilgisayar dışlama seçeneğiniz varsa, her ikisi de sağlamanız gerekmez.

> [!NOTE]
> Yapılandırma sayfaları yalnızca ATA yöneticileri tarafından değiştirilebilir.


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [ATA yapılandırmasında değişiklik yapma](modifying-ata-center-configuration.md)
