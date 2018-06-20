---
title: Bilinen ATA sorunlarını giderme | Microsoft Docs
description: Bilinen Advanced Threat Analytics sorunlarını nasıl giderebileceğinizi açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: d89e7aff-a6ef-48a3-ae87-6ac2e39f3bdb
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: a7172447de5b4d4088da2d8d687a7bec47a01551
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
ms.locfileid: "30010491"
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*



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
|System.IO.IOException: Uzak taraf taşıma akışını kapattığından kimlik doğrulaması başarısız oldu.|TLS 1.0 ATA Gateway'de devre dışıdır, ancak .net TLS 1.2 kullanmak üzere ayarlanmış|Aşağıdaki seçeneklerden birini kullanın: </br> TLS 1.0 ‘ı ATA Gateway’de etkinleştirme </br>TLS 1.2 .net üzerinde SSL ve TLS, işletim sistemi Varsayılanları şu şekilde kullanmak için kayıt defteri anahtarlarını ayarlayarak etkinleştirin: </br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001` </br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001`</br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SchUseStrongCrypto"=dword:00000001 `</br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] " SchUseStrongCrypto"=dword:00000001`|
|System.TypeLoadException: 'Microsoft.Opn.Runtime.Values.BinaryValueBufferManager' türü, 'Microsoft.Opn.Runtime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' derlemesinden yüklenemiyor|ATA Gateway gerekli ayrıştırma dosyalarını yüklemede başarısız oldu.|Microsoft İleti Çözümleyicisi’nin yüklü olup olmadığını kontrol edin. İleti Çözümleyicisi’nin ATA Gateway veya Lightweight Gateway ile birlikte yüklü olması desteklenmemektedir. İleti Çözümleyicisi'ni kaldırın ve Gateway hizmetini yeniden başlatın.|
|System.Net.WebException: Uzak sunucu bir hata döndürdü: (407) Ara Sunucu Kimlik Doğrulaması Gerekli|ATA Center ile ATA Gateway iletişimi ara sunucu tarafından kesiliyor.|ATA Gateway makinesinde ara sunucuyu devre dışı bırakın. <br></br>Ara sunucu ayarlarının hesaba göre değişebileceğini unutmayın.|
|System.IO.DirectoryNotFoundException: Sistem, belirtilen yolu bulamıyor. (HRESULT: 0x80070003 özel durumu)|ATA’yı çalıştırması gereken bir veya daha fazla hizmet başlatılamadı.|Aşağıdaki hizmetleri başlatın: <br></br>Performans Günlükleri ve Uyarıları (PLA), Görev Zamanlayıcı (Zamanlama).|
|System.Net.WebException: Uzak sunucu bir hata döndürdü: (403) Yasak|ATA Gateway veya Lightweight Gateway ATA Center güvenilir olmadığı için bir HTTP bağlantısı kurmadan alınamaz.|NetBIOS adı ve ATA Center FQDN'sini güvenilen Web siteleri listesine ekleyin ve Interne Explorer (veya yapılandırılmış NetBIOS/FQDN farklı olması durumunda yapılandırma belirtildiği gibi ATA Center adı) önbellekte temizleyin.|
|System.Net.Http.HttpRequestException: PostAsync failed [requestTypeName=StopNetEventSessionRequest]|ATA Gateway veya ATA Lightweight Gateway olamaz durdurun ve WMI sorunu nedeniyle ağ trafiğini toplar ETW oturumunu Başlat|' Ndaki yönergeleri izleyin [WMI: WMI deposunu yeniden](https://blogs.technet.microsoft.com/askperf/2009/04/13/wmi-rebuilding-the-wmi-repository/) WMI sorunu gidermek için|
|System.Net.Sockets.SocketException: Yuva erişim izinlerini tarafından yasaklanmış bir şekilde erişmek için girişimde bulunuldu|Başka bir uygulama ATA Gateway'de bağlantı noktası 514 kullanıyor|Kullanım `netstat -o` Bu bağlantı noktası hangi işlemin kullandığını kurmak için.|
 
