---
title: Advanced Threat Analytics konsolunu anlama| Microsoft Docs
description: "ATA Konsolu’nda oturum açma işlemi ve konsolun bileşenleri açıklanır"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/28/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1bf264d9-9697-44b5-9533-e1c498da4f07
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 793273aeea3c78b54d4dc189acaff9bdf8ae58f9
ms.sourcegitcommit: 46dd0e695f16a0dd23bbfa140eba15ea6a34d7af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="working-with-the-ata-console"></a>ATA Konsolu’yla çalışma

ATA tarafından algılanan kuşkulu etkinliği izlemek ve yanıtlamak için ATA Konsolu’nu kullanın.

? anahtarını girmek, ATA Portal erişilebilirliği için klavye kısayollarını sağlayacaktır. 

## <a name="enabling-access-to-the-ata-console"></a>ATA Konsolu’na erişimi etkinleştirme
ATA Konsolunda başarıyla oturum açmak amacıyla, ATA Konsoluna erişmek için doğru ATA rolünün atandığı bir kullanıcıyla oturum açmanız gerekir. ATA’da role dayalı erişim denetimi (RBAC) hakkında daha fazla bilgi için bkz. [ATA rol gruplarıyla çalışma](ata-role-groups.md).

## <a name="logging-into-the-ata-console"></a>ATA Konsolu’nda oturum açma

>[!NOTE]
 > ATA 1.8 ve üzeri sürümlerde, ATA Konsolu’nda oturum açma işlemi çoklu oturum açma yoluyla gerçekleştirilir.

1. ATA Center sunucusunda, masaüstündeki **Microsoft ATA Konsolu** simgesine tıklayın veya tarayıcıyı açıp ATA Konsolu’na göz atın.

    ![ATA sunucusu simgesi](media/ata-server-icon.png)

 >[!NOTE]
 > Ayrıca ATA Center veya ATA Gateway’den tarayıcıyı açabilir ve ATA Center yüklemesinde ATA Konsolu için yapılandırdığınız IP adresine göz atabilirsiniz.    

2.  ATA Center’ın yüklü olduğu bilgisayar ile ATA Konsolu’na erişmeye çalıştığınız bilgisayar etki alanına katılmışsa ATA, Windows kimlik doğrulaması ile tümleştirilmiş çoklu oturum açmayı destekler - bilgisayarınızda zaten oturum açtıysanız ATA bu belirteci kullanarak ATA Konsolu’nda sizin için oturum açar. Ayrıca bir akıllı kart kullanarak da oturum açabilirsiniz. ATA’daki izinleriniz, [yönetici rolünüze](ata-role-groups.md) karşılık gelecektir.

 > [!NOTE]
 > ATA Konsolu’na erişmeye çalıştığınız bilgisayarda, ATA yönetici kullanıcı adı ve parolanızla oturum açmayı unutmayın. Bunun yerine tarayıcınızı farklı bir kullanıcı olarak çalıştırabilir veya Windows oturumunuzu kapatıp ATA yönetici kullanıcınızla oturum açabilirsiniz. ATA Konsolu’ndan kimlik bilgileri talep etmesini istemek için bir IP adresi kullanarak konsola erişin, böylece kimlik bilgilerinizi girmeniz istenecektir.

3. SSO kullanarak oturum açmak için ATA konsolunun tarayıcınızda yerel özel ağ sitesi olarak tanımlandığından ve konsola bir kısa ad veya yerel konak kullanarak erişebildiğinizden emin olun.

> [!NOTE]
> Her bir şüpheli etkinlik ve sistem durumu uyarısının günlüğe kaydedilmesinin yanı sıra, ATA Konsolu’nda yaptığınız tüm yapılandırma değişiklikleri ATA Center makinesindeki **Uygulamalar ve hizmetler günlüğü**’nün altında bulunan **Microsoft ATA** bölümündeki Windows Olay Günlüğü’nde denetlenir. ATA konsolunda gerçekleştirilen her oturum açma işlemi de denetlenir.<br></br>  ATA Gateway’i etkileyen yapılandırma da ATA Gateway makinesinin Windows Olay Günlüğü’ne kaydedilir. 



## <a name="the-ata-console"></a>ATA Konsolu

ATA Konsolu tarih sırasına göre tüm kuşkulu etkinliklerin hızlı bir görünümünü sağlar. Herhangi bir etkinliği detayına gitmenize ve bu etkinliklere dayalı olarak eylemler yapmanıza olanak tanır. Konsol ayrıca, ATA ağındaki sorunları veya kuşkulu sayılan yeni etkinlikleri vurgulamak için uyarılar ve bildirimler de görüntüler.

Bunlar ATA Konsolu’nun başlıca öğeleridir.


### <a name="attack-time-line"></a>Saldırı zaman çizelgesi

Bu, ATA Konsolu’nda oturum açtığınızda gittiğiniz varsayılan giriş sayfasıdır. Varsayılan olarak, tüm kuşkulu etkinliler saldırı zaman çizelgesinde gösterilir. Tüm, saldırı zaman çizelgesine filtre açık, çıkarılan veya Suppressed kuşkulu etkinlikler. Ayrıca, her etkinliğe atanmış olan önem düzeyini de görebilirsiniz.

![ATA saldırı zaman çizelgesi resmi](media/ATA-Suspicious-Activity-Timeline.jpg)

Daha fazla bilgi için bkz. [Kuşkulu etkinliklerle çalışma](working-with-suspicious-activities.md)

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

### <a name="user-and-computer-profiles"></a>Kullanıcı ve bilgisayar profilleri

ATA, ağdaki her kullanıcı ve bilgisayar için bir profil oluşturur. ATA, kullanıcı profilinde grup üyeliği, son oturum açmalar ve son erişilen kaynaklar gibi genel bilgileri görüntüler. Ayrıca kullanıcının VPN yoluyla bağlandığı tüm konumların bir listesini sağlar. ATA’nın gizli olarak değerlendirdiği grup üyeliklerinin listesi için aşağıya bakın.

![Kullanıcı profili](media/user-profile.png)

ATA, bilgisayar profilinde son oturum açmalar ve son erişilen kaynaklar gibi genel bilgileri görüntüler.

![Bilgisayar profili](media/computer-profile.png)

ATA, varlıklar (bilgisayarlar, cihazlar, kullanıcılar) hakkındaki genel bilgileri şu sayfalarda sağlar: Özet, Etkinlikler ve Kuşkulu Etkinlikler.

ATA’nın tümüyle çözümleyemediği bir profil, yanında gösterilen yarısı dolu daire simgesiyle tanımlanır.


![ATA çözümlenmemiş profilinin resmi](media/ATA-Unresolved-Profile.jpg)

### <a name="sensitive-groups"></a>Gizli gruplar

ATA tarafından **Gizli** olarak değerlendirilen gruplar aşağıda listelenmiştir. Şu grupların üyesi olan herhangi bir varlık, gizli olarak kabul edilir:

- Enterprise Read Only Domain Controllers 
- Etki Alanı Yöneticileri 
- Domain Controllers 
- Schema Admins,
- Enterprise Admins 
- Group Policy Creator Owners 
- Read Only Domain Controllers 
- Yöneticiler  
- İleri Kullanıcılar  
- Account Operators  
- Server Operators   
- Print Operators,
- Backup Operators,
- Replicators 
- Uzak Masaüstü Kullanıcıları 
- Ağ Yapılandırması İşleçleri 
- Incoming Forest Trust Builders 
- DNS Admins 


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
