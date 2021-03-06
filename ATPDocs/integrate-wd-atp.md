---
title: Windows Defender ATP ile Azure Gelişmiş tehdit koruması tümleştirme | Microsoft Docs
description: Azure Gelişmiş tehdit koruması için tam tehdit algılama kapsamının Windows Defender ATP ile tümleştirme
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: f6f3ed75-d6bb-4966-a9a7-5339c4f3ebac
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 52445e15a4465f0fa4b399cf99ccf6620db7a572
ms.sourcegitcommit: 59ed430fa0cd8ac34a70609026ec5fc2f5972f57
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2018
ms.locfileid: "49480693"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*

# <a name="integrate-azure-atp-with-windows-defender-atp"></a>Azure ATP Windows Defender ATP ile tümleştirme

Azure Gelişmiş tehdit koruması, Azure ATP daha eksiksiz bir tehdit koruması çözümü için Windows Defender ATP ile tümleştirmenize olanak sağlar. Azure ATP etki alanı denetleyicileriniz üzerindeki trafiği izlerken, Windows Defender ATP birlikte ortamınızı korumaya tek bir arabirim sağlayan uç noktalarınızı izler.

Windows Defender ATP Azure ATP ile tümleştirerek, iki hizmet de tam gücünden yararlanın ve, ortamınızın güvenliğini de dahil olmak üzere:

- Azure ATP algılayıcı ve tek başına algılayıcı: doğrudan etki alanı denetleyicileri veya kimlik doğrulaması (Kerberos, DNS, RPC, NTLM ve diğerleri gibi) birden çok protokolün ağ trafiğini yakalamak ve ayrıştırmak için ATP için bağlantı noktası yansıtma etki alanı denetleyicilerinizden üzerine yerleştirilebilir Yetkilendirme ve bilgi toplama. 

-   Uç nokta davranış sensörlerini: Windows 10'da katıştırılmış, bu sensörlerden ve davranış sinyalleri işletim sisteminden (örneğin, işlem, kayıt defteri, dosya ve ağ iletişimi) işlem verilerini toplar ve bu algılayıcı, özel, yalıtılmış, buluta gönderir Windows Defender ATP örneği.

