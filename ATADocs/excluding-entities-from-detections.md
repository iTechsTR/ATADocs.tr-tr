---
title: "Advanced Threat Analytics’te varlıkları algılamalardan dışlama | Microsoft Docs"
description: "ATA’nın belirli varlık etkinliklerini şüpheli olarak algılamasını nasıl engelleyeceğinizi açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/7/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 344c0f33-45e1-42e2-a051-f722a4504531
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: f9fce36074b5c31e35f95f028b856b18fa3bae0b
ms.sourcegitcommit: 4d2ac5b02c682840703edb0661be09055d57d728
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="excluding-entities-from-detections"></a>Varlıkları algılamalardan dışlama
Bu makalede, doğru zararsız pozitif sonuç en aza ancak aynı anda true pozitif sonuç catch emin olmak için uyarıları tetikleme varlıkları dışlama açıklanmaktadır. ATA, belirli kullanıcılardan, normal Ritim iş parçası olabilir etkinlikleri hakkında gürültülü engellemek için quiet - edebilir veya dışarıda bırakabilirsiniz - uyarıları oluşturma gelen belirli varlıklar.

Örneğin, kuruluşunuzdaki rutin BT işlemleri gereği DNS keşfi yapan bir güvenlik tarayıcınız veya etki alanı denetleyicisinde uzaktan betik çalıştıran bir yöneticiniz varsa (ve bunlar tasdikli eylemlerse) bu özelliğe ihtiyaç duyabilirsiniz.

Varlıkların ATA’da uyarı tetiklemesini engellemek için:

Varlıkları dışlamak için iki yol vardır: Doğrudan şüpheli etkinlik üzerinden veya **Yapılandırma** sayfasındaki **Dışlamalar** sekmesinden.

- **Kuşkulu etkinliğin**: bir etkinlikte bir kullanıcı veya bilgisayar veya belirli etkinlik gerçekleştirmesine izin verilen ve sık, bunu yapabilirsiniz IP adresi için bir uyarı aldığınızda, şüpheli etkinlik zaman çizelgesi, sağ tıklatın, üç nokta Bu varlık ve select kuşkulu etkinlik için satır sonu **kapatın ve dışlama**. <br></br>Bu kullanıcı, bilgisayar veya IP adresi, şüpheli etkinlik için dışlama listesine ekler. Kuşkulu etkinliği kapatır ve artık listelenen **açık** olaylar listesinde **şüpheli etkinlik zaman çizelgesi**.

    ![Varlık dışlama](./media/exclude-in-sa.png)

- **Yapılandırma sayfasından**: gözden geçirmek veya herhangi Dışlamalar değiştirmek için: altında **yapılandırma**, tıklatın **Dışlamalar** ve şüpheli etkinlik gibi seçin  **Hassas hesap kimlik bilgilerini kullanıma sunulan**.

    ![Dışlama yapılandırma](./media/exclusions-config-page.png)

Bir varlığı **Dışlamalar** yapılandırmasından kaldırmak için: Varlık adının yanındaki eksi işaretine tıklayın ve sayfanın sonundaki **Kaydet** düğmesine basın.

Algılama dışlamalarını yalnızca, aldığınız bir uyarı türünün doğru zararsız pozitif sonuç olduğunu belirlemeniz durumunda eklemeniz önerilir. 

> [!NOTE]
> Güvenliğiniz için, dışlama ayarlama seçeneği algılamaların tamamında sunulmaz. 

Bazı algılamalar, neleri dışlayabileceğinize karar vermeniz için ipuçları sağlar. 

Her dışlama bağlama bağlıdır, diğerleri için bilgisayarları veya IP adresi ayarlayabilirsiniz karşın bazı durumlarda, kullanıcılar ayarlayabilirsiniz. 

Birini veya diğerini - dışlayabilirsiniz bir IP adresi veya bir bilgisayar hariç olanağına sahip olduğunuzda, her ikisi de sağlamanız gerekmez.

> [!NOTE]
> Yapılandırma sayfaları yalnızca ATA yöneticileri tarafından değiştirilebilir.


## <a name="see-also"></a>Ayrıca bkz:
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [ATA yapılandırmasında değişiklik yapma](modifying-ata-center-configuration.md)
