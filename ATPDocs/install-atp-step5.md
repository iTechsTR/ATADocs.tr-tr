---
title: Azure Gelişmiş tehdit Koruması'nı yükleme | Microsoft Docs
description: Azure ATP yükleme işleminin beşinci adımı, Azure ATP tek başına algılayıcı için ayarları yapılandırmanıza yardımcı olur.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: d7c95f8c-04f8-4946-9bae-c27ed362fcb0
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 6f65b3af56e683a385f7128a989170c8c4073b3e
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48783874"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="install-azure-atp---step-5"></a>Azure ATP - 5. Adım'ı yükleme

> [!div class="step-by-step"]
> [«4. adım](install-atp-step4.md)



## <a name="step-5-configure-the-azure-atp-sensor-settings"></a>Adım 5. Azure ATP algılayıcısı ayarlarını yapılandırma
Azure ATP algılayıcısını yüklendikten sonra Azure ATP algılayıcısı ayarlarını yapılandırmak için aşağıdaki adımları gerçekleştirin.

1.  Azure ATP portalında Git **yapılandırma** ve altında **sistem**seçin **algılayıcı**.
   
     ![Algılayıcı ayarlarını yapılandırma resmi](media/atp-sensor-config.png)


2.  Üzerinde aşağıdaki bilgileri girin ve yapılandırmak istediğiniz algılayıcı tıklayın:

    ![Algılayıcı ayarlarını yapılandırma resmi](media/atp-sensor-config-2.png)

  - **Açıklama**: (isteğe bağlı) Azure ATP algılayıcısını için bir açıklama girin.
  - **Etki alanı denetleyicileri (FQDN)** (tek başına Azure ATP algılayıcısını için gerekli, bu Azure ATP algılayıcısını için değiştirilemez): etki alanı denetleyicinizin tam FQDN'sini girin ve listeye eklemek için artı işaretine tıklayın. Örneğin, **dc01.contoso.com**

      Aşağıdaki bilgiler, **Etki Alanı Denetleyicileri** listesine girdiğiniz sunucular için geçerlidir:
      - Tüm etki alanı denetleyicileri, trafiği izlenmekte bağlantı noktası yansıtma yoluyla Azure ATP tek başına algılayıcı tarafından yer alması gerekir **etki alanı denetleyicileri** listesi. Bir etki alanı denetleyicisi **Etki Alanı Denetleyicileri** listesinde yer almıyorsa, kuşkulu etkinlikleri algılama özelliği beklendiği gibi çalışmayabilir.
      - Listedeki etki alanı denetleyicilerinden en az biri genel katalog olmalıdır. Bu bilgisayar ve kullanıcı nesneleri ormanındaki diğer etki alanlarındaki gidermek Azure ATP sağlar.

  - **Yakalama Ağ bağdaştırıcıları** (gerekli):
   
     - Bir Azure ATP algılayıcısını için bu, kuruluşunuzdaki diğer bilgisayarlarla iletişim için kullanılan tüm ağ bağdaştırıcıları olmalıdır.
    - Ayrılmış bir sunucuya bir Azure ATP tek başına algılayıcı için hedef yansıtma bağlantı noktası olarak yapılandırılan ağ bağdaştırıcılarını seçin. Bunlar, yansıtılmış etki alanı denetleyicisi trafiği alır.

    - **Etki alanı Eşitleyici adayı**: Azure ATP tek başına algılayıcı olsa da varsayılan olarak, Azure ATP algılayıcı etki alanı Eşitleyici adayı değildir. El ile bir Azure ATP algılayıcısını bir etki alanı syncronizer adayı olarak seçmek için geçiş **etki alanı Eşitleyici adayı** Değiştir seçeneğini **ON** yapılandırma ekranında. 
    
        Etki alanı Eşitleyicisi Azure ATP ile Active Directory etki alanınız arasında eşitlemeden sorumlu. Etki alanının büyüklüğüne ilk eşitleme biraz zaman alabilir ve yoğun kaynak sahiptir. 
   Herhangi bir uzak site etki alanı Eşitleyici adayı engeller Azure ATP sensor(s) devre dışı bırakmanız önerilir.
   Etki alanı denetleyiciniz salt okunur ise, bir etki alanı Eşitleyici adayı olarak ayarlamayın. Azure ATP etki alanı eşitleme hakkında daha fazla bilgi için bkz: [Azure ATP mimarisi](atp-architecture.md#azure-atp-sensor-features)
  
4. **Kaydet**'e tıklayın.


## <a name="validate-installations"></a>Yüklemeleri doğrulama
Azure ATP algılayıcısını başarıyla dağıtıldığını doğrulamak için aşağıdakileri denetleyin:

1.  Adlı hizmetin onay **Azure Gelişmiş tehdit koruması algılayıcı** çalışıyor. Azure ATP algılayıcısı ayarlar kaydedildikten sonra hizmeti başlatmak için birkaç saniye sürebilir.

2.  Hizmet başlatılmazsa, "%programfiles%\Azure Gelişmiş tehdit koruması sensor\Version X\Logs" aşağıdaki varsayılan klasörde bulunan "Microsoft.Tri.sensor-Errors.log" dosyasını gözden geçirin.
 
 >[!NOTE]
 > Azure ATP portalında, en son sürümünü denetlemek için sık sık Azure ATP güncelleştirmelerin sürümünü Git **yapılandırma** ardından **hakkında**. 

3.  Çalışma alanı URL'nizi gidin. Azure ATP Portalı'nda, arama çubuğunda, bir kullanıcı veya etki alanınızdaki Grup gibi bir şey arayın.



> [!div class="step-by-step"]
> [«4. adım](install-atp-step4.md)



## <a name="see-also"></a>Ayrıca Bkz.

- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
