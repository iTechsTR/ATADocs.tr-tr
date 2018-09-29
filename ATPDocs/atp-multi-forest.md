---
title: Azure Gelişmiş tehdit koruması aktarılacaksa orman desteği | Microsoft Docs
description: Azure ATP birden çok Active Directory ormanlarında desteği ayarlama yapma.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: effca0f2-fcae-4fca-92c1-c37306decf84
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: ad120cfe3e736935a557f66417794cd531fa5b2e
ms.sourcegitcommit: b283bf66e63d76e6dba4564a229e804792794c6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47454097"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*

# <a name="install-azure-atp---step-9"></a>Azure ATP - 9. Adım'ı yükleme

> [!div class="step-by-step"]
> [«8. adım](install-atp-step8-samr.md)

## <a name="step-9--set-up-azure-advanced-threat-protection-multi-forest-support"></a>9. Adım  Azure Gelişmiş tehdit koruması çok ormanlı desteği ayarlayın

Azure ATP kuruluşlar arasında tek bir cam bölmeyle ormanlardan etkinliği ve kullanıcı profili kolayca izleme yeteneği sağlayan birden çok ormanlı destekleyebilir. 

Büyük kuruluşlar genellikle birden çok Active Directory ormanları - eski altyapılarını Kurumsal birleşmeler ve satın almalar, coğrafi dağıtım ve güvenlik sınırları (kırmızı ormanları) dahil olmak üzere farklı amaçlar için sık kullanılan sahiptir. Birden çok ormanı tek bir cam bölmeyle araştırmak ve izlemek için bir oluşturabilmesini sağlayan Azure ATP kullanarak koruyabilirsiniz.

Birden çok Active Directory ormanını desteklemek için aşağıdakileri sağlar:
-   Görüntüleyebilir ve tek bir cam bölmeyle gelen birden çok orman genelinde kullanıcılar tarafından gerçekleştirilen etkinlikleri araştırın. 
-   Geliştirilmiş bir algılama ve Gelişmiş Active Directory tümleştirme ve hesap çözüm sağlayarak daha az hatalı pozitif sonuç. 
-   Daha fazla denetim ve daha kolay dağıtım. Gelişmiş izleme uyarıları ve etki alanı denetleyicilerinizin tümünü tek bir Azure ATP konsoldan izlenen çapraz kuruluş kapsamı için raporlama.


## <a name="how-azure-atp-detects-activities-across-multiple-forests"></a>Nasıl Azure ATP birden çok orman içinde etkinlikleri algılar. 

Ormanlar arası etkinlikleri algılamak için Azure ATP algılayıcı dahil, kullanıcıları ve bilgisayarları uzaktan ormanlarından dahil olmak üzere tüm varlıklar için profilleri oluşturmak için Uzak Ormanlardaki etki alanı denetleyicileri sorgulayın. 

> [!NOTE]
> - (En düşük tek yönlü bir güven varsa), azure ATP algılayıcı tüm ormanlara yüklenebilir.
> - Altında Azure ATP konsolunda yapılandırdığınız kullanıcı **Dizin Hizmetleri** tüm ormanlar güvenilir olması gerekir.


Üzerinde hangi hiçbir Azure ATP algılayıcı yüklü ormanınız varsa, Azure ATP için yine de bu ormanlardan kaynaklanan etkinlikleri görüntüleyin ve izleyin. Yüklü ATP algılayıcı, tüm bağlı uzak ormanın etki alanı denetleyicileri, kullanıcılar, makineleri çözmek ve bunların her biri için profilleri oluşturmak için sorgulayabilirsiniz. 

## <a name="installation-requirements"></a>Yükleme gereksinimleri 

-   Azure ATP tek başına algılayıcı tek başına makineler yerine doğrudan etki alanı denetleyicilerinde yükleniyorsa, makineler tüm LDAP kullanarak uzak bir ormandaki etki alanı denetleyicileri ile iletişim kurmasına izin emin olun. 
- Altında Azure ATP konsolunda yapılandırdığınız kullanıcı **Dizin Hizmetleri** tüm diğer ormanlara güvenmesi ve en az etki alanı denetleyicilerinde LDAP sorguları gerçekleştirmek için yalnızca okuma izni olmalıdır.

- Azure ATP algılayıcı ve tek başına algılayıcı ATP ile iletişim kurduğu ATP için sırada ATP algılayıcı yüklendiği her Machine aşağıdaki bağlantı noktalarını açın:

 
  |Protokol|Aktarım|Bağlantı Noktası|Hedef/Kaynak|Yön|
  |----|----|----|----|----|
  |**Internet bağlantı noktaları**||||
  |SSL (*.atp.azure.com)|TCP|443|Azure ATP bulut hizmeti|Giden|
  |**İç bağlantı noktaları**||||           
  |LDAP|TCP ve UDP|389|Etki alanı denetleyicileri|Giden|
  |Güvenli LDAP (LDAPS)|TCP|636|Etki alanı denetleyicileri|Giden|
  |LDAP - Genel Katalog|TCP|3268|Etki alanı denetleyicileri|Giden|
  |LDAPS - Genel Katalog|TCP|3269|Etki alanı denetleyicileri|Giden|


## <a name="multi-forest-support-network-traffic-impact"></a>Çoklu orman desteği ağ trafiği etkisi 

Azure ATP ormanlarınız eşler, aşağıdaki etkileyen bir işlem kullanır:

-   Azure ATP algılayıcısını çalışmaya başladıktan sonra uzak Active Directory ormanları sorgular ve kullanıcıları ve profil oluşturma için makine verisi listesini alır.
-   5 dakikada bir, ağdaki tüm ormanlardaki eşlenecek her ormanda her etki alanındaki bir etki alanı denetleyicisi her Azure ATP algılayıcısını sorgular.
-   Her Azure ATP algılayıcısını "trustedDomain" Nesne Active Directory'de oturum açma ve güven tür denetimini kullanarak orman eşler.
-   ATP algılayıcısını çapraz orman etkinlik algıladığında, geçici trafiği görebilirsiniz. Böyle bir durumda ATP algılayıcı varlık bilgilerini almak için ilgili etki alanı denetleyicileri için bir LDAP sorgusu gönderir. 

## <a name="known-limitations"></a>Bilinen sınırlamalar
-   Başka bir ormandaki kaynaklara erişmek için tek bir ormandaki kullanıcıları tarafından gerçekleştirilen etkileşimli oturum açma işlemi Azure ATP Panoda görüntülenmez.


> [!div class="step-by-step"]
> [«8. adım](install-atp-step8-samr.md)


## <a name="see-also"></a>Ayrıca Bkz.
- [ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [ATP mimarisi](atp-architecture.md)
- [ATP yükleyin](install-atp-step1.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)

