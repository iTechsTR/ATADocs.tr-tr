---
title: Azure Gelişmiş tehdit koruması Gelişmiş Denetim İlkesi denetimi | Microsoft Docs
description: Bu makalede, Azure ATP'ın gelişmiş denetim ilkesi onay genel bir bakış sağlar.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 9/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: ab1e8dd9-a6c2-4c68-89d5-343b8ec56142
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: d54bfa71c2f587450fe7c68aaca1e721356c11d7
ms.sourcegitcommit: 8e80f59409c65e7d8d60ec7de8b96b621795699a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47168544"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="azure-atp-advanced-audit-policy-check"></a>Azure ATP Gelişmiş Denetim İlkesi denetimi

Azure ATP algılama üzerinde belirli Windows için olay günlüklerini görünürlük NTLM oturum açma, güvenlik grubu değişiklikleri ve benzer olaylar gibi belirli senaryolarda kullanır. Doğru olaylar denetlenir ve Windows olay günlüğüne dahil doğru Gelişmiş Denetim İlkesi ayarları etki alanı denetleyicilerinizin gerektirir. Gelişmiş Denetim İlkesi ayarları yanlış, eksik Azure ATP kapsam içinde kritik olay günlükleri ve sonuç dışında bırakın.

Azure ATP, her bir etki alanı denetleyicisinin Gelişmiş denetim ilkesinin geçerli durumunu doğrulamak kolaylaştırmak için var olan gelişmiş denetim ilkeleri ve sorunların sistem durumu uyarıları değişikliği gerektiren bir ilke ayarları için otomatik olarak denetler. Her sistem durumu Uyarısı, etki alanı denetleyicisi, sorunlu İlkesi yanı sıra düzeltme önerileri belirli ayrıntılar sağlar.

![Gelişmiş Denetim İlkesi sistem durumu Uyarısı](media/atp-health-alert-audit-policy.png)


Gelişmiş Güvenlik denetleme ilkesi üzerinden etkinleştirilir **varsayılan etki alanı denetleyicileri İlkesi** GPO. Bu denetim olayları, etki alanı denetleyicisinin Windows olaylarına kaydedilir. 



<br>Gelişmiş denetim ilkeleri aşağıdaki yönergeleri kullanarak etki alanı denetleyicinizin değiştirin:

1. Oturum açma olarak sunucuya **etki alanı yöneticisi**.
2. Grup İlkesi Yönetimi Düzenleyicisi'nde yük **Sunucu Yöneticisi'ni** > **Araçları** > **Grup İlkesi Yönetimi**. 
3. Genişletin **etki alanı denetleyicileri kuruluş birimleri**, sağ tıklayın **varsayılan etki alanı denetleyicileri İlkesi** seçip **Düzenle**. 

    ![Etki alanı denetleyicisi ilkesi Düzenle](media/atp-advanced-audit-policy-check-step-1.png)

4. Açılır penceresinden Git **Bilgisayar Yapılandırması** > **ilkeleri** > **Windows ayarları**  >  **Güvenlik ayarları** > **Gelişmiş denetim ilkesi yapılandırmasını**.

    ![Gelişmiş Denetim İlkesi Yapılandırması](media/atp-advanced-audit-policy-check-step-2.png)

5. Çift tıklayın, hesap oturum açma için Git **kimlik bilgisi doğrulamayı denetleme** seçip **aşağıdaki denetim olaylarını Yapılandır** hem başarılı ve başarısız olaylar için. 

    ![Kimlik bilgileri doğrulaması](media/atp-advanced-audit-policy-check-step-3.png)

6. Hesap Yönetimi'ne gidin, çift tıklayın **güvenlik grubu yönetimini denetleme** seçip **aşağıdaki denetim olaylarını Yapılandır** hem başarılı ve başarısız olaylar için.

    ![Güvenlik Grubu Yönetimini Denetleme](media/atp-advanced-audit-policy-check-step-4.png)

> [!NOTE]
> - Yerel ilke kullanmayı seçerseniz, eklediğinizden emin olun **hesap oturumu açma** ve **hesap yönetimi** denetim günlükleri, yerel ilke. Gelişmiş Denetim İlkesi yapılandırıyorsanız, zorlamak emin olun [denetim ilkesi alt kategorisi](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/audit-force-audit-policy-subcategory-settings-to-override).

7. GPO uygulandıktan sonra yeni olayları altında görünür, **Windows olay günlükleri**.

## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
