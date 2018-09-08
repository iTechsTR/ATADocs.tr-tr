---
title: ATA sürüm 1.7’deki yenilikler | Microsoft Docs
description: ATA sürüm 1.7’teki yenilikleri ve bilinen sorunları listeler
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: be9ee613-4eb3-40f1-8973-e7f0a707ff57
ms.reviewer: ''
ms.suite: ems
ms.openlocfilehash: 73b62edd2a03001998a5fdcef75a14a71177d1d7
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44166536"
---
# <a name="whats-new-in-ata-version-17"></a>ATA sürüm 1.7’deki yenilikler
Bu sürüm notları, Advanced Threat Analytics’in bu sürümündeki bilinen sorunlar hakkında bilgi sağlar.

## <a name="whats-new-in-the-ata-17-update"></a>ATA 1.7 güncelleştirmesindeki yenilikler
ATA 1.7 güncelleştirmesi aşağıdaki alanlarda geliştirmeler sağlar:

-   Yeni ve güncelleştirilmiş algılamalar

-   Rol tabanlı erişim denetimi

-   Windows Server 2016 ve Windows Server 2016 Core desteği

-   Kullanıcı deneyimi iyileştirmeleri

-   Küçük değişiklikler


### <a name="new--updated-detections"></a>Yeni ve güncelleştirilmiş algılamalar


- **Dizin Hizmetleri Numaralandırması kullanarak keşif** Keşif aşamasının bir parçası olarak, saldırganlar farklı yöntemler kullanarak ağdaki varlıklar hakkında bilgi toplar. SAM-R protokolünü kullanan Dizin hizmetleri numaralandırması saldırganların bir etki alanındaki kullanıcıların ve grupların listesini ele geçirmesini ve farklı varlıklar arasındaki etkileşimi anlamasını sağlar. 

- **Karma Değer Geçişi Geliştirmeleri** Karma Değer Geçişi algılamayı geliştirmek için varlıkların kimlik doğrulama modellerine yönelik ek davranışsal modeller ekledik. Bu modeller ATA’nın varlık davranışını şüpheli NTLM kimlik doğrulamalarıyla ilişkilendirmesini ve gerçek zamanlı Karma Değer Geçişi saldırılarını yanlış pozitif senaryoların davranışından ayırt etmesini sağlar.

- **Anahtar Geçişi Geliştirmeleri** Gelişmiş saldırıları genel olarak ve özellikle Anahtar Geçişi için başarılı bir şekilde algılamak amacıyla bir IP adresi ve bilgisayar hesabı arasındaki bağıntının doğru olması gerekir. Bu, IP adreslerinin tasarımsal olarak hızla değiştiği ortamlarda (örneğin, Wi-Fi ağları ve aynı ana bilgisayarı paylaşan birden çok sanal makine) zordur. Bu zorluğun üstesinden gelmek ve Anahtar Geçişi algılamasının doğruluğunu artırmak için ATA’nın Ağ Adı Çözümleme (NNR) mekanizması yanlış pozitifleri azaltmak için önemli ölçüde iyileştirilmiştir.

- **Anormal Davranış Geliştirmeleri** ATA 1.7’de, NTLM kimlik doğrulama verileri anormal davranış algılamaları için bir veri kaynağı olarak eklenmiş ve böylece algoritmaların ağdaki varlık davranışını daha geniş bir şekilde kapsaması sağlanmıştır. 

- **Olağan Dışı Protokol Uygulaması Geliştirmeleri** ATA artık Kerberos protokolünde olağan dışı protokol uygulamalarını ve NTLM protokolündeki ek anormallikleri algılamaktadır. Özellikle, Kerberos’taki bu yeni anormallikler Karma Değeri Atlayarak Geçiş saldırılarında yaygın olarak kullanılır.


### <a name="infrastructure"></a>Altyapı

- **Rol tabanlı erişim denetimi** Rol Tabanlı Erişim Denetimi (RBAC) kapasitesi. ATA 1.7 üç rol içerir: ATA Yöneticisi, ATA Analisti ve ATA İdarecisi.

- **Windows Server 2016 ve Windows Server Core Desteği** ATA 1.7; Windows Server 2008 R2 SP1 (Server Core içermeyen), Windows Server 2012, Windows Server 2012 R2 ve Windows Server 2016 (Core içerip Nano içermeyen) çalıştıran etki alanı denetleyicilerinde Lightweight Gateway’lerinin dağıtımını destekler. Ayrıca, bu sürüm Windows Server 2016’yı hem ATA Center hem de ATA Gateway bileşenleri için destekler.

### <a name="user-experience"></a>Kullanıcı Deneyimi
- **Yapılandırma Deneyimi** Bu sürümde, ATA yapılandırması deneyimi daha iyi bir kullanıcı deneyimi sağlama amacıyla ve birden çok ATA Gateway bileşenine sahip ortamları daha iyi destekleyecek şekilde tasarlanmıştır. Bu sürüm ayrıca, çeşitli Ağ Geçitlerinin otomatik güncelleştirme işlemlerinin daha kolay, daha iyi yönetilmesi için ATA Gateway güncelleştirme sayfasını getirmiştir.

## <a name="known-issues"></a>Bilinen sorunlar
Bu sürümün bilinen sorunları şunlardır:

