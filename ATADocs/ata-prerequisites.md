---
title: "Advanced Threat Analytics önkoşulları | Microsoft Docs"
description: "Ortamınızda başarılı bir ATA dağıtımının gereksinimlerini açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/2/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: a5f90544-1c70-4aff-8bf3-c59dd7abd687
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: b810d066c59ea4663157027894eb7e2a39f7ff14
ms.sourcegitcommit: 53b56220fa761671442da273364bdb3d21269c9e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/05/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# ATA Önkoşulları
<a id="ata-prerequisites" class="xliff"></a>
Bu makalede, ortamınızda başarılı bir ATA dağıtımı için gereksinimler açıklanır.

>[!NOTE]
> Kaynakları ve kapasiteyi planlama hakkında daha fazla bilgi için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).


ATA yazılımı ATA Center, ATA Gateway ve/veya ATA Lightweight Gateway’den oluşur. ATA bileşenleri hakkında daha fazla bilgi için bkz. [ATA mimarisi](ata-architecture.md)

ATA Sistemi Active Directory orman sınırının üzerinde çalışır ve Orman İşlevsel Düzeyi (FFL) için Windows 2003 ve üstünü destekler.


[Başlamadan önce](#before-you-start): Bu bölümde, ATA yüklemesine başlamadan önce toplamanız gereken bilgiler ve sahip olmanız gereken hesaplarla ağ varlıkları listelenir.

[ATA Center](#ata-center-requirements): Bu bölümde ATA Center donanım ve yazılım gereksinimlerinin yanı sıra, ATA Center sunucunuzda yapılandırmanız gereken ayarlar listelenir.

[ATA Gateway](#ata-gateway-requirements): Bu bölümde ATA Gateway donanım ve yazılım gereksinimlerinin yanı sıra, ATA Gateway sunucularınızda yapılandırmanız gereken ayarlar listelenir.

[ATA Lightweight Gateway](#ata-lightweight-gateway-requirements): Bu bölümde ATA Lightweight Gateway donanım ve yazılım gereksinimleri listelenmiştir.

[ATA Konsolu](#ata-console): Bu bölümde, ATA Konsolu’nu çalıştırmak için tarayıcı gereksinimleri listelenir.

![ATA mimarisi diyagramı](media/ATA-architecture-topology.jpg)

## Başlamadan önce
<a id="before-you-start" class="xliff"></a>
Bu bölümde, ATA yüklemesine başlamadan önce toplamanız gereken bilgiler ve sahip olmanız gereken hesaplarla ağ varlıkları listelenir.


-   İzlenecek etki alanlarındaki tüm nesnelere okuma erişimi olan kullanıcı hesabı ve parolası.

    > [!NOTE]
    > Etki alanınızdaki çeşitli Kurumsal Birimlerde (OU) özel ACL’ler ayarladıysanız, seçili kullanıcının bu OU’lar üzerinde okuma izinleri olmasına dikkat edin.

-   Bir ATA Gateway veya Lightweight Gateway’e Microsoft İleti Çözümleyicisi yüklemeyin. İleti Çözümleyicisi sürücüsü, ATA Gateway ve Lightweight Gateway sürücüleriyle çakışır. ATA Gateway’de Wireshark çalıştırırsanız Wireshark yakalamasını durdurduktan sonra Microsoft Advanced Threat Analytics Gateway Service’i yeniden başlatmanız gerekir. Aksi halde Gateway artık hiç trafik yakalamayacaktır. ATA Lightweight Gateway’de Wireshark çalıştırmanın, ATA Lightweight Gateway’i etkilemediğini unutmayın.

-    Önerilir: Kullanıcı, Silinmiş Nesneler kapsayıcısı üzerinde salt okuma izinlerine sahip olmalıdır. Bu, ATA’nın etki alanında toplu nesne silme işlemlerini algılamasını sağlar. Silinmiş Nesneler kapsayıcısı üzerinde salt okuma izinlerini yapılandırma hakkında bilgi için, [Dizin Nesnesi Üzerindeki İzinleri Görüntüleme veya Ayarlama](https://technet.microsoft.com/library/cc816824%28v=ws.10%29.aspx) konusunun **Silinmiş nesne kapsayıcısı üzerindeki izinleri değiştirme** bölümüne bakın.

-   İsteğe bağlı: Ağ etkinlikleri olmayan bir kullanıcının kullanıcı hesabı. Bu hesap ATA Honeytoken kullanıcısı olarak yapılandırılır. Honeytoken kullanıcısını yapılandırmak için, kullanıcı adına değil kullanıcı hesabının SID değerine ihtiyacınız vardır. Daha fazla bilgi için [ATA Algılama Ayarlarıyla Çalışma](https://docs.microsoft.com/en-us/advanced-threat-analytics/deploy-use/working-with-detection-settings) konusuna bakın.

-   İsteğe bağlı: Etki alanı denetleyicilerinden gelen ve denetleyicilere giden ağ trafiğini toplama ve çözümlemeye ek olarak ATA; ATA Pass-the-Hash, Deneme Yanılma, Gizli grup değişikliği ve Honey Token tehditlerini algılamayı daha da güçlendirmek için 4776, 4732, 4733, 4728, 4729, 4756 ve 4757 numaralı Windows olaylarını kullanabilir. Bunlar, SIEM’inizden alınabileceği gibi etki alanı denetleyicinizden Windows Olay İletme’yi ayarlanarak da alınabilir. Toplanan olaylar ATA’ya etki alanı denetleyicisi ağ trafiği yoluyla sağlanmayan ek bilgiler sağlar.


## ATA Center gereksinimleri
<a id="ata-center-requirements" class="xliff"></a>
Bu bölümde, ATA Center’ın gereksinimleri listelenir.
### Genel
<a id="general" class="xliff"></a>
ATA Center, Windows Server 2012 R2 veya Windows Server 2016 çalıştıran sunuculara yüklemeyi destekler. ATA Center bir etki alanının veya çalışma grubunun üyesi olan sunuculara yüklenebilir.

Windows 2012 R2 çalıştıran ATA Center’ı yüklemeden önce şu güncelleştirmenin yüklendiğini onaylayın: [KB2919355](https://support.microsoft.com/kb/2919355/).

Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb2919355]`.

ATA Center’ın bir sanal makine olarak yüklenmesi desteklenir. 

>[!NOTE] 
> Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.

ATA Center’ı sanal makine olarak çalıştırıyorsanız, olası veritabanı bozulmalarını önlemek için yeni bir denetim noktası oluşturmadan önce sunucuyu kapatın.
### Sunucu belirtimleri
<a id="server-specifications" class="xliff"></a>
Fiziksel bir sunucuda çalışırken, ATA veritabanı için BIOS’ta tekdüzen olmayan bellek erişimini (NUMA) **devre dışı bırakmanız** gerekir. Sisteminizde NUMA Düğüm Araya Ekleme (Node Interleaving) olarak geçiyor olabilir ve bu durumda NUMA’yı devre dışı bırakmak için Düğüm Araya Ekleme’yi **etkinleştirmeniz** gerekecektir. Daha fazla bilgi için BIOS belgelerinize bakın. ATA Center bir sanal sunucuda çalışırken bunun geçerli olmadığını unutmayın.<br>
En iyi performans için, ATA Center’ın **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.<br>
İzlediğiniz etki alanı denetleyicilerinin sayısı ve etki alanı denetleyicilerinden her birinin yükü sunucu belirtimlerini belirler; daha ayrıntılı bilgi için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).


### Zaman eşitleme
<a id="time-synchronization" class="xliff"></a>
ATA Center sunucusu, ATA Gateway sunucuları ve etki alanı denetleyicilerinin zamanlarının 5 dakika içinde birbiriyle eşitlenmesi gerekir.


### Ağ bağdaştırıcıları
<a id="network-adapters" class="xliff"></a>
Aşağıdakilere sahip olmanız gerekir:
-   En az bir ağ bağdaştırıcısı (VLAN ortamında fiziksel sunucu kullanılıyorsa, iki ağ bağdaştırıcısı kullanılması önerilir)

-   İki IP adresi (önerilir ancak gerekli değildir)

ATA Center ile ATA Gateway arasındaki iletişim, bağlantı noktası 443 üzerinde SSL kullanılarak şifrelenir. Ayrıca, ATA Konsolu da bağlantı noktası 443 üzerinde SSL kullanır. **İki IP adresi** kullanılması önerilir. ATA Center hizmeti bağlantı noktası 443’ü ilk IP adresine bağlar ve ATA Konsolu da bağlantı noktası 443’ü ikinci IP adresine bağlar.

> [!NOTE]
> İki farklı bağlantı noktasıyla tek IP adresi kullanılabilir, ama iki IP adresi kullanılması önerilir.

### Bağlantı noktaları
<a id="ports" class="xliff"></a>
Aşağıdaki tabloda, ATA Center’ın düzgün çalışması için açılması gereken minimum bağlantı noktaları listelenir.

|Protokol|Aktarım|Bağlantı Noktası|Hedef/Kaynak|Yön|
|------------|-------------|--------|-----------|-------------|
|**SSL** (ATA İletişimi)|TCP|443 veya yapılandırılabilir|ATA Gateway|Gelen|
|**HTTP** (isteğe bağlı)|TCP|80|Şirket Ağı|Gelen|
|**HTTPS**|TCP|443|Şirket Ağı ve ATA Gateway|Gelen|
|**SMTP** (isteğe bağlı)|TCP|25|SMTP Sunucusu|Giden|
|**SMTPS** (isteğe bağlı)|TCP|465|SMTP Sunucusu|Giden|
|**Syslog** (isteğe bağlı)|TCP|514|Syslog sunucusu|Giden|
|**LDAP**|TCP ve UDP|389|Etki alanı denetleyicileri|Giden|
|**LDAPS** (isteğe bağlı)|TCP|636|Etki alanı denetleyicileri|Giden|
|**DNS**|TCP ve UDP|53|DNS sunucuları|Giden|
|**Kerberos** (etki alanına katılmış ise isteğe bağlı)|TCP ve UDP|88|Etki alanı denetleyicileri|Giden|
|**Netlogon** (etki alanına katılmış ise isteğe bağlı)|TCP ve UDP|445|Etki alanı denetleyicileri|Giden|
|**Windows Saati** (etki alanına katılmış ise isteğe bağlı)|UDP|123|Etki alanı denetleyicileri|Giden|

### Sertifikalar
<a id="certificates" class="xliff"></a>
ATA Center’ın CRL dağıtım noktanıza erişimi olduğundan emin olun. ATA Gateway bileşenlerinin İnternet erişimi yoksa, [CRL’yi el ile içeri aktarma yordamını](https://technet.microsoft.com/library/aa996972%28v=exchg.65%29.aspx) izleyin ve tüm zincir için CRL dağıtım noktalarının tümünü yükleme işlemini gerçekleştirin.

ATA’nın yüklenmesini kolaylaştırmak için, işlem sırasında otomatik olarak imzalanan sertifikalar yükleyebilirsiniz. Dağıtım sonrasında otomatik olarak imzalanan sertifikayı ATA Gateway tarafından kullanılacak bir iç Sertifika Yetkilisi’nin sertifikasıyla değiştirebilirsiniz.<br>
> [!NOTE]
> Sertifikanın Sağlayıcı Türü, Şifreleme Hizmeti Sağlayıcısı (CSP) veya Anahtar Depolama Alanı Sağlayıcısı (KSP) olmalıdır.


> Otomatik sertifika yenilemenin kullanılması desteklenmez.


> [!NOTE]
> ATA Konsolu’na başka bilgisayarlardan erişecekseniz, söz konusu bilgisayarların ATA Center tarafından kullanılan sertifikaya güvendiğinden emin olun; aksi takdirde sayfada oturum açmadan önce Web sitesinin güvenlik sertifikasında sorun olduğunu bildiren bir uyarı sayfası alırsınız.

## ATA Gateway gereksinimleri
<a id="ata-gateway-requirements" class="xliff"></a>
Bu bölümde, ATA Gateway’in gereksinimleri listelenir.
### Genel
<a id="general" class="xliff"></a>
ATA Gateway, Windows Server 2012 R2 veya Windows Server 2016 çalıştıran sunuculara yüklemeyi destekler (Sunucu çekirdeği dahil).
ATA Gateway bir etki alanının veya çalışma grubunun üyesi olan sunuculara yüklenebilir.
ATA Gateway, Etki Alanı İşlev Düzeyi Windows 2003 ve üstü olan Etki Alanı Denetleyicilerini izlemek için kullanılabilir.

Windows 2012 R2 çalıştıran ATA Gateway’i yüklemeden önce şu güncelleştirmenin yüklendiğini onaylayın: [KB2919355](https://support.microsoft.com/kb/2919355/).

Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb2919355]`.


ATA Gateway ile sanal makineleri kullanma hakkında bilgi için bkz. [Bağlantı noktası yansıtmasını yapılandırma](configure-port-mirroring.md)

> [!NOTE]
> En az 5 GB alan gereklidir ve 10 GB önerilir. Buna, ATA ikili dosyaları, [ATA günlükleri](troubleshooting-ata-using-logs.md) ve [performans günlükleri](troubleshooting-ata-using-perf-counters.md) için gereken alan da dahildir.

### Sunucu belirtimleri
<a id="server-specifications" class="xliff"></a>
En iyi performans için, ATA Gateway’in **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.<br>
ATA Gateway, etki alanı denetleyicilerinden gelen ve giden ağ trafiği miktarına bağlı olarak, birden çok etki alanı denetleyicisinin izlenmesini destekleyebilir.

>[!NOTE] 
> Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.

ATA Gateway donanım gereksinimleri hakkında daha fazla bilgi için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).

### Zaman eşitleme
<a id="time-synchronization" class="xliff"></a>
ATA Center sunucusu, ATA Gateway sunucuları ve etki alanı denetleyicilerinin zamanlarının 5 dakika içinde birbiriyle eşitlenmesi gerekir.

### Ağ bağdaştırıcıları
<a id="network-adapters" class="xliff"></a>
ATA Gateway için en az bir Yönetim bağdaştırıcısı ve en az bir Yakalama bağdaştırıcısı gerekir:

-   **Yönetim bağdaştırıcısı** - şirket ağınızdaki iletişim için kullanılır. Bu bağdaştırıcı, aşağıdakilerle yapılandırılmalıdır:

    -   Varsayılan ağ geçidi dahil statik IP adresi

    -   Tercih edilen ve alternatif DNS sunucuları

    -   **Bu bağlantı için DNS son eki**, izlenen her etki alanı için etki alanının DNS adı olmalıdır.

        ![Gelişmiş TCP/IP ayarlarında DNS son ekini yapılandırma](media/ATA-DNS-Suffix.png)

        > [!NOTE]
        > ATA Gateway etki alanının üyesiyse, bu özellik otomatik olarak yapılandırılabilir.

-   **Yakalama bağdaştırıcısı** - etki alanı denetleyicilerinden gelen ve giden trafiği yakalamak için kullanılır.

    > [!IMPORTANT]
    > -   Etki alanı denetleyicisi ağ trafiğinin hedefi olarak yakalama bağdaştırıcısı için bağlantı noktası yansıtmasını yapılandırın. Daha fazla bilgi için bkz. [Bağlantı noktası yansıtmasını yapılandırma](configure-port-mirroring.md). Normalde, bağlantı noktası yansıtmasını yapılandırmak için ağ veya sanallaştırma ekibiyle çalışmanız gerekir.
    > -   Varsayılan ağ geçidi ve DNS sunucu adresleri olmadan ortamınız için statik yönlendirilemeyen bir IP adresi yapılandırın. Örneğin, 1.1.1.1/32. Bu, yakalama ağ bağdaştırıcısının en yüksek miktarda trafiği yakalayabilmesini ve gerekli ağ trafiğini göndermek ve almak için yönetim ağ bağdaştırıcısının kullanılmasını güvence altına alır.

### Bağlantı noktaları
<a id="ports" class="xliff"></a>
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
|SSL|TCP|443 veya Center Hizmeti için yapılandırılmış olan|ATA Center:<br /><br />-   Center Hizmeti IP Adresi<br />-   Konsol IP Adresi|Giden|
|Syslog (isteğe bağlı)|UDP|514|SIEM Sunucusu|Gelen|

> [!NOTE]
> ATA Gateway tarafından yapılan çözümleme işlemi kapsamında, ATA Gateway bileşenlerinden aşağıdaki bağlantı noktaları ağdaki cihazlarda gelen trafik için açılmalıdır.
>
> -   RPC üzerinden NTLM (TCP Bağlantı Noktası 135)
> -   NetBIOS (UDP bağlantı noktası 137)

## ATA Lightweight Gateway gereksinimleri
<a id="ata-lightweight-gateway-requirements" class="xliff"></a>
Bu bölümde, ATA Lightweight Gateway’in gereksinimleri listelenir.
### Genel
<a id="general" class="xliff"></a>
ATA Lightweight Gateway; Windows Server 2008 R2 SP1 (Server Core içermez), Windows Server 2012, Windows Server 2012 R2 veya Windows Server 2016 (Core dahil ancak Nano hariç) çalıştıran bir etki alanı denetleyicisine yüklemeyi destekler.

Etki alanı denetleyicisi salt okunur bir etki alanı denetleyicisi (RODC) olabilir.

Windows Server 2012 R2 çalıştıran bir etki alanı denetleyicisine ATA Lightweight Gateway yüklemeden önce şu güncelleştirmenin yüklendiğini onaylayın: [KB2919355](https://support.microsoft.com/kb/2919355/).

Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb2919355]`

Yükleme, Windows Server 2012 R2 Sunucu Çekirdeği içinse şu güncelleştirmenin de yüklü olması gerekir: [KB3000850](https://support.microsoft.com/help/3000850/november-2014-update-rollup-for-windows-rt-8.1%2c-windows-8.1%2c-and-windows-server-2012-r2).

 Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb3000850]`


Yükleme sırasında .Net Framework 4.6.1 yüklenir ve etki alanı denetleyicisinin yeniden başlatılmasına neden olabilir.


> [!NOTE]
> En az 5 GB alan gereklidir ve 10 GB önerilir. Buna, ATA ikili dosyaları, [ATA günlükleri](troubleshooting-ata-using-logs.md) ve [performans günlükleri](troubleshooting-ata-using-perf-counters.md) için gereken alan da dahildir.

### Sunucu belirtimleri
<a id="server-specifications" class="xliff"></a>

ATA Lightweight Gateway, etki alanı denetleyicisinde en az 2 çekirdek ve 6 GB RAM kurulu olmasını gerektirir.
En iyi performans için, ATA Lightweight Gateway’in **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.
ATA Lightweight Gateway, etki alanı denetleyicilerinden gelen ve giden ağ trafiğinin miktarına ve bu etki alanında kurulu kaynakların miktarına bağlı olarak çeşitli yük ve büyüklükte etki alanı denetleyicilerinde dağıtılabilir.

>[!NOTE] 
> Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.

ATA Lightweight Gateway donanım gereksinimleri hakkında daha fazla bilgi için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).

### Zaman eşitleme
<a id="time-synchronization" class="xliff"></a>
ATA Center sunucusu, ATA Lightweight Gateway sunucuları ve etki alanı denetleyicilerinin zamanlarının 5 dakika içinde birbiriyle eşitlenmesi gerekir.
### Ağ bağdaştırıcıları
<a id="network-adapters" class="xliff"></a>
ATA Lightweight Gateway etki alanı denetleyicisinin ağ bağdaştırıcılarının hepsindeki yerel trafiği izler. <br>
Dağıtımdan sonra, hangi ağ bağdaştırıcılarının izlendiğini değiştirmek isterseniz ATA Konsolu’nu kullanabilirsiniz.

### Bağlantı noktaları
<a id="ports" class="xliff"></a>
Aşağıdaki tabloda, ATA Lightweight Gateway için gereken minimum bağlantı noktaları listelenir.

|Protokol|Aktarım|Bağlantı Noktası|Hedef/Kaynak|Yön|
|------------|-------------|--------|-----------|-------------|
|DNS|TCP ve UDP|53|DNS Sunucuları|Giden|
|RPC üzerinden NTLM|TCP|135|Ağdaki tüm cihazlar|Giden|
|NetBIOS|UDP|137|Ağdaki tüm cihazlar|Giden|
|SSL|TCP|443 veya Center Hizmeti için yapılandırılmış olan|ATA Center:<br /><br />-   Center Hizmeti IP Adresi<br />-   Konsol IP Adresi|Giden|
|Syslog (isteğe bağlı)|UDP|514|SIEM Sunucusu|Gelen|

> [!NOTE]
> ATA Lightweight Gateway tarafından yapılan çözümleme işlemi kapsamında, ATA Lightweight Gateway bileşenlerinden aşağıdaki bağlantı noktaları ağdaki cihazlarda gelen trafik için açılmalıdır.
>
> -   RPC üzerinden NTLM
> -   NetBIOS

## ATA Konsolu
<a id="ata-console" class="xliff"></a>
ATA Konsolu’na tarayıcı yoluyla erişilir ve aşağıdakiler desteklenir:

-   Internet Explorer sürüm 10 ve üstü

-   Microsoft Edge

-   Google Chrome 40 ve üstü

-   Minimum ekran genişliği çözünürlüğü 1700 piksel

## Ayrıca bkz.
<a id="see-also" class="xliff"></a>

- [ATA mimarisi](ata-architecture.md)
- [ATA’yı yükleme](install-ata-step1.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)


