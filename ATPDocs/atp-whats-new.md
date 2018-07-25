---
title: ATA'daki yenilikler | Microsoft Docs
description: Azure ATP en son sürümlerini açıklar ve her sürümdeki yenilikler hakkında bilgi sağlar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/21/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 7d0f33db-2513-4146-a395-290e001f4199
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: be3a4315384d5df03b1f04f0a71a960c66858b05
ms.sourcegitcommit: 63a36cd96aec30e90dd77bee1d0bddb13d2c4c64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39227232"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="whats-new-in-azure-atp"></a>ATA'daki yenilikler 


## <a name="azure-atp-release-241"></a>Azure ATP yayın 2.41

22 Temmuz 2018'de yayınlanan

- **Azure ATP çok ormanlı destek kademeli olarak (Önizleme) sunulacaktır** <br> Azure ATP ormanlar arasında yeteneği etkinliğini izleme ve profil kullanıcılar sağlayan birden çok ormanı olan kuruluşlar artık desteklenir. Bu yeni özellik sağlar:

  - Görüntüleyebilir ve tek bir cam bölmeyle gelen birden çok orman genelinde kullanıcılar tarafından gerçekleştirilen etkinlikleri araştırın.
  - Algılama artırır ve Gelişmiş Active Directory Tümleştirmesi ve hesap çözüm sağlayarak hatalı pozitif sonuçları azaltır.
  - Daha iyi izleme uyarıları ve çapraz kuruluş kapsamı için raporlama alın.


-   **Yeni algılamalar: DCShadow**<br>Etki alanı denetleyicisi gölge (DCShadow) saldırılarına karşı korumaya yardımcı olmak üzere iki yeni algılamalar eklendi:

    -   Şüpheli etki alanı denetleyicisi yükseltme (olası DCShadow saldırısı) – bu algılama yöntemi, bir makine bir etki alanı denetleyicisi özelliklerini saldırıları algılamaya yardımcı olur ve diğer etki alanı denetleyicileri, etki alanınızdaki değişiklikleri yaymak için çoğaltma kullanmaya çalışır.

    -   Şüpheli çoğaltma isteği (olası DCShadow saldırısı) – bu algılama dizin nesneleri değiştirmek için etki alanı denetleyicileri olmayan makineler, DC yükseltmesine gerçekleştirmeye saldırılarına karşı korumaya yardımcı olur.

-   **Şifreleme düşürme bilgileri geliştirildi**<br>Şifreleme düşürme artık algılama saldırısı algılandı belirli türü ile ilgili daha fazla bilgi sağlar:-karmayı, altın ve iskelet anahtar. Ayrıca, bu uyarılar araştırmayı daha kolay etkinleştirmek için toplanmış.
- Bu sürüm, düzeltmeleri ve geliştirmeleri için birden çok sorunları içerir. 



## <a name="azure-atp-release-240"></a>Azure ATP yayın 2.40

15 Temmuz 2018'de yayınlanan

- Pass--ticket algılama artık uyarı ayrıntıları sayfasındaki bir kanıt bölüm içerir. Bu uyarıyla ilgili araştırma için ek bilgi sağlar.

- Öznitelikleri üzerinde olan ve kapalı olan daha iyi anlamak için dizin verilerini bir kullanıcının profilinde bulunabilir, kullanıcı erişimi denetim bayrakları bir gösterge artık içerir.  

## <a name="azure-atp-release-239"></a>Azure ATP yayın 2.39

