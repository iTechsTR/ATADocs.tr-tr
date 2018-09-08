---
title: Advanced Threat Analytics kişisel veri ilkesi | Microsoft Docs
description: ATA'dan özel bilgileri ve kişisel verileri silme hakkında daha fazla bilgi için bağlantılar sağlar.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 9/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 1b2d185c-62cd-45f0-b0dd-687b51317f32
ms.reviewer: ophirp
ms.suite: ems
ms.openlocfilehash: ae5a28f793abe74331e58e92f2cbc2e021f772ea
ms.sourcegitcommit: 7f3ded32af35a433d4b407009f87cfa6099f8edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44126337"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*

# <a name="ata-data-security-and-privacy"></a>ATA veri güvenlik ve gizlilik

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

## <a name="searching-for-and-identifying-personal-data"></a>Arama ve kişisel verileri tanımlama 

Ata'da varlıklara ilişkili tüm verileri Active Directory (AD) türetilmiş ve buradan ATA'ya yinelenmiş. Kişisel verileri için arama yaparken, aramayı dikkate almanız gereken ilk AD yerdir. 

ATA Center'dan Arama çubuğuna veritabanında depolanan bir kişisel verilerini görüntülemek için kullanın. Kullanıcıların, belirli bir kullanıcı veya cihaz için arama yapabilirsiniz. Varlığa tıklandığında, kullanıcı veya cihaz profil sayfası açılır. Profil, varlık, buna ait geçmişi ve ilgili ağ etkinliği AD'den türetilmiş kapsamlı ayrıntılarını sağlar. 

## <a name="updating-personal-data"></a>Kişisel verileri güncelleştirme 

Kullanıcılar ve varlıkların ata'da hakkındaki kişisel verileri, kullanıcının türetilmiştir nesne kuruluşunuzdaki kullanıcının AD. Bu nedenle, ATA kullanıcı profiline AD'de yapılan değişiklikler yansıtılır. 

## <a name="deleting-personal-data"></a>Kişisel verileri silme 

Ata'da verinin kopyalandığı ve her zaman bir varlık AD'de silindiğinde, AD'den güncelleştirildi ancak Ata varlığın verilerine güvenlik araştırma amacıyla korunur. 

Kullanıcı ile ilgili verileri ATA veritabanından kalıcı olarak silmek için aşağıdaki yordamı izleyin: 

1. [İndirme](https://aka.ms/ata-gdpr-script) MongoDB betik (gdpr.js).  

2. ATA Center makinesindeki betiğini kopyalayın ve ATA Center makineden aşağıdaki komutu çalıştırın: 

Aşağıdaki bölümlerde açıklandığı gibi varlıkları silin ve varlık etkinlik verilerini silmek için ATA GDPR veritabanı betiğini kullanın.

### <a name="delete-entities"></a>Varlıkları silme

Bu eylem bir varlık ATA veritabanından kalıcı olarak siler. Bu komutu çalıştırmak için komut adı sağlayın. `deleteAccount`ve `SamName`, `UpnName` veya `GUID` , bilgisayar ya da silmek istediğiniz kullanıcı adı. Örneğin: 

`"C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\mongo.exe" ATA --eval "var params='deleteAccount,admin1@contoso.com';" GDPR.js`

Bu tamamen çalıştırmak kaldırır UPN ile varlık admin1@contoso.com yanı sıra tüm etkinlikleri ve güvenlik uyarılarını varlıkla ilişkili veritabanından. 

### <a name="delete-entity-activity-data"></a>Varlık etkinlik verilerini sil

Bu eylem, bir varlığın etkinlikleri veri ATA veritabanından kalıcı olarak siler. Tüm varlıkları oluşturacak değiştirilmemiş olan, ancak belirtilen zaman çerçevesi içinde bunlarla ilgili güvenlik uyarıları ve etkinlikleri silinir. 

Bu komutu çalıştırmak için komut adı sağlayın. `deleteOldData`ve veri veritabanında tutmak istediğiniz gün sayısı. 

Örneğin: 

`"C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\mongo.exe" ATA --eval "var params='deleteOldData,30';" GDPR.js`

Bu betik, 30 günden eski olan veritabanından tüm varlık etkinlikleri ve güvenlik uyarıları için tüm verileri kaldırır. Yalnızca son 30 Günün verilerini korur.

## <a name="exporting-personal-data"></a>Kişisel verileri dışarı aktarma 

ATA varlıklarla ilgili verileri AD'den türetildiğinden, bu veri kümesini yalnızca ATA veritabanında depolanır. Bu nedenle, veri varlığı ile ilgili AD dışarı aktarmanız gerekir. 

ATA, kişisel verileri içerebilir tüm güvenlikle ilgili bilgileri, Excel'e olanak tanır. 

 
## <a name="opt-out-of-system-generated-logs"></a>Sistem tarafından oluşturulan günlüklerin çevirme 

ATA, her dağıtım hakkında anonim sistem tarafından oluşturulan günlükleri toplar ve bu verileri HTTPS üzerinden Microsoft sunucularına iletir. Bu veriler Microsoft tarafından ATA’nın gelecek sürümlerini geliştirmeye yardımcı olmak için kullanılır. 

Daha fazla bilgi için [sistem tarafından oluşturulan günlükleri yönetme](manage-telemetry-settings.md).

Veri toplamayı devre dışı bırakmak için:

1. ATA Konsolu’nda oturum açın, araç çubuğundaki üç noktaya tıklayın ve **Hakkında**’yı seçin. 
2. **Gelecekte müşteri deneyiminizi geliştirmeye yardımcı olmak için bize kullanım bilgilerini gönderin** kutusunun işaretini kaldırın. 

## <a name="additional-resources"></a>Ek kaynaklar

- ATA güven ve Uyumluluk hakkında daha fazla bilgi için bkz. [hizmet güveni portalı](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted) ve [Microsoft 365 Kurumsal GDPR uyumluluğu site](https://docs.microsoft.com/microsoft-365/compliance/compliance-solutions-overview).