### <a name="gateway-automatic-update-may-fail"></a>Ağ geçidi otomatik güncelleştirme işlemi başarısız olabilir
**Belirtiler:** Yavaş WAN bağlantılarına sahip ortamlarda, ATA Gateway güncelleştirmesi güncelleştirme zaman aşımına (100 saniye) ulaşabilir ve başarıyla tamamlanamayabilir.
ATA Konsolunda, ATA Gateway uzun bir süre “Güncelleştiriliyor (paket indiriliyor)” durumuna sahip olur ve sonunda başarısız olur.
**Geçici çözüm:** Bu sorunu çözmek için en son ATA Gateway paketini ATA Konsolundan indirin ve ATA Gateway’i el ile güncelleştirin.

 > [!IMPORTANT]
 ATA tarafından kullanılan sertifikalar için otomatik sertifika yenileme desteklenmez. Bu sertifikaların kullanılması sertifika otomatik olarak yenilendiğinde ATA’nın çalışmasının durmasına neden olabilir. 

### <a name="no-browser-support-for-jis-encoding"></a>JIS kodlama için tarayıcı desteği sağlanmıyor
**Belirtiler:** ATA Konsolu, JIS kodlama kullanan tarayıcılarda beklendiği gibi çalışmayabilir **Geçici Çözüm:** Tarayıcının kodlamasını Unicode UTF-8 olarak değiştirin.
 
### <a name="dropped-port-mirror-traffic-when-using-vmware"></a>Bağlantı noktası yansıtılmış trafik, VMware kullanırken bırakıldı

VMware üzerinde basit ağ geçidi kullanılırken bağlantı noktası yansıtılmış trafik uyarıları bırakıldı.

VMware sanal makinelerindeki etki alanı denetleyicileri kullanıyorsanız, **Bırakılan bağlantı noktası yansıtılmış ağ trafiği** hakkında uyarı alabilirsiniz. Bu, bir VMware yapılandırma uyuşmazlığından kaynaklanıyor olabilir. Bu uyarıları önlemek için aşağıdaki ayarların sanal makinede 0 veya Devre Dışı olarak ayarlandığını denetleyebilirsiniz:  

- TsoEnable
- LargeSendOffload(IPv4)
- IPv4 TSO Boşaltma

Ayrıca, IPv4 Büyük TSO Boşaltma’yı devre dışı bırakabilirsiniz. Daha fazla bilgi için VMware belgelerinize başvurun.

### <a name="automatic-gateway-update-fail-when-updating-to-17-update-1"></a>1.7 güncelleştirme 1’e güncelleştirirken Automatic Gateway güncelleştirme hatası

ATA 1.7’den ATA 1.7 güncelleştirme 1 sürümüne geçilirken, ATA Gateway otomatik güncelleştirme işlemi ve ağ geçitlerini Gateway paketi aracılığıyla el ile yükleme işlemi beklendiği gibi çalışmayabilir.
ATA Center tarafından kullanılan sertifika, ATA güncelleştirilmeden önce değiştirildiyse bu sorun oluşur.
Bu sorunu doğrulamak için, ATA Gateway’deki **Microsoft.Tri.Gateway.Updater.log** günlüğünü gözden geçirin ve şu özel durumları arayın: **System.Net.Http.HttpRequestException: İstek gönderilirken bir hata oluştu. ---> System.Net.WebException: Ana bağlantı kesildi: Gönderme sırasında beklenmeyen bir hata oluştu. ---> System.IdentityModel.Tokens.SecurityTokenValidationException: Sertifika parmak izi doğrulanamadı**

![ATA ağ geçidi güncelleştirme hatası](media/17update_gatewaybug.png)

Bu sorunu çözmek için, sertifikayı değiştirdikten sonra yükseltilmiş komut isteminden **%ProgramFiles%\Microsoft Advanced Threat Analytics\Center\MongoDB\bin** konumuna gidin ve şu komutu çalıştırın:

1. Mongo.exe ATA (ATA büyük harfle yazılmalıdır) 

2. CenterThumbprint=db.SystemProfile.find({_t:"CenterSystemProfile"}).toArray()[0].Configuration.SecretManagerConfiguration.CertificateThumbprint;

3. db.SystemProfile.update({_t:"ServiceSystemProfile"},{$set:{"Configuration.ManagementClientConfiguration.ServerCertificateThumbprint":CenterThumbprint}}, {multi: true})

### <a name="export-suspicious-activity-details-to-excel-may-fail"></a>Şüpheli etkinlik ayrıntılarını Excel'e dışarı aktarma başarısız olabilir
Şüpheli etkinlik ayrıntılarını bir Excel dosyasına dışarı aktarmaya çalıştığınızda, işlem şu hatayı vererek başarısız olabilir: *Error [BsonClassMapSerializer`1] System.FormatException: An error occurred while deserializing the Activity property of class Microsoft.Tri.Common.Data.NetworkActivities.SuspiciousActivityActivity: Element 'ResourceIdentifier' does not match any field or property of class Microsoft.Tri.Common.Data.EventActivities.NtlmEvent. ---> System.FormatException: Element 'ResourceIdentifier' does not match any field or property of class Microsoft.Tri.Common.Data.EventActivities.NtlmEvent.*

Yükseltilmiş bir komut isteminden bu sorunu çözmek için aşağıdaki konumuna göz atın: **%ProgramFiles%\Microsoft Advanced Threat Analytics\Center\MongoDB\bin** ve aşağıdaki komutları çalıştırın:
1.  `Mongo.exe ATA` (ATA büyük harfle yazılmalıdır)
2.  `db.SuspiciousActivityActivity.update({ "Activity._t": "NtlmEvent" },{$unset: {"Activity.ResourceIdentifier": ""}}, {multi: true});`

## <a name="minor-changes"></a>Küçük değişiklikler

- ATA, ATA Konsolu için artık IIS yerine OWIN kullanıyor.
- ATA Center hizmeti kapalıysa ATA Konsolu'na erişemez.
- ATA NNR’deki değişikliklerden dolayı artık kısa vadeli Kiralama alt ağları gerekmiyor.

## <a name="see-also"></a>Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

[ATA 1.7’ye güncelleştirme - geçiş rehberi](ata-update-1.7-migration-guide.md)