- Bulut güvenlik analizleri: büyük veri, makine öğrenimi ve benzersiz Microsoft görünümü yararlanarak Windows ekosisteminde (gibi [Microsoft Kötü Amaçlı Yazılımları Temizleme Aracı](https://www.microsoft.com/download/malicious-software-removal-tool-details.aspx)), Kurumsal bulut ürünleri (örneğin, Office 365 için) ve çevrimiçi varlıkların (Bing ve SmartScreen URL saygınlığı gibi), davranış sinyalleri Öngörüler algılamalar, çevrilmiş ve Gelişmiş tehditlere yanıt önerilir.

- Tehdit bilgileri: güvenliği ekiplerinin Microsoft arayanlar tarafından oluşturulan ve iş ortakları tarafından sağlanan tehdit bilgileri tarafından Genişletilmiş, tehdit zekası sağlar saldırgan araçları, teknikleri, yordamları tanımlamak ve oluşturmak Windows Defender ATP uyarıları Bu etkinlikler toplanan algılayıcı verilerini gözlenmiştir.

Azure ATP teknolojisi siber saldırı ölüm zincirinin, belirtilen çeşitli aşamalarına odaklanarak birden çok şüpheli etkinliği algılar:

- Keşif aşamasında saldırganlar ortamın nasıl oluşturulduğunu bilgi toplamak, hangi farklı varlıklardır ve hangi varlık yoktur. Bunlar genellikle burada saldırının sonraki aşamaları için kendi planı oluşturun.

- Yanal hareket döngüsü aşamasında saldırgan, ağınızdaki saldırı yüzeyini genişletmek için zaman ve çaba harcar.

- Etki alanı hakimiyeti (Kalıcılık) aşamasında saldırgan bunları çeşitli ayarlar giriş noktaları, kimlik bilgileri ve teknikler kullanarak sürdürmesine olanak sağlayan bilgileri yakalar.

Aynı anda sağlayarak Microsoft teknolojisini ve uzmanlığını Gelişmiş siber saldırılardan algılamak için Windows Defender ATP yararlanır:

- Davranış tabanlı bulut destekli, Gelişmiş saldırı algılama<br></br>(Algılama ihlal sonrası) tüm diğer savunmaları yapılan saldırıları bulur, bunların etkinliklerini uç noktalarda Gizle çalışılırken bilinen ve Bilinmeyen saldırganlar için eyleme dönüştürülebilecek, ilişkili uyarıları sağlar.

- Adli araştırma ve risk azaltma için zengin zaman çizelgesi<br></br>Kolayca ihlal ya da zengin makine zaman çizelgesi aracılığıyla herhangi bir makinede şüpheli davranış kapsamını araştırın. Dosya, URL'ler ve ağ üzerinden ağ bağlantısı envanteri. Herhangi bir dosya veya URL için ayrıntılı toplama ve çözümleme ("detonation") kullanarak ek Öngörüler elde edin.

- Benzersiz tehdit zekası Bilgi Bankası'ndaki yerleşik<br></br>Optik her tehdit için aktör ayrıntıları ve hedefi bağlam sağlar benzersiz tehdit algılama-birleştirme birinci ve üçüncü taraf iş zekası kaynakları temel.

## <a name="prerequisites"></a>Önkoşullar

Bu özelliği etkinleştirmek için hem Azure ATP hem de Windows Defender ATP için bir lisans gerekir. 


## <a name="how-to-integrate-azure-atp-with-windows-defender-atp"></a>Azure ATP Windows Defender ATP ile tümleştirme

1. Azure ATP Portalı'nda açmak **yapılandırma**. 

    ![Azure ATP yapılandırma menüsü](./media/atp-configuration-wd.png)
2. Yapılandırmaları listesinde **Windows Defender ATP** ve tümleştirme getirin **üzerinde**. 

    ![Windows Defender'ın tümleştirmesini etkinleştirme](./media/enable-integration.png)


3. İçinde [Windows Defender ATP portalına](https://securitycenter.windows.com/preferences/advanced)Git **ayarları**, **Gelişmiş Özellikler** ayarlayıp **Azure ATP tümleştirme** için  **ON**. 

    ![Windows Defender ATP etkinleştir tümleştirme](./media/wd-atp-enable.png)

4. Azure ATP portalında Tümleştirme durumunu denetlemek için Git **ayarları** > **Windows Defender ATP tümleştirme**. Tümleştirme durumunu görebilir ve bir şeyler yanlış ise, bir hata görürsünüz. 

## <a name="how-it-works"></a>Nasıl Çalışır?

Azure ATP ve Windows Defender ATP tam olarak, Azure ATP portalı, Mini profil açılır ve varlık profili sayfası tümleştirilmiştir sonra Windows Defender ATP'de var. her varlık, Windows Defender ATP ile tümleşik olduğunu göstermek için bir rozet içerir. 

 ![Windows Defender ATP uyarıları](./media/profile-alerts-wd.png)

Windows Defender atp'de uyarı varlık varsa kaç uyarıları ortaya çıktı size bildirmek üzere bir sayı rozet yanındaki yoktur.

 ![Azure ATP uyarıları](./media/atp-integrated-wd-icon-alerts.png)

Rozeti oylayıp tıklarsanız, Windows Defender ATP portalına burada görüntüleyebilir ve Uyarıları gidermek kapsama alınır. Varlık Windows Defender ATP tarafından tanınmıyorsa rozet gri renkte gösterilir. 

 ![Windows Defender ATP gri](./media/wd-grey.png)

Windows Defender ATP Portalı'ndan Azure ATP uyarıları görüntülemek için bir uç noktaya tıklayın. Windows Defender ATP bu varlık için uyarıları tıklarsanız, ATA'daki varlığın profil sayfası açılır. 
 
 > [!NOTE]
 > Şu anda yalnızca kullanıcı ve şirket içi makineler Windows Defender ATP ile Azure ATP tümleştirme destekler AD. Azure ad kullanıcıları ve Azure'da yönetilen sanal makineler, tümleşik bir parçası olarak görüntülenmeyecek 

![Windows Defender ATP uyarıları](./media/wd-atp-alerts.png)


## <a name="see-also"></a>Ayrıca Bkz.

- [Azure ATP ile yanal hareket yollarını araştırma](use-case-lateral-movement-path.md)
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Azure ATP mimarisi](atp-architecture.md)
- [ATP yükleyin](install-atp-step1.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)

