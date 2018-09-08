---
title: Varlıkları Azure Gelişmiş tehdit koruması, algılamalardan dışlama | Microsoft Docs
description: Azure ATP belirli varlık etkinliklerini şüpheli olarak algılamasını durdurmak açıklar
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/2/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: cae3ed45-8fbc-4f25-ba24-3cc407c6ea93
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: d5ac2ae53dfe13b850a06f6dd4b89a91ffedd946
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44166043"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="excluding-entities-from-detections"></a>Varlıkları algılamalardan dışlama
Bu makalede, doğru zararsız pozitif sonuçları en aza indirmek, ancak aynı zamanda doğru pozitif sonuçları yakalamak emin olmak için uyarılar tetiklemesini önlemek varlıkları açıklanmaktadır. Azure ATP, belirli kullanıcılar tarafından normal ritmi iş parçası olabilecek etkinlikleri hakkında gürültülü engellemek için quiet - edebilir veya hariç tutabilirsiniz - belirli varlıkların uyarılarını susturabilir.

Örneğin, kuruluşunuzdaki rutin BT işlemleri gereği DNS keşfi yapan bir güvenlik tarayıcınız veya etki alanı denetleyicisinde uzaktan betik çalıştıran bir yöneticiniz varsa (ve bunlar tasdikli eylemlerse) bu özelliğe ihtiyaç duyabilirsiniz. Hangi varlıkları dışlamak için karar vermenize yardımcı olacak Azure ATP algılamalar hakkında daha fazla bilgi için bkz: [şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md).

Azure ATP uyarıları göndermesini engelleme varlıkları dışlamak için:

Varlıkları dışlamak için iki yol vardır: Doğrudan şüpheli etkinlik üzerinden veya **Yapılandırma** sayfasındaki **Dışlamalar** sekmesinden.

- **Şüpheli etkinlik**: bir kullanıcı veya bilgisayar veya belirli etkinlik gerçekleştirmesine izin verilen ve sık sık, bunu yapabilirsiniz, IP adresi için bir etkinlik hakkında uyarı aldığınızda, şüpheli etkinlik zaman çizelgesi, üç noktaya sağ tıklayın Bu varlık ve select kuşkulu etkinlik için bir satır sonu **Kapat ve dışla**. <br></br>Bu kullanıcı, bilgisayar veya IP adresini bu şüpheli etkinliğin Dışlamalar listesine ekler. Şüpheli etkinlik kapatır ve artık listelenen **açık** olayları listeyi **şüpheli etkinlik zaman çizelgesi**.

    ![Varlık dışlama](./media/exclude-in-sa.png)

- **Yapılandırma sayfasından**: gözden geçirmek veya herhangi bir özel değiştirmek için: altında **yapılandırma**, tıklayın **dışlamaları** ve şüpheli etkinlik gibi ardından **DNS Keşif**.

    ![Dışlama yapılandırma](./media/exclusions.png)

Bir varlık eklemek için **dışlamaları** yapılandırma: varlık adını girin ve ardından artı işaretine tıklayın ve ardından **Kaydet** sayfanın alt kısmındaki.

Bir varlığı **Dışlamalar** yapılandırmasından kaldırmak için: Varlık adının yanındaki eksi işaretine tıklayın ve sayfanın sonundaki **Kaydet** düğmesine basın.

Algılama dışlamalarını yalnızca, aldığınız bir uyarı türünün doğru zararsız pozitif sonuç olduğunu belirlemeniz durumunda eklemeniz önerilir. 

> [!NOTE]
> Güvenliğiniz için, dışlama ayarlama seçeneği algılamaların tamamında sunulmaz. 

Bazı algılamalar, neleri dışlayabileceğinize karar vermeniz için ipuçları sağlar. 

Her dışlama bağlam üzerinde bağlıdır, diğerleri için bilgisayar veya IP adresleri ayarlayabilirsiniz ancak bazı durumlarda kullanıcılar ayarlayabilirsiniz. 

Birini veya diğerini - hariç tutabilirsiniz bir IP adresi veya bilgisayar dışlama seçeneğiniz varsa, her ikisi de sağlamanız gerekmez.

> [!NOTE]
> Yapılandırma sayfaları yalnızca Azure ATP yöneticileri tarafından değiştirilebilir.


## <a name="see-also"></a>Ayrıca Bkz.

- [Windows Defender ATP ile tümleştirme](integrate-wd-atp.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)