Yayın Tarihi: 5 Temmuz 2018
-   **Eklenen yeni algılama: Kerberos altın bileti - varolmayan hesabı** (Önizleme)<br>Bu yeni algılama kuruluşunuz, etki alanında var olmayan bir hesap için bir altın anahtar oluşturulduğu saldırılarına karşı korumanıza yardımcı olur. Daha fazla bilgi için [Azure Gelişmiş tehdit koruması şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md#golden-ticket)

- Bu sürüm, düzeltmeleri ve geliştirmeleri için birden çok sorunları içerir. 


## <a name="azure-atp-release-238"></a>Azure ATP yayın 2.38

1 Temmuz 2018'de yayınlanan

- Bu sürüm, düzeltmeler ve geliştirmeler Azure ATP Portalı'nın yanı sıra birden çok sorunlar için geliştirmeler içerir.

## <a name="azure-atp-release-237"></a>Azure ATP yayın 2.37

24 Haziran 2018'de yayınlanan

- Bu sürüm, düzeltmeleri ve geliştirmeleri için birden çok sorunları içerir. 

## <a name="azure-atp-release-236"></a>Azure ATP yayın 2,36

Yayın Tarihi: 17 Haziran 2018

- Bu sürüm, düzeltmeleri ve geliştirmeleri için birden çok sorunları içerir. 


## <a name="azure-atp-release-235"></a>Azure ATP yayın 2.35

Yayın Tarihi: 10 Haziran 2018
 
- **Yeni Önizleme algılamalar**<br></br>Şimdi, Azure ATP bir bulut hizmeti olduğunu faydalanması burada yeni özellikler olarak dağıtılabilecek döngüleri--hızlı ve yeni algılamalar ile mümkün olan en kısa sürede sağlayın. Bu yeni algılamalar "ilk olduklarında preview" serbest olarak etiketlenir. Genellikle yeni bir algılama preview'dan birkaç hafta içinde genel kullanılabilirlik taşınır. Varsayılan olarak Önizleme algılamalar görürsünüz. İletişimlerini hakkında daha fazla bilgi için bkz: [Önizleme algılamalar](working-with-suspicious-activities.md#preview-detections).
 
- **Şüpheli VPN algılama**<br></br>Bu yayın, bir önizleme sürümünü şüpheli VPN algılama tanıtır. Azure ATP makineler de dahil olmak üzere kullanıcı VPN davranışını açan kullanıcılar ve kullanıcı bağlantı konumları öğrenir ve bir sapma Beklenen davranış olduğunda sizi uyarır. Daha fazla bilgi için [şüpheli VPN algılama](suspicious-activity-guide.md#suspicious-vpn-detection).

- **Ertelenmiş güncelleştirme**<br></br>Artık Azure ATP algılayıcı daha sonra Azure ATP her güncelleştirdiğinde güncelleştirmek için ayarlanacak seçenek var. Artık her Azure ATP algılayıcısını ayarlayabilirsiniz **Gecikmeli güncelleştirme** böylece 24 saat sonra Azure ATP bulut hizmet güncelleştirmeleri güncelleştirir. Bu özellik, belirli test sensörlerden güncelleştirmesinde test etmek ve yalnızca, üretim sensörlerden daha sonra güncelleştirmek sağlar. İlk güncelleştirme döngüsü sırasında bir sorun bulursanız, bir destek bileti açın. Daha fazla bilgi için [güncelleştirme Azure ATP algılayıcı](sensor-update.md).

- **Güncelleştirilmiş olağan dışı protokol uygulaması algılama**<br></br>Olağan dışı protokol uygulaması algılama artık daha fazla bilgi sağlar. Hangi olası saldırı aracı Azure ATP şüphelerini bakın ağınızdaki İşte artık bunu yapabilirsiniz. Daha fazla bilgi için [şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md).
 
- **Güncel olmayan sensör Uyarısı**<br></br>Azure ATP algılayıcı eski üçten fazla sürümleri olup olmadığını size bildirmek için yeni bir izleme uyarı içerir. Bu uyarıyı görürseniz, algılayıcı güncelleştirme veya algılayıcı neden otomatik olarak güncelleştirilmiyor araştırmak gerekir. Uyarı almaya devam ederseniz, kaldırın ve algılayıcıyı yükleyin.

- Bu sürüm, düzeltmeleri ve geliştirmeleri için birden çok sorunları içerir. 

## <a name="azure-atp-release-234"></a>Azure ATP yayın 2.34

3 Haziran 2018'de yayınlanan
 
- Bu sürüm, düzeltmeleri ve geliştirmeleri için birden çok sorunları içerir. 

 
## <a name="azure-atp-release-233"></a>Azure ATP yayın 2.33

Yayın Tarihi: 27 Mayıs 2018

- Önizleme özelliği: Azure ATP artık yeni diller ve 13 yeni yerel ayarları destekler:
    - Çekçe
    - Macarca
    - İtalyanca
    - Kore dili
    - Hollanda dili
    - Lehçe
    - Portekizce (Brezilya)
    - Portekizce (Portekiz)
    - Rusya
    - İsveç dili
    - Türkçe
    - Çince (Çin)
    - Çince (Tayvan)



## <a name="azure-atp-release-232"></a>Azure ATP yayın 2.32

Yayın Tarihi: 13 Mayıs 2018
 
- Bu sürüm, düzeltmeleri ve geliştirmeleri için birden çok sorunları içerir. 

## <a name="azure-atp-release-231"></a>Azure ATP yayın 2.31

6 Mayıs 2018'de yayınlanan
 
- Ad çözümlemesi için iyileştirmeler yapıldı. RPC ve NetBIOS etkin çözüm yanı sıra bu çalışmaların bir parçası olarak algılayıcı RDP uç noktası için bir TLS istemci Hello paket sorunu (3389 numaralı) bağlantı noktası. 
- Bu sürüm, düzeltmeleri ve geliştirmeleri için birden çok sorunları içerir. 

## <a name="azure-atp-release-230"></a>Azure ATP yayın 2.30

29 Nisan 2018'de yayınlanan
 
- Şifreleme düşürme şüpheli etkinlikleri artık Azure ATP tarafından algılanan bir şifreleme düşürme etkinliği ilkelerinden olduğunu düşündüğünüz neden Belirtiler açıklayan bir kanıt bölümü içerir. 
-   Azure ATP, uyarı ve raporları izleme şüpheli etkinlikleri de dahil olmak üzere Azure ATP ' gönderilen tüm e-postalar için artık Azure e-posta Orchestrator kullanır. Bu e-posta bildirimleri artık kullanım kolaylığı için tutarlı bir biçim izleyin ve Excel dosyalarını konsoldan indirilmesi e-postasındaki bağlanacağı görürsünüz.
 
 

## <a name="azure-atp-release-229"></a>Azure ATP yayın 2.29

22 Nisan 2018'de yayınlanan
 
- Bu sürüm, düzeltmeleri ve geliştirmeleri için birden çok sorunları içerir. 
 
 
## <a name="azure-atp-release-228"></a>Azure ATP yayın 2.28

15 Nisan 2018'de yayınlanan
 
-   Artık Azure ATP kullanıcı ve Azure ATP görüntüleyiciler rol gruplarının üyeleri olan kullanıcılar, izleme uyarıları görmek için izinlere sahip.
- Bu sürüm, düzeltmeleri ve geliştirmeleri için birden çok sorunları içerir. 


## <a name="azure-atp-release-227"></a>Azure ATP yayın 2,27

8 Nisan 2018'de yayınlanan

- Üst gezinti çubuğunda kullanıcı geri bildirim sağlama yeteneği artık var. Menü çubuğunda gülen yüz tıklayarak Azure Gelişmiş tehdit koruması ekibine geri bildirim ile bir e-posta göndermenize olanak sağlar.

- Bu sürüm, düzeltmeleri ve geliştirmeleri için birden çok sorunları içerir. 
 

## <a name="azure-atp-release-226"></a>Azure ATP yayın 2.26

Yayın Tarihi: 25 Mart 2018

- (Bir şüpheli etkinlik değil meşru bir eylem), zararsız pozitif sonuç olarak tanımlayan bir şüpheli etkinlik Azure ATP uyarıları, bilgisayarlar ve de dahil olmak üzere daha fazla algılamaları için IP adreslerini hariç tutmak için seçeneğiniz vardır: şifrelemeyi düşürme, LDAP deneme yanılma, sahte PAC, deneme yanılma yoluyla yapılan zorla ve Pass--hash.
-   Azure ATP algılayıcısı performansı İyileştirildi.
-   Yeni bir bölgeye eklenen çalışma alanı dağıtımı için bir çalışma alanında Asya artık dağıtabilirsiniz. 


## <a name="azure-atp-release-225"></a>Azure ATP yayın 2,25

Yayın Tarihi: 18 Mart 2018

- Çok faktörlü kimlik doğrulaması (MFA), ATA'daki artık desteklenmektedir. Mfa'yı kullanarak kiracının artık Azure ATP portalı girebilirsiniz.
- Azure ATP artık sahip bir [ **sistem durumu** ](https://health.atp.azure.com/) çalışma alanı Yönetim Portalı algılamalar ile bir sorun varsa ve algılayıcı gönderebilmesi için ise yukarı ve etkin olup dair bilgi sağlamak için sayfa Bulut trafiği. Erişebildiğiniz **sistem durumu** Azure ATP menü çubuğundan.


## <a name="azure-atp-release-224"></a>Azure ATP yayın 2,24

Yayın Tarihi: 11 Mart 2018

**Yeni ve güncelleştirilmiş algılamalar**
  - Şüpheli hizmet oluşturma – saldırganlar, ağınızdaki kuşkulu hizmetlerini çalıştırmak çalışır. Belirli bir bilgisayardaki şüpheli yeni bir hizmetinin çalışıp çalışmadığını belirlediğinde azure ATP artık bir uyarı başlatır. Bu Algılama olayları (ağ trafiği değil) temel alır ve Azure ATP olay 7045 ilettiğini ağınızda herhangi bir etki alanı denetleyicisinde algılandı. Daha fazla bilgi için [şüpheli etkinlik Kılavuzu](suspicious-activity-guide.md).

**Gelişmiş araştırma**
  - Azure ATP içeren bir zenginleştirilmiş [varlık profili](entity-profiles.md). Varlık profili kullanıcı etkinlikleri bu erişmeleri kaynakları içerir yakından incelenmesi için tasarlanmış bir platform, bunlar oturum açmış bilgisayarlar ve çok daha fazlasını sağlar. Varlık profili de dizin verilerini sağlar ve böylece olası ihlallerini kuruluşunuzdaki hakkında daha fazla bilgi, varlıktan ya da olası yanal hareket yollarını tanımlamak üzere sağlar.

  - ATP olanak el ile etiketi varlıklar olarak *hassas* algılama ve izleme geliştirmek için. Bu etiketleme gizli Grup değişikliği algılama gibi birçok Azure ATP algılamalar etkiler ve [yanal hareket yolunun](use-case-lateral-movement-path.md), hassas olarak kabul edilen varlıkların kullanır.

**Araştırmanıza yardımcı olacak yeni raporlar**
  - [Parolalarını düz metin raporda ifşa](reports.md) hizmetleri hesabı kimlik bilgileri düz metin olarak gönderilir gönderdiğinizde algılamanıza olanak tanır. Bu, hizmetleri araştırın ve ağ güvenlik düzeyini artırmak sağlar. Bu rapor, düz metin olarak şüpheli etkinlik uyarılarını değiştirir.
  - [Yana hareket yollarını hassas hesapları raporuna](reports.md) yanal hareket yollarını sunulan hassas hesapları listeler. Bu, bu yollar azaltmak ve saldırı yüzeyi riski en aza indirmek için ağ sağlamlaştırma sağlar. Bu, böylece bunlar sanal güvenlik ikramiye isabet kadar saldırganlar ağınızdaki kullanıcılar ve bilgisayarlar arasında taşıyamazsınız yanal hareket önlemenize olanak sağlar: küçük harf duyarlı yönetici hesabı kimlik bilgilerinizle.

- Kolayca bir bağlantıdan belgelerine erişim sağlayan bir şüpheli etkinlik uyarısı içinde görüntülemek için artık [uygulayabileceğiniz araştırma adımlarının](suspicious-activity-guide.md). 

**Performans iyileştirmeleri**
 -  Azure ATP algılayıcısı altyapı performans için İyileştirildi: Toplu trafik görünümünü CPU ve paket işlem hattının etkinleştirir ve SSL oturumlarını DC'ye en aza indirmek için etki alanı denetleyicilerine yuva kullanır.

## <a name="see-also"></a>Ayrıca bkz:
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)