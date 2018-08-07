---
title: Kullanıcıları ve bilgisayarları Azure ATP ile araştırma | Microsoft Docs
description: Kullanıcılar, varlıklar, bilgisayarları veya cihazları Azure Gelişmiş tehdit Koruması (ATP) kullanarak tarafından gerçekleştirilen şüpheli etkinlikleri araştırma açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/6/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 43e57f87-ca85-4922-8ed0-9830139fe7cb
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 32f5ab58ba9e17d36761ce5b99f4711d0e390ff7
ms.sourcegitcommit: 14c05a210ae92d35100c984ff8c6d171db7c3856
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39567874"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="investigate-an-entity-with-azure-atp"></a>Azure ATP sahip bir varlık araştırın

Bu makalede, Azure Gelişmiş tehdit Koruması (ATP ile) şüpheli etkinlikleri tespit edilen sonra varlıkları araştırma işlemi açıklanır. Zaman çizelgesinde kuşkulu bir etkinlik izledikten sonra etkinliğin ilgili varlık incelemek ve ne olduğunu ve riski azaltmak için yapmanız gerekenler hakkında daha fazla bilgi için ayrıntıları ve aşağıdaki parametreleri kullanın.

## <a name="look-at-the-entity-profile"></a>Varlık profili Ara

Varlık profili, kullanıcılar, bilgisayarlar, cihazlar ve geçmişlerini birlikte erişime sahip oldukları kaynakları tam yakından incelenmesi için tasarlanmış kapsamlı varlık sayfa sağlar. Profil sayfasında, bir grup etkinlik (bir dakikaya kadar toplanmış) gerçekleşen bakın ve daha iyi anlamak gerçek etkinliklerini vermek için tek bir mantıksal etkinliğini gruplamak yeni Azure ATP mantıksal etkinliği Çeviricisi yararlanır Kullanıcılarınızın.

Bir varlık profili sayfasına erişmek için şüpheli etkinlik zaman çizelgesinde bir kullanıcı adı gibi varlık adını tıklayın. Varlık adının üzerine gelerek varlık profili kuşkulu etkinlik sayfasında kısa bir sürümünü de görebilirsiniz.

Varlık profili, varlık etkinlikleri görüntülemek, dizin verilerini görüntüleyin ve varlığın yanal hareket yollarını görüntülemenize olanak tanır. Daha fazla bilgi için [varlık profilleri araştırma ](entity-profiles.md).

## <a name="check-entity-tags"></a>Varlık etiketleri denetleyin

Azure ATP Active Directory Kullanıcıları ve varlıkları izlemek için tek bir arabirim sağlamak için Active Directory etiketler çeker. Bu etiketler varlık bilgilerini Active Directory'den sağlamak da dahil olmak üzere:
- Kısmi: Bu kullanıcı, bilgisayar veya grup etki alanından eşitlenmedi ve genel bir katalog kısmen çözümlendi. Bazı öznitelikler kullanılamıyor.
- Çözülmemiş: Bu bilgisayar için geçerli bir varlık active directory ormanındaki çözümlenmedi. Hiçbir dizin bilgileri kullanılabilir.
- Silinen: Varlık Active Directory'den silindi.
- Devre dışı: Varlık Active Directory'de devre dışı bırakıldı.
- Kilitli: Varlık, birden çok kez yanlış parola girilen ve kilitli.
- Süresi doldu: Active Directory'de varlığın süresi dolmuş.
- Yeni: Varlık 30 günden kısa süre önce oluşturuldu.

## <a name="look-at-the-user-account-control-flags"></a>Kullanıcı hesabı denetim bayrakları Ara

Kullanıcı hesabı denetim bayrakları, aynı zamanda Active Directory'den içeri aktarılır. Azure ATP araştırma için etkin olan 10 bayraklarını içerir: 
- Parola her zaman geçerli olsun
- Temsilci seçme için güvenilir
- Akıllı kart gerekmez
- Parolanın süresi doldu
- Boş parolaya izin verilir
- Düz metin parola depolanır
- Temsilci olarak seçilemez
- Yalnızca DES şifrelemesi
- Kerberos ön kimlik gerekli değildir
- Hesap devre dışı bırakıldı 

