---
title: Yükleme Azure Gelişmiş tehdit koruması - 5. adım | Microsoft Docs
description: Azure ATP yükleme işleminin beşinci adımı, Azure ATP tek başına algılayıcı için ayarları yapılandırmanıza yardımcı olur.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/12/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: d7c95f8c-04f8-4946-9bae-c27ed362fcb0
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 05355460ec8dac4febc24096e802135cf52e1cc8
ms.sourcegitcommit: dc56b9e9533db1a2dc314b199e90191bb25adaba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/14/2018
ms.locfileid: "41734785"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="install-azure-atp---step-5"></a>Azure ATP - 5. Adım'ı yükleme

>[!div class="step-by-step"]
[« 4. Adım](install-atp-step4.md)
[6. Adım »](install-atp-step6-vpn.md)


## <a name="step-5-configure-the-azure-atp-sensor-settings"></a>Adım 5. Azure ATP algılayıcısı ayarlarını yapılandırma
Azure ATP algılayıcısını yüklendikten sonra Azure ATP algılayıcısını ayarlarını yapılandırmak için aşağıdaki adımları gerçekleştirin.

1.  Azure ATP çalışma alanı Portalı'nda Git **yapılandırma** ve altında **sistem**seçin **algılayıcı**.
   
     ![Algılayıcı ayarlarını yapılandırma resmi](media/atp-sensor-config.png)


2.  Üzerinde aşağıdaki bilgileri girin ve yapılandırmak istediğiniz algılayıcı tıklayın:

    ![Algılayıcı ayarlarını yapılandırma resmi](media/atp-sensor-config-2.png)

  - **Açıklama**: (isteğe bağlı) Azure ATP algılayıcısını için bir açıklama girin.
  - **Etki alanı denetleyicileri (FQDN)** (tek başına Azure ATP algılayıcısını için gerekli, bu Azure ATP algılayıcısını için değiştirilemez): etki alanı denetleyicinizin tam FQDN'sini girin ve listeye eklemek için artı işaretine tıklayın. Örneğin, **dc01.contoso.com**

      Aşağıdaki bilgiler, **Etki Alanı Denetleyicileri** listesine girdiğiniz sunucular için geçerlidir:
      - Tüm etki alanı denetleyicileri, trafiği izlenmekte bağlantı noktası yansıtma yoluyla Azure ATP tek başına algılayıcı tarafından yer alması gerekir **etki alanı denetleyicileri** listesi. Bir etki alanı denetleyicisi **Etki Alanı Denetleyicileri** listesinde yer almıyorsa, kuşkulu etkinlikleri algılama özelliği beklendiği gibi çalışmayabilir.
      - Listedeki etki alanı denetleyicilerinden en az biri genel katalog olmalıdır. Bu bilgisayar ve kullanıcı nesneleri ormanındaki diğer etki alanlarındaki gidermek Azure ATP sağlar.

  - **Yakalama Ağ bağdaştırıcıları** (gerekli):
     - Ayrılmış bir sunucuya bir Azure ATP tek başına algılayıcı için hedef yansıtma bağlantı noktası olarak yapılandırılan ağ bağdaştırıcılarını seçin. Bunlar, yansıtılmış etki alanı denetleyicisi trafiği alır.
     - Bir Azure ATP algılayıcısını için bu, kuruluşunuzdaki diğer bilgisayarlarla iletişim için kullanılan tüm ağ bağdaştırıcıları olmalıdır.

    - **Etki alanı Eşitleyici adayı**: herhangi bir Azure ATP tek başına algılayıcı bir etki alanı Eşitleyici adayı olarak ayarlanmalıdır, Azure ATP ile Active Directory etki alanınız arasında eşitlemeden sorumlu olabilir. Etki alanının büyüklüğüne ilk eşitleme biraz zaman alabilir ve yoğun kaynak sahiptir. Varsayılan olarak, yalnızca Azure ATP tek başına algılayıcı etki alanı Eşitleyici adayı olarak ayarlanır.
   Etki alanı Eşitleyici adayı engeller herhangi bir uzak site Azure ATP algılayıcısını devre dışı bırakmanız önerilir.
   Etki alanı denetleyiciniz salt okunur ise, onu Etki Alanı eşitleyici adayı olarak ayarlamayın. Daha fazla bilgi için [Azure ATP mimarisi](atp-architecture.md#azure-atp-sensor-features).
  
4. **Kaydet**'e tıklayın.


## <a name="validate-installations"></a>Yüklemeleri doğrulama
Azure ATP algılayıcısını başarıyla dağıtıldığını doğrulamak için aşağıdakileri denetleyin:

1.  Adlı hizmetin onay **Azure Gelişmiş tehdit koruması algılayıcı** çalışıyor. Azure ATP algılayıcısı ayarlar kaydedildikten sonra hizmeti başlatmak için birkaç saniye sürebilir.

2.  Hizmet başlatılmazsa, "%programfiles%\Azure Gelişmiş tehdit koruması sensor\Version X\Logs" aşağıdaki varsayılan klasörde bulunan "Microsoft.Tri.sensor-Errors.log" dosyasını gözden geçirin.
 
 >[!NOTE]
 > Azure ATP çalışma alanı portalında, en son sürümünü denetlemek için sık sık Azure ATP güncelleştirmelerin sürümünü Git **yapılandırma** ardından **hakkında**. 

3.  Çalışma alanı URL'nizi gidin. Çalışma alanı Portalı'nda, arama çubuğunda, bir kullanıcı veya etki alanınızdaki Grup gibi bir şey arayın.



>[!div class="step-by-step"]
[« 4. Adım](install-atp-step4.md)
[6. Adım »](install-atp-step6-vpn.md)


## <a name="see-also"></a>Ayrıca Bkz.

- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
