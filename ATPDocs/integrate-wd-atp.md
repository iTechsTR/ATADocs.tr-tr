---
title: Windows Defender ATP ile Azure Advanced Threat Protection tümleştirme | Microsoft Docs
description: Azure Advanced Threat Protection tam tehdit algılama kapsamı için Windows Defender ATP ile tümleştirme
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/16/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: f6f3ed75-d6bb-4966-a9a7-5339c4f3ebac
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 17ade33a55039eaf8abc98901cdab9ebeef850c5
ms.sourcegitcommit: 714a01edc9006b38d1163d03852dafc2a5fddb5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*

# <a name="integrating-azure-atp-with-windows-defender-atp"></a>Azure ATP Windows Defender ATP ile tümleştirme

Azure Advanced Threat Protection, Azure ATP bile daha eksiksiz bir tehdit koruma çözüm için Windows Defender ATP ile tümleştirmenize olanak sağlar. Azure ATP etki alanı denetleyicileriniz trafiğinde izlerken, Windows Defender ATP birlikte ortamınızı koruyabilmeniz için tek bir arabirim sağlayan uç noktalarınızı izler.

> [!NOTE]
> Yalnızca, bir Windows Defender ATP özel Önizleme müşterisiyseniz tümleştirme şu anda etkin.
 
Windows Defender ATP Azure ATP tümleştirerek, her iki hizmet gücünden yararlanan ve ortamınızı güvenli dahil olmak üzere:

- Azure ATP algılayıcılar ve tek başına algılayıcılar: doğrudan etki alanı denetleyicileri veya yakalama ve kimlik doğrulaması (Kerberos, DNS, RPC, NTLM ve diğerleri gibi) birden çok protokollerin ağ trafiğini ayrıştırmak için ATP için bağlantı noktası yansıtma etki alanı denetleyicilerinden üzerinde kalmaya devam Yetkilendirme ve bilgi toplama. 

-   Uç nokta davranış algılayıcılar: Windows 10'da katıştırılmış, bu algılayıcılar toplayıp işletim sisteminden (örneğin, işlem, kayıt defteri, dosya ve ağ iletişimi) davranış sinyalleri işlemek ve özel, yalıtılmış, bulut için bu algılayıcı verileri gönderir. Windows Defender ATP örneği.

