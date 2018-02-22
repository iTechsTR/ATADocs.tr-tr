---
title: "Yükleme Azure Gelişmiş tehdit koruması - 6. adım | Microsoft Docs"
description: "ATP yükleme Bu adımda, VPN tümleştirin."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/14/2018
ms.topic: get-started-article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 0d9d2a1d-6c76-4909-b6f9-58523df16d4f
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: d29210983f3f9f879b462ef760d0b3fe6e53cd5d
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="install-azure-atp---step-6"></a>Azure ATP - 6. adım yükleme

>[!div class="step-by-step"]
[«5. Adım](install-atp-step5.md)
[7. Adım»](install-atp-step7.md)

## <a name="step-6-integrate-vpn"></a>6. Adım. VPN tümleştirme

Azure Gelişmiş tehdit Koruması (ATP) alınan VPN çözümleri hesap bilgilerini toplayabilirsiniz. Yapılandırıldığında, kullanıcının profili sayfasını VPN bağlantıları, IP adresleri ve bağlantıları geldiği konumlar gibi bilgileri içerir. Bu, olağan dışı VPN bağlantıları için yeni bir algılama yanı sıra kullanıcı etkinliği ek bilgileri sağlayarak araştırma işlemi tamamlar. Dış IP adresini bir konuma çözümlemek için anonim çağrıdır. Hiçbir kişisel tanımlayıcı bu çağrısında gönderilir.

Azure ATP Azure ATP algılayıcılar iletilen RADIUS hesap olaylarını dinleme VPN çözümünüzün tümleştirir. Bu mekanizma RADIUS Standart hesap temel alır ([RFC 2866](https://tools.ietf.org/html/rfc2866)), ve aşağıdaki VPN satıcıları desteklenir:

-   Microsoft
-   F5
-   Check Point
-   Cisco ASA

## <a name="prerequisites"></a>Önkoşullar

VPN tümleştirmeyi etkinleştirmek için aşağıdaki parametreleri ayarladığınızdan emin olun:

-   Bağlantı noktası UDP 1813 Azure ATP tek başına algılayıcılar ve Azure ATP algılayıcı açın.


Aşağıdaki örnek, Microsoft Routing ve Uzaktan erişim sunucusu (RRAS) VPN yapılandırma işlemi tanımlamak için kullanır.

Bir üçüncü taraf VPN çözümü kullanıyorsanız, RADIUS hesaplama etkinleştirme hakkında yönergeler için kendi belgelerine başvurun.

## <a name="configure-radius-accounting-on-the-vpn-system"></a>RADIUS hesaplama VPN sistemde yapılandırın

RRAS sunucusunda aşağıdaki adımları gerçekleştirin.
 
1.  Yönlendirme ve Uzaktan Erişim konsolunu açın.
2.  Sunucu adını sağ tıklatıp **özellikleri**.
3.  İçinde **güvenlik** sekmesinde, altında **hesap sağlayıcısı**seçin **RADIUS hesaplama** tıklatıp **yapılandırma**.

    ![RADIUS Kurulumu](./media/radius-setup.png)

4.  İçinde **RADIUS sunucusu Ekle** penceresinde, türü **sunucu adı** en yakın Azure ATP tek başına algılayıcı veya Azure ATP algılayıcı. Altında **bağlantı noktası**, 1813 varsayılan yapılandırıldığından emin olun. Tıklatın **değişiklik** ve yeni bir paylaşılan gizli anımsamasını sağlayabilirsiniz alfasayısal karakter dizesi yazın. Daha sonra Azure ATP yapılandırmanızda doldurmak gerekir. Denetleme **RADIUS hesabı üzerinde göndermek ve hesap kapatma iletilerinin** kutusuna ve ardından **Tamam** tüm açık iletişim kutularında.
 
     ![VPN Kurulumu](./media/vpn-set-accounting.png)
     
### <a name="configure-vpn-in-atp"></a>İçinde ATP VPN bağlantısını yapılandırma

Azure ATP hangi bilgisayarların konumlardan ağ ve anormal VPN bağlantıları algılayabilir bağlanmasını profili yardımcı olan VPN verileri toplar.

VPN veri ATP yapılandırmak için:

1.  Azure ATP çalışma Portalı'nda yapılandırma dişlisine tıklayın ve ardından **VPN**.
 

2.  Aç **RADIUS hesaplama**ve yazın **paylaşılan gizlilik** RRAS VPN sunucunuza daha önce yapılandırılmış. Daha sonra **Kaydet**'e tıklayın.
 

  ![Azure ATP VPN bağlantısını yapılandırma](./media/atp-vpn-radius.png)


Bu özellik etkinleştirildikten sonra tüm Azure ATP tek başına algılayıcılar ve algılayıcılar dinler 1813 RADIUS hesaplama olayları için bağlantı noktası. 

Kurulumunuzu tamamlanır. 

Azure ATP algılayıcı VPN olaylarını alır ve bunları işlemek için Azure ATP bulut hizmetine gönderir sonra varlık profili ayrı erişilen VPN konumlarını gösterir ve etkinlikleri profilinde konumlarını gösterir.





>[!div class="step-by-step"]
[«Adım 6](install-atp-step5.md)
[7. adım»](install-atp-step7.md)


## <a name="see-also"></a>Ayrıca bkz:
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
