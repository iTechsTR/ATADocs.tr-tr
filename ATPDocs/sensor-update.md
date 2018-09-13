---
title: Uygulamanızı Azure ATP algılayıcı güncelleştirme | Microsoft Docs
description: Bu, Azure ATP algılayıcı güncelleştirme işlemi açıklanmaktadır.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 9/12/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 603d9e09-a07d-4357-862f-d5682c8bc3dd
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 8a6481070abf1188507f31dbd01b26f7221b2e36
ms.sourcegitcommit: a5823d0dfc48783ab990a99ca3f65b614fb49e75
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44697251"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="update-azure-atp-sensors"></a>Azure ATP algılayıcı güncelleştirme
Azure Gelişmiş tehdit koruması, kuruluşunuz için en iyi olası korumasını etkinleştirmek için güncel tutmak önemlidir.

Azure ATP hizmeti, yeni algılamalar hata düzeltmeleri ve performans geliştirmeleri ile ayda birkaç kez güncelleştirilir. Bazen bu güncelleştirmeler için sensörlerden karşılık gelen bir güncelleştirme gerektirir. 

Algılayıcılar güncelleştirmezseniz, bunlar hizmet düşmesine neden neden Azure ATP bulut hizmetiyle iletişim kurmak mümkün olmayabilir. 

Güçlü, sertifika tabanlı karşılıklı kimlik doğrulaması, sensör ve Azure bulut hizmeti arasında kimlik doğrulaması kullanır. 

Her güncelleştirme test ve tüm desteklenen işletim sistemlerinde ağ ve işlemleri için en az etki neden doğrulandı.

### <a name="azure-atp-sensor-update-types"></a>Azure ATP algılayıcı güncelleştirme türleri   

Azure ATP algılayıcı güncelleştirmeleri iki çeşit destekler:
- Alt sürüm güncelleştirmeleri: 
  - Sık kullanılan 
  - MSI yükleme gerekmez ve hiçbir kayıt defteri değişiklikleri gerektirir
  - Azure ATP algılayıcı hizmeti yeniden başlatma
  - Etki alanı denetleyicileri ve sunucu yeniden başlatılması gerekmez

- Ana sürüm güncelleştirmeleri:
 - Nadir
 - Etki alanı denetleyicileri ve sunucuları yeniden başlatma gerekebilir
 - Önemli değişiklikler içeren 

> [!NOTE]
>- Otomatik olarak yeniden başlatılmasını sensörlerden (önemli güncelleştirmeler) yapılandırma sayfasında denetlenebilir. 
> - Azure ATP algılayıcısını her zaman en az % 15 bellek ve CPU kullanılabilir korur. Hizmet çok fazla bellek kullanırsa, Azure ATP algılayıcısı updater hizmeti tarafından otomatik olarak yeniden başlatılır.

## <a name="delayed-sensor-update"></a>Algılayıcı güncelleştirme ertelendi
Daha aşamalı bir güncelleştirme işlemi izin vermek için Azure ATP algılayıcı olarak ayarlamanıza olanak tanır bir **Gecikmeli güncelleştirme** aday. 

Normalde, algılayıcılar Azure ATP bulut hizmeti güncelleştirildiğinde otomatik olarak güncelleştirilir. Algılayıcılar kümesine **Gecikmeli güncelleştirme** ilk bulut hizmet güncelleştirmesinden sonra 24 saat güncelleştirir.

Bu belirli sensörlerden üzerinde güncelleştirme otomatik olarak kullanıma sunulma seçin ve yalnızca ilk güncelleştirme sorunsuz oluştu gördükten sonra algılayıcılar gecikme, kalan güncelleştirmenize olanak sağlar.

> [!NOTE]
> Bir hata oluşursa ve algılayıcıyı güncelleştirilmediği bir destek bileti açın.

Bir algılayıcı için Gecikmeli güncelleştirme ayarlamak için:

1. Azure ATP çalışma alanı portalından, ayarlar simgesine tıklayın ve seçin **yapılandırma**.
2. Tıklayarak **güncelleştirmeleri** sekmesi.
3. Gecikme istediğiniz her algılayıcı yanındaki tablosu satır kümesi **Gecikmeli güncelleştirme** kaydırıcısını **üzerinde**.
4. **Kaydet**'e tıklayın.
 
## <a name="sensor-update-process"></a>Algılayıcı güncelleştirme işlemi

Birkaç dakikada Azure ATP algılayıcı en son sürüme sahip olup olmadığını denetleyin. Azure ATP bulut hizmeti, yeni bir sürüme güncelleştirildikten sonra Azure ATP algılayıcı hizmeti güncelleştirme işlemi başlar:

1. Azure ATP bulut hizmet güncelleştirmeleri için en son sürümü.
2. Azure ATP algılayıcısı updater hizmetini, güncelleştirilmiş bir sürümü olduğunu öğrenir.
3. İçin ayarlanmamış algılayıcılar **Gecikmeli güncelleştirme** güncelleştirme işlemi başlatın:
  1. Azure ATP algılayıcısı updater hizmetini gireceği bulut hizmetinden (bir cab dosya biçiminde) çeker.
  2. Azure ATP algılayıcısı güncelleştirici dosya imzayı doğrular.
  3. Azure ATP algılayıcısı updater hizmetini cab dosyası algılayıcının yükleme klasöründe yeni bir klasöre ayıklayın. Varsayılan olarak bu şekilde ayıklanır *C:\Program Files\Azure Gelişmiş tehdit koruması algılayıcı\<sürüm numarası >*
  4. Azure ATP algılayıcısı updater hizmetini Azure ATP algılayıcısı hizmetini yeniden başlatır.
  5. Azure ATP algılayıcı hizmetinin yeni dosyaları cab dosyasından ayıklanan işaret eder.
  > [!NOTE]
  >Algılayıcılar, küçük bir güncelleştirme değil bir MSI yükleme veya herhangi bir kayıt defteri değeri veya sistem dosyaları değiştirin. Hatta bekleyen bir yeniden başlatma sensörlerden güncelleştirilmesini etkilemez. 
  6. Algılayıcılar yeni güncelleştirilmiş sürümüne bağlı olarak çalıştırın.
  7. Algılayıcı Azure bulut hizmetinden payını alır. Bu, doğrulanabilir **güncelleştirmeleri** sayfası.
  8. Sonraki algılayıcı güncelleştirme işlemi başlatır. 

4. 24 saat sonra Azure ATP bulut hizmeti güncelleştirildi, seçili algılayıcıları ** Gecikmeli güncelleştirme güncelleştirme işlemini başlatın.

![Algılayıcı güncelleştirme](./media/sensor-update.png)


Başarısızlık durumunda algılayıcı güncelleştirme işlemi tamamlanmadıysa ilgili izleme uyarısı tetiklenir ve bildirim olarak gönderilir.

![eski algılayıcısı](./media/sensor-outdated.png)


## <a name="see-also"></a>Ayrıca Bkz.

- [Olay iletme'yi yapılandırma](configure-event-forwarding.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)