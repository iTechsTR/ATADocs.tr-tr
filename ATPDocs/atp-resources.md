---
title: Yararlı kaynaklara bir listesi için Azure Advanced Threat Protection | Microsoft Docs
description: Bu makalede Azure ATP için yararlı kaynakların bir listesini sağlar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/29/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 34dc152c-6b7f-4128-93fe-aad56c282730
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: b8d91468664a76436078772ad1fc8510ea56d67a
ms.sourcegitcommit: 5c0f914b44bfb8e03485f12658bfa9a7cd3d8bbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
ms.locfileid: "32298505"
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="azure-atp-readiness-guide"></a>Azure ATP hazırlık Kılavuzu

Bu makale, Azure Advanced Threat Analytics ile çalışmaya başlamak için yardımcı kaynakların bir listesini sağlayan bir hazırlık yol haritası sağlar. 

## <a name="understanding-azure-atp"></a>Azure ATP anlama

Azure Gelişmiş tehdit Koruması (ATP), kuruluşunuzdaki İleri düzey hedeflenmiş siber saldırılara ve içeriden gelen tehditleri birden çok türlerine karşı korunmasına yardımcı olan bir bulut hizmetidir. Azure ATP hakkında daha fazla bilgi için aşağıdaki kaynakları kullanın: 
- [Azure ATP genel bakış](what-is-atp.md)
- [Azure ATP tanıtım videosunu - tam](https://www.youtube.com/watch?v=KX-xpFc0sBw) 

## <a name="deployment-decisions"></a>Dağıtım kararları

Azure ATP Azure ve bir etki alanı denetleyicisinde veya adanmış sunuculara yüklenebilir algılayıcılar bulunan bir bulut hizmeti oluşur. Hazır ve çalışır Azure ATP ulaşmadan ne algılayıcılar daha iyi uyacak dağıtımınızı türünü seçin önemlidir.<br>Fiziksel sunucuları kullanıyorsanız, kapasite planlamanız gerekir. Yardım için algılayıcılar alan ayırmak için boyutlandırma aracından alabilirsiniz: 
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool) -Azure ATP izler trafik miktarı koleksiyonunu boyutlandırma aracı otomatikleştirir. Otomatik olarak desteklenebilirlik ve algılayıcılar için kaynak önerileri sağlar. 
- [ATA kapasite planlama Kılavuzu](atp-capacity-planning.md)

## <a name="deploy-azure-atp"></a>Azure ATP dağıtma

Bu kaynakları Azure ATP ayarlayın, Active Directory'ye bağlamanın, algılayıcı paketini indirin, olay toplamayı ayarlama ve isteğe bağlı olarak, VPN ile tümleştirmek ve honeytoken hesapları ve özel durumları ayarlamanız yardımcı olur. 
- [Azure ATP (EMS E5 parçası) deneyin](http://aka.ms/aatptrial) deneme 90 gün boyunca geçerlidir.
- [Dağıtım Kılavuzu'na](install-atp-step1.md) dağıtmak Azure ATP ortamınızdaki şu adımları izleyin.
- [Azure ATP Windows Defender ATP ile tümleştirme](integrate-wd-atp.md)
- 
## <a name="azure-atp-settings"></a>Azure ATP ayarları

Çalışma alanı oluştururken, Azure ATP temel gerekli ayarlarında yapılandırılır. Ancak, algılamaların SIEM tümleştirme gibi ortamınız için daha kesin ve denetim ayarlarını Azure ATP ince ayar yapmak için yapılandırabileceğiniz çeşitli diğer ayarlar vardır. 

- [Azure ATP genel belgeleri](what-is-atp.md)
- [Denetim ayarları](https://blogs.technet.microsoft.com/positivesecurity/2017/08/18/ata-auditing-auditpol-advanced-audit-settings-enforcement-lightweight-gateway-service-discovery/) – önce ve sonra bir ATA dağıtımı, etki alanı denetleyicisi durumunu denetleme. 

## <a name="work-with-azure-atp"></a>Azure ATP ile çalışma

Azure ATP kurulup çalışmaya başladıktan sonra etkinlik zaman satırda algılanan kuşkulu etkinlikleri görüntüleyebilirsiniz. Bu, Azure ATP portalına oturum açtığınızda gittiğiniz varsayılan giriş sayfasıdır. Varsayılan olarak, tüm kuşkulu etkinliler saldırı zaman çizelgesinde gösterilir. Ayrıca, her etkinliğe atanmış olan önem düzeyini de görebilirsiniz. Daha fazla bilgi sağlayan varlıklarının içinde (bilgisayarlar, cihazlar, kullanıcılar) kendi profil sayfalarını açmak için detaya tarafından her kuşkulu etkinlik araştırın. Bu kaynakları Azure ATP'ın kuşkulu etkinliklerle çalışmanıza yardımcı olur: 

- [Azure ATP şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md) önceliklendirme ve sonraki adımlar, Azure ATP algılamaların ile öğrenin.
- [Hassas olarak grupları etiketi](sensitive-accounts.md) elde kimlik bilgilerinin açıklanmasını hassas güvenlik grupları üzerinde görünürlük.

## <a name="security-best-practices"></a>En iyi güvenlik uygulamaları

- [Azure ATP sık sorulan sorular](atp-technical-faq.md) -bu makalede Azure ATP hakkında sık sorulan soruların listesi ve ve öngörülerle yanıtlar sağlar. 
## <a name="community-resources"></a>Topluluk kaynakları

Blog: [Azure ATP blogu](https://aka.ms/aatpblog)

Ortak topluluk: [Azure ATP Teknoloji Topluluğu](https://aka.ms/AatpCom)

Özel topluluk: [Azure ATP Yammer grubu](https://www.yammer.com/azureadvisors/#/threads/inGroup?type=in_group&feedId=9386893&view=all)

Kanal 9: [Microsoft Güvenlik Channel 9 sayfası](https://channel9.msdn.com/Shows/Microsoft-Security/)



## <a name="see-also"></a>Ayrıca bkz:

- [Hassas hesaplar ile çalışma](sensitive-accounts.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)