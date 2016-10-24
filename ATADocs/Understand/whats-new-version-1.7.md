---
title: "ATA sürüm 1.7’daki yenilikler | Microsoft ATA"
description: "ATA sürüm 1.7’teki yenilikleri ve bilinen sorunları listeler"
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 09/20/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a024cab5e706b32273d563095f5d7e690d6ed055
ms.openlocfilehash: dec9fc03cdf718627dd72ac0c48f934fe507c7ac


---

# ATA sürüm 1.7’deki yenilikler
Bu sürüm notları, Advanced Threat Analytics’in bu sürümündeki bilinen sorunlar hakkında bilgi sağlar.

## ATA 1.7 güncelleştirmesindeki yenilikler
ATA 1.7 güncelleştirmesi aşağıdaki alanlarda geliştirmeler sağlar:

-   Yeni ve güncelleştirilmiş algılamalar

-   Rol tabanlı erişim denetimi

-   Windows Server 2016 ve Windows Server Core desteği

-   Kullanıcı deneyimi iyileştirmeleri

-   Küçük değişiklikler


### Yeni ve güncelleştirilmiş algılamalar


- **Dizin Hizmetleri Numaralandırması kullanarak keşif** Keşif aşamasının bir parçası olarak, saldırganlar farklı yöntemler kullanarak ağdaki varlıklar hakkında bilgi toplar. SAM-R protokolünü kullanan Dizin hizmetleri numaralandırması saldırganların bir etki alanındaki kullanıcıların ve grupların listesini ele geçirmesini ve farklı varlıklar arasındaki etkileşimi anlamasını sağlar. 

- **Karma Değer Geçişi Geliştirmeleri** Karma Değer Geçişi algılamayı geliştirmek için varlıkların kimlik doğrulama modellerine yönelik ek davranışsal modeller ekledik. Bu modeller ATA’nın varlık davranışını şüpheli NTLM kimlik doğrulamalarıyla ilişkilendirmesini ve gerçek zamanlı Karma Değer Geçişi saldırılarını yanlış pozitif senaryoların davranışından ayırt etmesini sağlar.

- **Anahtar Geçişi Geliştirmeleri** Gelişmiş saldırıları genel olarak ve özellikle Anahtar Geçişi için başarılı bir şekilde algılamak amacıyla bir IP adresi ve bilgisayar hesabı arasındaki bağıntının doğru olması gerekir. Bu, IP adreslerinin tasarımsal olarak hızla değiştiği ortamlarda (örneğin, Wi-Fi ağları ve aynı ana bilgisayarı paylaşan birden çok sanal makine) zordur. Bu zorluğun üstesinden gelmek ve Anahtar Geçişi algılamasının doğruluğunu artırmak için ATA’nın Ağ Adı Çözümleme (NNR) mekanizması yanlış pozitifleri azaltmak için önemli ölçüde iyileştirilmiştir.

- **Anormal Davranış Geliştirmeleri** ATA 1.7’de, NTLM kimlik doğrulama verileri anormal davranış algılamaları için bir veri kaynağı olarak eklenmiş ve böylece algoritmaların ağdaki varlık davranışını daha geniş bir şekilde kapsaması sağlanmıştır. 

- **Olağan Dışı Protokol Uygulaması Geliştirmeleri** ATA artık Kerberos protokolünde olağan dışı protokol uygulamalarını ve NTLM protokolündeki ek anormallikleri algılamaktadır. Özellikle, Kerberos’taki bu yeni anormallikler Karma Değeri Atlayarak Geçiş saldırılarında yaygın olarak kullanılır.


### Altyapı

- **Rol tabanlı erişim denetimi** Rol Tabanlı Erişim Denetimi (RBAC) kapasitesi. ATA 1.7 üç rol içerir: ATA Yöneticisi, ATA Analisti ve ATA İdarecisi.

- **Windows Server 2016 ve Windows Server Core Desteği** ATA 1.7, Windows Server 2012 için Server Core ve Windows Server 2012 R2 için Server Core çalıştıran etki alanı denetleyicilerinde Lightweight Gateway bileşenlerinin dağıtımını destekler. Ayrıca, bu sürüm Windows Server 2016’yı hem ATA Center hem de ATA Gateway bileşenleri için destekler.

### Kullanıcı Deneyimi
- **Yapılandırma Deneyimi** Bu sürümde, ATA yapılandırması deneyimi daha iyi bir kullanıcı deneyimi sağlama amacıyla ve birden çok ATA Gateway bileşenine sahip ortamları daha iyi destekleyecek şekilde tasarlanmıştır. Bu sürüm ayrıca, çeşitli Ağ Geçitlerinin otomatik güncelleştirme işlemlerinin daha kolay, daha iyi yönetilmesi için ATA Gateway güncelleştirme sayfasını getirmiştir.

## Bilinen sorunlar
Bu sürümün bilinen sorunları şunlardır:

### Ağ geçidi otomatik güncelleştirme işlemi başarısız olabilir
**Belirtiler:** Yavaş WAN bağlantılarına sahip ortamlarda, ATA Gateway güncelleştirmesi güncelleştirme zaman aşımına (100 saniye) ulaşabilir ve başarıyla tamamlanamayabilir.
ATA Konsolunda, ATA Gateway uzun bir süre “Güncelleştiriliyor (paket indiriliyor)” durumuna sahip olur ve sonunda başarısız olur.
**Geçici çözüm:** Bu sorunu çözmek için en son ATA Gateway paketini ATA Konsolundan indirin ve ATA Gateway’i el ile güncelleştirin.

 > [!IMPORTANT]
 ATA tarafından kullanılan sertifikalar için otomatik sertifika yenileme desteklenmez. Bu sertifikaların kullanılması sertifika otomatik olarak yenilendiğinde ATA’nın çalışmasının durmasına neden olabilir. 

### JIS kodlama için tarayıcı desteği sağlanmıyor
**Belirtiler:** ATA Konsolu, JIS kodlama kullanan tarayıcılarda beklendiği gibi çalışmayabilir **Geçici Çözüm:** Tarayıcının kodlamasını Unicode UTF-8 olarak değiştirin.
 
### Bağlantı noktası yansıtılmış trafik, VMware kullanırken bırakıldı

Bağlantı noktası yansıtılmış trafik uyarıları, basit ağ geçidi üzerinde VMware kullanırken bırakıldı

VMware sanal makinelerindeki etki alanı denetleyicileri kullanıyorsanız, **Bırakılan bağlantı noktası yansıtılmış ağ trafiği** hakkında uyarı alabilirsiniz. Bu, bir VMware yapılandırma uyuşmazlığından kaynaklanıyor olabilir. Bu uyarıları önlemek için aşağıdaki ayarların 0 veya Devre Dışı olarak ayarlandığını denetleyebilirsiniz: TsoEnable, LargeSendOffload, IPv4, TSO Veri Boşaltma. Ayrıca, IPv4 Büyük TSO Boşaltma’yı devre dışı bırakabilirsiniz. Daha fazla bilgi için VMware belgelerinize başvurun.

## Küçük değişiklikler

- ATA, ATA Konsolu için artık IIS yerine OWIN kullanıyor.
- ATA Center hizmeti kapalıysa ATA Konsolu’na erişemezsiniz.
- ATA NNR’deki değişikliklerden dolayı artık kısa vadeli Kiralama alt ağları gerekmiyor.

## Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

[ATA 1.7’ye güncelleştirme - taşıma rehberi](ata-update-1.7-migration-guide.md)




<!--HONumber=Oct16_HO2-->


