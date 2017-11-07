---
title: "Advanced Threat Analytics’te varlıkları algılamalardan dışlama | Microsoft Docs"
description: "ATA’nın belirli varlık etkinliklerini şüpheli olarak algılamasını nasıl engelleyeceğinizi açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 344c0f33-45e1-42e2-a051-f722a4504531
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: c185060a4fb889121c6a02b353fb0d176f0c9274
ms.sourcegitcommit: e2cb3af9c1dbb0b75946dc70cc439b19d654541c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="excluding-entities-from-detections"></a>Varlıkları algılamalardan dışlama
Bu konuda, doğru zararsız pozitif sonuçları olabildiğince azaltmak ve aynı zamanda doğru pozitif sonuçları yakalamak için varlıkların uyarı tetiklemesini nasıl engelleyeceğiniz açıklanmaktadır. Belirli kullanıcılar tarafından normal iş düzeninize uygun olarak gerçekleştirilen etkinlikler konusunda ATA’nın sizi gereksiz yere rahatsız etmesini önlemek için, seçtiğiniz varlıkların uyarılarını susturabilir veya dışlayabilirsiniz.

Örneğin, kuruluşunuzdaki rutin BT işlemleri gereği DNS keşfi yapan bir güvenlik tarayıcınız veya etki alanı denetleyicisinde uzaktan betik çalıştıran bir yöneticiniz varsa (ve bunlar tasdikli eylemlerse) bu özelliğe ihtiyaç duyabilirsiniz.

Varlıkların ATA’da uyarı tetiklemesini engellemek için:

Varlıkları dışlamak için iki yol vardır: Doğrudan şüpheli etkinlik üzerinden veya **Yapılandırma** sayfasındaki **Dışlamalar** sekmesinden.

- **Şüpheli etkinlik üzerinden**: Şüpheli etkinlik zaman çizelgesinde bir kullanıcı, bilgisayar veya IP adresinin izinli olduğu ve sık sık gerçekleştirebileceği bir etkinlik hakkında uyarı aldığınızda, bu varlığa ait şüpheli etkinliğin bulunduğu satırın sonundaki üç nokta simgesine tıklayıp **Kapat ve dışla**’yı seçin. <br></br>Böylelikle bu kullanıcı, bilgisayar veya IP adresini bu şüpheli etkinliğin dışlamalar listesine eklemiş olursunuz. Ayrıca şüpheli etkinliği kapattığınız için etkinlik, **Şüpheli etkinlik zaman çizelgesi**’ndeki **Açık** olaylar listesinden de kaldırılır.

    ![Varlık dışlama](./media/exclude-in-sa.png)

- **Yapılandırma sayfasından**: Ayarladığınız dışlamaları gözden geçirmek veya değiştirmek için: **Yapılandırma** altında bulunan **Dışlamalar**’a tıklayın ve şüpheli etkinliği (örneğin, **Gizli hesap kimlik bilgileri açığa çıkarıldı**) seçin.

    ![Dışlama yapılandırma](./media/exclusions-config-page.png)

Bir varlığı **Dışlamalar** yapılandırmasından kaldırmak için: Varlık adının yanındaki eksi işaretine tıklayın ve sayfanın sonundaki **Kaydet** düğmesine basın.

Algılama dışlamalarını yalnızca, aldığınız bir uyarı türünün doğru zararsız pozitif sonuç olduğunu belirlemeniz durumunda eklemeniz önerilir. 

> [!NOTE]
> Güvenliğiniz için, dışlama ayarlama seçeneği algılamaların tamamında sunulmaz. 

Bazı algılamalar, neleri dışlayabileceğinize karar vermeniz için ipuçları sağlar. 

Her dışlama, bağlama göre değişen özellikler taşır. Bazılarında kullanıcı ayarlayabilir, bazılarında ise bilgisayar veya IP adresleri ayarlayabilirsiniz. 

Bir IP adresi veya bilgisayar dışlama seçeneğiniz varsa, bunlardan yalnızca birini dışlamanız yeterlidir.

> [!NOTE]
> Yapılandırma sayfaları yalnızca ATA yöneticileri tarafından değiştirilebilir.


## <a name="see-also"></a>Ayrıca bkz:
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [ATA yapılandırmasında değişiklik yapma](modifying-ata-center-configuration.md)
