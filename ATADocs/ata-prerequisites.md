---
title: Advanced Threat Analytics önkoşulları | Microsoft Docs
description: Ortamınızda başarılı bir ATA dağıtımının gereksinimlerini açıklar
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/9/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: a5f90544-1c70-4aff-8bf3-c59dd7abd687
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 06789ac50d52a9b202eea9fb9fb6ea74aaf7a5f3
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133972"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="ata-prerequisites"></a>ATA Önkoşulları
Bu makalede, ortamınızda başarılı bir ATA dağıtımı için gereksinimler açıklanır.

> [!NOTE]
> Kaynakları ve kapasiteyi planlama hakkında daha fazla bilgi için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).


ATA Center, ATA Gateway ve/veya ATA Lightweight Gateway ATA oluşur. ATA bileşenleri hakkında daha fazla bilgi için bkz. [ATA mimarisi](ata-architecture.md)

ATA Sistemi Active Directory orman sınırının üzerinde çalışır ve Orman İşlevsel Düzeyi (FFL) için Windows 2003 ve üstünü destekler.


[Başlamadan önce](#before-you-start): Bu bölümde, ATA yüklemesine başlamadan önce toplamanız gereken bilgiler ve sahip olmanız gereken hesaplarla ağ varlıkları listelenir.

[ATA Center](#ata-center-requirements): Bu bölümde ATA Center donanım ve yazılım gereksinimlerinin yanı sıra, ATA Center sunucunuzda yapılandırmanız gereken ayarlar listelenir.

[ATA Gateway](#ata-gateway-requirements): Bu bölümde ATA Gateway donanım ve yazılım gereksinimlerinin yanı sıra, ATA Gateway sunucularınızda yapılandırmanız gereken ayarlar listelenir.

[ATA Lightweight Gateway](#ata-lightweight-gateway-requirements): Bu bölümde ATA Lightweight Gateway donanım ve yazılım gereksinimleri listelenmiştir.

[ATA Konsolu](#ata-console): Bu bölümde, ATA Konsolu’nu çalıştırmak için tarayıcı gereksinimleri listelenir.

![ATA mimarisi diyagramı](media/ATA-architecture-topology.jpg)

## <a name="before-you-start"></a>Başlamadan önce
Bu bölümde, hesapları ve ATA yüklemesine başlamadan önce olmalıdır. ağ varlıklarının yanı sıra toplamanız gereken bilgiler listelenir.


-   Kullanıcı hesabı ve parola ile izlenen etki alanlarındaki tüm nesnelere okuma erişimi.

    > [!NOTE]
    > Etki alanınızdaki çeşitli Kurumsal Birimlerde (OU) özel ACL’ler ayarladıysanız, seçili kullanıcının bu OU’lar üzerinde okuma izinleri olmasına dikkat edin.

-   Bir ATA Gateway veya Lightweight Gateway'e Microsoft ileti Çözümleyicisi yüklemeyin. ATA Gateway ve Lightweight Gateway sürücüleriyle ileti Çözümleyicisi sürücüsü çakışıyor. ATA Gateway’de Wireshark çalıştırırsanız Wireshark yakalamasını durdurduktan sonra Microsoft Advanced Threat Analytics Gateway Service’i yeniden başlatmanız gerekir. Aksi durumda, ağ geçidi trafiği yakalama durdurur. Bir ATA Lightweight Gateway'de Wireshark çalıştıran ATA Lightweight Gateway'i etkilemediğini.

-    Önerilen: Kullanıcının silinmiş nesneler kapsayıcısı üzerinde salt okuma izinleri olmalıdır. Bu, Ata'nın etki alanında toplu nesne silme işlemlerini algılamasını sağlar. Silinmiş nesneler kapsayıcısı üzerinde salt okuma izinlerini yapılandırma hakkında daha fazla bilgi için bkz: **Silinmiş nesne kapsayıcısı üzerindeki izinleri değiştirme** konusundaki [görünümü veyadizinnesnesiüzerindekiizinleriayarlayın](https://technet.microsoft.com/library/cc816824%28v=ws.10%29.aspx) makalesi.

-   İsteğe bağlı: Ağ etkinlikleri olmayan bir kullanıcının kullanıcı hesabı. Bu hesap ATA Honeytoken kullanıcısı olarak yapılandırılır. Honeytoken kullanıcısını yapılandırmak için kullanıcı adına değil kullanıcı hesabının SID değerine ihtiyacınız vardır. Daha fazla bilgi için [yapılandırma IP adresi dışlamalarını ve Honeytoken kullanıcısını](install-ata-step7.md).

-   İsteğe bağlı: toplama ve analiz etme ve ağ trafiğini yanı sıra etki alanı denetleyicilerinden ATA Windows olayları 4776, 4732, 4733, 4728, 4729, 4756 ve 4757'yi ATA Pass--Hash, deneme yanılma, gizli Grup değişiklikleri daha da geliştirmek için kullanabilirsiniz ve Token honey. Bu olayları sıem sistemlerinizden alınabileceği gibi veya etki alanı denetleyicinizden Windows Olay iletme'yi ayarlayarak da alınabilir. Toplanan olaylar ATA’ya etki alanı denetleyicisi ağ trafiği yoluyla sağlanmayan ek bilgiler sağlar.


## <a name="ata-center-requirements"></a>ATA Center gereksinimleri
Bu bölümde, ATA Center’ın gereksinimleri listelenir.
### <a name="general"></a>Genel
ATA Center, Windows Server 2012 R2 veya Windows Server 2016 çalıştıran sunuculara yüklemeyi destekler. 

 > [!NOTE]
 > ATA Center, Windows Server core desteklemez.

ATA Center bir etki alanının veya çalışma grubunun üyesi olan sunuculara yüklenebilir.

Windows 2012 R2 çalıştıran ATA Center’ı yüklemeden önce şu güncelleştirmenin yüklendiğini onaylayın: [KB2919355](https://support.microsoft.com/kb/2919355/).

Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb2919355]`.

ATA Center’ın bir sanal makine olarak yüklenmesi desteklenir. 

> [!NOTE] 
> Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.

ATA Center’ı sanal makine olarak çalıştırıyorsanız, olası veritabanı bozulmalarını önlemek için yeni bir denetim noktası oluşturmadan önce sunucuyu kapatın.

### <a name="server-specifications"></a>Sunucu belirtimleri

Fiziksel bir sunucuda çalışırken, ATA veritabanı için BIOS’ta tekdüzen olmayan bellek erişimini (NUMA) **devre dışı bırakmanız** gerekir. Sisteminizde NUMA düğüm araya ekleme, bu durumda düğüm araya Ekleme'yi **etkinleştirme** NUMA devre dışı bırakmak için düğüm araya ekleme. Daha fazla bilgi için BIOS belgelerinize bakın.<br>

En iyi performans için, ATA Center’ın **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.<br>
İzlediğiniz etki alanı denetleyicileri ve etki alanı denetleyicilerinden her birinin yükü sayısı, gerekli sunucu belirtimlerini belirler. Daha fazla bilgi için [ATA kapasite planlaması](ata-capacity-planning.md).


### <a name="time-synchronization"></a>Zaman eşitleme

ATA Center sunucusu, ATA Gateway sunucuları ve etki alanı denetleyicileri için beş dakika içinde birbiriyle eşitlenmesi olması gerekir.


### <a name="network-adapters"></a>Ağ bağdaştırıcıları

Şu olmalıdır:
-   En az bir ağ bağdaştırıcısı (VLAN ortamında fiziksel sunucu kullanılıyorsa, iki ağ bağdaştırıcısı kullanılması önerilir)

-   Bağlantı noktası 443 üzerinde SSL kullanılarak şifrelenir ATA Gateway ile ATA Center arasında iletişimi için bir IP adresi. (ATA Center'a bağlantı noktası 443 üzerinde bulunan tüm IP adresleri için ATA hizmeti bağlar.)

### <a name="ports"></a>Bağlantı noktaları
Aşağıdaki tabloda, ATA Center’ın düzgün çalışması için açılması gereken minimum bağlantı noktaları listelenir.

|Protokol|Aktarım|Bağlantı Noktası|Hedef/Kaynak|Yön|
|------------|-------------|--------|-----------|-------------|
|**SSL** (ATA İletişimi)|TCP|443|ATA Gateway|Gelen|
|**HTTP** (isteğe bağlı)|TCP|80|Şirket Ağı|Gelen|
|**HTTPS**|TCP|443|Şirket Ağı ve ATA Gateway|Gelen|
|**SMTP** (isteğe bağlı)|TCP|25|SMTP Sunucusu|Giden|
|**SMTPS** (isteğe bağlı)|TCP|465|SMTP Sunucusu|Giden|
|**Syslog** (isteğe bağlı)|TCP/UPS/TLS (yapılandırılabilir)|514 (varsayılan)|Syslog sunucusu|Giden|
|**LDAP**|TCP ve UDP|389|Etki alanı denetleyicileri|Giden|
|**LDAPS** (isteğe bağlı)|TCP|636|Etki alanı denetleyicileri|Giden|
|**DNS**|TCP ve UDP|53|DNS sunucuları|Giden|
|**Kerberos** (etki alanına katılmış ise isteğe bağlı)|TCP ve UDP|88|Etki alanı denetleyicileri|Giden|
|**Windows Saati** (isteğe bağlı etki alanına katılmış ise)|UDP|123|Etki alanı denetleyicileri|Giden|

> [!NOTE]
> LDAP, etki alanı denetleyicileri ATA Gateway bileşenleri arasında kullanılacak kimlik bilgilerini test etmek için gereklidir. Test sonra ve ATA Gateway LDAP, normal çözümleme işlemi kapsamında kullanır, bu kimlik bilgileri geçerliliğini sınamak için bir etki alanı denetleyicisinde ATA Center'dan gerçekleştirilir.

### <a name="certificates"></a>Sertifikalar

Yüklemek ve ATA daha hızlı bir şekilde dağıtmak için yükleme sırasında otomatik olarak imzalanan sertifikalar yükleyebilirsiniz. Otomatik olarak imzalanan sertifikalar seçtiyseniz, ilk dağıtımdan sonra ATA Center tarafından kullanılacak bir iç sertifika yetkilisi sertifikalarını otomatik olarak imzalanan sertifikaları değiştirmek için önerilir.


ATA Center ve ATA Gateway bileşenlerinin CRL dağıtım noktanıza erişimi olduğundan emin olun. Internet erişimi yoksa izleyin [el ile bir CRL içeri aktarma yordamını](https://technet.microsoft.com/library/aa996972%28v=exchg.65%29.aspx), tüm CRL dağıtım yükleme işlemini gerçekleştirin ve tüm zincir için işaret eder.

Sertifika olması gerekir:
-   Özel anahtar
-   Şifreleme hizmeti sağlayıcısı (CSP) veya anahtar depolama sağlayıcısı (KSP) sağlayıcısı türü
-   Ortak anahtar uzunluğu 2048 bit
-   Bir değer KeyEncipherment ve ServerAuthentication özelliğinin kullanımı bayrakları
-   KeySpec öğesinin (KeyNumber) "KeyExchange" değerini (en\_KEYEXCHANGE). Dikkat "Signature" değeri (en\_imzası) desteklenmiyor. 

Örneğin, standart kullanabileceğiniz **Web sunucusu** veya **bilgisayar** şablonları.

> [!WARNING]
> Mevcut bir sertifikayı yenileme işlemi desteklenmiyor. Bir sertifikayı yenilemek için tek yolu, yeni bir sertifika oluşturmak ve yeni sertifikayı kullanmak için Ata'yı yapılandırma ' dir.


> [!NOTE]
> - Aksi takdirde kullanacaksanız ATA Konsolu'na başka bilgisayarlardan erişecekseniz, söz konusu bilgisayarların ATA Center tarafından kullanılan sertifikaya güvendiğinden emin olduğunu Web sitesinin güvenlik sertifikasında problem oturum açma sayfasında almadan önce bir uyarı sayfası alın.
> - ATA sürüm 1.8 ile başlayarak, ATA Gateway ve Lightweight Gateway bileşenlerinin kendi sertifikalarını yönetme ve bunları yönetmek için yönetici etkileşimi gerekir.

## <a name="ata-gateway-requirements"></a>ATA Gateway gereksinimleri
Bu bölümde, ATA Gateway’in gereksinimleri listelenir.
### <a name="general"></a>Genel
ATA Gateway, Windows Server 2012 R2 veya Windows Server 2016'ın (Sunucu Çekirdeği dahil) çalıştıran sunuculara yüklemeyi destekler.
ATA Gateway bir etki alanının veya çalışma grubunun üyesi olan sunuculara yüklenebilir.
ATA Gateway, Etki Alanı İşlev Düzeyi Windows 2003 ve üstü olan Etki Alanı Denetleyicilerini izlemek için kullanılabilir.

Windows 2012 R2 çalıştıran ATA Gateway’i yüklemeden önce şu güncelleştirmenin yüklendiğini onaylayın: [KB2919355](https://support.microsoft.com/kb/2919355/).

Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb2919355]`.


ATA Gateway ile sanal makineleri kullanma hakkında bilgi için bkz. [Bağlantı noktası yansıtmasını yapılandırma](configure-port-mirroring.md)

> [!NOTE]
> En az 5 GB alan gereklidir ve 10 GB önerilir. Bu ATA günlükleri, ATA ikili için gereken alan da dahildir ve [performans günlükleri](troubleshooting-ata-using-perf-counters.md).

### <a name="server-specifications"></a>Sunucu belirtimleri
En iyi performans için, ATA Gateway’in **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.<br>
ATA Gateway, etki alanı denetleyicilerinden gelen ve giden ağ trafiği miktarına bağlı olarak, birden çok etki alanı denetleyicisinin izlenmesini destekleyebilir.

> [!NOTE] 
> Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.

ATA Gateway donanım gereksinimleri hakkında daha fazla bilgi için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).

### <a name="time-synchronization"></a>Zaman eşitleme
ATA Center sunucusu, ATA Gateway sunucuları ve etki alanı denetleyicileri için beş dakika içinde birbiriyle eşitlenmesi olması gerekir.

### <a name="network-adapters"></a>Ağ bağdaştırıcıları
ATA Gateway için en az bir Yönetim bağdaştırıcısı ve en az bir Yakalama bağdaştırıcısı gerekir:

-   **Yönetim bağdaştırıcısı** - şirket ağınızdaki iletişim için kullanılır. Bu bağdaştırıcı, aşağıdaki ayarlarla yapılandırılması gerekir:

    -   Varsayılan ağ geçidi dahil statik IP adresi

    -   Tercih edilen ve alternatif DNS sunucuları

    -   **Bu bağlantı için DNS son eki**, izlenen her etki alanı için etki alanının DNS adı olmalıdır.

        ![Gelişmiş TCP/IP ayarlarında DNS son ekini yapılandırma](media/ATA-DNS-Suffix.png)

        > [!NOTE]
        > ATA Gateway etki alanının üyesiyse, bu özellik otomatik olarak yapılandırılabilir.

-   **Yakalama bağdaştırıcısı** - etki alanı denetleyicilerinden gelen ve giden trafiği yakalamak için kullanılır.

    > [!IMPORTANT]
    > -   Etki alanı denetleyicisi ağ trafiğinin hedefi olarak yakalama bağdaştırıcısı için bağlantı noktası yansıtmasını yapılandırın. Daha fazla bilgi için [bağlantı noktası yansıtmayı yapılandırma](configure-port-mirroring.md). Genellikle, bağlantı noktası yansıtmasını yapılandırmak için ağ veya sanallaştırma ekibiyle çalışmanız gerekir.
    > -   Varsayılan ağ geçidi ve DNS sunucu adresleri olmadan ortamınız için statik yönlendirilemeyen bir IP adresi yapılandırın. Örneğin, 1.1.1.1/32. Bu yakalama ağ bağdaştırıcısının en yüksek miktarda trafiği yakalayabilmesini ve gerekli ağ trafiğini gönderip için yönetim ağ bağdaştırıcısı kullanıldığını sağlar.

### <a name="ports"></a>Bağlantı noktaları
Aşağıdaki tabloda, ATA Gateway için yönetim bağdaştırıcısında yapılandırılması gereken minimum bağlantı noktaları listelenir.

|Protokol|Aktarım|Bağlantı Noktası|Hedef/Kaynak|Yön|
|------------|-------------|--------|-----------|-------------|
|LDAP|TCP ve UDP|389|Etki alanı denetleyicileri|Giden|
|Güvenli LDAP (LDAPS)|TCP|636|Etki alanı denetleyicileri|Giden|
|LDAP - Genel Katalog|TCP|3268|Etki alanı denetleyicileri|Giden|
|LDAPS - Genel Katalog|TCP|3269|Etki alanı denetleyicileri|Giden|
|Kerberos|TCP ve UDP|88|Etki alanı denetleyicileri|Giden|
|Netlogon (SMB, CIFS, SAM-R)|TCP ve UDP|445|Ağdaki tüm cihazlar|Giden|
|Windows Saati|UDP|123|Etki alanı denetleyicileri|Giden|
|DNS|TCP ve UDP|53|DNS Sunucuları|Giden|
|RPC üzerinden NTLM|TCP|135|Ağdaki tüm cihazlar|Her İkisi|
|NetBIOS|UDP|137|Ağdaki tüm cihazlar|Her İkisi|
|SSL|TCP|443|ATA Center|Giden|
|Syslog (isteğe bağlı)|UDP|514|SIEM Sunucusu|Gelen|


> [!NOTE]
> ATA Gateway tarafından yapılan çözümleme işlemi kapsamında, ATA Gateway bileşenlerinden aşağıdaki bağlantı noktaları ağdaki cihazlarda gelen trafik için açılmalıdır.
>
> -   RPC üzerinden NTLM (TCP Bağlantı Noktası 135)
> -   NetBIOS (UDP bağlantı noktası 137)
> - Dizin hizmeti kullanıcı hesabını kullanarak, ATA Gateway uç noktaları oluşturmak için SAM-R (ağ oturumu açma) kullanarak Yerel yöneticilerin kuruluşunuzdaki sorgular [yanal hareket yolu graf](use-case-lateral-movement-path.md). Daha fazla bilgi için [SAM-R yapılandırmak gerekli izinler](install-ata-step9-samr.md).
> - Aşağıdaki bağlantı noktalarının açık cihazlarda gelen trafik ağ ATA gateway'den gerekir:
>   -   Çözümleme amacıyla (TCP bağlantı noktası 135) RPC üzerinden NTLM
>   -   Çözümleme amacıyla NetBIOS (UDP bağlantı noktası 137)

## <a name="ata-lightweight-gateway-requirements"></a>ATA Lightweight Gateway gereksinimleri
Bu bölümde, ATA Lightweight Gateway’in gereksinimleri listelenir.
### <a name="general"></a>Genel
ATA Lightweight Gateway; Windows Server 2008 R2 SP1 (Server Core içermez), Windows Server 2012, Windows Server 2012 R2 veya Windows Server 2016 (Core dahil ancak Nano hariç) çalıştıran bir etki alanı denetleyicisine yüklemeyi destekler.

Etki alanı denetleyicisi salt okunur etki alanı denetleyicisi (RODC) olabilir.

Windows Server 2012 R2 çalıştıran bir etki alanı denetleyicisine ATA Lightweight Gateway yüklemeden önce şu güncelleştirmenin yüklendiğini onaylayın: [KB2919355](https://support.microsoft.com/kb/2919355/).

Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb2919355]`

Yükleme, Windows Server 2012 R2 Sunucu Çekirdeği içinse şu güncelleştirmenin de yüklü olması gerekir: [KB3000850](https://support.microsoft.com/help/3000850/november-2014-update-rollup-for-windows-rt-8.1%2c-windows-8.1%2c-and-windows-server-2012-r2).

 Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb3000850]`


Yükleme sırasında .Net Framework 4.6.1 yüklenir ve etki alanı denetleyicisinin yeniden başlatılmasına neden olabilir.


> [!NOTE]
> En az 5 GB alan gereklidir ve 10 GB önerilir. Bu ATA günlükleri, ATA ikili için gereken alan da dahildir ve [performans günlükleri](troubleshooting-ata-using-perf-counters.md).

### <a name="server-specifications"></a>Sunucu belirtimleri

ATA Lightweight Gateway, etki alanı denetleyicisinde en az 2 çekirdek ve 6 GB RAM kurulu olmasını gerektirir.
En iyi performans için, ATA Lightweight Gateway’in **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.
ATA Lightweight Gateway, etki alanı denetleyicilerinden gelen ve giden ağ trafiğinin miktarına ve bu etki alanında kurulu kaynakların miktarına bağlı olarak çeşitli yük ve büyüklükte etki alanı denetleyicilerinde dağıtılabilir.

> [!NOTE] 
> Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.

ATA Lightweight Gateway donanım gereksinimleri hakkında daha fazla bilgi için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).

### <a name="time-synchronization"></a>Zaman eşitleme

ATA Center sunucusu, ATA Lightweight Gateway sunucuları ve etki alanı denetleyicileri için beş dakika içinde birbiriyle eşitlenmesi olması gerekir.

### <a name="network-adapters"></a>Ağ bağdaştırıcıları

ATA Lightweight Gateway etki alanı denetleyicisinin ağ bağdaştırıcılarının hepsindeki yerel trafiği izler. <br>
Dağıtımdan sonra, hangi ağ bağdaştırıcılarının izlendiğini değiştirmek isterseniz ATA Konsolu’nu kullanabilirsiniz.

> [!NOTE]
> Lightweight Gateway, etki alanı denetleyicileri Broadcom ağ bağdaştırıcısı ekibi oluşturma ile Windows 2008 R2 çalıştıran etkin üzerinde desteklenmiyor.

### <a name="ports"></a>Bağlantı noktaları
Aşağıdaki tabloda, ATA Lightweight Gateway için gereken minimum bağlantı noktaları listelenir.

|Protokol|Aktarım|Bağlantı Noktası|Hedef/Kaynak|Yön|
|------------|-------------|--------|-----------|-------------|
|DNS|TCP ve UDP|53|DNS Sunucuları|Giden|
|RPC üzerinden NTLM|TCP|135|Ağdaki tüm cihazlar|Her İkisi|
|NetBIOS|UDP|137|Ağdaki tüm cihazlar|Her İkisi|
|SSL|TCP|443|ATA Center|Giden|
|Syslog (isteğe bağlı)|UDP|514|SIEM Sunucusu|Gelen|
|Netlogon (SMB, CIFS, SAM-R)|TCP ve UDP|445|Ağdaki tüm cihazlar|Giden|

> [!NOTE]
> ATA Lightweight Gateway tarafından yapılan çözümleme işlemi kapsamında, ATA Lightweight Gateway bileşenlerinden aşağıdaki bağlantı noktaları ağdaki cihazlarda gelen trafik için açılmalıdır.
>
> -   RPC üzerinden NTLM
> -   NetBIOS
> - Dizin hizmeti kullanıcı hesabını kullanarak, ATA Lightweight Gateway uç noktaları oluşturmak için SAM-R (ağ oturumu açma) kullanarak Yerel yöneticilerin kuruluşunuzdaki sorgular [yanal hareket yolu graf](use-case-lateral-movement-path.md). Daha fazla bilgi için [SAM-R yapılandırmak gerekli izinler](install-ata-step9-samr.md).
> - Aşağıdaki bağlantı noktalarının açık cihazlarda gelen trafik ağ ATA gateway'den gerekir:
>   -   Çözümleme amacıyla (TCP bağlantı noktası 135) RPC üzerinden NTLM
>   -   Çözümleme amacıyla NetBIOS (UDP bağlantı noktası 137)

## <a name="ata-console"></a>ATA Konsolu
ATA Konsolu tarayıcılar ve ayarları destekleyen bir tarayıcı erişilebilir:

-   Internet Explorer sürüm 10 ve üstü

-   Microsoft Edge

-   Google Chrome 40 ve üstü

-   Minimum ekran genişliği çözünürlüğü 1700 piksel

## <a name="related-videos"></a>İlgili videolar
- [ATA Gateway türü sağ seçme](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA boyutlandırma aracı](http://aka.ms/atasizingtool)
- [ATA mimarisi](ata-architecture.md)
- [ATA’yı yükleme](install-ata-step1.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)


