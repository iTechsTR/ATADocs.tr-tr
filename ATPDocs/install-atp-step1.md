---
title: Yükleme Azure Gelişmiş tehdit koruması - 1. adım | Microsoft Docs
description: Azure ATP yüklemenin ilk adımı, Azure ATP dağıtımınız için bir çalışma alanı oluşturmayı içerir.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/10/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 15ee7d0b-9a0c-46b9-bc71-98d0b4619ed0
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: cadd708c20733324b939db1e35d12aae3f2d80f2
ms.sourcegitcommit: 40dbce8045f689376a50275fb12e3c5c32ca8092
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/04/2018
ms.locfileid: "37799085"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="creating-a-workspace-in-the-azure-atp-workspace-management-portal---step-1"></a>Azure ATP çalışma alanı Yönetim Portalı'nda - 1. adım bir çalışma alanı oluşturma

>[!div class="step-by-step"]
[2. Adım »](install-atp-step2.md)

Bu yükleme yordamı, oluşturma ve Azure ATP çalışma alanı yönetim portalında bir çalışma alanı yönetme için yönergeler sağlar. Azure ATP mimarisi hakkında daha fazla bilgi için bkz. [Azure ATP mimarisi](atp-architecture.md).

Azure ATP yönetme ve birden çok çalışma alanı izleme olanağına sahip. Bir tanıtım ve bir test çalışma, PT Azure ATP bunu sunulmadan önce tüm kuruluşunuza işlemini oluşturmak istiyorsanız bu özellikle yararlıdır. Bu çok ormanlı dağıtımlar desteklemek için gereklidir. Tek bir çalışma alanı, yalnızca birden çok etki alanından tek bir ormana izleyebilirsiniz. 

> [!NOTE]
> Şu anda Avrupa, Kuzey Amerika/Orta Amerika/Karayipler ve Asya Azure ATP veri merkezlerinde dağıtılır.

## <a name="step-1-enter-the-workspace-management-portal"></a>1. Adım Çalışma alanı Yönetim Portalı'nı girin

Ağınızı algılayıcı gereksinimlerini karşıladığını doğruladıktan sonra Azure ATP çalışma alanının oluşturulmasını geçebilirsiniz.

> [!NOTE]
>Çalışma alanı yönetim portalına erişmek için genel yönetici veya Kiracı güvenlik yöneticisi olmanız gerekir.


1.  Girin [Azure ATP çalışma alanı portalı](https://portal.atp.azure.com).

2.  Azure Active Directory kullanıcı hesabınızla oturum açın.

## <a name="step-2-create-a-workspace"></a>2. Adım Çalışma alanı oluşturma

1. Tıklayın **çalışma alanı oluşturma**.

2. İçinde **yeni çalışma alanı oluşturma** iletişim kutusunda, çalışma alanınızı adlandırın, karar, birincil çalışma alanınız olup olmadığını ve seçin bir **coğrafi konum** veri merkeziniz için. Yalnızca bir çalışma, birincil olarak ayarlanabilir. Bir çalışma alanı, birincil tümleştirmeler etkiler - yalnızca Azure ATP Windows Defender ATP ile birincil çalışma alanınız için tümleştirebilirsiniz olarak ayarlanıyor. Hangi çalışma alanının birincil daha sonra kaldırmak için geçerli birincil çalışma alanı zaten ayarlanmış herhangi tümleştirmeler gerekmez, ancak yapmak üzere olduğunu değiştirebilirsiniz.
 > [!NOTE]
 > Bir coğrafi konum seçtikten sonra değiştiremezsiniz.
    ![Azure ATP çalışma alanı](media/create-workspace.png)

3. Tıklayabilirsiniz **yönetme Azure ATP kullanıcı rollerini** doğrudan erişmek için bağlantı [Azure Active Directory Yönetim Merkezi](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) ve rol gruplarınızı yönetin.

 > [!NOTE]
 > Azure ATP başarıyla oturum açmak için Azure ATP çalışma alanı portalına erişmek için uygun Azure ATP rolünün atandığı bir kullanıcıyla oturum açmalısınız. Azure ATP rol tabanlı access control (RBAC) hakkında daha fazla bilgi için bkz: [Azure ATP rol gruplarıyla çalışma](atp-role-groups.md).

4. Bu çalışma alanı için yeni çalışma alanı erişimi Azure ATP çalışma alanı portalı adına tıklayın.

    ![Azure ATP çalışma alanları](media/atp-workspaces.png)

- Yalnızca birincil çalışma alanı düzenlenebilir. Diğer çalışma alanlarında değişiklik yapmak için bunları silin ve yeniden ekleyin. Birincil çalışma alanını silmek istiyorsanız, önce tümleştirmeler devre dışı açmak ve olmaması için çalışma alanını ayarlamanız gerekir **birincil** silinecek açmadan önce.
- Birincil bir çalışma alanı düzenlemek için önce mevcut tümleştirme çalışma alanında kapatmanız gerekir.

- Veri saklama – silinmiş çalışma alanları kullanıcı Arabiriminde görünmez. Azure ATP veri saklama hakkında daha fazla bilgi için bkz. [With Azure ATP verilerinin güvenliğine ve gizliliğine](atp-privacy-compliance.md).


>[!div class="step-by-step"]
[« Yükleme öncesi](configure-port-mirroring.md)
[2. Adım »](install-atp-step2.md)


## <a name="see-also"></a>Ayrıca bkz:
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