Azure ATP, bu bayraklar açıp Azure Active Directory'de olup olmadığını bilmenizi sağlar. Renkli simgeler bayrağı üzerinde Active Directory'de gerektiğini belirtmiş olursunuz; yalnızca aşağıdaki örnekte **hesap devre dışı** Active Directory'de açıktır.

 ![kullanıcı hesabı denetim bayrakları](./media/user-access-flags.png)

## <a name="cross-check-with-windows-defender"></a>Windows Defender ile Çapraz denetimi

İle çapraz ürün Öngörüler sağlamak için açık uyarılar, Windows Defender'ın bir rozetle birlikte sahip varlıklar, varlık profili sağlar. Bu rozet, Windows Defender ve bunların önem derecesi nedir varlık sahip kaç açık uyarılar bilmenizi sağlar. Rozet, doğrudan Windows Defender'ın bu varlıktaki ilgili uyarılar gitmek için tıklayın.


## <a name="keep-an-eye-on-sensitive-users-and-groups"></a>Hassas kullanıcılar ve gruplar takip

Azure ATP, Azure Active Directory'den Active Directory'de aşağıdaki grupların üyesi oldukları için hangi kullanıcıların otomatik olarak gizli olarak kabul edilir belirlemenize olanak sağlayan, kullanıcı ve grup bilgisini alır:

-   Yöneticiler
-   İleri Kullanıcılar
-   Account Operators
-   Server Operators
-   Print Operators
-   Backup Operators
-   Replicators
-   Uzak Masaüstü Kullanıcıları 
-   Ağ Yapılandırması İşleçleri 
-   Incoming Forest Trust Builders
-   Etki Alanı Yöneticileri
-   Domain Controllers
-   Group Policy Creator Owners 
-   salt okunur etki alanı denetleyicileri 
-   Kurumsal salt okunur etki alanı denetleyicileri 
-   Schema Admins 
-   Enterprise Admins

Ayrıca, aşağıdakileri yapabilirsiniz **el ile etiketleme** varlıklar Azure ATP içinde hassas olarak. Gizli Grup değişikliği algılama ve yanal hareket yolunun gibi bazı Azure ATP algılamalar varlığın duyarlılık durumuna bağımlı olduğundan bu önemlidir. El ile ek kullanıcılar veya gruplar Pano üyeleri ve yöneticiler şirket satış directory'lerin gibi hassas olarak etiket, Azure ATP bunları hassas dikkate alacaktır. Daha fazla bilgi için [hassas hesaplar ile çalışma](sensitive-accounts.md).

## <a name="be-aware-of-lateral-movement-paths"></a>Yanal hareket yollarını unutmayın

Azure ATP, yanal hareket yollarını kullanma saldırılarını önlemeye yardımcı olabilir. Yanal hareket, bir saldırganın hassas hesaplara yönelik erişim elde etmek için hassas olmayan hesapları proaktif olarak kullanır. andır.

Yanal hareket yolunun bir varlıkta, varlığın profil sayfası varsa, tıklayın mümkün olmayacak **yana hareket yollarını** sekmesi. Görüntülenen diyagram hassas kullanıcı için olası yolları sahip bir eşleme sağlar. 

Daha fazla bilgi için [Investigating Azure ATP ile yanal hareket yollarını](use-case-lateral-movement-path.md).


## <a name="is-it-a-honeytoken-entity"></a>Honeytoken varlık nedir?

Araştırmanızı taşımadan önce varlık bir honeytoken olup olmadığını bilmek önemlidir. Azure ATP içinde honeytokens olarak hesaplar ve varlıkları etiketleyebilirsiniz. Varlık profili veya bir hesabı ya da bir honeytoken etiketlendi varlık Mini profili açtığınızda honeytoken rozet görürsünüz. İncelerken, honeytoken rozeti, gözden geçirme etkinliği bir honeytoken etiketlenmiş bir hesap tarafından gerçekleştirildiğini sizi uyarır.


    
## <a name="see-also"></a>Ayrıca bkz.

- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)