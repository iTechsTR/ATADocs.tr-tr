---
title: Advanced Threat Analytics’i yükleme - 7. Adım | Microsoft Docs
description: Ata'yı yükleme Bu adımda, VPN'iniz tümleştirin.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: e0aed853-ba52-46e1-9c55-b336271a68e7
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 8a651e177d37361ccbca178075fb2ac33a434a90
ms.sourcegitcommit: b283bf66e63d76e6dba4564a229e804792794c6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453927"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="install-ata---step-7"></a>ATA’yı Yükleme - 7. Adım

> [!div class="step-by-step"]
> [«5. adım](install-ata-step5.md)
> [8. adım»](install-ata-step7.md)

## <a name="step-7-integrate-vpn"></a>7. Adım VPN tümleştirin

Microsoft Advanced Threat Analytics (ATA) sürüm 1.8 alınan VPN çözümleri hesap bilgilerini toplayabilirsiniz. Yapılandırıldığında, kullanıcının profil sayfasını VPN bağlantıları, IP adresleri ve bağlantı geldiği konumlar gibi bilgileri içerir. Bu, kullanıcı etkinliği hakkında ek bilgi sağlayarak araştırma işlemi tamamlar. Dış IP adresi için bir konum yapılan çağrının anonimdir. Hiçbir kişisel tanımlayıcı bu çağrıda gönderilir.

ATA, ATA Gateway bileşenleri için iletilen RADIUS muhasebe olayları dinleme VPN çözümünüz ile tümleştirilir. Bu mekanizma, RADIUS Standart hesap bağlıdır ([RFC 2866](https://tools.ietf.org/html/rfc2866)), ve aşağıdaki VPN satıcıları desteklenir:

-   Microsoft
-   F5
-   Cisco ASA

## <a name="prerequisites"></a>Önkoşullar

VPN tümleştirmeyi etkinleştirmek için aşağıdaki parametreleri ayarladığınızdan emin olun:

-   ATA Gateway ve ATA Lightweight Gateway bileşenleri üzerinde UDP 1813 numaralı bağlantı noktasını açın.

-   ATA Center erişebilir *ti.ata.azure.com* HTTPS (443 numaralı bağlantı noktası) kullanarak konumu gelen IP adreslerini sorgulayabilirsiniz.

Aşağıdaki örnek, Microsoft Routing ve Uzaktan erişim sunucusu (RRAS) VPN yapılandırma işlemi tanımlamak için kullanır.

Bir üçüncü taraf VPN çözümü kullanıyorsanız, RADIUS hesaplama etkinleştirme hakkında yönergeler için kendi belgelerine başvurun.

## <a name="configure-radius-accounting-on-the-vpn-system"></a>VPN sistemde RADIUS hesap yapılandırma

RRAS sunucunuzda aşağıdaki adımları gerçekleştirin.
 
1.  Yönlendirme ve Uzaktan Erişim konsolunu açın.
2.  Sunucu adını sağ tıklatıp **özellikleri**.
3.  İçinde **güvenlik** sekmesindeki **hesap sağlayıcısı**seçin **RADIUS hesap** tıklatıp **yapılandırma**.

    ![RADIUS Kurulumu](./media/radius-setup.png)

4.  İçinde **RADIUS sunucusu Ekle** penceresinde, tür **sunucu adı** en yakın ATA Gateway veya ATA Lightweight Gateway. Altında **bağlantı noktası**, 1813 varsayılan yapılandırıldığından emin olun. Tıklayın **değişiklik** ve yeni bir paylaşılan gizli dizisini hatırlayabileceğiniz bir alfasayısal karakter türü. Daha sonra ATA yapılandırmanızı doldurun gerekir. Denetleme **RADIUS hesap üzerinde gönderin ve hesap kapalı iletileri** kutusuna ve ardından **Tamam** tüm açık iletişim kutularında.
 
     ![VPN Kurulum](./media/vpn-set-accounting.png)
     
### <a name="configure-vpn-in-ata"></a>ATA'da VPN yapılandırma

ATA VPN verilerini toplar ve ne zaman ve nerede VPN kimlik bilgilerinin kullanıldığını tanımlar ve bu verileri, araştırmasını tümleştirir. Bu, ATA tarafından bildirilen uyarıları araştırmanıza yardımcı olacak ek bilgiler sağlar.

ATA'da VPN verilerini yapılandırmak için:

1.  ATA Konsolu'nda ATA yapılandırma sayfasını açın ve gidin **VPN**.
 
  ![ATA yapılandırma menüsü](./media/config-menu.png)

2.  Açma **RADIUS hesap**yazın **paylaşılan gizlilik** RRAS VPN sunucunuzda daha önce yapılandırılmış. Daha sonra **Kaydet**'e tıklayın.
 

  ![ATA VPN yapılandırma](./media/vpn.png)


Bu etkinleştirildikten sonra tüm ATA Gateway ve Lightweight Gateway için RADIUS hesap olaylarını 1813 numaralı bağlantı noktasında dinler. 

Kurulumunuz tamamlandıktan ve artık kullanıcı profili sayfasında VPN etkinliği görebilirsiniz:
 
   ![VPN Kurulum](./media/vpn-user.png)

ATA Gateway VPN olaylarını alır ve bunları işlemek için ATA Center'a gönderir sonra ATA Center erişmesi gereken *ti.ata.azure.com* VPN olaylara dış IP adresleriyle çözümleyebilmesi için HTTPS (443 numaralı bağlantı noktası) kullanma kendi coğrafi konum.




> [!div class="step-by-step"]
> [«6. Adım](install-ata-step5.md)
> [8. Adım»](install-ata-step7.md)



## <a name="related-videos"></a>İlgili videolar
- [ATA dağıtımı genel bakış](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)
- [ATA Gateway türü sağ seçme](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA POC Dağıtım Kılavuzu](http://aka.ms/atapoc)
- [ATA boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)

