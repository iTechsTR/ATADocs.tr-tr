---
title: "Advanced Threat Analytics’i yükleme - 7. Adım | Microsoft Docs"
description: "Ata'yı yükleme Bu adımda, VPN tümleştirin."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: e0aed853-ba52-46e1-9c55-b336271a68e7
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 42cedc6f23f61b9ff5f4789c10aad1282b1308a7
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*



# <a name="install-ata---step-7"></a>ATA’yı Yükleme - 7. Adım

>[!div class="step-by-step"]
[«5. adım](install-ata-step5.md)
[8. adım»](install-ata-step7.md)

## <a name="step-7-integrate-vpn"></a>7. Adım VPN tümleştirme

Microsoft Advanced Threat Analytics (ATA) sürüm 1,8 alınan VPN çözümleri hesap bilgilerini toplayabilirsiniz. Yapılandırıldığında, kullanıcının profili sayfasını VPN bağlantıları, IP adresleri ve bağlantıları geldiği konumlar gibi bilgileri içerir. Bu, kullanıcı etkinliğini ek bilgileri sağlayarak araştırma işlemi tamamlar. Dış IP adresini bir konuma çözümlemek için anonim çağrıdır. Hiçbir kişisel tanımlayıcı bu çağrısında gönderilir.

ATA, ATA Gateway iletilen RADIUS hesap olaylarını dinleme VPN çözümünüzün tümleştirir. Bu mekanizma RADIUS Standart hesap temel alır ([RFC 2866](https://tools.ietf.org/html/rfc2866)), ve aşağıdaki VPN satıcıları desteklenir:

-   Microsoft
-   F5
-   Cisco ASA

## <a name="prerequisites"></a>Önkoşullar

VPN tümleştirmeyi etkinleştirmek için aşağıdaki parametreleri ayarladığınızdan emin olun:

-   Bağlantı noktası UDP 1813 ATA Gateway ve ATA Lightweight Gateway açın.

-   ATA Center erişebilir *ti.ata.azure.com* gelen IP adreslerini konumunu sorgulayabilmesi HTTPS (443 numaralı) kullanarak.

Aşağıdaki örnek, Microsoft Routing ve Uzaktan erişim sunucusu (RRAS) VPN yapılandırma işlemi tanımlamak için kullanır.

Bir üçüncü taraf VPN çözümü kullanıyorsanız, RADIUS hesaplama etkinleştirme hakkında yönergeler için kendi belgelerine başvurun.

## <a name="configure-radius-accounting-on-the-vpn-system"></a>RADIUS hesaplama VPN sistemde yapılandırın

RRAS sunucusunda aşağıdaki adımları gerçekleştirin.
 
1.  Yönlendirme ve Uzaktan Erişim konsolunu açın.
2.  Sunucu adını sağ tıklatıp **özellikleri**.
3.  İçinde **güvenlik** sekmesinde, altında **hesap sağlayıcısı**seçin **RADIUS hesaplama** tıklatıp **yapılandırma**.

    ![RADIUS Kurulumu](./media/radius-setup.png)

4.  İçinde **RADIUS sunucusu Ekle** penceresinde, türü **sunucu adı** yakın ATA Gateway veya ATA Lightweight Gateway. Altında **bağlantı noktası**, 1813 varsayılan yapılandırıldığından emin olun. Tıklatın **değişiklik** ve yeni bir paylaşılan gizli anımsamasını sağlayabilirsiniz alfasayısal karakter dizesi yazın. Daha sonra ATA yapılandırmanızı doldurmak gerekir. Denetleme **RADIUS hesabı üzerinde göndermek ve hesap kapatma iletilerinin** kutusuna ve ardından **Tamam** tüm açık iletişim kutularında.
 
     ![VPN Kurulumu](./media/vpn-set-accounting.png)
     
### <a name="configure-vpn-in-ata"></a>ATA VPN bağlantısını yapılandırma

ATA VPN verilerini toplar ve ne zaman ve nerede VPN aracılığıyla kimlik bilgilerini kullanıldığını tanımlar ve bu verileri, araştırmasını tümleştirir. Bu, ATA tarafından bildirilen uyarıları araştırmanıza yardımcı olacak ek bilgiler sağlar.

ATA VPN verileri yapılandırmak için:

1.  ATA Konsolu'nda ATA yapılandırma sayfasını açın ve gidin **VPN**.
 
  ![ATA config menu](./media/config-menu.png)

2.  Aç **RADIUS hesaplama**ve yazın **paylaşılan gizlilik** RRAS VPN sunucunuza daha önce yapılandırılmış. Daha sonra **Kaydet**'e tıklayın.
 

  ![ATA VPN bağlantısını yapılandırma](./media/vpn.png)


Bu özellik etkinleştirildikten sonra tüm ATA Gateway ve Lightweight Gateway RADIUS hesaplama olayları 1813 numaralı bağlantı noktasında dinler. 

Kurulum tamamlandıktan ve kullanıcıların profili sayfasını VPN etkinliğinde şimdi görebilirsiniz:
 
   ![VPN Kurulumu](./media/vpn-user.png)

ATA Gateway VPN olaylarını alır ve ATA Center işleme için gönderir sonra ATA Center erişmesi *ti.ata.azure.com* VPN olaylara dış IP adreslerinin çözümleyebilmesi için HTTPS (443 numaralı) kullanma kendi coğrafi konum.




>[!div class="step-by-step"]
[«6. Adım](install-ata-step5.md)
[8. Adım»](install-ata-step7.md)



## <a name="related-videos"></a>İlgili videolar
- [ATA dağıtımına genel bakış](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)
- [ATA Gateway türü sağ seçme](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)


## <a name="see-also"></a>Ayrıca bkz:
- [ATA POC Dağıtım Kılavuzu](http://aka.ms/atapoc)
- [ATA boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)

