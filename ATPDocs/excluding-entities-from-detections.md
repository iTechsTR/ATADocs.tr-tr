---
title: Varlıklar Azure Advanced Threat Protection algılamaların dışında bırakma | Microsoft Docs
description: Belirli bir varlık etkinlikler kuşkulu olarak algılama Azure ATP durdurmayı açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: cae3ed45-8fbc-4f25-ba24-3cc407c6ea93
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 60a2fae0ef044993786fb3b7e2d21a3ac27bb9f0
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
ms.locfileid: "29446032"
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="excluding-entities-from-detections"></a>Varlıkları algılamalardan dışlama
Bu makalede, doğru zararsız pozitif sonuç en aza ancak aynı anda true pozitif sonuç catch emin olmak için uyarıları tetikleme varlıkları dışlama açıklanmaktadır. Azure ATP belirli kullanıcılardan, normal Ritim iş parçası olabilir, etkinlikleri hakkında gürültülü engellemek için quiet - edebilir veya dışarıda bırakabilirsiniz - uyarıları oluşturma gelen belirli varlıklar.

Örneğin, kuruluşunuzdaki rutin BT işlemleri gereği DNS keşfi yapan bir güvenlik tarayıcınız veya etki alanı denetleyicisinde uzaktan betik çalıştıran bir yöneticiniz varsa (ve bunlar tasdikli eylemlerse) bu özelliğe ihtiyaç duyabilirsiniz. Hariç tutmak için hangi varlıkların karar vermenize yardımcı olacak Azure ATP algılamaların hakkında daha fazla bilgi için bkz: [kuşkulu etkinlikleri Kılavuzu](suspicious-activity-guide.md).

Azure ATP uyarıları oluşturma varlıkları dışlamak için:

Varlıkları dışlamak için iki yol vardır: Doğrudan şüpheli etkinlik üzerinden veya **Yapılandırma** sayfasındaki **Dışlamalar** sekmesinden.

- **Kuşkulu etkinliğin**: bir etkinlikte bir kullanıcı veya bilgisayar veya belirli etkinlik gerçekleştirmesine izin verilen ve sık, bunu yapabilirsiniz IP adresi için bir uyarı aldığınızda, şüpheli etkinlik zaman çizgisi, sağ tıklatın, üç nokta Bu varlık ve select kuşkulu etkinlik için satır sonu **kapatın ve dışlama**. <br></br>Bu kullanıcı, bilgisayar veya IP adresi, şüpheli etkinlik için dışlama listesine ekler. Kuşkulu etkinliği kapatır ve artık listelenen **açık** olaylar listesinde **şüpheli etkinlik zaman çizelgesi**.

    ![Varlık dışlama](./media/exclude-in-sa.png)

- **Yapılandırma sayfasından**: gözden geçirmek veya herhangi Dışlamalar değiştirmek için: altında **yapılandırma**, tıklatın **Dışlamalar** ve şüpheli etkinlik gibi seçin **DNS Keşif**.

    ![Dışlama yapılandırma](./media/exclusions.png)

Bir varlık eklemek için **Dışlamalar** yapılandırma: varlık adı girin ve ardından artı ve ardından **kaydetmek** sayfanın sonundaki.

Bir varlığı **Dışlamalar** yapılandırmasından kaldırmak için: Varlık adının yanındaki eksi işaretine tıklayın ve sayfanın sonundaki **Kaydet** düğmesine basın.

Algılama dışlamalarını yalnızca, aldığınız bir uyarı türünün doğru zararsız pozitif sonuç olduğunu belirlemeniz durumunda eklemeniz önerilir. 

> [!NOTE]
> Güvenliğiniz için, dışlama ayarlama seçeneği algılamaların tamamında sunulmaz. 

Bazı algılamalar, neleri dışlayabileceğinize karar vermeniz için ipuçları sağlar. 

Her dışlama bağlama bağlıdır, diğerleri için bilgisayarları veya IP adresi ayarlayabilirsiniz karşın bazı durumlarda, kullanıcılar ayarlayabilirsiniz. 

Birini veya diğerini - dışlayabilirsiniz bir IP adresi veya bir bilgisayar hariç olanağına sahip olduğunuzda, her ikisi de sağlamanız gerekmez.

> [!NOTE]
> Yapılandırma sayfaları yalnızca Azure ATP yöneticiler tarafından değiştirilebilir.


## <a name="see-also"></a>Ayrıca bkz:

- [Windows Defender ATP ile tümleştirme](integrate-wd-atp.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)