- Bulut güvenlik analizleri: büyük veri, machine learning ve benzersiz Microsoft görünüm Windows ekosistemi yararlanarak (gibi [Microsoft Kötü Amaçlı Yazılımları Temizleme Aracı](https://www.microsoft.com/download/malicious-software-removal-tool-details.aspx)), Kurumsal bulut ürünleri (örneğin, Office 365 için) ve çevrimiçi varlıkları (Bing ve SmartScreen URL saygınlığı gibi), davranış sinyalleri Öngörüler, algılama, çevrilen ve Gelişmiş tehditleri yanıtlarını önerilir.

- Tehdit Intelligence: güvenlik ekiplerinden Microsoft arayanlar tarafından oluşturulan ve iş ortakları tarafından sağlanan tehdit bilgileri tarafından genişletilebilir, Intelligence etkinleştirir saldırgan araçları, teknikleri ve yordamları tanımlamak ve oluşturmak Windows Defender ATP tehdit ne zaman uyarıları Bu, toplanan algılayıcı verileri gözetilir.

Azure ATP teknolojisi siber saldırı sonlandırma zinciri de dahil olmak üzere çeşitli aşamaları odaklanan birden çok kuşkulu etkinlikleri algılar:

- Keşif sırasında saldırganlar ortamı nasıl yapılandırıldığını bilgi toplamak, hangi farklı varlıkları içerir ve hangi varlık yoktur. Bunlar genellikle planlarına saldırı sonraki aşamaları için yapı oluşturma.

- Yanal hareket döngüsü aşamasında saldırgan, ağınızdaki saldırı yüzeyini genişletmek için zaman ve çaba harcar.

- Etki alanı hakimiyeti (kalıcı) sırasında bir saldırganın çeşitli ayarlar giriş noktaları, kimlik bilgileri ve teknikleri kullanarak kendi kampanya sürdürmeye vermeden bilgilerini yakalar.

Aynı anda sağlayan Microsoft teknolojisi ve uzmanlık Gelişmiş siber saldırıları algılamak için Windows Defender ATP yararlanır:

- Davranış tabanlı bulut yönetimli, Gelişmiş saldırı algılama<br></br>(İhlali algılama sonrası) tüm diğer savunma yapılan saldırıları bulur, bunların etkinliklerini uç noktaları Gizle çalışılırken bilinen ve bilinmeyen rakiplerin için işlem yapılabilir, bağıntılı uyarılar sağlar.

- Adli araştırma ve azaltma için zengin zaman çizelgesi<br></br>Kolayca ihlal ya da şüpheli davranışları zengin makine zaman çizelgesi aracılığıyla herhangi bir makinede kapsamını araştırın. Dosya, URL'ler ve ağ üzerinden ağ bağlantısı stok. Herhangi bir dosya veya URL için derin toplama ve analiz ("detonation") kullanılarak ek kavramak.

- Benzersiz tehdit yönetim bilgileri Bilgi Bankası'nda oluşturulmuş<br></br>Benzersiz tehdit optik her tehdit Intel tabanlı algılama için – birleştirme ilk ve üçüncü taraf kaynakları aktör ayrıntıları ve hedefi bağlamı sağlar.

## <a name="prerequisites"></a>Önkoşullar

Bu özelliği etkinleştirmek için bir lisans Azure ATP ve Windows Defender ATP için gerekir. 


## <a name="how-to-integrate-azure-atp-with-windows-defender-atp"></a>Azure ATP Windows Defender ATP ile tümleştirme

1. Olarak tümleştirmek istediğiniz çalışma kümesi **birincil**. Yalnızca bir çalışma alanı birincil çalışma olabilir ve yalnızca birincil çalışma diğer hizmetleriyle tümleştirebilirsiniz. Belirli bir noktada gelecekte bu çalışma alanı artık birincil çalışma yapmak istediğiniz, ilk birincil olmayan ayarlamadan önce tümleştirme kaldırmanız gerekir.

 ![birincil çalışma](./media/primary-workspace.png)

2. Tıklatın **yapılandırma**ve altında **veri kaynakları** seçin **Windows Defender ATP**. Bağlantısını tıklatın **çalışma Yönetim**. Bu yalnızca bir lisans için Windows Defender ATP varsa ve zaten devreye alma işlemi için Windows Defender ATP gerçekleştirilen kullanılabilir. 

3. Birincil çalışma alanınızda, ayarlar dişlisine tıklayın.

 ![Çalışma alanı tümleştirme](./media/edit-workspace.png)
 
3. Tümleştirmeyi ayarlamak **üzerinde**. 

 ![Tümleştirmeyi Etkinleştir](./media/enable-integration.png)

4. İçinde [Windows Defender ATP portal](https://beta.securitycenter.windows.com/preferences/advanced)gidin **ayarları**, **Gelişmiş Özellikler** ve **Azure ATP tümleştirme** için  **ON**. 

 ![Windows Defender ATP etkinleştir tümleştirme](./media/wd-atp-enable.png)

5. Azure ATP çalışma portalında Tümleştirme durumunu denetlemek için Git **ayarları** ve ardından **Windows Defender ATP tümleştirme**. Tümleştirme durumunu görebilirsiniz; bir şeyler yanlış ise, bir hata görürsünüz. Ayrıca, hangi çalışma alanında Windows Defender ATP ile tümleşik görebilirsiniz.

## <a name="how-it-works"></a>Nasıl Çalışır?

Azure ATP ve Windows Defender ATP tam olarak, Azure ATP çalışma portal, Mini profil açılır ve varlık profili sayfasını tümleşiktir sonra Windows Defender ATP var. her varlık Windows ile tümleşik olduğunu göstermek için bir gösterge içerir. Defender ATP. 

 ![Windows Defender ATP uyarıları](./media/profile-alerts-wd.png)

Varlık Windows Defender ATP uyarılar içeriyorsa, kaç tane uyarılar ortaya çıktı size bildirmek için bir sayı rozet yanındaki yoktur.

 ![Azure ATP uyarıları](./media/atp-integrated-wd-icon-alerts.png)

Üzerinde rozet tıklarsanız, burada görüntüleyebilir ve Uyarıları azaltmak Windows Defender ATP portalına yönlendirilirsiniz. Varlık Windows Defender ATP tarafından tanınmıyorsa rozet gri renkte görüntülenir. 

 ![Windows Defender ATP gri](./media/wd-grey.png)

Windows Defender ATP Portalı'nda bir noktadaki tıklattığınızda Azure ATP uyarılarını görüntüleyebilirsiniz. Windows Defender ATP bu varlık için Uyarılardaki tıklarsanız, Azure ATP varlığın profili sayfasını açar. 
 
 > ! [NOT] Şu anda, Windows Defender ATP ile Azure ATP tümleştirme yalnızca kullanıcılar ve şirket içi makineler destekler AD. Azure AD kullanıcıları ve Azure'da yönetilen sanal makineler tümleştirme bir parçası olarak görüntülenmeyecek 

![Windows Defender ATP uyarıları](./media/wd-atp-alerts.png)


## <a name="see-also"></a>Ayrıca bkz:

- [Yanal hareket yollarını Azure ATP ile araştırma](use-case-lateral-movement-path.md)
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Azure ATP mimarisi](atp-architecture.md)
- [ATP yükleyin](install-atp-step1.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)

