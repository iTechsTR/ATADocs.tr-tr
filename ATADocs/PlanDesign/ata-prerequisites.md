---
title: "ATA Önkoşulları | Microsoft Gelişmiş Tehdit Analizi"
description: "Ortamınızda başarılı bir ATA dağıtımının gereksinimlerini açıklar"
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: a5f90544-1c70-4aff-8bf3-c59dd7abd687
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1f85b9a0f51bd18edaa91ea208d6e6c7c7de56cc
ms.openlocfilehash: da887431d8e63a7ae8ceeb3e7e22011d356e3590


---

# ATA Önkoşulları
Bu makalede, ortamınızda başarılı bir ATA dağıtımı için gereksinimler açıklanır.

>[!NOTE]
> Kaynakları ve kapasiteyi planlama hakkında daha fazla bilgi için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).


ATA yazılımı ATA Center, ATA Gateway ve/veya ATA Lightweight Gateway’den oluşur. ATA bileşenleri hakkında daha fazla bilgi için bkz. [ATA mimarisi](ata-architecture.md)


[Başlamadan önce](#before-you-start): Bu bölümde, ATA yüklemesine başlamadan önce toplamanız gereken bilgiler ve sahip olmanız gereken hesaplarla ağ varlıkları listelenir.

[ATA Center](#ata-center-requirements): Bu bölümde ATA Center donanım ve yazılım gereksinimlerinin yanı sıra, ATA Center sunucunuzda yapılandırmanız gereken ayarlar listelenir.

[ATA Gateway](#ata-gateway-requirements): Bu bölümde ATA Gateway donanım ve yazılım gereksinimlerinin yanı sıra, ATA Gateway sunucularınızda yapılandırmanız gereken ayarlar listelenir.

[ATA Lightweight Gateway](#ata-lightweight-gateway-requirements): Bu bölümde ATA Lightweight Gateway donanım ve yazılım gereksinimleri listelenmiştir.

[ATA Konsolu](#ata-console): Bu bölümde, ATA Konsolu’nu çalıştırmak için tarayıcı gereksinimleri listelenir.

![ATA mimarisi diyagramı](media/ATA-architecture-topology.jpg)

## Başlamadan önce
Bu bölümde, ATA yüklemesine başlamadan önce toplamanız gereken bilgiler ve sahip olmanız gereken hesaplarla ağ varlıkları listelenir.


-   İzlenecek etki alanlarındaki tüm nesnelere okuma erişimi olan kullanıcı hesabı ve parolası.

    > [!NOTE]
    > Etki alanınızdaki çeşitli Kurumsal Birimlerde (OU) özel ACL’ler ayarladıysanız, seçili kullanıcının bu OU’lar üzerinde okuma izinleri olmasına dikkat edin.

-   Ağınızda VPN ve Wi-Fi için kullanılan ve IP adreslerini cihazlar arasında çok kısa sürede (saniyeler veya dakikalar içinde) atayan tüm alt ağların bir listesine sahip olmalısınız.  Bu kısa süreli kiralık alt ağları tanımlamak istersiniz, çünkü böylece ATA cihazlar arasında hızlı yeniden atamayı yapabilmek için önbellek yaşam sürelerini kısaltabilir. Kısa süreli kiralık alt ağ yapılandırması için bkz. [ATA’yı Yükleme](/advanced-threat-analytics/deploy-use/install-ata).
-   İleti Çözümleyicisi ve Wire Shark’ın ATA Gateway veya ATA Center’a yüklenmediğinden emin olun.
-    İsteğe bağlı: Kullanıcının Silinmiş Nesneler kapsayıcısı üzerinde salt okuma izinleri olmalıdır. Bu, ATA’nın etki alanında toplu nesne silme işlemlerini algılamasını sağlar. Silinmiş Nesneler kapsayıcısı üzerinde salt okuma izinlerini yapılandırma hakkında bilgi için, [Dizin Nesnesi Üzerindeki İzinleri Görüntüleme veya Ayarlama](https://technet.microsoft.com/library/cc816824%28v=ws.10%29.aspx) konusunun **Silinmiş nesne kapsayıcısı üzerindeki izinleri değiştirme** bölümüne bakın.

-   İsteğe bağlı: Ağ etkinlikleri olmayan bir kullanıcının kullanıcı hesabı. Bu hesap ATA Honeytoken kullanıcısı olarak yapılandırılır. Honeytoken kullanıcısını yapılandırmak için, kullanıcı adına değil kullanıcı hesabının SID değerine ihtiyacınız vardır.

-   İsteğe bağlı: Etki alanı denetleyicilerinden gelen ve giden ağ trafiğini toplamaya ve çözümlemeye ek olarak, ATA Windows olayı 4776’yı kullanarak ATA Karma Değer Geçişi algılamasını daha da geliştirir. Bu SIEM sistemlerinizden alınabileceği gibi, etki alanı denetleyicinizden Windows Olay İletme’yi ayarlayarak da alınabilir. Toplanan olaylar ATA’ya etki alanı denetleyicisi ağ trafiği yoluyla sağlanmayan ek bilgiler sağlar.


## ATA Center gereksinimleri
Bu bölümde, ATA Center’ın gereksinimleri listelenir.
### Genel
ATA Center, Windows Server 2012 R2 çalıştıran sunuculara yüklemeyi destekler. ATA Center bir etki alanının veya çalışma grubunun üyesi olan sunuculara yüklenebilir.

ATA Center’ı yüklemeden önce şu güncelleştirmenin yüklendiğini onaylayın: [KB2919355](https://support.microsoft.com/kb/2919355/).

Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb2919355]`.

ATA Center’ın bir sanal makine olarak yüklenmesi desteklenir. 

ATA Center’ı sanal makine olarak çalıştırıyorsanız, olası veritabanı bozulmalarını önlemek için yeni bir denetim noktası oluşturmadan önce sunucuyu kapatın.
### Sunucu belirtimleri
Fiziksel bir sunucuda çalışırken, ATA veritabanı için BIOS’ta tekdüzen olmayan bellek erişimini (NUMA) **devre dışı bırakmanız** gerekir. Sisteminizde NUMA Düğüm Araya Ekleme (Node Interleaving) olarak geçiyor olabilir ve bu durumda NUMA’yı devre dışı bırakmak için Düğüm Araya Ekleme’yi **etkinleştirmeniz** gerekecektir. Daha fazla bilgi için BIOS belgelerinize bakın. ATA Center bir sanal sunucuda çalışırken bunun geçerli olmadığını unutmayın.<br>
En iyi performans için, ATA Center’ın **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.<br>
İzlediğiniz etki alanı denetleyicilerinin sayısı ve etki alanı denetleyicilerinden her birinin yükü sunucu belirtimlerini belirler; daha ayrıntılı bilgi için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).

>[!NOTE] 
> Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.

### Zaman eşitleme
ATA Center sunucusu, ATA Gateway sunucuları ve etki alanı denetleyicilerinin zamanlarının 5 dakika içinde birbiriyle eşitlenmesi gerekir.


### Ağ bağdaştırıcıları
Aşağıdakilere sahip olmanız gerekir:
-   En az bir ağ bağdaştırıcısı

-   İki IP adresi (önerilir ancak gerekli değildir)

ATA Center ile ATA Gateway arasındaki iletişim, bağlantı noktası 443 üzerinde SSL kullanılarak şifrelenir. Buna ek olarak, ATA Konsolu IIS üzerinde çalışır ve bağlantı noktası 443 üzerinde SSL kullanılarak güvenlik altına alınır. **İki IP adresi** kullanılması önerilir. ATA Center hizmeti bağlantı noktası 443’ü ilk IP adresine bağlar ve IIS de bağlantı noktası 443’ü ikinci IP adresine bağlar.

> [!NOTE]
> İki farklı bağlantı noktasıyla tek IP adresi kullanılabilir, ama iki IP adresi kullanılması önerilir.

### Bağlantı noktaları
Aşağıdaki tabloda, ATA Center’ın düzgün çalışması için açılması gereken minimum bağlantı noktaları listelenir.

Bu tabloda, IP adresi 1 ATA Center hizmetine ve IP adresi 2 de ATA Konsolu için IIS hizmetine bağlanmıştır.

|Protokol|Aktarım|Bağlantı Noktası|Hedef/Kaynak|Yön|IP Adresi|
|------------|-------------|--------|-----------|-------------|--------------|
|**SSL** (ATA İletişimi)|TCP|443 veya yapılandırılabilir|ATA Gateway|Gelen|IP adresi 1|
|**HTTP**|TCP|80|Şirket Ağı|Gelen|IP adresi 2|
|**HTTPS**|TCP|443|Şirket Ağı ve ATA Gateway|Gelen|IP adresi 2|
|**SMTP** (isteğe bağlı)|TCP|25|SMTP Sunucusu|Giden|IP adresi 2|
|**SMTPS** (isteğe bağlı)|TCP|465|SMTP Sunucusu|Giden|IP adresi 2|
|**Syslog** (isteğe bağlı)|TCP|514|Syslog sunucusu|Giden|IP adresi 2|

### Sertifikalar
ATA Center’ın CRL dağıtım noktanıza erişimi olduğundan emin olun. ATA Gateway bileşenlerinin İnternet erişimi yoksa, [CRL’yi el ile içeri aktarma yordamını](https://technet.microsoft.com/library/aa996972%28v=exchg.65%29.aspx) izleyin ve tüm zincir için CRL dağıtım noktalarının tümünü yükleme işlemini gerçekleştirin.

ATA Center’ın yüklemesini kolaylaştırmak için, ATA Center’ın yüklemesi sırasında otomatik olarak imzalanan sertifikalar yükleyebilirsiniz. Dağıtım sonrasında otomatik olarak imzalanan sertifikayı ATA Gateway tarafından kullanılacak bir iç Sertifika Yetkilisi’nin sertifikasıyla değiştirebilirsiniz.<br>
> [!NOTE]
> Sertifikanın Sağlayıcı Türü, Şifreleme Hizmeti Sağlayıcısı (CSP) olmalıdır.


ATA Center’a aşağıdaki hizmetler için sertifika gerekir:

-   Internet Information Services (IIS) – Web sunucu sertifikası

-   ATA Center hizmeti – Sunucu kimlik doğrulama sertifikası

> [!NOTE]
> ATA Konsolu’na başka bilgisayarlardan erişecekseniz, söz konusu bilgisayarların IIS tarafından kullanılan sertifikaya güvendiğinden emin olmaz; aksi takdirde sayfada oturum açmadan önce web sitesinin güvenlik sertifikasında sorun olduğunu bildiren bir uyarı sayfası alırsınız.

## ATA Gateway gereksinimleri
Bu bölümde, ATA Gateway’in gereksinimleri listelenir.
### Genel
ATA Gateway, Windows Server 2012 R2 çalıştıran sunuculara yüklemeyi destekler.
ATA Gateway bir etki alanının veya çalışma grubunun üyesi olan sunuculara yüklenebilir.

ATA Gateway’i yüklemeden önce şu güncelleştirmenin yüklendiğini onaylayın: [KB2919355](https://support.microsoft.com/kb/2919355/).

Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb2919355]`.

ATA Gateway ile sanal makineleri kullanma hakkında bilgi için bkz. [Bağlantı noktası yansıtmasını yapılandırma](/advanced-threat-analytics/deploy-use/configure-port-mirroring)

### Sunucu belirtimleri
En iyi performans için, ATA Gateway’in **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.<br>
ATA Gateway, etki alanı denetleyicilerinden gelen ve giden ağ trafiği miktarına bağlı olarak, birden çok etki alanı denetleyicisinin izlenmesini destekleyebilir.

>[!NOTE] 
> Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.

### Zaman eşitleme
ATA Center sunucusu, ATA Gateway sunucuları ve etki alanı denetleyicilerinin zamanlarının 5 dakika içinde birbiriyle eşitlenmesi gerekir.

### Ağ bağdaştırıcıları
ATA Gateway için en az bir Yönetim bağdaştırıcısı ve en az bir Yakalama bağdaştırıcısı gerekir:

-   **Yönetim bağdaştırıcısı** - şirket ağınızdaki iletişim için kullanılır. Bu bağdaştırıcı, aşağıdakilerle yapılandırılmalıdır:

    -   Varsayılan ağ geçidi dahil statik IP adresi

    -   Tercih edilen ve alternatif DNS sunucuları

    -   **Bu bağlantı için DNS son eki**, izlenen her etki alanı için etki alanının DNS adı olmalıdır.

        ![Gelişmiş TCP/IP ayarlarında DNS son ekini yapılandırma](media/ATA-DNS-Suffix.png)

        > [!NOTE]
        > ATA Gateway etki alanının üyesiyse, bu otomatik olarak yapılandırılır.

-   **Yakalama bağdaştırıcısı** - etki alanı denetleyicilerinden gelen ve giden trafiği yakalamak için kullanılır.

    > [!IMPORTANT]
    > -   Etki alanı denetleyicisi ağ trafiğinin hedefi olarak yakalama bağdaştırıcısı için bağlantı noktası yansıtmasını yapılandırın. Ek bilgi için bkz. [Bağlantı noktası yansıtmasını yapılandırma](/advanced-threat-analytics/deploy-use/configure-port-mirroring). Normalde, bağlantı noktası yansıtmasını yapılandırmak için ağ veya sanallaştırma ekibiyle çalışmanız gerekir.
    > -   Varsayılan ağ geçidi ve DNS sunucu adresleri olmadan ortamınız için statik yönlendirilemeyen bir IP adresi yapılandırın. Örneğin, 1.1.1.1/32. Bu, yakalama ağ bağdaştırıcısının en yüksek miktarda trafiği yakalayabilmesini ve gerekli ağ trafiğini göndermek ve almak için yönetim ağ bağdaştırıcısının kullanılmasını güvence altına alır.

### Bağlantı noktaları
Aşağıdaki tabloda, ATA Gateway için yönetim bağdaştırıcısında yapılandırılması gereken minimum bağlantı noktaları listelenir.

|Protokol|Aktarım|Bağlantı Noktası|Hedef/Kaynak|Yön|
|------------|-------------|--------|-----------|-------------|
|LDAP|TCP ve UDP|389|Etki alanı denetleyicileri|Giden|
|Güvenli LDAP (LDAPS)|TCP|636|Etki alanı denetleyicileri|Giden|
|LDAP - Genel Katalog|TCP|3268|Etki alanı denetleyicileri|Giden|
|LDAPS - Genel Katalog|TCP|3269|Etki alanı denetleyicileri|Giden|
|Kerberos|TCP ve UDP|88|Etki alanı denetleyicileri|Giden|
|Netlogon|TCP ve UDP|445|Etki alanı denetleyicileri|Giden|
|Windows Saati|UDP|123|Etki alanı denetleyicileri|Giden|
|DNS|TCP ve UDP|53|DNS Sunucuları|Giden|
|RPC üzerinden NTLM|TCP|135|Ağdaki tüm cihazlar|Giden|
|NetBIOS|UDP|137|Ağdaki tüm cihazlar|Giden|
|SSL|TCP|443 veya Center Hizmeti için yapılandırılmış olan|ATA Center:<br /><br />-   Center Hizmeti IP Adresi<br />-   IIS IP Adresi|Giden|
|Syslog (isteğe bağlı)|UDP|514|SIEM Sunucusu|Gelen|

> [!NOTE]
> ATA Gateway tarafından yapılan çözümleme işlemi kapsamında, ATA Gateway bileşenlerinden aşağıdaki bağlantı noktaları ağdaki cihazlarda gelen trafik için açılmalıdır.
>
> -   RPC üzerinden NTLM
> -   NetBIOS

### Sertifikalar
ATA Center’ın CRL dağıtım noktanıza erişimi olduğundan emin olun. ATA Gateway bileşenlerinin İnternet erişimi yoksa, CRL’yi el ile içeri aktarma yordamını izleyin ve tüm zincir için CRL dağıtım noktalarının tümünü yükleme işlemini gerçekleştirin.<br>
ATA Center’ın yüklemesini kolaylaştırmak için, ATA Center’ın yüklemesi sırasında otomatik olarak imzalanan sertifikalar yükleyebilirsiniz. Dağıtım sonrasında otomatik olarak imzalanan sertifikayı ATA Gateway tarafından kullanılacak bir iç Sertifika Yetkilisi’nin sertifikasıyla değiştirebilirsiniz.

> [!NOTE]
> Sertifikanın Sağlayıcı Türü, Şifreleme Hizmeti Sağlayıcısı (CSP) olmalıdır.<br>

Yerel Bilgisayar deposunda yer alan ATA Gateway’in Bilgisayar deposunda **Sunucu Kimlik Doğrulaması**’nı destekleyen bir sertifikanın yüklenmesi gerekir. ATA Center tarafından bu sertifikaya güvenilmelidir.

## ATA Lightweight Gateway gereksinimleri
Bu bölümde, ATA Lightweight Gateway’in gereksinimleri listelenir.
### Genel
ATA Lightweight Gateway; Windows Server 2008 R2 SP1, Windows Server 2012 veya Windows Server 2012 R2 çalıştıran bir etki alanı denetleyicisine yüklemeyi destekler.

Etki alanı denetleyicisi salt okunur bir etki alanı denetleyicisi (RODC) olabilir.

Etki alanı denetleyicisi Sunucu Çekirdeği olamaz.

ATA Lightweight Gateway bileşenini Windows Server 2012 R2 SP1 çalıştıran bir etki alanı denetleyicisine yüklemeden önce, şu güncelleştirmenin yüklendiğini onaylayın: [KB2919355](https://support.microsoft.com/kb/2919355/).
Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb2919355]`.

### Sunucu belirtimleri

ATA Lightweight Gateway, etki alanı denetleyicisinde en az 2 çekirdek ve 6 GB RAM kurulu olmasını gerektirir.
En iyi performans için, ATA Lightweight Gateway’in **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.
ATA Lightweight Gateway, etki alanı denetleyicilerinden gelen ve giden ağ trafiğinin miktarına ve bu etki alanında kurulu kaynakların miktarına bağlı olarak çeşitli yük ve büyüklükte etki alanı denetleyicilerinde dağıtılabilir.

>[!NOTE] 
> Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.


### Zaman eşitleme
ATA Center sunucusu, ATA Lightweight Gateway sunucuları ve etki alanı denetleyicilerinin zamanlarının 5 dakika içinde birbiriyle eşitlenmesi gerekir.
### Ağ bağdaştırıcıları
ATA Lightweight Gateway etki alanı denetleyicisinin ağ bağdaştırıcılarının hepsindeki yerel trafiği izler. <br>
Dağıtımdan sonra, hangi ağ bağdaştırıcılarının izlendiğini değiştirmek isterseniz ATA Konsolu’nu kullanabilirsiniz.

### Bağlantı noktaları
Aşağıdaki tabloda, ATA Lightweight Gateway için gereken minimum bağlantı noktaları listelenir.

|Protokol|Aktarım|Bağlantı Noktası|Hedef/Kaynak|Yön|
|------------|-------------|--------|-----------|-------------|
|DNS|TCP ve UDP|53|DNS Sunucuları|Giden|
|RPC üzerinden NTLM|TCP|135|Ağdaki tüm cihazlar|Giden|
|NetBIOS|UDP|137|Ağdaki tüm cihazlar|Giden|
|SSL|TCP|443 veya Center Hizmeti için yapılandırılmış olan|ATA Center:<br /><br />-   Center Hizmeti IP Adresi<br />-   IIS IP Adresi|Giden|
|Syslog (isteğe bağlı)|UDP|514|SIEM Sunucusu|Gelen|

> [!NOTE]
> ATA Lightweight Gateway tarafından yapılan çözümleme işlemi kapsamında, ATA Lightweight Gateway bileşenlerinden aşağıdaki bağlantı noktaları ağdaki cihazlarda gelen trafik için açılmalıdır.
>
> -   RPC üzerinden NTLM
> -   NetBIOS

### Sertifikalar
ATA Center’ın CRL dağıtım noktanıza erişimi olduğundan emin olun. ATA Lightweight Gateway bileşenlerinin İnternet erişimi yoksa, CRL’yi el ile içeri aktarma yordamını izleyin ve tüm zincir için CRL dağıtım noktalarının tümünü yükleme işlemini gerçekleştirin.
ATA Center’ın yüklemesini kolaylaştırmak için, ATA Center’ın yüklemesi sırasında otomatik olarak imzalanan sertifikalar yükleyebilirsiniz. Dağıtım sonrasında otomatik olarak imzalanan sertifikayı ATA Lightweight Gateway tarafından kullanılacak bir iç Sertifika Yetkilisi’nin sertifikasıyla değiştirebilirsiniz.
> [!NOTE]
> Sertifikanın Sağlayıcı Türü, Şifreleme Hizmeti Sağlayıcısı (CSP) olmalıdır.

Yerel Bilgisayar deposunda yer alan ATA Lightweight Gateway’in Bilgisayar deposunda Sunucu Kimlik Doğrulaması’nı destekleyen bir sertifikanın yüklenmesi gerekir. ATA Center tarafından bu sertifikaya güvenilmelidir.

## ATA Konsolu
ATA Konsolu’na tarayıcı yoluyla erişilir ve aşağıdakiler desteklenir:

-   Internet Explorer sürüm 10 ve üstü

-   Google Chrome 40 ve üstü

-   Minimum ekran genişliği çözünürlüğü 1700 piksel

## Ayrıca Bkz.

- [ATA mimarisi](ata-architecture.md)
- [ATA’yı yükleme](/advanced-threat-analytics/deploy-use/install-ata)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)




<!--HONumber=Jun16_HO5-->