## <a name="deployment-errors"></a>Dağıtım hataları
> [!div class="mx-tableFixed"]
|Hata|Description|Çözüm|
|-------------|----------|---------|
|.Net Framework 4.6.1 yüklemesi 0x800713ec hatasıyla başarısız oldu|.Net Framework 4.6.1 ön koşulları sunucuda yüklü değil. |ATA’yı yüklemeden önce, [KB2919442](https://www.microsoft.com/download/details.aspx?id=42135) ve [KB2919355](https://support.microsoft.com/kb/2919355) Windows güncelleştirmelerinin sunucuda yüklü olduğunu doğrulayın.|
|System.Threading.Tasks.TaskCanceledException: Bir görev iptal edildi|Dağıtım işlemi, ATA Center’a erişemediği için zaman aşımına uğradı.|1.    IP adresi ile ATA Center’a gözatarak ağ bağlantısını kontrol edin. <br></br>2.    Ara sunucu veya güvenlik duvarı yapılandırması olup olmadığını denetleyin.|
|System.Net.Http.HttpRequestException: İsteği gönderirken bir hata oluştu. ---> System.Net.WebException: Uzak sunucu bir hata döndürdü: (407) Ara Sunucu Kimlik Doğrulaması Gerekli.|Dağıtım işlemi, bir ara sunucunun yanlış yapılandırması nedeniyle ATA Center’a erişemediği için zaman aşımına uğradı.|Dağıtımdan önce ara sunucu yapılandırmasını devre dışı bırakın ve ardından ara sunucu yapılandırmasını yeniden etkinleştirin. Veya bunun yerine ara sunucuda bir özel durum yapılandırabilirsiniz.|
|System.Net.Sockets.SocketException: Varolan bir bağlantıyı zorla uzak ana bilgisayar tarafından kapatıldı||Aşağıdaki seçeneklerden birini kullanın: </br>TLS 1.0 ‘ı ATA Gateway’de etkinleştirme </br>TLS 1.2 .net üzerinde SSL ve TLS, işletim sistemi Varsayılanları şu şekilde kullanmak için kayıt defteri anahtarlarını ayarlayarak etkinleştirin:</br> `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001`</br> `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001`</br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SchUseStrongCrypto"=dword:00000001` </br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] " SchUseStrongCrypto"=dword:00000001`|
|Hata [\[] DeploymentModel [\]] başarısız yönetim kimlik doğrulama [\[] CurrentlyLoggedOnUser =<domain>\<kullanıcı adı > Durum = FailedAuthentication özel durum = [\]]|ATA Gateway veya ATA Lightweight Gateway dağıtım işlemini başarıyla ATA Center'a karşı kimlik doğrulaması yapamıyor|Dağıtım işlemi başarısız makineden bir tarayıcı açın ve ATA Konsolu erişebilir, bkz. </br>Aksi durumda, tarayıcının ATA Center'a karşı neden doğrulanamaz görmek için sorun gidermeyi başlatma. </br>Denetlenecek öğeler: </br>Proxy yapılandırması</br>Ağ sorunları</br>Grup İlkesi ayarları ATA Center'dan farklı bu makinede kimlik doğrulaması için.|





## <a name="ata-gateway-and-lightweight-gateway-issues"></a>ATA Gateway ve Lightweight Gateway sorunları

> [!div class="mx-tableFixed"]
|Sorun|Description|Çözüm|
|-------------|----------|---------|
|Etki alanı denetleyicisinden trafik alınmıyor ama izleme uyarıları gözlemleniyor|    ATA Gateway’den bağlantı noktası yansıtma kullanan bir etki alanı denetleyicisinden trafik alınmadı|ATA Gateway yakalama NIC’sindeki **Gelişmiş Ayarlar**’da şu özellikleri devre dışı bırakın:<br></br>Alma Kesimi Birleştirme (IPv4)<br></br>Alma Kesimi Birleştirme (IPv6)|
|Bu izleme uyarı görüntülenir: **olmayan bazı ağ trafiğini analiz ediliyor**|VMware sanal makineleri bir ATA Gateway veya Lightweight Gateway varsa, bu izleme uyarı alabilirsiniz. Bu VMware yapılandırma uyuşmazlık nedeniyle olur.|Aşağıdaki ayarları ayarlamak **0** veya **devre dışı** sanal makinenin NIC yapılandırmasında: TsoEnable LargeSendOffload, TSO boşaltma, çok büyük TSO boşaltma|TLS 1.0 için ATA Gateway'de devre dışı ancak .net TLS 1.2 kullanmak üzere ayarlanmış|




## <a name="see-also"></a>Ayrıca bkz:
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
