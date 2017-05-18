---
title: "Advanced Threat Analytics hata günlüğü sorunlarını giderme | Microsoft Docs"
description: "ATA’da sık karşılaşılan hataları nasıl giderebileceğinizi açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/14/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: d89e7aff-a6ef-48a3-ae87-6ac2e39f3bdb
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: a87fed6bf8ce69ea3391e729c57217d1cff8ffc2
ms.sourcegitcommit: a1595b51c95235eede3d3b34a02f24bedd5dfc5a
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2017
---
*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*



# <a name="troubleshooting-the-ata-error-log"></a>ATA hata günlüğü sorunlarını giderme

Bu bölüm, ATA dağıtımlarındaki olası hataları ve bunları gidermek için gereken adımları açıklar.

## <a name="ata-gateway-errors"></a>ATA Gateway hataları

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
|Live consumer  başlatılamadı ---> Microsoft.Opn.Runtime.Monitoring.MessageSessionException: PEFNDIS olay sağlayıcısı hazır değil|PEF (İleti Çözümleyicisi) doğru şekilde yüklenmedi.|Hyper-V kullanıyorsanız Hyper-V Tümleştirme hizmetlerini yükseltmeyi deneyin; aksi takdirde, geçici bir çözüm için desteğe başvurun.|
|Yükleme şu hatayla başarısız oldu: 0x80070652|Bilgisayarınızdaki bekleyen başka yüklemeler var.|Diğer yüklemelerin tamamlanmasını bekleyin ve gerekirse bilgisayarı yeniden başlatın.|
|System.InvalidOperationException: 'Microsoft.Tri.Gateway' örneği belirtilen Kategoride yok.|ATA Gateway’deki işlem adları için PID’ler etkinleştirilmiş|İşlem adlarında PID’leri devre dışı bırakmak için [KB281884](https://support.microsoft.com/en-us/kb/281884)’yi kullanın|
|System.InvalidOperationException: Kategori yok.|Sayaçlar kayıt defterinde devre dışı bırakılmış olabilir|Performans Sayaçlarını yeniden oluşturmak için [KB2554336](https://support.microsoft.com/en-us/kb/2554336)’yı kullanın|
|System.ApplicationException: ETW oturumu MMA-ETW-Livecapture-a4f595bd-f567-49a7-b963-20fa4e370329 başlatılamıyor|HOSTS dosyasında makinenin kısa adına işaret eden bir ana bilgisayar girişi var|Ana bilgisayar girişini C:\Windows\System32\drivers\etc\HOSTS dosyasından kaldırın ya da bir FQDN olarak değiştirin.|
|System.IO.IOException: Uzak taraf taşıma akışını kapattığından kimlik doğrulaması başarısız oldu.|TLS 1.0, ATA Gateway’de devre dışı bırakıldı ancak .Net, TLS 1.2 kullanmak üzere ayarlanmış|Aşağıdaki seçeneklerden birini kullanın: </br> TLS 1.0 ‘ı ATA Gateway’de etkinleştirme </br>TLS 1.2’yi .Net üzerinde etkinleştirmek amacıyla kayıt defteri anahtarlarını LLS ve TLS için işletim sistemi varsayılanları kullanacak şekilde ayarlayın: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001` </br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001`|



## <a name="ata-lightweight-gateway-errors"></a>ATA Lightweight Gateway hataları

**Hata**: VMware’de Lightweight Gateway kullanırken alınan, bağlantı noktası yansıtma trafiği bırakıldı uyarıları

**Açıklama**: VMware sanal makinelerinde etki alanı denetleyicileri kullanıyorsanız, **Bağlantı noktası yansıtma trafiği bırakıldı** uyarıları alabilirsiniz. Bunun sebebi, bir VMware yapılandırma uyuşmazlığı olabilir. 
**Çözüm**: Bu uyarıları önlemek için, şu ayarların 0 veya Devre Dışı olarak belirlendiğinden emin olun: TsoEnable, LargeSendOffload, IPv4, TSO Offload. Ayrıca, IPv4 Büyük TSO Boşaltma’yı devre dışı bırakabilirsiniz. Daha fazla bilgi için VMware belgelerinize başvurun.


## <a name="ata-iis-errors-not-applicable-for-ata-v17-and-above"></a>ATA IIS hataları (ATA v1.7 ve üzeri sürümlerde uygulanamaz)
|Hata|Açıklama|Çözüm|
|-------------|----------|---------|
|HTTP Hatası 500.19 – İç Sunucu Hatası|IIS URL Yeniden yazma modülü düzgün şekilde yüklenemedi.|IIS URL Yeniden yazma modülünü kaldırıp yeniden yükleyin.<br>[IIS URL Yeniden yazma Modülü’nü indirin](http://go.microsoft.com/fwlink/?LinkID=615137)|

## <a name="deployment-errors"></a>Dağıtım hataları
|Hata|Açıklama|Çözüm|
|-------------|----------|---------|
|.Net Framework 4.6.1 yüklemesi 0x800713ec hatasıyla başarısız oldu|.Net Framework 4.6.1 ön koşulları sunucuda yüklü değil. |ATA’yı yüklemeden önce, [KB2919442](https://www.microsoft.com/download/details.aspx?id=42135) ve [KB2919355](https://support.microsoft.com/kb/2919355) Windows güncelleştirmelerinin sunucuda yüklü olduğunu doğrulayın.|

![ATA .NET yükleme hatası görüntüsü](media/netinstallerror.png)


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [ATA kapasite planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [Olay koleksiyonunu yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [Windows olay iletme özelliğini yapılandırma](/advanced-threat-analytics/deploy-use/configure-event-collection#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
