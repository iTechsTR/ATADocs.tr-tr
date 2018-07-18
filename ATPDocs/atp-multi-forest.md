---
title: Azure Gelişmiş tehdit koruması aktarılacaksa orman desteği | Microsoft Docs
description: Azure ATP birden çok Active Directory ormanlarında desteği ayarlama yapma.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/17/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: effca0f2-fcae-4fca-92c1-c37306decf84
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: c76e459709c786082bea7566a61e5384a235eda4
ms.sourcegitcommit: 8feb9b65dc0e1de0ace00aca11784e54f9852a15
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39098204"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*

# <a name="install-azure-atp---step-9"></a>Azure ATP - 9. Adım'ı yükleme

>[!div class="step-by-step"]
[«8. adım](install-atp-step8-samr.md)

## <a name="step-9--set-up-azure-advanced-threat-protection-multi-forest-support"></a>9. Adım  Azure Gelişmiş tehdit koruması çok ormanlı desteği ayarlayın

Azure ATP ormanlar arasında yeteneği etkinliğini izleme ve profil kullanıcılar sağlayan birden çok ormanlı kuruluşlara destekleyebilir. 

Bir kurumsal kuruluş, birden çok Active Directory ormanları - eski altyapılarını Kurumsal birleşmeler ve satın almalar, coğrafi dağıtım ve güvenlik sınırları (kırmızı ormanları) dahil olmak üzere farklı amaçlar için sık kullanılan olabilir. Birden çok ormanı tek bir cam bölmeyle araştırmak ve izlemek için bir oluşturabilmesini sağlayan Azure tüm verilerin tek, birincil çalışma alanına raporlama ATP ile kullanarak koruyabilirsiniz.

Birden çok Active Directory ormanını desteklemek için aşağıdakileri sağlar:
-   Görüntüleyebilir ve tek bir cam bölmeyle gelen birden çok orman genelinde kullanıcılar tarafından gerçekleştirilen etkinlikleri araştırın. 
-   Çok ormanlı destek algılama artırır ve Gelişmiş Active Directory Tümleştirmesi ve hesap çözüm sağlayarak hatalı pozitif sonuçları azaltır. 
-   Çoklu foresst destek birden çok çalışma alanı gereksinimini ortadan kaldırır. daha fazla denetim sahibi ve merkezi olarak tek bir Azure ATP izlenen tüm konsol, etki alanı denetleyicilerinizin çalışırken daha kolay dağıtım daha iyi izleme uyarıları sağlar ve Çapraz kuruluş kapsamı için raporlama.


## <a name="how-azure-atp-detects-activities-across-multiple-forests"></a>Nasıl Azure ATP birden çok orman içinde etkinlikleri algılar. 

Ormanlar arası etkinlikleri algılamak için Azure ATP algılayıcı dahil, kullanıcıları ve bilgisayarları uzaktan ormanlarından dahil olmak üzere tüm varlıklar için profilleri oluşturmak için Uzak Ormanlardaki etki alanı denetleyicileri sorgulayın. 

> [!NOTE]
> - Bunun çalışması sırada Azure ATP algılayıcı yüklendiği orman diğer ormanlardaki tarafından güvenilmesi gerekir.
> - Altında Azure ATP konsolunda yapılandırdığınız kullanıcı **Dizin Hizmetleri** tüm ormanlar güvenilir olması gerekir.


Üzerinde hangi hiçbir Azure ATP algılayıcı yüklü ormanınız varsa, Azure ATP için yine de bu ormanlardan kaynaklanan etkinlikleri görüntüleyin ve izleyin. Yüklü ATP algılayıcı, tüm bağlı uzak ormanın etki alanı denetleyicileri, kullanıcılar ve makineler çözmek ve bunların her biri için profilleri oluşturmak için sorgulayabilirsiniz. 

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
-   ATP algılayıcısını çapraz orman etkinlik algıladığında, geçici trafiği görebilirsiniz. Böyle bir durumda ATP algılayıcı sipariş alma varlık bilgilerini ilgili etki alanı denetleyicileri bir LDAP sorgusu gönderir. 

## <a name="known-limitations"></a>Bilinen sınırlamalar
-   Başka bir ormandaki kaynaklara erişmek için tek bir ormandaki kullanıcıları tarafından gerçekleştirilen etkileşimli oturum açma işlemi Azure ATP Panoda görüntülenmez.


>[!div class="step-by-step"]
[«8. adım](install-atp-step8-samr.md)


## <a name="see-also"></a>Ayrıca bkz:
- [ATA boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [ATA mimarisi](atp-architecture.md)
- [ATA’yı yükleme](install-atp-step1.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)

