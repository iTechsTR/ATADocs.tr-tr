---
# required metadata

title: ATA Önkoşulları | Microsoft Gelişmiş Tehdit Analizi
description: Ortamınızda başarılı bir ATA dağıtımının gereksinimlerini açıklar
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: a5f90544-1c70-4aff-8bf3-c59dd7abd687

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ATA Önkoşulları
Bu makalede, ortamınızda başarılı bir ATA dağıtımı için gereksinimler açıklanır.

ATA iki bileşenden oluşur: ATA Center ve ATA Gateway. ATA bileşenleri hakkında daha fazla bilgi için bkz. [ATA mimarisi](/advanced-threat-analytics/understand-explore/ata-architecture).

[Başlamadan önce](#before-you-start): Bu bölümde, ATA yüklemesine başlamadan önce toplamanız gereken bilgiler ve sahip olmanız gereken hesaplarla ağ varlıkları listelenir.

[ATA Center](#ata-center-requirements): Bu bölümde ATA Center donanım ve yazılım gereksinimlerinin yanı sıra, ATA Center sunucunuzda yapılandırmanız gereken ayarlar listelenir.

[ATA Gateway](#ata-gateway-requirements): Bu bölümde ATA Gateway donanım ve yazılım gereksinimlerinin yanı sıra, ATA Gateway sunucularınızda yapılandırmanız gereken ayarlar listelenir.

[ATA Konsolu](#ata-console): Bu bölümde, ATA Konsolu’nu çalıştırmak için tarayıcı gereksinimleri listelenir.

![ATA mimarisi diyagramı](media/ATA-architecture-topology.jpg)

## Başlamadan önce
Bu bölümde, ATA yüklemesine başlamadan önce toplamanız gereken bilgiler ve sahip olmanız gereken hesaplarla ağ varlıkları listelenir.

-   **Etki alanı denetleyicileri**: Windows Server 2008 ve sonraki sürümlerde çalışan denetleyiciler.

-   **Kullanıcı hesabı ve parolası**: İzlenecek etki alanlarındaki **tüm nesnelere** okuma erişimi olan hesaplar.

    > [!NOTE]
    > Etki alanınızdaki çeşitli Kurumsal Birimlerde (OU) özel ACL’ler ayarladıysanız, seçili kullanıcının bu OU’lar üzerinde okuma izinleri olmasına dikkat edin.

    İsteğe bağlı: Kullanıcının Silinmiş Nesneler kapsayıcısı üzerinde salt okuma izinleri olmalıdır. Bu, ATA’nın etki alanında toplu nesne silme işlemlerini algılamasını sağlar. Silinmiş Nesneler kapsayıcısı üzerinde salt okuma izinlerini yapılandırma hakkında bilgi için, [Dizin Nesnesi Üzerindeki İzinleri Görüntüleme veya Ayarlama](https://technet.microsoft.com/library/cc816824%28v=ws.10%29.aspx) konusunun **Silinmiş nesne kapsayıcısı üzerindeki izinleri değiştirme** bölümüne bakın.

-   İsteğe bağlı: Ağ etkinlikleri olmayan bir kullanıcının kullanıcı hesabı. Bu hesap ATA Honeytoken kullanıcısı olarak yapılandırılır. Honeytoken kullanıcısını yapılandırmak için, kullanıcı adına değil kullanıcı hesabının SID değerine ihtiyacınız vardır.

-   İsteğe bağlı: Etki alanı denetleyicilerinden gelen ve giden ağ trafiğini toplamaya ve çözümlemeye ek olarak, ATA Windows olayı 4776’yı kullanarak ATA Karma Değer Geçişi algılamasını daha da geliştirir. Bu SIEM sistemlerinizden alınabileceği gibi, etki alanı denetleyicinizden Windows Olay İletme’yi ayarlayarak da alınabilir. Toplanan olaylar ATA’ya etki alanı denetleyicisi ağ trafiği yoluyla sağlanmayan ek bilgiler sağlar.

-   Ağınızda VPN ve Wi-Fi için kullanılan ve IP adreslerini cihazlar arasında çok kısa sürede (saniyeler veya dakikalar içinde) atayan tüm alt ağların bir listesine sahip olmanız yararlı olabilir.  Bu kısa süreli kiralık alt ağları tanımlamak istersiniz, çünkü böylece ATA cihazlar arasında hızlı yeniden atamayı yapabilmek için önbellek yaşam sürelerini kısaltabilir. Kısa süreli kiralık alt ağ yapılandırması için bkz. [ATA’yı Yükleme](/advanced-threat-analytics/deploy-useinstall-ata).

## ATA Center gereksinimleri
Bu bölümde, ATA Center’ın gereksinimleri listelenir.

ATA Center, Windows Server 2012 R2 çalıştıran sunuculara yüklemeyi destekler. Windows Update’i çalıştırın ve tüm önemli güncelleştirmelerin yüklendiğinden emin olun.
 Donanım gereksinimleri, izlediğiniz etki alanı denetleyicilerinin sayısına ve etki alanı denetleyicilerinden her birinin yüküne göre belirlenir.

ATA Center’ın bir sanal makine olarak yüklenmesi desteklenir. Daha fazla bilgi için bkz. [Bağlantı noktası yansıtmasını yapılandırma](configure-port-mirroring.md).

ATA Center’ı sanal makine olarak çalıştırıyorsanız, olası veritabanı bozulmalarını önlemek için yeni bir denetim noktası oluşturmadan önce sunucuyu kapatın.

> [!NOTE]
> - ATA Center bir etki alanının veya çalışma grubunun üyesi olan sunuculara yüklenebilir.
>
> - Kullanıcı davranış analizi için ATA Center’a en az 21 günlük veri gerekir.
>
> - Donanım gereksinimleri hakkında daha fazla bilgi için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).


### Zaman eşitleme
ATA Center sunucusu, ATA Gateway sunucuları ve etki alanı denetleyicilerinin zamanlarının 5 dakika içinde birbiriyle eşitlenmesi gerekir.

### BIOS ayarları
ATA veritabanı için, BIOS’ta tekdüzen olmayan bellek erişimini (NUMA) **devre dışı bırakmanız** gerekir. Sisteminizde NUMA Düğüm Araya Ekleme (Node Interleaving) olarak geçiyor olabilir ve bu durumda Düğüm Araya Ekleme’yi **etkinleştirmeniz** gerekecektir. Daha fazla bilgi için BIOS belgelerinize bakın.

### Ağ bağdaştırıcıları
Gereksinimler:

-   Bir ağ bağdaştırıcısı

-   İki IP adresi

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
|**HTTPS**|TCP|443|Şirket Ağı veya ATA Gateway|Gelen|IP adresi 2|
|**SMTP** (isteğe bağlı)|TCP|25|SMTP Sunucusu|Giden|IP adresi 2|
|**SMTPS** (isteğe bağlı)|TCP|465|SMTP Sunucusu|Giden|IP adresi 2|
|**Syslog** (isteğe bağlı)|TCP|514|Syslog sunucusu|Giden|IP adresi 2|

### Sertifikalar
ATA Gateway bileşenlerinin CRL dağıtım noktanıza erişimi olduğundan emin olun. ATA Gateway bileşenlerinin İnternet erişimi yoksa, [CRL’yi el ile içeri aktarma yordamını](https://technet.microsoft.com/en-us/library/aa996972%28v=exchg.65%29.aspx) izleyin ve tüm zincir için CRL dağıtım noktalarının tümünü yükleme işlemini gerçekleştirin.

ATA Center’ın yüklemesini kolaylaştırmak için, ATA Center’ın yüklemesi sırasında otomatik olarak imzalanan sertifikalar yükleyebilirsiniz. Dağıtım sonrasında otomatik olarak imzalanan sertifikayı ATA Gateway tarafından kullanılacak bir iç Sertifika Yetkilisi’nin sertifikasıyla değiştirebilirsiniz.

> [!NOTE]
> Otomatik olarak imzalanan sertifikalar yalnızca laboratuvar dağıtımında kullanılmalıdır.

ATA Center’a aşağıdaki hizmetler için sertifika gerekir:

-   Internet Information Services (IIS) – Web sunucu sertifikası

-   ATA Center hizmeti – Sunucu kimlik doğrulama sertifikası

> [!NOTE]
> ATA Konsolu’na başka bilgisayarlardan erişecekseniz, söz konusu bilgisayarların IIS tarafından kullanılan sertifikaya güvendiğinden emin olmaz; aksi takdirde sayfada oturum açmadan önce web sitesinin güvenlik sertifikasında sorun olduğunu bildiren bir uyarı sayfası alırsınız.

## ATA Gateway gereksinimleri
ATA Gateway, Windows Server 2012 R2 çalıştıran sunuculara yüklemeyi destekler.

Windows Update’i çalıştırın ve tüm **Önemli** güncelleştirmelerin yüklenmiş olduğundan emin olun.
ATA Gateway’i yüklemeden önce şu güncelleştirmenin yüklendiğini onaylayın: [KB2919355](https://support.microsoft.com/en-us/kb/2919355/).

Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb2919355]`.

> [!NOTE]
> -   ATA Gateway bir etki alanının veya çalışma grubunun üyesi olan sunuculara yüklenebilir.
> -   ATA Gateway bir etki alanı denetleyicisine yüklenemez.

ATA Gateway ile sanal makineleri kullanma hakkında bilgi için bkz. [Bağlantı noktası yansıtmasını yapılandırma](configure-port-mirroring.md).

> [!NOTE]
> ATA Gateway’i sanal makine olarak çalıştırıyorsanız, olası veritabanı bozulmalarını önlemek için yeni bir denetim noktası oluşturmadan önce sunucuyu kapatın.

ATA Gateway, etki alanı denetleyicilerinden gelen ve giden ağ trafiği miktarına bağlı olarak, birden çok etki alanı denetleyicisinin izlenmesini destekleyebilir.
Daha fazla bilgi için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).

### Güç ayarları
En iyi performans için, ATA Gateway’in **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın..

### Zaman eşitleme
ATA Center sunucusu ve ATA Gateway sunucusunun zamanlarının 5 dakika içinde birbiriyle eşitlenmesi gerekir.

Buna ek olarak, ATA Gateway ve onun bağlandığı etki alanı denetleyicilerinin zamanlarının 5 dakika içinde birbiriyle eşitlenmesi gerekir.

### Ağ bağdaştırıcıları
ATA Gateway için en az bir Yönetim bağdaştırıcısı ve en az bir Yakalama sunucusu gerekir:

-   **Yönetim bağdaştırıcısı** - şirket ağınızdaki iletişim için kullanılır. Bu bağdaştırıcı, aşağıdakilerle yapılandırılmalıdır:

    -   Varsayılan ağ geçidi dahil statik IP adresi

    -   Tercih edilen ve alternatif DNS sunucuları

    -   **Bu bağlantı için DNS son eki**, izlenen her etki alanı için etki alanının DNS adı olmalıdır.

        ![Gelişmiş TCP/IP ayarlarında DNS son ekini yapılandırma](media/ATA-DNS-Suffix.png)

        > [!NOTE]
        > ATA Gateway etki alanının üyesiyse, bu otomatik olarak yapılandırılır.

-   **Yakalama bağdaştırıcısı** - etki alanı denetleyicilerinden gelen ve giden trafiği yakalamak için kullanılır.

    > [!IMPORTANT]
    > -   Etki alanı denetleyicisi ağ trafiğinin hedefi olarak yakalama bağdaştırıcısı için bağlantı noktası yansıtmasını yapılandırın. Ek bilgi için bkz. [Bağlantı noktası yansıtmasını yapılandırma](configure-port-mirroring.md). Normalde, bağlantı noktası yansıtmasını yapılandırmak için ağ veya sanallaştırma ekibiyle çalışmanız gerekir.
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
ATA Center’ın yüklemesini kolaylaştırmak için, ATA Center’ın yüklemesi sırasında otomatik olarak imzalanan sertifikalar yükleyebilirsiniz. Dağıtım sonrasında otomatik olarak imzalanan sertifikayı ATA Gateway tarafından kullanılacak bir iç Sertifika Yetkilisi’nin sertifikasıyla değiştirebilirsiniz.

> [!NOTE]
> Otomatik olarak imzalanan sertifikalar yalnızca laboratuvar dağıtımında kullanılmalıdır.

Yerel Bilgisayar deposunda yer alan ATA Gateway’in Bilgisayar deposunda **Sunucu Kimlik Doğrulaması**’nı destekleyen bir sertifikanın yüklenmesi gerekir. ATA Center tarafından bu sertifikaya güvenilmelidir.

## ATA Konsolu
ATA Konsolu’na tarayıcı yoluyla erişilir ve aşağıdakiler desteklenir:

-   Internet Explorer sürüm 10 ve üstü

-   Google Chrome 40 ve üstü

-   Minimum ekran genişliği çözünürlüğü 1700 piksel

## Ayrıca Bkz.
- [ATA mimarisi](/advanced-threat-analytics/understand-explore/ata-architecture)
- [ATA’yı yükleme](/advanced-threat-analytics/deploy-useinstall-ata)
- [Destek için forumumuzu gözden geçirin!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=Apr16_HO4-->


