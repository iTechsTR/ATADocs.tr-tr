---
title: Azure Gelişmiş tehdit koruması VPN tümleştirmesi yükleyin | Microsoft Docs
description: Bir VPN tümleştirerek Azure ATP için hesap bilgilerini toplayın.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 0d9d2a1d-6c76-4909-b6f9-58523df16d4f
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 9f5caf3ef7c0c986404cfe90a6f8cc40aa9462b4
ms.sourcegitcommit: 30d874808cfeafd46ee8fbbf34e0bbcb337f6544
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49089381"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="integrate-vpn"></a>VPN tümleştirin

Azure Gelişmiş tehdit Koruması (ATP) alınan VPN çözümleri hesap bilgilerini toplayabilirsiniz. Yapılandırıldığında, kullanıcının profil sayfasını VPN bağlantıları, IP adresleri ve bağlantı geldiği konumlar gibi bilgileri içerir. Bu, olağan dışı VPN bağlantıları için yeni bir algılama yanı sıra, kullanıcı etkinliğinin ek bilgi sağlayarak araştırma işlemi tamamlar. Dış IP adresi için bir konum yapılan çağrının anonimdir. Hiçbir kişisel tanımlayıcı bu çağrıda gönderilir.

Azure ATP Azure ATP algılayıcı için iletilen RADIUS muhasebe olayları dinleme VPN çözümünüz ile tümleştirilir. Bu mekanizma, RADIUS Standart hesap bağlıdır ([RFC 2866](https://tools.ietf.org/html/rfc2866)), ve aşağıdaki VPN satıcıları desteklenir:

-   Microsoft
-   F5
-   Check Point
-   Cisco ASA

## <a name="prerequisites"></a>Önkoşullar

VPN tümleştirmeyi etkinleştirmek için aşağıdaki parametreleri ayarladığınızdan emin olun:

-   Azure ATP algılayıcı ve/veya Azure ATP tek başına algılayıcı UDP 1813 numaralı bağlantı noktasını açın.


Aşağıdaki örnek, Microsoft Routing ve Uzaktan erişim sunucusu (RRAS) VPN yapılandırma işlemi tanımlamak için kullanır.

Bir üçüncü taraf VPN çözümü kullanıyorsanız, RADIUS hesaplama etkinleştirme hakkında yönergeler için kendi belgelerine başvurun.

## <a name="configure-radius-accounting-on-the-vpn-system"></a>VPN sistemde RADIUS hesap yapılandırma

RRAS sunucunuzda aşağıdaki adımları gerçekleştirin.
 
1.  Yönlendirme ve Uzaktan Erişim konsolunu açın.
2.  Sunucu adını sağ tıklatıp **özellikleri**.
3.  İçinde **güvenlik** sekmesindeki **hesap sağlayıcısı**seçin **RADIUS hesap** tıklatıp **yapılandırma**.

    ![RADIUS Kurulumu](./media/radius-setup.png)

4.  İçinde **RADIUS sunucusu Ekle** penceresinde, tür **sunucu adı** en yakın Azure ATP tek başına algılayıcı veya Azure ATP algılayıcısını. Altında **bağlantı noktası**, 1813 varsayılan yapılandırıldığından emin olun. Tıklayın **değişiklik** ve yeni bir paylaşılan gizli dizisini hatırlayabileceğiniz bir alfasayısal karakter türü. Daha sonra Azure ATP yapılandırma doldurun gerekir. Denetleme **RADIUS hesap üzerinde gönderin ve hesap kapalı iletileri** kutusuna ve ardından **Tamam** tüm açık iletişim kutularında.
 
     ![VPN Kurulum](./media/vpn-set-accounting.png)
     
### <a name="configure-vpn-in-atp"></a>ATP'de VPN yapılandırma

Azure ATP ağa ve şüpheli VPN bağlantıları algılamak için hangi bilgisayarların konumlardan connect profili yardımcı olacak VPN verilerini toplar.

ATP'de VPN verilerini yapılandırmak için:

1.  Azure ATP Portalı'nda yapılandırma dişlisine tıklayın ve ardından **VPN**.
 

2.  Açma **RADIUS hesap**yazın **paylaşılan gizlilik** RRAS VPN sunucunuzda daha önce yapılandırılmış. Daha sonra **Kaydet**'e tıklayın.
 

  ![Azure ATP VPN yapılandırma](./media/atp-vpn-radius.png)


Bu etkinleştirildikten sonra tüm Azure ATP algılayıcı ve tek başına algılayıcı RADIUS muhasebe olayları için 1813 numaralı bağlantı noktasında dinleme ve kurulumunuz tamamlandıktan. 

 Azure ATP algılayıcısını VPN olayları alıp bunları işleme için Azure ATP bulut hizmetine gönderir sonra varlık profili ayrı erişilen VPN konumları gösterir ve etkinlikleri profilinde konumlarını gösterir.



## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
