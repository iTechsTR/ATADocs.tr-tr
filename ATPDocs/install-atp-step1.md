---
title: "Yükleme Azure Gelişmiş tehdit koruması - 1. adım | Microsoft Docs"
description: "Azure ATP yüklemek için ilk adım, Azure ATP dağıtımınız için bir çalışma alanı oluşturma içerir."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/11/2018
ms.topic: get-started-article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 15ee7d0b-9a0c-46b9-bc71-98d0b4619ed0
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 5eabf4fc3965e8745b7e2c0fbae4973deb358814
ms.sourcegitcommit: 912e453753156902618ae6ebb8489c2320c06fc6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*


# <a name="creating-a-workspace-in-the-azure-atp-workspace-management-portal---step-1"></a>Azure ATP çalışma Yönetim Portalı'nda - 1. adım bir çalışma alanı oluşturma

>[!div class="step-by-step"]
[2. Adım »](install-atp-step2.md)

Bu yükleme yordamı oluşturmak ve bir çalışma alanı Azure ATP çalışma Yönetim Portalı'nda yönetmek için yönergeler sağlar. Azure ATP mimarisi hakkında daha fazla bilgi için bkz: [Azure ATP mimarisi](atp-architecture.md).

Azure ATP yönetme ve birden çok çalışma izleme olanağına sahip. Bir tanıtım çalışma ve, PT Azure ATP onu sunulmadan önce tüm kuruluşa işlemini test çalışma alanı oluşturmak isterseniz bu özellikle yararlıdır. Bu çok ormanlı dağıtımlar desteklemek için gereklidir. Tek bir çalışma alanı yalnızca tek bir ormandaki birden çok etki alanı izleyebilirsiniz. 

> [!NOTE]
> En fazla iki etkin çalışma alanları olabilir. Bir çalışma alanı sildikten sonra yeniden etkinleştirmek için desteğine başvurabilirsiniz. Bir üç silinen çalışma alanlarının bir mazimum sahip. Kaydedilmiş, silinen çalışma alanları sayısını artırmak için Azure ATP desteğe başvurun.

## <a name="step-1-enter-the-workspace-management-portal"></a>1. Adım Çalışma alanı Yönetim Portalı'nı girin

Ağınız algılayıcı gereksinimleri karşıladığını doğruladıktan sonra Azure ATP çalışma alanı oluşturma ile devam edebilirsiniz.

> [!NOTE]
>Çalışma alanı yönetim portalına erişmek için bir genel yönetici veya Kiracı güvenlik yöneticisi olmanız gerekir.


1.  Girin [Azure ATP çalışma portal](https://portal.atp.azure.com).

2.  En azından okuma erişimi izlenen etki alanlarındaki tüm nesnelere, şirket içi Azure Active Directory kullanıcı hesabıyla oturum açın.

## <a name="step-2-create-a-workspace"></a>2. Adım Çalışma alanı oluşturma

1. Tıklatın **çalışma alanı oluşturma**.

2. İçinde **yeni çalışma alanı oluşturma** iletişim kutusunda, çalışma alanınızı adlandırın, onu birincil çalışma alanınız olup olmadığını karar verin ve seçin bir **coğrafi konuma** , veri merkezi için. Yalnızca bir çalışma alanı birincil olarak ayarlanabilir. Bir çalışma alanı birincil tümleştirmeler etkiler - yalnızca Azure ATP Windows Defender ATP için birincil çalışma alanınızda tümleştirebilirsiniz olarak ayarlanıyor. Hangi çalışma alanının birincil daha sonra geçerli birincil çalışma alanı için zaten ayarlanmış tümleştirmeler kaldırmak zorunda şekilde yapmak amacıyla ancak olduğunu değiştirebilirsiniz.
 > [!NOTE]
 > Bir coğrafi konum seçtikten sonra değiştiremezsiniz.
    ![Azure ATP çalışma](media/create-workspace.png)

3. Tıklayabilirsiniz **yönetmek Azure ATP kullanıcı rolleri** doğrudan erişmek için bağlantı [Azure Active Directory Yönetim Merkezi](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) ve rol gruplarını yönetin.

 > [!NOTE]
 > Azure ATP başarıyla oturum açmak için Azure ATP çalışma portalına erişmek için uygun Azure ATP rolü atanmış bir kullanıcıyla oturum gerekir. Rol tabanlı erişim denetimi (RBAC) Azure ATP hakkında daha fazla bilgi için bkz: [Azure ATP rol gruplarıyla çalışma](atp-role-groups.md).

4. Bu çalışma alanı için yeni çalışma erişim Azure ATP çalışma portal adını tıklatın.

    ![Azure ATP çalışma alanları](media/atp-workspaces.png)

- Yalnızca birincil çalışma düzenlenebilir. Diğer çalışma alanları için değişiklik yapmak için bunları silin ve yeniden ekleyin. Birincil çalışma silmek istiyorsanız, öncelikle tümleştirmeler devre dışı bırakma ve olmaması için çalışma kümesi **birincil** silinecek açmadan önce.
- Birincil bir çalışma alanı düzenlemek için önce varolan tümleştirmeler çalışma alanında kapatmanız gerekir.

- Veri saklama – silinen çalışma alanları görünmez kullanıcı Arabiriminde verilerine göre tutulur ancak [Microsoft Veri Bekletme İlkesi](https://www.microsoft.com/trustcenter/privacy/you-own-your-data).


>[!div class="step-by-step"]
[« Yükleme öncesi](configure-port-mirroring.md)
[2. Adım »](install-atp-step2.md)


## <a name="see-also"></a>Ayrıca bkz:
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
