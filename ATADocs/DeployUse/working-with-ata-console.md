---
title: "ATA Konsolu ile çalışma | Microsoft Docs"
description: "ATA Konsolu’nda oturum açma işlemi ve konsolun bileşenleri açıklanır"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1bf264d9-9697-44b5-9533-e1c498da4f07
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7dc860fe31da1374a4466f8e56e55e6520bc10dc
ms.openlocfilehash: c315b3b307628b31b42a6d393513b86ce88e8aa1


---

*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*



# <a name="working-with-the-ata-console"></a>ATA Konsolu’yla çalışma

ATA tarafından algılanan kuşkulu etkinliği izlemek ve yanıtlamak için ATA Konsolu’nu kullanın.

## <a name="enabling-access-to-the-ata-console"></a>ATA Konsolu’na erişimi etkinleştirme
ATA Konsolunda başarıyla oturum açmak amacıyla, ATA Konsoluna erişmek için doğru ATA rolünün atandığı bir kullanıcıyla oturum açmanız gerekir. ATA’da role dayalı erişim denetimi (RBAC) hakkında daha fazla bilgi için bkz. [ATA rol gruplarıyla çalışma](ata-role-groups.md).

## <a name="logging-into-the-ata-console"></a>ATA Konsolu’nda oturum açma

1. ATA Center sunucusunda, masaüstündeki **Microsoft ATA Konsolu** simgesine tıklayın veya tarayıcıyı açıp ATA Konsolu’na göz atın.

    ![ATA sunucusu simgesi](media/ata-server-icon.png)

>[!NOTE]
> Ayrıca ATA Center veya ATA Gateway’den tarayıcıyı açabilir ve ATA Center yüklemesinde ATA Konsolu için yapılandırdığınız IP adresine göz atabilirsiniz.    

2.  Kullanıcı adınızla parolanızı girin ve **Oturum aç**’a tıklayın.

![ATA oturum açma ekranının resmi](media/ATA-log-in-screen.png)


## <a name="the-ata-console"></a>ATA Konsolu

ATA Konsolu tarih sırasına göre tüm kuşkulu etkinliklerin hızlı bir görünümünü sağlar. Herhangi bir etkinliği detayına gitmenize ve bu etkinliklere dayalı olarak eylemler yapmanıza olanak tanır. Konsol ayrıca, ATA ağındaki sorunları veya kuşkulu sayılan yeni etkinlikleri vurgulamak için uyarılar ve bildirimler de görüntüler.

Bunlar ATA Konsolu’nun başlıca öğeleridir.


### <a name="attack-time-line"></a>Saldırı zaman çizelgesi

Bu, ATA Konsolu’nda oturum açtığınızda gittiğiniz varsayılan giriş sayfasıdır. Varsayılan olarak, tüm kuşkulu etkinliler saldırı zaman çizelgesinde gösterilir. Saldırı zaman çizelgesine filtre uygulayarak, Tüm, Açık, Çıkarılan veya Çözülen kuşkulu etkinlikleri görüntüleyebilirsiniz. Ayrıca, her etkinliğe atanmış olan önem düzeyini de görebilirsiniz.

![ATA saldırı zaman çizelgesi resmi](media/attack-timeline-1.7.png)

Daha fazla bilgi için bkz. [Kuşkulu etkinliklerle çalışma](/advanced-threat-analytics/deploy-use/working-with-suspicious-activities)

### <a name="notification-bar"></a>Bildirim çubuğu

Kuşkulu bir etkinlik algılandığında, bildirim çubuğu sağ tarafta otomatik olarak açılır. Son oturum açmanızdan bu yana yeni kuşkulu etkinlikler varsa, başarılı oturum açma işleminden sonra bildirim çubuğu açılır. İstediğiniz zaman sağ taraftaki oka tıklayarak bildirim çubuğunu açabilirsiniz.

![ATA bildirim çubuğu resmi](media/notification-bar-1.7.png)

### <a name="filtering-panel"></a>Filtreleme paneli

Kuşkulu etkinlikleri Durum ve Önem Derecesi’ne göre filtreleyerek, saldırı zaman çizelgesinde veya varlık profili kuşkulu etkinlikler sekmesinde hangi etkinliklerin görüntüleneceğini belirtebilirsiniz.

### <a name="search-bar"></a>Arama çubuğu

Üst menüde arama çubuğunu bulacaksınız. ATA’da belirli kullanıcı, bilgisayar veya grupları arayabilirsiniz. Denemek için, yazmaya başlamanız yeterlidir.

![ATA konsolu arama resmi](media/ATA-console-search.png)

### <a name="health-center"></a>Sistem Durumu Merkezi

Sistem Durumu Merkezi, ATA dağıtımınızda düzgün çalışmayan bir şey olduğunda size uyarılar sağlar.

![ATA sistem durumu merkezinin resmi](media/ATA-Health-Issue.jpg)

Sisteminizde bağlantı hatası veya bağlantısı kesik ATA Gateway gibi herhangi bir sorunla karşılaşıldığında, Sistem Durumu Merkezi simgesi kırmızı bir nokta göstererek bu durumu öğrenmenizi sağlar. ![ATA sistem durumu merkezi kırmızı noktasının resmi](media/ATA-Health-Center-Alert-red-dot.png)

Sistem Durumu Merkezi uyarıları bırakılabilir veya çözülebilir ve bu uyarılar önem derecesine bağlı olarak Yüksek, Orta ve Düşük kategorilerine ayrılır. Bir uyarıyı çözerseniz ve ATA hizmeti bunu hala etkin olarak algılıyorsa, uyarı otomatik olarak Açık uyarılar listesine taşınır. Sistem artık bir uyarı için neden olmadığını (durumun düzeltildiğini) algılarsa, uyarı otomatik olarak çözülen uyarı listesine taşınır.

### <a name="user-and-computer-profiles"></a>Kullanıcı ve bilgisayar profilleri

ATA, ağdaki her kullanıcı ve bilgisayar için bir profil oluşturur. ATA, kullanıcı profilinde grup üyeliği, son oturum açmalar ve son erişilen kaynaklar gibi genel bilgileri görüntüler.

![Kullanıcı profili](media/user-profile.png)

ATA, bilgisayar profilinde son oturum açmalar ve son erişilen kaynaklar gibi genel bilgileri görüntüler.

![Bilgisayar profili](media/computer-profile.png)

ATA, varlıklar (bilgisayarlar, cihazlar, kullanıcılar) hakkındaki genel bilgileri şu sayfalarda sağlar: Özet, Etkinlikler ve Kuşkulu Etkinlikler.

ATA’nın tümüyle çözümleyemediği bir profil, yanında gösterilen yarısı dolu daire simgesiyle tanımlanır.


![ATA çözümlenmemiş profilinin resmi](media/ATA-Unresolved-Profile.jpg)

### <a name="mini-profile"></a>Mini profil

Konsolun, kullanıcı veya bilgisayar gibi tek bir varlığın bulunduğu herhangi bir yerinde, farenizi varlığın üzerine getirirseniz otomatik olarak mini profil açılır ve varsa aşağıdaki bilgileri görüntüler:

![ATA mini profilinin resmi](media/ATA-mini-profile.jpg)

-   Ad

-   Resim

-   E-posta

-   Telefon

-   Önem derecesine göre kuşkulu etkinlik sayısı



## <a name="see-also"></a>Ayrıca bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Nov16_HO5-->


