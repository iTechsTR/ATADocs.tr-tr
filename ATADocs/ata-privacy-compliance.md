---
title: Gelişmiş tehdit analizi uyumluluk, güven, veri güvenliği ve gizliliği | Microsoft Docs
description: ATA kaynakları, videoları, Başlarken, dağıtım ve hazırlık yol haritası bağlantılar listesini sağlar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/16/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 1b2d185c-62cd-45f0-b0dd-687b51317f32
ms.reviewer: ophirp
ms.suite: ems
ms.openlocfilehash: dee55446c18ee9bc560045c94f9421840fc28fc2
ms.sourcegitcommit: 714a01edc9006b38d1163d03852dafc2a5fddb5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*

# <a name="ata-compliance-trust-data-security-and-privacy"></a>ATA uyumluluk, güven, veri güvenliği ve gizlilik 

ATA güven ve uyumluluğu hakkında daha fazla bilgi için bkz: [hizmet güven portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted) ve [Microsoft 365 Kurumsal GDPR uyumluluk site](https://docs.microsoft.com/microsoft-365/compliance/compliance-solutions-overview).

## <a name="searching-for-and-identifying-personal-data"></a>Arama ve kişisel veri tanımlama 

Varlıklara ilişkili ATA tüm verileri Active Directory (AD) türetilmiş ve buradan ATA çoğaltılır. Kişisel veriler için arama yaparken arama dikkate almanız gereken ilk AD yerdir. 

ATA Center'dan arama çubuğunu veritabanında depolanan bir kişisel verileri görüntülemek için kullanın. Kullanıcıların belirli bir kullanıcı veya aygıt için arama yapabilirsiniz. Varlık üzerinde tıklandığında kullanıcı veya aygıt profili sayfası açılır. Profil varlık, buna ait geçmişi ve ilgili ağ etkinliği AD'den türetilmiş hakkında kapsamlı ayrıntıları sağlar. 

## <a name="updating-personal-data"></a>Kişisel verileri güncelleştirme 

Kullanıcılar ve ATA varlıkları hakkındaki kişisel verileri kullanıcının türetilen nesne kuruluşunuzdaki kullanıcının AD. Bu nedenle, kullanıcı profili için AD içinde yapılan değişiklikler ATA yansıtılır. 

## <a name="deleting-personal-data"></a>Kişisel verileri silme 

Ata verinin kopyalandığı ve her zaman AD içinde bir varlık silindiğinde, AD'den güncelleştirildi ancak ATA varlığın verilerde güvenlik araştırma amacıyla korunur. 

ATA veritabanından kullanıcıyla ilgili veriler kalıcı olarak silmek için bu yordamı izleyin: 

1. [Karşıdan](https://aka.ms/ata-gdpr-script) MongoDB komut dosyası (gdpr.js).  

2. ATA Center makine betiğini kopyalayın ve ATA Center makineden aşağıdaki komutu çalıştırın: 

Aşağıdaki bölümlerde açıklandığı gibi varlıkları silmek ve varlık etkinlik verilerini silmek için ATA GDPR veritabanı komut dosyası kullanın.

### <a name="delete-entities"></a>Varlıkları silme

Bu eylem, bir varlık ATA veritabanından kalıcı olarak siler. Bu komutu çalıştırmak için komut adı sağlamanız `deleteAccount`ve `SamName`, `UpnName` veya `GUID` bilgisayarın veya silmek istediğiniz kullanıcı adı. Örneğin: 

`C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\mongo.exe" ATA --eval “var params= deleteAccount,admin1@contoso.com;” GDPR.js `

Bu tamamen çalıştığını kaldırır UPN varlıkla admin1@contoso.com tüm etkinlikleri ve güvenlik uyarıları varlıkla ilişkilendirilen birlikte veritabanından. 

### <a name="delete-entity-activity-data"></a>Varlık etkinlik verilerini sil

Bu eylem, bir varlığın etkinlikleri veri ATA veritabanından kalıcı olarak siler. Tüm varlıklar olan değişmeden ancak etkinlikleri ve bunlara belirli bir zaman çerçevesi için ilgili güvenlik uyarıları silinir. 

Bu komutu çalıştırmak için komut adı sağlamanız `deleteOldData`ve veritabanında korumak istediğiniz verilerin gün sayısı. 

Örneğin: 

`C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\mongo.exe" ATA --eval “var params= deleteOldData,30;” GDPR.js`

Bu komut dosyasını 30 günden eski olan veritabanı tüm varlık etkinlikleri ve güvenlik uyarıları için tüm verileri kaldırır. Verileri yalnızca son 30 gün saklar.

## <a name="exporting-personal-data"></a>Kişisel verileri dışarı aktarma 

ATA varlıklarla ilgili verileri AD'den türetildiği için yalnızca bir veri alt kümesini, ATA veritabanına depolanır. Bu nedenle, ilgili varlık veri AD vermeniz gerekir. 

ATA, kişisel verileri içerebilen tüm güvenlikle ilgili bilgileri, Excel'e sağlar. 

 
## <a name="opt-out-of-telemetry"></a>Üyelikten çıkmak telemetri 

ATA, her dağıtım hakkında anonim telemetri toplar ve bu verileri HTTPS üzerinden Microsoft sunucularına iletir. Bu veriler Microsoft tarafından ATA’nın gelecek sürümlerini geliştirmeye yardımcı olmak için kullanılır. 

Daha fazla bilgi için bkz: [telemetri ayarlarını yönetme](manage-telemetry-settings.md).

Veri toplamayı devre dışı bırakmak için:

1. ATA Konsolu’nda oturum açın, araç çubuğundaki üç noktaya tıklayın ve **Hakkında**’yı seçin. 
2. **Gelecekte müşteri deneyiminizi geliştirmeye yardımcı olmak için bize kullanım bilgilerini gönderin** kutusunun işaretini kaldırın. 

 

 

 

## <a name="additional-resources"></a>Ek kaynaklar

[Microsoft Güvenlik Channel 9 sayfası](https://channel9.msdn.com/Shows/Microsoft-Security/)

## <a name="community-resources"></a>Topluluk kaynakları

[ATA blogu](https://aka.ms/ATABlog)
[ATA topluluk](https://aka.ms/ATACommunity)
[ATA hakkında geri bildirim sağlayın](https://aka.ms/ATAUserVoice)
