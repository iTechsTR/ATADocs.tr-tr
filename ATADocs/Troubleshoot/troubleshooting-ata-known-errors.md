---
title: "ATA hata günlüğü sorunlarını giderme | Microsoft ATA"
description: "ATA’da sık karşılaşılan hataları nasıl giderebileceğinizi açıklar"
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: d89e7aff-a6ef-48a3-ae87-6ac2e39f3bdb
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5c7163bc7b1989672e587bfb4fa6a65cd4e3751
ms.openlocfilehash: cf2e1ab1fec4906e0bf2df8e0407b1951081e62f


---

# ATA hata günlüğü sorunlarını giderme
Bu bölüm, ATA dağıtımlarındaki olası hataları ve bunları gidermek için gereken adımları açıklar.
## ATA Gateway hataları
|Hata|Açıklama|Çözüm|
|-------------|----------|---------|
|System.DirectoryServices.Protocols.LdapException: Yerel bir hata oluştu|ATA Gateway, etki alanı denetleyicisine karşı kimlik doğrulaması yapamadı.|1. Etki alanı denetleyicisinin DNS kaydının DNS sunucusunda düzgün şekilde yapılandırıldığını doğrulayın. <br>2. ATA Gateway saatinin etki alanı denetleyicisinin saatiyle eşitlendiğini doğrulayın.|
|System.IdentityModel.Tokens.SecurityTokenValidationException: Sertifika zinciri doğrulanamadı|ATA Gateway, ATA Center sertifikasını doğrulayamadı.|1. Kök CA sertifikasının ATA Gateway’de güvenilir sertifika yetkilisi sertifika deposuna yüklendiğini doğrulayın. <br>2. Sertifika iptal listesinin (CRL) kullanılabildiğini ve sertifika iptali doğrulama işleminin yapılabildiğini doğrulayın.|
|Microsoft.Common.ExtendedException: Oluşturulan saat ayrıştırılamadı|ATA Gateway, SIEM’den iletilen syslog iletilerini ayrıştıramadı.|SIEM’in iletileri ATA tarafından desteklenen biçimlerden birinde iletecek şekilde yapılandırıldığını doğrulayın.|
|System.ServiceModel.FaultException: İletinin güvenliği doğrulanırken hata oluştu.|ATA Gateway, ATA Center’a karşı kimlik doğrulaması yapamadı.|ATA Gateway saatinin ATA Center’ın saatiyle eşitlendiğini doğrulayın.|
|System.ServiceModel.EndpointNotFoundException: net.tcp://center.ip.addr:443/IEntityReceiver ile bağlantı kurulamadı|ATA Gateway, ATA Center’a bağlantı kuramadı.|Ağ ayarlarınızın doğru olduğundan ve ATA Gateway ile ATA Center arasındaki ağ bağlantısının etkin olduğundan emin olun.|
|System.DirectoryServices.Protocols.LdapException: LDAP sunucusu kullanılamıyor.|ATA Gateway,LDAP protokolünü kullanarak etki alanı denetleyicisini sorgulayamadı.|1.ATA tarafından Active Directory etki alanına bağlanmak için kullanılan kullanıcı hesabının Active Directory ağacındaki tüm nesnelere okuma erişimi olduğunu doğrulayın. <br>2.Etki alanı denetleyicisinin, ATA tarafından kullanılan kullanıcı hesaplarından gelen LDAP sorgularını engellemek üzere güçlendirilmediğinden emin olun.|
|Microsoft.Tri.Infrastructure.ContractException: Sözleşme özel durumu|ATA Gateway, ATA Center’dan yapılandırmayı eşitleyemedi.|ATA Konsolu’nda ATA Gateway yapılandırmasını tamamlayın.|
|System.Reflection.ReflectionTypeLoadException: İstenen türlerden bir veya birkaçı yüklenemiyor. Daha fazla bilgi için LoaderExceptions özelliğini alın.|İleti Çözümleyicisi ATA Gateway’de yüklüdür.| İleti Çözümleyicisi’ni kaldırın.|
|Hata [Layout] System.OutOfMemoryException: 'System.OutOfMemoryException' türünde özel durum oluşturuldu.|ATA Gateway’de yeterli bellek yok.|Etki alanı denetleyicisindeki bellek miktarını artırın.|
|Live consumer  başlatılamadı ---> Microsoft.Opn.Runtime.Monitoring.MessageSessionException: PEFNDIS olay sağlayıcısı hazır değil|PEF (İleti Çözümleyicisi) doğru şekilde yüklenmedi.|Geçici bir çözüm için destek birimine başvurun.|
|Yükleme şu hatayla başarısız oldu: 0x80070652|Bilgisayarınızdaki bekleyen başka yüklemeler var.|Diğer yüklemelerin tamamlanmasını bekleyin ve gerekirse bilgisayarı yeniden başlatın.|

## ATA Konsolu hataları
|Hata|Açıklama|Çözüm|
|-------------|----------|---------|
|HTTP Hatası 500.19 – İç Sunucu Hatası|IIS URL Yeniden yazma modülü düzgün şekilde yüklenemedi.|IIS URL Yeniden yazma modülünü kaldırıp yeniden yükleyin.<br>[IIS URL Yeniden yazma modülünü indirin](http://go.microsoft.com/fwlink/?LinkID=615137)|

## Dağıtım hataları
|Hata|Açıklama|Çözüm|
|-------------|----------|---------|
|.Net Framework 4.6.1 yüklemesi 0x800713ec hatasıyla başarısız oldu|.Net Framework 4.6.1 ön koşulları sunucuda yüklü değil. |ATA’yı yüklemeden önce, [KB2919442](https://www.microsoft.com/download/details.aspx?id=42135) ve [KB2919355](https://support.microsoft.com/kb/2919355) Windows güncelleştirmelerinin sunucuda yüklü olduğunu doğrulayın.|

![ATA .NET yükleme hatası görüntüsü](media/netinstallerror.png)


## Ayrıca Bkz.
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [ATA kapasite planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [Olay koleksiyonunu yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [Windows olay iletme özelliğini yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jul16_HO3-->


