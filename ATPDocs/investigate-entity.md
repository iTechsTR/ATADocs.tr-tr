---
title: Azure ATP olan kullanıcıları ve bilgisayarları araştırmak nasıl | Microsoft Docs
description: Kullanıcıları, varlıklar, bilgisayarları veya Azure Gelişmiş tehdit Koruması (ATP) kullanarak cihazları tarafından gerçekleştirilen şüpheli etkinlikleri araştırmaya açıklar
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
ms.openlocfilehash: 4ef4151a311dd5b076737cba9f3c7aa7454a32a7
ms.sourcegitcommit: 39a1ddeb6c9dd0817f92870b711627350b7f6f03
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2018
---
*Uygulandığı öğe: Azure Advanced Threat Protection sürüm 1.9*



# <a name="investigate-an-entity-with-azure-atp"></a>Azure ATP sahip bir varlık araştırın

Bu makalede Azure Gelişmiş tehdit Koruması (ATP ile) şüpheli etkinlikler algılandı sonra varlıklar araştırma işlemi açıklanmaktadır. Kuşkulu bir etkinlik zaman satırda görüntüledikten sonra etkinliğin ilgili varlık ayrıntılarına ve neler olduğunu ve riski azaltmak için yapmanız gerekenler hakkında daha fazla bilgi için ayrıntıları ve aşağıdaki parametreleri kullanın.

## <a name="look-at-the-entity-profile"></a>Varlık profili arayın

Varlık profili ile kapsamlı varlık sayfası, kullanıcılar, bilgisayarlar, aygıtları ve erişime sahip oldukları kaynakları ve geçmişlerini tam derin Dalış araştırma için tasarlanmış sağlar. Profil sayfası, bir grup (en fazla bir dakika toplanmış) gerçekleştirilen etkinlikler bakın ve daha iyi anlamak gerçek etkinliklerini vermek için tek bir mantıksal etkinliğin gruplandırın yeni Azure ATP mantıksal etkinliği Çeviricisi yararlanır Kullanıcılarınızın.

Bir varlık profili sayfasına erişmek için bir kullanıcı şüpheli etkinlik zaman çizelgesi gibi varlık adı tıklayın. Varlık adı gelerek varlık profili kuşkulu etkinlik sayfasında kısa bir sürümünü de görebilirsiniz.

Varlık profili varlık etkinlikleri görüntülemek, dizin verilerini görüntülemek ve varlığın yanal hareket yollarını görüntüleme olanak sağlar. Daha fazla bilgi için bkz: [varlık profilleri araştırma ](entity-profiles.md).

## <a name="check-entity-tags"></a>Varlık etiketleri denetleyin

Azure ATP Active Directory Kullanıcıları ve varlıkları izleme için tek bir arabirim sağlamak için Active Directory dışında etiketleri çeker. Bu etiketler varlık hakkında bilgi ile Active Directory'den sağladığınız dahil olmak üzere:
- Kısmi: Bu kullanıcı, bilgisayar veya grup etki alanından eşitlenmedi ve bir genel katalog ile kısmen çözümlendi. Bazı öznitelikler kullanılabilir değil.
- Çözümlenmemiş: Bu bilgisayar için geçerli bir varlık active directory ormanında çözümlenemedi. Hiçbir dizin bilgisi yok.
- Silinen: Varlık Active Directory'den silindi.
- Devre dışı: Varlık Active Directory'de devre dışı bırakılır.
- Kilitli: Varlık çok fazla kez yanlış parola girilen ve kilitlenir.
- Doldu: Varlık Active Directory'de süresi doldu.
- Yeni: Varlık 30 günden önce oluşturuldu.

## <a name="look-at-the-user-access-control-flags"></a>Kullanıcı erişim denetim bayrakları arayın

Ayrıca kullanıcı erişim denetim bayrakları Active Directory'den içe aktarılır. Azure ATP araştırma için etkili 10 bayrakları içerir: 
- Parola her zaman geçerli olsun
- Temsilci olarak güvenilir
- Akıllı kart gerekiyor
- Parolanın süresi doldu
- Boş parolaya izin verildi
- Depolanan düz metin parolası
- Devredilemez
- Yalnızca DES şifreleme
- Kerberos ön kimlik gerekli değil
- Hesap devre dışı 

Azure ATP, bu bayraklar veya Azure Active Directory içinde olup olmadığını bilmenizi sağlar. Renkli simgeler bayrağı üzerinde Active Directory içinde olduğunu gösteriyor; yalnızca aşağıdaki örnekte **hesap devre dışı** Active Directory'de açıktır.

 ![Kullanıcı erişim denetim bayrakları](./media/user-access-flags.png)

## <a name="cross-check-with-windows-defender"></a>Windows Defender ile Çapraz denetimi

Çapraz ürün ınsights ile sağlamak için açık uyarılar Windows Defender'ın içeren bir gösterge varlıklar, varlık profili sağlar. Bu gösterge, Windows Defender ve bunların önem düzeyi nedir varlık sahip kaç açık uyarılar bilmenizi sağlar. Doğrudan Windows Defender'ın bu varlık ilgili uyarılar gitmek için rozet tıklayın.


## <a name="keep-an-eye-on-sensitive-users-and-groups"></a>Hassas kullanıcılar ve gruplar takip

Azure ATP, Azure Active Directory'den, Active Directory'de aşağıdaki grupların üyesi olduğundan hangi kullanıcıların otomatik olarak hassas kabul edilir tanımlamak etkinleştirme, kullanıcı ve grup bilgilerini alır:

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
-   Kuruluş salt okunur etki alanı denetleyicileri 
-   Schema Admins 
-   Enterprise Admins

Buna ek olarak, şunları yapabilirsiniz **manuel olarak etiketleme** varlıkları Azure ATP içinde hassas olarak. Hassas grubu değişikliği algılama ve yanal hareket yolu gibi bazı Azure ATP algılamaların bir varlığın duyarlılık durumuna dayandığından, bu önemlidir. Ek kullanıcılar veya gruplar Panosu üyeleri, şirket Yöneticiler ve satış müdürü gibi hassas olarak el ile etiketi, Azure ATP bunları hassas göz önüne alır. Daha fazla bilgi için bkz: [hassas hesapları ile çalışma](sensitive-accounts.md).

## <a name="be-aware-of-lateral-movement-paths"></a>Yanal hareket yollarını unutmayın

Azure ATP yanal hareket yolları kullanma saldırıların önlenmesine yardımcı olabilir. Yanal hareket, saldırganın hassas hesapları erişim kazanmak için hassas olmayan hesapları proaktif olarak kullanır. durumdur.

Bir varlığın varlık profili sayfasını yanal hareket yol varsa, tıklatın kuramaz **yanal hareket yolları** sekmesi. Görüntülenen diyagramı, hassas kullanıcı olası yolları bir haritasını sağlar. 

Daha fazla bilgi için bkz: [Investigating yanal hareket yollarını Azure ATP ile](use-case-lateral-movement-path.md).


## <a name="is-it-a-honeytoken-entity"></a>Honeytoken varlık mi?

Araştırmanızı ile taşımadan önce entity bir honeytoken olup olmadığını bilmek önemlidir. Size kolaylık sağlamak için Azure ATP etiketi hesapları ve varlıklar honeytokens sağlar. Ardından, inceleme sırasında varlık veya mini profili açtığınızda Baktığınız etkinlik honeytoken etiketli bir hesap tarafından gerçekleştirilen uyarmak için honeytoken rozet görürsünüz.


    
## <a name="see-also"></a>Ayrıca bkz.

- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)