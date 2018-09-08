---
title: Bilinen ATA sorunlarını giderme | Microsoft Docs
description: Bilinen Advanced Threat Analytics sorunlarını nasıl giderebileceğinizi açıklar
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 7/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: d89e7aff-a6ef-48a3-ae87-6ac2e39f3bdb
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: 855c4d01f67be6331bb566b1f91821e5721e6911
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44166587"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="troubleshooting-ata-known-issues"></a>Bilinen ATA sorunlarını giderme

Bu bölüm, ATA dağıtımlarındaki olası hataları ve bunları gidermek için gereken adımları açıklar.

## <a name="ata-gateway-and-lightweight-gateway-errors"></a>ATA Gateway ve Lightweight Gateway hataları

> [!div class="mx-tableFixed"]
|Hata|Description|Çözüm|
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
|System.InvalidOperationException: 'Microsoft.Tri.Gateway' örneği belirtilen Kategoride yok.|ATA Gateway’deki işlem adları için PID’ler etkinleştirilmiş|İşlem adlarında PID’leri devre dışı bırakmak için [KB281884](https://support.microsoft.com/kb/281884)’yi kullanın|
|System.InvalidOperationException: Kategori yok.|Sayaçlar kayıt defterinde devre dışı bırakılmış olabilir|Performans Sayaçlarını yeniden oluşturmak için [KB2554336](https://support.microsoft.com/kb/2554336)’yı kullanın|
|System.ApplicationException: ETW oturumu MMA-ETW-Livecapture-a4f595bd-f567-49a7-b963-20fa4e370329 başlatılamıyor|HOSTS dosyasında makinenin kısa adına işaret eden bir ana bilgisayar girişi var|Ana bilgisayar girişini C:\Windows\System32\drivers\etc\HOSTS dosyasından kaldırın ya da bir FQDN olarak değiştirin.|
|System.IO.IOException: Uzak taraf taşıma akışını kapattığından kimlik doğrulaması başarısız oldu.|TLS 1.0, ATA Gateway'de devre dışı bırakıldı ancak .net TLS 1.2 kullanmak üzere ayarlanmış|Aşağıdaki seçeneklerden birini kullanın: </br> TLS 1.0 ‘ı ATA Gateway’de etkinleştirme </br>TLS 1.2 .net üzerinde SSL ve TLS için işletim sistemi varsayılanları kullanacak şekilde kayıt defteri anahtarlarını ayarlayarak etkinleştir: </br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001` </br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001`</br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SchUseStrongCrypto"=dword:00000001 `</br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] " SchUseStrongCrypto"=dword:00000001`|
|System.TypeLoadException: 'Microsoft.Opn.Runtime.Values.BinaryValueBufferManager' türü, 'Microsoft.Opn.Runtime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' derlemesinden yüklenemiyor|ATA Gateway gerekli ayrıştırma dosyalarını yüklemede başarısız oldu.|Microsoft İleti Çözümleyicisi’nin yüklü olup olmadığını kontrol edin. İleti Çözümleyicisi’nin ATA Gateway veya Lightweight Gateway ile birlikte yüklü olması desteklenmemektedir. İleti Çözümleyicisi'ni kaldırın ve Gateway hizmetini yeniden başlatın.|
|System.Net.WebException: Uzak sunucu bir hata döndürdü: (407) Ara Sunucu Kimlik Doğrulaması Gerekli|ATA Center ile ATA Gateway iletişimi ara sunucu tarafından kesiliyor.|ATA Gateway makinesinde ara sunucuyu devre dışı bırakın. <br></br>Ara sunucu ayarlarının hesaba göre değişebileceğini unutmayın.|
|System.IO.DirectoryNotFoundException: Sistem, belirtilen yolu bulamıyor. (HRESULT: 0x80070003 özel durumu)|ATA’yı çalıştırması gereken bir veya daha fazla hizmet başlatılamadı.|Aşağıdaki hizmetleri başlatın: <br></br>Performans Günlükleri ve Uyarıları (PLA), Görev Zamanlayıcı (Zamanlama).|
|System.Net.WebException: Uzak sunucu bir hata döndürdü: (403) Yasak|ATA Gateway veya Lightweight Gateway ATA Center güvenilir olmadığı için bir HTTP bağlantısı kurmasını Yasak.|ATA Center'ın FQDN ve NetBIOS adını güvenilir Web siteleri listesine ekleyin ve Interne Explorer (veya yapılandırılmış NetBIOS/FQDN farklı olması durumunda yapılandırmasında belirtilen ATA Center'ın adı) önbelleğini temizleyin.|
|System.Net.Http.HttpRequestException: PostAsync başarısız oldu. [requestTypeName StopNetEventSessionRequest =]|ATA Gateway veya ATA Lightweight Gateway olamaz durdurup WMI sorun nedeniyle ağ trafiği toplayan ETW oturumu|Bölümündeki yönergeleri [WMI: WMI deposunun yeniden](https://blogs.technet.microsoft.com/askperf/2009/04/13/wmi-rebuilding-the-wmi-repository/) WMI sorunu düzeltmek için|
|System.Net.Sockets.SocketException: Bir yuva, erişim izinleri tarafından yasaklanmış bir şekilde erişmek girişiminde bulunuldu|Başka bir uygulama, ATA Gateway'e bağlantı noktası 514 kullanıyor|Kullanım `netstat -o` Bu bağlantı noktası hangi işlemin kullandığını kurmak için.|
 
## <a name="deployment-errors"></a>Dağıtım hataları
> [!div class="mx-tableFixed"]
|Hata|Description|Çözüm|
|-------------|----------|---------|
|.Net Framework 4.6.1 yüklemesi 0x800713ec hatasıyla başarısız oldu|.Net Framework 4.6.1 ön koşulları sunucuda yüklü değil. |ATA’yı yüklemeden önce, [KB2919442](https://www.microsoft.com/download/details.aspx?id=42135) ve [KB2919355](https://support.microsoft.com/kb/2919355) Windows güncelleştirmelerinin sunucuda yüklü olduğunu doğrulayın.|
|System.Threading.Tasks.TaskCanceledException: Bir görev iptal edildi|Dağıtım işlemi, ATA Center’a erişemediği için zaman aşımına uğradı.|1.    IP adresi ile ATA Center’a gözatarak ağ bağlantısını kontrol edin. <br></br>2.    Ara sunucu veya güvenlik duvarı yapılandırması olup olmadığını denetleyin.|
|System.Net.Http.HttpRequestException: İsteği gönderirken bir hata oluştu. ---> System.Net.WebException: Uzak sunucu bir hata döndürdü: (407) Ara Sunucu Kimlik Doğrulaması Gerekli.|Dağıtım işlemi, bir ara sunucunun yanlış yapılandırması nedeniyle ATA Center’a erişemediği için zaman aşımına uğradı.|Dağıtımdan önce ara sunucu yapılandırmasını devre dışı bırakın ve ardından ara sunucu yapılandırmasını yeniden etkinleştirin. Veya bunun yerine ara sunucuda bir özel durum yapılandırabilirsiniz.|
|System.Net.Sockets.SocketException: Var olan bir bağlantı uzak konak tarafından zorla kapatılıp||Aşağıdaki seçeneklerden birini kullanın: </br>TLS 1.0 ‘ı ATA Gateway’de etkinleştirme </br>TLS 1.2 .net üzerinde SSL ve TLS için işletim sistemi varsayılanları kullanacak şekilde kayıt defteri anahtarlarını ayarlayarak etkinleştir:</br> `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001`</br> `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001`</br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SchUseStrongCrypto"=dword:00000001` </br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] " SchUseStrongCrypto"=dword:00000001`|
|Hata [\[] DeploymentModel [\]] başarısız yönetim kimlik doğrulama [\[] CurrentlyLoggedOnUser =<domain>\<kullanıcıadı > Durum FailedAuthentication özel durum = = [\]]|ATA Gateway veya ATA Lightweight Gateway dağıtım işlemini başarıyla ATA Center'a karşı kimlik doğrulaması yapılamadı|Dağıtım işlemi başarısız makineden bir tarayıcıyı açıp ATA Konsolu'na ulaşıp ulaşamadığını. </br>Aksi durumda, tarayıcının ATA Center'a karşı neden kimlik doğrulaması yapamaz görmek için sorun gidermeyi başlatma. </br>Denetlenecek noktalar şunlardır: </br>Proxy yapılandırması</br>Ağ sorunları</br>Grup İlkesi ayarları ATA Center'dan farklı bu makinede kimlik doğrulaması için.|


## <a name="ata-center-errors"></a>ATA Center hataları
> [!div class="mx-tableFixed"]
|Hata|Description|Çözüm|
|-------------|----------|---------|
|System.Security.Cryptography.CryptographicException: erişim reddedildi.|ATA Center, şifre çözme için sertifikayı kullanmak başarısız oldu. Bu büyük olasılıkla son bir sertifikanın imza ayarlamak KeySpec öğesinin (KeyNumber) ile kullanılacak gerçekleştiği (ADRESİNDEKİ\_imzası) desteklenmeyen KeyExchange kullanmak yerine şifre çözme için (en\_KEYEXCHANGE).|1.    ATA Center hizmeti durdurun. <br></br>2.     ATA Center sertifikasını merkezi sertifika deposundan silin. (Silmeden önce bir PFX dosyasında özel anahtarla yedeklediğiniz sertifikayı sahip olduğunuzdan emin olun.) <br></br>3.    Yükseltilmiş bir komut istemi açın ve certutil - importpfx "CenterCertificate.pfx" AT çalıştırma\_KEYEXCHANGE <br></br>4.     ATA Center hizmeti başlatın. <br></br>5.     Her şeyin beklendiği gibi çalıştığını doğrulayın.|


## <a name="ata-gateway-and-lightweight-gateway-issues"></a>ATA Gateway ve Lightweight Gateway sorunları

> [!div class="mx-tableFixed"]
|Sorun|Description|Çözüm|
|-------------|----------|---------|
|Etki alanı denetleyicisinden trafik alınmıyor ama izleme uyarıları gözlemleniyor|    ATA Gateway’den bağlantı noktası yansıtma kullanan bir etki alanı denetleyicisinden trafik alınmadı|ATA Gateway yakalama NIC’sindeki **Gelişmiş Ayarlar**’da şu özellikleri devre dışı bırakın:<br></br>Alma Kesimi Birleştirme (IPv4)<br></br>Alma Kesimi Birleştirme (IPv6)|
|Bu uyarı görüntülenir: **ağ trafiğinin bir kısmı analiz edilmiyor**|VMware sanal makinelerindeki bir ATA Gateway veya Lightweight Gateway varsa, bu uyarı alabilirsiniz. Bu, bir VMware yapılandırma uyuşmazlık nedeniyle olur.|Aşağıdaki ayarlar **0** veya **devre dışı** sanal makine NIC yapılandırması: TsoEnable, LargeSendOffload, tso veri boşaltma, büyük TSO boşaltma|TLS 1.0, ATA Gateway'de devre dışı bırakıldı ancak .net TLS 1.2 kullanmak üzere ayarlanmış|




## <a name="see-also"></a>Ayrıca Bkz.
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
