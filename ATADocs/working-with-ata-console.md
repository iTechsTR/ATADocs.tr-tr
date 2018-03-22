---
title: Advanced Threat Analytics konsolunu anlama| Microsoft Docs
description: "ATA Konsolu’nda oturum açma işlemi ve konsolun bileşenleri açıklanır"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1bf264d9-9697-44b5-9533-e1c498da4f07
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 2ecffce7d692a9f1ecea8d8c5220ce3b2dbf848e
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*



# <a name="working-with-the-ata-console"></a>ATA Konsolu’yla çalışma

ATA tarafından algılanan kuşkulu etkinliği izlemek ve yanıtlamak için ATA Konsolu’nu kullanın.

Yazmaya `?` anahtar ATA Portal erişilebilirlik için klavye kısayolları sağlar. 

## <a name="enabling-access-to-the-ata-console"></a>ATA Konsolu’na erişimi etkinleştirme
Başarıyla ATA Konsolu'nda oturum açmak için ATA Konsolu'na erişmek için uygun ATA rolü atanmış bir kullanıcıyla oturum sahip. Rol tabanlı erişim denetimi (RBAC) ATA hakkında daha fazla bilgi için bkz: [ATA rol gruplarıyla çalışma](ata-role-groups.md).

## <a name="logging-into-the-ata-console"></a>ATA Konsolu’nda oturum açma

>[!NOTE]
 > ATA 1.8 ve üzeri sürümlerde, ATA Konsolu’nda oturum açma işlemi çoklu oturum açma yoluyla gerçekleştirilir.

1. ATA Center sunucusunda, masaüstündeki **Microsoft ATA Konsolu** simgesine tıklayın veya tarayıcıyı açıp ATA Konsolu’na göz atın.

    ![ATA sunucusu simgesi](media/ata-server-icon.png)

 >[!NOTE]
 > Ayrıca ATA Center veya ATA Gateway’den tarayıcıyı açabilir ve ATA Center yüklemesinde ATA Konsolu için yapılandırdığınız IP adresine göz atabilirsiniz.    

2.  ATA Center yüklendikten ve ATA konsolu erişim çalıştığınız bilgisayar olan her iki etki alanına katılmış değilse, ATA destekler, zaten bilgisayarınızda oturum açtıysanız, çoklu oturum açma tümleşik Windows kimlik doğrulaması ile - ATA kullanır. ATA Konsolu'nda oturum açın, belirteci. Ayrıca bir akıllı kart kullanarak da oturum açabilirsiniz. İzinlerinizi Ata ile karşılık gelen, [Yönetici rolü](ata-role-groups.md).

 > [!NOTE]
 > ATA yönetici kullanıcı adı ve parola kullanarak ATA Konsolu'na erişmek istediğiniz bilgisayarda oturum açmak emin olun. Bunun yerine tarayıcınızı farklı bir kullanıcı olarak çalıştırabilir veya Windows oturumunuzu kapatıp ATA yönetici kullanıcınızla oturum açabilirsiniz. Kimlik bilgilerini sor, bir IP kullanan konsoluna erişmek için ATA Konsolu istemek için adresi ve kimlik bilgilerini girmeniz istenir.

3. SSO kullanarak oturum açması ATA Konsolu sitesini yerel intranet sitesine tarayıcınızda olarak tanımlanır ve bir kısaad veya bir localhost kullanarak erişim emin olun.

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

### <a name="whats-new"></a>Yenilikler

ATA'ın yeni bir sürüm yayımlandıktan sonra **yenilikler** penceresi görünür üst ne en son sürümde eklenen size bildirmek için sağ. Ayrıca, sürüm indirme bağlantı sağlar.

### <a name="filtering-panel"></a>Filtreleme paneli

Kuşkulu etkinlikleri Durum ve Önem Derecesi’ne göre filtreleyerek, saldırı zaman çizelgesinde veya varlık profili kuşkulu etkinlikler sekmesinde hangi etkinliklerin görüntüleneceğini belirtebilirsiniz.

### <a name="search-bar"></a>Arama çubuğu

Üst menüde arama çubuğunu bulabilirsiniz. Belirli bir kullanıcı, bilgisayar veya ATA gruplarında arayabilirsiniz. Denemek için, yazmaya başlamanız yeterlidir.

![ATA konsolu arama resmi](media/ATA-console-search.png)

### <a name="health-center"></a>Sistem Durumu Merkezi

Sistem Durumu Merkezi, ATA dağıtımınızda düzgün çalışmayan bir şey olduğunda size uyarılar sağlar.

![ATA sistem durumu merkezinin resmi](media/ATA-Health-Issue.jpg)

Sisteminizin bağlantı hatası veya bağlantısı kesilmiş ATA Gateway gibi bir sorunla karşılaştığında her zaman sistem durumu Merkezi simgesi, kırmızı bir nokta göstererek bilmenizi sağlar. ![ATA sistem durumu merkezi kırmızı noktasının resmi](media/ATA-Health-Center-Alert-red-dot.png)

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

Farenizi konsol başka bir yerindeki bir varlık üzerine, söz konusu olduğunda, bir kullanıcı veya bir bilgisayar gibi tek bir varlığın varsa aşağıdaki bilgileri görüntüleyen mini profil otomatik olarak açılır:

![ATA mini profilinin resmi](media/ATA-mini-profile.jpg)

-   Ad

-   Resim

-   E-posta

-   Telefon

-   Önem derecesine göre kuşkulu etkinlik sayısı



## <a name="see-also"></a>Ayrıca bkz:
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
