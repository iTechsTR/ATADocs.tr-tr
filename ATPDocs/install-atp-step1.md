---
title: Azure Gelişmiş tehdit Koruması'nı yükleme | Microsoft Docs
description: Azure ATP yüklemenin ilk adımı, Azure ATP dağıtımınız için örneği oluşturmanızı gerektirir.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/4/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 15ee7d0b-9a0c-46b9-bc71-98d0b4619ed0
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 97cce3de3a1cbe049523c54901ecbc9228aaee53
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48783024"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="creating-your-azure-atp-instance-in-the-portal---step-1"></a>Azure ATP örneğinizi oluşturma portalı - 1. adım

> [!div class="step-by-step"]
> [2. Adım »](install-atp-step2.md)

Bu yükleme yordamı, oluşturma ve Azure ATP örneği veya çalışma alanını yönetme için yönergeler sağlar. Azure ATP mimarisi hakkında daha fazla bilgi için bkz. [Azure ATP mimarisi](atp-architecture.md).

Azure ATP tek örnek veya tek bir cam bölmesinden birden çok ormanı yönetmenize olanak sağlayan bir çalışma alanı gerekir. 

> [!NOTE]
> Şu anda Avrupa, Kuzey Amerika/Orta Amerika/Karayipler ve Asya Azure ATP veri merkezlerinde dağıtılır.

## <a name="step-1-enter-the-azure-atp-portal"></a>1. Adım Azure ATP portalı girin

Ağınızı algılayıcı gereksinimlerini karşıladığını doğruladıktan sonra Azure ATP çalışma alanının oluşturulmasını geçebilirsiniz.

> [!NOTE]
>Yönetim Portalı'na erişmek için genel yönetici veya Kiracı güvenlik yöneticisi olmanız gerekir.


1.  Girin [Azure ATP portalı](https://portal.atp.azure.com).

2.  Azure Active Directory kullanıcı hesabınızla oturum açın.

## <a name="step-2-create-your-workspace"></a>2. Adım Çalışma alanınızı oluşturma

1. Tıklayın **çalışma alanı oluşturma**.

2. İçinde **yeni çalışma alanı oluşturma** iletişim kutusunda, çalışma alanınızı adlandırın ve seçin bir **coğrafi konum** veri merkeziniz için. Çalışma alanınız olduğunu **birincil** varsayılan olarak. 
 > [!NOTE]
 > Bir coğrafi konum seçtikten sonra değiştiremezsiniz.
    ![Azure ATP çalışma alanı](media/create-workspace.png)

3. Tıklayabilirsiniz **yönetme Azure ATP kullanıcı rollerini** doğrudan erişmek için bağlantı [Azure Active Directory Yönetim Merkezi](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) ve rol gruplarınızı yönetin.

 > [!NOTE]
 > Azure ATP başarıyla oturum açmak için Azure ATP portalına erişmek için uygun Azure ATP rolünün atandığı bir kullanıcıyla oturum açmalısınız. Azure ATP rol tabanlı access control (RBAC) hakkında daha fazla bilgi için bkz: [Azure ATP rol gruplarıyla çalışma](atp-role-groups.md).

4. Azure ATP portalına erişmek için çalışma alanının adına tıklayın.

    ![Azure ATP çalışma alanları](media/atp-workspaces.png)

- Yalnızca birincil çalışma alanı düzenlenebilir. Birincil çalışma alanınızı silmek istiyorsanız, silinecek açmadan önce tümleştirmeler devre dışı önce etkinleştirmeniz gerekir.

- Veri saklama – daha önce silinmiş çalışma alanları kullanıcı Arabiriminde görünmez. Azure ATP veri saklama hakkında daha fazla bilgi için bkz. [With Azure ATP verilerinin güvenliğine ve gizliliğine](atp-privacy-compliance.md).


>[!div class="step-by-step"]
[« Yükleme öncesi](atp-prerequisites.md)
[2. Adım »](install-atp-step2.md)



## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
