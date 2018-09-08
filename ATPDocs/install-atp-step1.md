---
title: Yükleme Azure Gelişmiş tehdit koruması - 1. adım | Microsoft Docs
description: Azure ATP yüklemenin ilk adımı, Azure ATP dağıtımınız için örneği oluşturmanızı gerektirir.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 9/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 15ee7d0b-9a0c-46b9-bc71-98d0b4619ed0
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 6f44bbf50cff2e983a7ddb1ef1cf54ebaf928741
ms.sourcegitcommit: 7f3ded32af35a433d4b407009f87cfa6099f8edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44126238"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="creating-a-workspace-in-the-azure-atp-workspace-management-portal---step-1"></a>Azure ATP çalışma alanı Yönetim Portalı'nda - 1. adım bir çalışma alanı oluşturma

>[!div class="step-by-step"]
[2. Adım »](install-atp-step2.md)

Bu yükleme yordamı, oluşturma ve Azure ATP örneğinizin yönetme için yönergeler sağlar. Azure ATP mimarisi hakkında daha fazla bilgi için bkz. [Azure ATP mimarisi](atp-architecture.md).

Azure ATP içinde tek bir çalışma alanı veya birden çok orman, tek bir cam bölmesinden yönetmenize olanak tanıyan örneği gerekir. 

> [!NOTE]
> Şu anda Avrupa, Kuzey Amerika/Orta Amerika/Karayipler ve Asya Azure ATP veri merkezlerinde dağıtılır.

## <a name="step-1-enter-the-management-portal"></a>1. Adım Yönetim Portalı'nı girin

Ağınızı algılayıcı gereksinimlerini karşıladığını doğruladıktan sonra Azure ATP çalışma alanının oluşturulmasını geçebilirsiniz.

> [!NOTE]
>Yönetim Portalı'na erişmek için genel yönetici veya Kiracı güvenlik yöneticisi olmanız gerekir.


1.  Girin [Azure ATP portalı](https://portal.atp.azure.com).

2.  Azure Active Directory kullanıcı hesabınızla oturum açın.

## <a name="step-2-create-your-workspace"></a>2. Adım Çalışma alanınızı oluşturma

1. Tıklayın **çalışma alanı oluşturma**.

2. İçinde **yeni çalışma alanı oluşturma** iletişim kutusunda, çalışma alanınızı adlandırın ve seçin bir **coğrafi konum** veri merkeziniz için. Yalnızca bir çalışma, birincil olarak ayarlanabilir. Bir çalışma alanı, birincil tümleştirmeler etkiler - yalnızca Azure ATP Windows Defender ATP ile birincil çalışma alanınız için tümleştirebilirsiniz olarak ayarlanıyor. Hangi çalışma alanının birincil daha sonra kaldırmak için geçerli birincil çalışma alanı zaten ayarlanmış herhangi tümleştirmeler gerekmez, ancak yapmak üzere olduğunu değiştirebilirsiniz.
 > [!NOTE]
 > Bir coğrafi konum seçtikten sonra değiştiremezsiniz.
    ![Azure ATP çalışma alanı](media/create-workspace.png)

3. Tıklayabilirsiniz **yönetme Azure ATP kullanıcı rollerini** doğrudan erişmek için bağlantı [Azure Active Directory Yönetim Merkezi](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) ve rol gruplarınızı yönetin.

 > [!NOTE]
 > Azure ATP başarıyla oturum açmak için Azure ATP çalışma alanı portalına erişmek için uygun Azure ATP rolünün atandığı bir kullanıcıyla oturum açmalısınız. Azure ATP rol tabanlı access control (RBAC) hakkında daha fazla bilgi için bkz: [Azure ATP rol gruplarıyla çalışma](atp-role-groups.md).

4. Bu çalışma alanı için Azure ATP çalışma alanı portalına erişmek için yeni çalışma alanının adına tıklayın.

    ![Azure ATP çalışma alanları](media/atp-workspaces.png)

- Yalnızca birincil çalışma alanı düzenlenebilir. Diğer çalışma alanlarında değişiklik yapmak için bunları silin ve yeniden ekleyin. Birincil çalışma alanını silmek istiyorsanız, önce tümleştirmeler devre dışı açmak ve olmaması için çalışma alanını ayarlamanız gerekir **birincil** silinecek açmadan önce.
- Birincil bir çalışma alanı düzenlemek için önce mevcut tümleştirme çalışma alanında kapatmanız gerekir.

- Veri saklama – silinmiş çalışma alanları kullanıcı Arabiriminde görünmez. Azure ATP veri saklama hakkında daha fazla bilgi için bkz. [With Azure ATP verilerinin güvenliğine ve gizliliğine](atp-privacy-compliance.md).


>[!div class="step-by-step"]
[« Yükleme öncesi](configure-port-mirroring.md)
[2. Adım »](install-atp-step2.md)


## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
