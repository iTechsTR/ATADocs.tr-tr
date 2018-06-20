---
title: Yükleme Azure Gelişmiş tehdit koruması - 3. adım | Microsoft Docs
description: Azure ATP yükleme üç adım Azure ATP tek başına algılayıcı Kurulum paketini indirmelisiniz yardımcı olur.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2017
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 95bb4ec1-841f-41b7-92fe-fbd144085724
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: aa07d6ce4418c051362652e70968a8e41313affb
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
ms.locfileid: "29446046"
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="install-azure-atp---step-3"></a>Azure ATP - 3. adım yükleme

>[!div class="step-by-step"]
[« 2. Adım](install-atp-step2.md)
[4. Adım »](install-atp-step4.md)

## <a name="step-3-download-the-azure-atp-sensor-setup-package"></a>3. Adım. Azure ATP algılayıcı Kurulum paketini indirin
Etki alanı bağlantı ayarlarını yapılandırdıktan sonra Azure ATP algılayıcı Kurulum paketini indirebilirsiniz. Azure ATP algılayıcı kurulum paketi, ayrılmış bir sunucuya veya bir etki alanı denetleyicisine yüklenebilir. Doğrudan etki alanı denetleyicisine yükleme, bir Azure ATP algılayıcı ayrılmış bir sunucuya yüklerken yüklenir ve bağlantı noktası yansıtma kullanarak, Azure ATP tek başına algılayıcı yüklenir. Azure ATP algılayıcı hakkında daha fazla bilgi için bkz: [Azure ATP mimarisi](atp-architecture.md). 

Tıklatın **karşıdan** sayfanın üst kısmındaki gitmek için adımları listesinde **algılayıcı** sayfası.

![Azure ATP algılayıcı yapılandırma ayarları](media/atp-sensor-config.png)

> [!NOTE] 
> Algılayıcı yapılandırma ekranında daha sonra ulaşmak için tıklatın **ayarlar simgesine** (sağ üst köşesinde) ve seçin **yapılandırma**, daha sonra altında **sistem**, tıklatın**algılayıcı**.  

1.  Tıklatın **algılayıcı**.
2.  Paketi yerel olarak kaydedin.
3.  Kopya **erişim tuşu**. Azure ATP çalışma alanına bağlanmak Azure ATP algılayıcı için erişim anahtarı gereklidir. Erişim anahtarı bir bir kerelik parola algılayıcı dağıtım, tüm iletişimin kimlik doğrulama ve TLS şifreleme için sertifikalar kullanılarak gerçekleştirilen için ' dir. Kullanım **yeniden** algılayıcı ilk kaydı için yalnızca kullanıldığından yeni erişim anahtarı yeniden gerekir, şunları yapabilirsiniz ve daha önce dağıtılan tüm algılayıcılar etkilemez düğmesi.
4.  Paket adanmış sunucu veya etki alanı denetleyicisi Azure ATP algılayıcı yüklüyorsanız kopyalayın. Alternatif olarak, ayrılmış sunucuya veya etki alanı denetleyicisi Azure ATP çalışma Portalı'nı açın ve bu adımı atlayın.

Zip dosyası aşağıdaki dosyaları içerir:

-   Azure ATP algılayıcı yükleyici

-   Azure ATP bulut hizmetine bağlanmak için gereken bilgilerin bulunduğu yapılandırma ayarı dosyası


>[!div class="step-by-step"]
[« 2. Adım](install-atp-step2.md)
[4. Adım »](install-atp-step4.md)


## <a name="see-also"></a>Ayrıca bkz:

- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)

- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)

- [Azure ATP önkoşulları](atp-prerequisites.md)

- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)