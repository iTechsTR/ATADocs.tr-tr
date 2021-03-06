---
title: Azure Gelişmiş tehdit Koruması'nı yükleme | Microsoft Docs
description: Azure ATP yükleme üç adım Azure ATP algılayıcısı Kurulum paketini indirmelisiniz yardımcı olur.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 95bb4ec1-841f-41b7-92fe-fbd144085724
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 5a9eea9550af90577ad1763384a134f5889edc5f
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48783789"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="install-azure-atp---step-3"></a>Azure ATP - 3. Adım'ı yükleme

> [!div class="step-by-step"]
> [« 2. Adım](install-atp-step2.md)
> [4. Adım »](install-atp-step4.md)

## <a name="step-3-download-the-azure-atp-sensor-setup-package"></a>3. Adım. Azure ATP algılayıcısı Kurulum paketini indirme
Etki alanı bağlantı ayarlarını yapılandırdıktan sonra Azure ATP algılayıcısı Kurulum paketini indirebilirsiniz. Azure ATP algılayıcısı Kurulum paketini, ayrılmış bir sunucuya veya bir etki alanı denetleyicisine yüklenebilir. Doğrudan bir etki alanı denetleyicisine yüklerken, ayrılmış bir sunucuya yüklerken bir Azure ATP algılayıcısını yüklendikten ve bağlantı noktası yansıtma kullanarak, Azure ATP tek başına algılayıcı yüklenir. Azure ATP algılayıcısını hakkında daha fazla bilgi için bkz. [Azure ATP mimarisi](atp-architecture.md). 

Tıklayın **indirme** gitmek için sayfanın üst kısmındaki adımları listesinde **algılayıcı** sayfası.

![Azure ATP algılayıcı yapılandırma ayarları](media/atp-sensor-config.png)

> [!NOTE] 
> Algılayıcı yapılandırma ekranına daha sonra ulaşmak için **ayarlar simgesine** (sağ üst köşesinde) seçip **yapılandırma**, daha sonra altında **sistem**, tıklayın**algılayıcı**.  

1.  Tıklayın **algılayıcı**.
2.  Paketi yerel olarak kaydedin.
3.  Kopyalama **erişim** **anahtar**. Azure ATP algılayıcısını Azure ATP çalışma alanınıza bağlanmak erişim anahtarı gereklidir. Erişim anahtarı bir bir kerelik parola kimlik doğrulaması ve TLS şifreleme için sertifikalar kullanılarak sonra tüm iletişim gerçekleştirilir, algılayıcı dağıtımı için ' dir. Kullanım **yeniden** hiç olmadığı kadar yeni erişim anahtarını yeniden gerekiyorsa, şunları yapabilirsiniz ve daha önceden dağıtılan tüm algılayıcılar etkilemez, yalnızca ilk kayıt algılayıcı için kullanıldığından düğmesi.
4.  Ayrılmış sunucudan veya etki alanı denetleyicisi ileride Azure ATP algılayıcısını yükleme paketi kopyalayın. Alternatif olarak, etki alanı denetleyicisi veya adanmış sunucu Azure ATP çalışma alanı portalını açın ve bu adımı atlayın.

Zip dosyası aşağıdaki dosyaları içerir:

-   Azure ATP algılayıcısı yükleyicisi

-   Azure ATP bulut hizmetine bağlanmak için gereken bilgilerin bulunduğu yapılandırma ayarı dosyası


> [!div class="step-by-step"]
> [« 2. Adım](install-atp-step2.md)
> [4. Adım »](install-atp-step4.md)


## <a name="see-also"></a>Ayrıca Bkz.

- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)

- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)

- [Azure ATP önkoşulları](atp-prerequisites.md)

- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)