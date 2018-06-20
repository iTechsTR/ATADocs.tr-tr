---
title: Yükleme Azure Gelişmiş tehdit koruması - 5. adım | Microsoft Docs
description: Azure ATP yükleme işleminin beşinci adımı, Azure ATP tek başına algılayıcı için ayarları yapılandırmanıza yardımcı olur.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2017
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: d7c95f8c-04f8-4946-9bae-c27ed362fcb0
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: a2e61758e06aedfe607afc0d3365227af872fe20
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
ms.locfileid: "29446039"
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="install-azure-atp---step-5"></a>Azure ATP - 5. adım yükleme

>[!div class="step-by-step"]
[« 4. Adım](install-atp-step4.md)
[6. Adım »](install-atp-step6-vpn.md)


## <a name="step-5-configure-the-azure-atp-sensor-settings"></a>Adım 5. Azure ATP algılayıcı ayarlarını yapılandırma
Azure ATP algılayıcı yüklendikten sonra Azure ATP algılayıcı ayarlarını yapılandırmak için aşağıdaki adımları gerçekleştirin.

1.  Azure ATP çalışma Portalı'nda Git **yapılandırma** ve altında **sistem**seçin **algılayıcı**.
   
     ![Algılayıcı ayarlarını yapılandırma resmi](media/atp-sensor-config.png)


2.  Aşağıdaki bilgileri girin ve yapılandırmak istediğiniz algılayıcı tıklatın:

    ![Algılayıcı ayarlarını yapılandırma resmi](media/atp-sensor-config-2.png)

  - **Açıklama**: Azure ATP algılayıcısı (isteğe bağlı) için bir açıklama girin.
  - **Etki alanı denetleyicileri (FQDN)** (Azure ATP tek başına algılayıcı için gereken, bu için Azure ATP algılayıcı değiştirilemez): etki alanı denetleyicinizin tam FQDN girin ve listeye eklemek için artı işaretine tıklayın. Örneğin, **dc01.contoso.com**

      Aşağıdaki bilgiler, **Etki Alanı Denetleyicileri** listesine girdiğiniz sunucular için geçerlidir:
      - Tüm etki alanı denetleyicileri, trafiği izlenmekte bağlantı noktası yansıtma yoluyla Azure ATP tek başına algılayıcı tarafından listelenmiş olmalıdır **etki alanı denetleyicileri** listesi. Bir etki alanı denetleyicisi **Etki Alanı Denetleyicileri** listesinde yer almıyorsa, kuşkulu etkinlikleri algılama özelliği beklendiği gibi çalışmayabilir.
      - Listedeki etki alanı denetleyicilerinden en az biri genel katalog olmalıdır. Bu bilgisayar ve kullanıcı nesnelerini ormandaki diğer etki alanlarındaki Azure ATP sağlar.

  - **Yakalama Ağ bağdaştırıcıları** (gerekli):
     - Ayrılmış bir sunucuya bir Azure ATP tek başına algılayıcı için hedef yansıtma bağlantı noktası olarak yapılandırılan ağ bağdaştırıcılarını seçin. Bunlar, yansıtılmış etki alanı denetleyicisi trafiği alırsınız.
     - Bir Azure ATP algılayıcı için bu, kuruluşunuzdaki diğer bilgisayarlarla iletişim için kullanılan tüm ağ bağdaştırıcıları olmalıdır.


  - **Etki alanı Eşitleyici adayı**: bir etki alanı Eşitleyici adayı olarak ayarlanmalıdır herhangi Azure ATP tek başına algılayıcı Azure ATP ve Active Directory etki alanınız arasında eşitlemeden sorumlu olabilir. Etki alanının büyüklüğüne ilk eşitleme biraz zaman alabilir ve yoğun bir kaynak gerçekleşir. Varsayılan olarak, yalnızca Azure ATP tek başına algılayıcılar etki alanı Eşitleyici adayı ayarlanır.
   Etki alanı Eşitleyici adayı engeller herhangi bir uzak site Azure ATP algılayıcı devre dışı bırakmanız önerilir.
   Etki alanı denetleyiciniz salt okunur ise, onu Etki Alanı eşitleyici adayı olarak ayarlamayın. Daha fazla bilgi için bkz: [Azure ATP mimarisi](atp-architecture.md#azure-atp-sensor-features).
  
4. **Kaydet**'e tıklayın.


## <a name="validate-installations"></a>Yüklemeleri doğrulama
Azure ATP algılayıcı başarıyla dağıtıldığını doğrulamak için aşağıdakileri denetleyin:

1.  Adlı hizmetin onay **Azure Advanced Threat Protection algılayıcı** çalışıyor. Azure ATP algılayıcı ayarlarını kaydettikten sonra hizmeti başlatmak için birkaç saniye sürebilir.

2.  Hizmet başlatılmazsa, "%programfiles%\Azure Gelişmiş tehdit koruması sensor\Version X\Logs" aşağıdaki varsayılan klasöründe yer alan "Microsoft.Tri.sensor-Errors.log" dosyasını gözden geçirin.
 
 >[!NOTE]
 > Azure ATP çalışma alanına portalında en son sürümünü denetlemek için sık sık Azure ATP güncelleştirmeleri sürümü Git **yapılandırma** ve ardından **hakkında**. 

3.  Çalışma alanı URL'sine gidin. Çalışma alanı Portalı'nda, bir kullanıcı veya grup, etki alanınızda gibi arama çubuğunda bir şey arayın.



>[!div class="step-by-step"]
[« 4. Adım](install-atp-step4.md)
[6. Adım »](install-atp-step6-vpn.md)


## <a name="see-also"></a>Ayrıca bkz:

- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
