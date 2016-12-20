---
title: "ATA Önkoşulları | Microsoft Docs"
description: "Ortamınızda başarılı bir ATA dağıtımının gereksinimlerini açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/14/2016
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: a5f90544-1c70-4aff-8bf3-c59dd7abd687
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 67b430fbed97bd08e5f538043c783e70ed2ab956
ms.openlocfilehash: 60ec036a8c22fb34c673653a6378437ab14f9853


---

*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*



# <a name="ata-prerequisites"></a>ATA Önkoşulları
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

## <a name="before-you-start"></a>Başlamadan önce
Bu bölümde, ATA yüklemesine başlamadan önce toplamanız gereken bilgiler ve sahip olmanız gereken hesaplarla ağ varlıkları listelenir.


-   İzlenecek etki alanlarındaki tüm nesnelere okuma erişimi olan kullanıcı hesabı ve parolası.

    > [!NOTE]
    > Etki alanınızdaki çeşitli Kurumsal Birimlerde (OU) özel ACL’ler ayarladıysanız, seçili kullanıcının bu OU’lar üzerinde okuma izinleri olmasına dikkat edin.

-   İleti Çözümleyicisi ve WireShark’ın ATA Gateway’e yüklenmediğinden emin olun.
-    Önerilir: Kullanıcı, Silinmiş Nesneler kapsayıcısı üzerinde salt okuma izinlerine sahip olmalıdır. Bu, ATA’nın etki alanında toplu nesne silme işlemlerini algılamasını sağlar. Silinmiş Nesneler kapsayıcısı üzerinde salt okuma izinlerini yapılandırma hakkında bilgi için, [Dizin Nesnesi Üzerindeki İzinleri Görüntüleme veya Ayarlama](https://technet.microsoft.com/library/cc816824%28v=ws.10%29.aspx) konusunun **Silinmiş nesne kapsayıcısı üzerindeki izinleri değiştirme** bölümüne bakın.

-   İsteğe bağlı: Ağ etkinlikleri olmayan bir kullanıcının kullanıcı hesabı. Bu hesap ATA Honeytoken kullanıcısı olarak yapılandırılır. Honeytoken kullanıcısını yapılandırmak için, kullanıcı adına değil kullanıcı hesabının SID değerine ihtiyacınız vardır. Daha fazla bilgi için [ATA Algılama Ayarlarıyla Çalışma](https://docs.microsoft.com/en-us/advanced-threat-analytics/deploy-use/working-with-detection-settings) konusuna bakın.

-   İsteğe bağlı: Etki alanı denetleyicilerinden gelen ve giden ağ trafiğini toplamaya ve çözümlemeye ek olarak, ATA Windows olayı 4776’yı kullanarak ATA Karma Değer Geçişi algılamasını daha da geliştirir. Bu SIEM sistemlerinizden alınabileceği gibi, etki alanı denetleyicinizden Windows Olay İletme’yi ayarlayarak da alınabilir. Toplanan olaylar ATA’ya etki alanı denetleyicisi ağ trafiği yoluyla sağlanmayan ek bilgiler sağlar.


## <a name="ata-center-requirements"></a>ATA Center gereksinimleri
Bu bölümde, ATA Center’ın gereksinimleri listelenir.
### <a name="general"></a>Genel
ATA Center, Windows Server 2012 R2 veya Windows Server 2016 çalıştıran sunuculara yüklemeyi destekler. ATA Center bir etki alanının veya çalışma grubunun üyesi olan sunuculara yüklenebilir.

Windows 2012 R2 çalıştıran ATA Center’ı yüklemeden önce şu güncelleştirmenin yüklendiğini onaylayın: [KB2919355](https://support.microsoft.com/kb/2919355/).

Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb2919355]`.

ATA Center’ın bir sanal makine olarak yüklenmesi desteklenir. 

>[!NOTE] 
> Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.

ATA Center’ı sanal makine olarak çalıştırıyorsanız, olası veritabanı bozulmalarını önlemek için yeni bir denetim noktası oluşturmadan önce sunucuyu kapatın.
### <a name="server-specifications"></a>Sunucu belirtimleri
Fiziksel bir sunucuda çalışırken, ATA veritabanı için BIOS’ta tekdüzen olmayan bellek erişimini (NUMA) **devre dışı bırakmanız** gerekir. Sisteminizde NUMA Düğüm Araya Ekleme (Node Interleaving) olarak geçiyor olabilir ve bu durumda NUMA’yı devre dışı bırakmak için Düğüm Araya Ekleme’yi **etkinleştirmeniz** gerekecektir. Daha fazla bilgi için BIOS belgelerinize bakın. ATA Center bir sanal sunucuda çalışırken bunun geçerli olmadığını unutmayın.<br>
En iyi performans için, ATA Center’ın **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.<br>
İzlediğiniz etki alanı denetleyicilerinin sayısı ve etki alanı denetleyicilerinden her birinin yükü sunucu belirtimlerini belirler; daha ayrıntılı bilgi için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).


### <a name="time-synchronization"></a>Zaman eşitleme
ATA Center sunucusu, ATA Gateway sunucuları ve etki alanı denetleyicilerinin zamanlarının 5 dakika içinde birbiriyle eşitlenmesi gerekir.


### <a name="network-adapters"></a>Ağ bağdaştırıcıları
Aşağıdakilere sahip olmanız gerekir:
-   En az bir ağ bağdaştırıcısı (VLAN ortamında fiziksel sunucu kullanılıyorsa, iki ağ bağdaştırıcısı kullanılması önerilir)

-   İki IP adresi (önerilir ancak gerekli değildir)

ATA Center ile ATA Gateway arasındaki iletişim, bağlantı noktası 443 üzerinde SSL kullanılarak şifrelenir. Ayrıca, ATA Konsolu da bağlantı noktası 443 üzerinde SSL kullanır. **İki IP adresi** kullanılması önerilir. ATA Center hizmeti bağlantı noktası 443’ü ilk IP adresine bağlar ve ATA Konsolu da bağlantı noktası 443’ü ikinci IP adresine bağlar.

> [!NOTE]
> İki farklı bağlantı noktasıyla tek IP adresi kullanılabilir, ama iki IP adresi kullanılması önerilir.

### <a name="ports"></a>Bağlantı noktaları
Aşağıdaki tabloda, ATA Center’ın düzgün çalışması için açılması gereken minimum bağlantı noktaları listelenir.

Bu tabloda IP adresi 1, ATA Center hizmetine ve IP adresi 2 de ATA Konsoluna bağlanmıştır:

|Protokol|Aktarım|Bağlantı Noktası|Hedef/Kaynak|Yön|IP Adresi|
|------------|-------------|--------|-----------|-------------|--------------|
|**SSL** (ATA İletişimi)|TCP|443 veya yapılandırılabilir|ATA Gateway|Gelen|IP adresi 1|
|**HTTP**|TCP|80|Şirket Ağı|Gelen|IP adresi 2|
|**HTTPS**|TCP|443|Şirket Ağı ve ATA Gateway|Gelen|IP adresi 2|
|**SMTP** (isteğe bağlı)|TCP|25|SMTP Sunucusu|Giden|IP adresi 2|
|**SMTPS** (isteğe bağlı)|TCP|465|SMTP Sunucusu|Giden|IP adresi 2|
|**Syslog** (isteğe bağlı)|TCP|514|Syslog sunucusu|Giden|IP adresi 2|

### <a name="certificates"></a>Sertifikalar
ATA Center’ın CRL dağıtım noktanıza erişimi olduğundan emin olun. ATA Gateway bileşenlerinin İnternet erişimi yoksa, [CRL’yi el ile içeri aktarma yordamını](https://technet.microsoft.com/library/aa996972%28v=exchg.65%29.aspx) izleyin ve tüm zincir için CRL dağıtım noktalarının tümünü yükleme işlemini gerçekleştirin.

ATA’nın yüklenmesini kolaylaştırmak için, işlem sırasında otomatik olarak imzalanan sertifikalar yükleyebilirsiniz. Dağıtım sonrasında otomatik olarak imzalanan sertifikayı ATA Gateway tarafından kullanılacak bir iç Sertifika Yetkilisi’nin sertifikasıyla değiştirebilirsiniz.<br>
> [!NOTE]
> Sertifikanın Sağlayıcı Türü, Şifreleme Hizmeti Sağlayıcısı (CSP) olmalıdır.


> Otomatik sertifika yenilemenin kullanılması desteklenmez.


> [!NOTE]
> ATA Konsolu’na başka bilgisayarlardan erişecekseniz, söz konusu bilgisayarların ATA Center tarafından kullanılan sertifikaya güvendiğinden emin olun; aksi takdirde sayfada oturum açmadan önce Web sitesinin güvenlik sertifikasında sorun olduğunu bildiren bir uyarı sayfası alırsınız.

## <a name="ata-gateway-requirements"></a>ATA Gateway gereksinimleri
Bu bölümde, ATA Gateway’in gereksinimleri listelenir.
### <a name="general"></a>Genel
ATA Gateway, Windows Server 2012 R2 veya Windows Server 2016 çalıştıran sunuculara yüklemeyi destekler (Sunucu çekirdeği dahil).
ATA Gateway bir etki alanının veya çalışma grubunun üyesi olan sunuculara yüklenebilir.
ATA Gateway, Etki Alanı İşlev Düzeyi Windows 2003 ve üstü olan Etki Alanı Denetleyicilerini izlemek için kullanılabilir.

Windows 2012 R2 çalıştıran ATA Gateway’i yüklemeden önce şu güncelleştirmenin yüklendiğini onaylayın: [KB2919355](https://support.microsoft.com/kb/2919355/).

Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb2919355]`.

ATA Gateway ile sanal makineleri kullanma hakkında bilgi için bkz. [Bağlantı noktası yansıtmasını yapılandırma](/advanced-threat-analytics/deploy-use/configure-port-mirroring)

> [!NOTE]
> En az 5 GB alan gereklidir ve 10 GB önerilir. Buna, ATA ikili dosyaları, [ATA günlükleri](/advanced-threat-analytics/troubleshoot/troubleshooting-ata-using-logs) ve [performans günlükleri](/advanced-threat-analytics/troubleshoot/troubleshooting-ata-using-perf-counters) için gereken alan da dahildir.

### <a name="server-specifications"></a>Sunucu belirtimleri
En iyi performans için, ATA Gateway’in **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.<br>
ATA Gateway, etki alanı denetleyicilerinden gelen ve giden ağ trafiği miktarına bağlı olarak, birden çok etki alanı denetleyicisinin izlenmesini destekleyebilir.

>[!NOTE] 
> Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.

ATA Gateway donanım gereksinimleri hakkında daha fazla bilgi için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).

### <a name="time-synchronization"></a>Zaman eşitleme
ATA Center sunucusu, ATA Gateway sunucuları ve etki alanı denetleyicilerinin zamanlarının 5 dakika içinde birbiriyle eşitlenmesi gerekir.

### <a name="network-adapters"></a>Ağ bağdaştırıcıları
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
    > -   Etki alanı denetleyicisi ağ trafiğinin hedefi olarak yakalama bağdaştırıcısı için bağlantı noktası yansıtmasını yapılandırın. Ek bilgi için bkz. [Bağlantı noktası yansıtmasını yapılandırma](/advanced-threat-analytics/deploy-use/configure-port-mirroring). Normalde, bağlantı noktası yansıtmasını yapılandırmak için ağ veya sanallaştırma ekibiyle çalışmanız gerekir.
    > -   Varsayılan ağ geçidi ve DNS sunucu adresleri olmadan ortamınız için statik yönlendirilemeyen bir IP adresi yapılandırın. Örneğin, 1.1.1.1/32. Bu, yakalama ağ bağdaştırıcısının en yüksek miktarda trafiği yakalayabilmesini ve gerekli ağ trafiğini göndermek ve almak için yönetim ağ bağdaştırıcısının kullanılmasını güvence altına alır.

### <a name="ports"></a>Bağlantı noktaları
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

### <a name="certificates"></a>Sertifikalar
ATA Center’ın CRL dağıtım noktanıza erişimi olduğundan emin olun. ATA Gateway bileşenlerinin İnternet erişimi yoksa, CRL’yi el ile içeri aktarma yordamını izleyin ve tüm zincir için CRL dağıtım noktalarının tümünü yükleme işlemini gerçekleştirin.<br>
ATA’nın yüklenmesini kolaylaştırmak için, işlem sırasında otomatik olarak imzalanan sertifikalar yükleyebilirsiniz. Dağıtım sonrasında otomatik olarak imzalanan sertifikayı ATA Gateway tarafından kullanılacak bir iç Sertifika Yetkilisi’nin sertifikasıyla değiştirebilirsiniz.

> [!NOTE]
> Sertifikanın Sağlayıcı Türü, Şifreleme Hizmeti Sağlayıcısı (CSP) olmalıdır.<br>

Yerel Bilgisayar deposunda yer alan ATA Gateway’in Bilgisayar deposunda **Sunucu Kimlik Doğrulaması**’nı destekleyen bir sertifikanın yüklenmesi gerekir. ATA Center tarafından bu sertifikaya güvenilmelidir.

## <a name="ata-lightweight-gateway-requirements"></a>ATA Lightweight Gateway gereksinimleri
Bu bölümde, ATA Lightweight Gateway’in gereksinimleri listelenir.
### <a name="general"></a>Genel
ATA Lightweight Gateway; Windows Server 2008 R2 SP1 (Server Core içermez), Windows Server 2012, Windows Server 2012 R2 veya Windows Server 2016 (Core dahil ancak Nano hariç) çalıştıran bir etki alanı denetleyicisine yüklemeyi destekler.

Etki alanı denetleyicisi salt okunur bir etki alanı denetleyicisi (RODC) olabilir.

ATA Lightweight Gateway bileşenini Windows Server 2012 R2 SP1 çalıştıran bir etki alanı denetleyicisine yüklemeden önce, şu güncelleştirmenin yüklendiğini onaylayın: [KB2919355](https://support.microsoft.com/kb/2919355/).
Şu Windows PowerShell cmdlet’ini çalıştırarak bunu denetleyebilirsiniz: `[Get-HotFix -Id kb2919355]`.

> [!NOTE]
> En az 5 GB alan gereklidir ve 10 GB önerilir. Buna, ATA ikili dosyaları, [ATA günlükleri](/advanced-threat-analytics/troubleshoot/troubleshooting-ata-using-logs.md) ve [performans günlükleri](/advanced-threat-analytics/troubleshoot/troubleshooting-ata-using-perf-counters.md) için gereken alan da dahildir.

### <a name="server-specifications"></a>Sunucu belirtimleri

ATA Lightweight Gateway, etki alanı denetleyicisinde en az 2 çekirdek ve 6 GB RAM kurulu olmasını gerektirir.
En iyi performans için, ATA Lightweight Gateway’in **Güç Seçeneğini** **Yüksek Performans** olarak ayarlayın.
ATA Lightweight Gateway, etki alanı denetleyicilerinden gelen ve giden ağ trafiğinin miktarına ve bu etki alanında kurulu kaynakların miktarına bağlı olarak çeşitli yük ve büyüklükte etki alanı denetleyicilerinde dağıtılabilir.

>[!NOTE] 
> Sanal makine olarak çalıştırırken dinamik bellek veya başka bir bellek balona alma özelliği desteklenmez.

ATA Lightweight Gateway donanım gereksinimleri hakkında daha fazla bilgi için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).

### <a name="time-synchronization"></a>Zaman eşitleme
ATA Center sunucusu, ATA Lightweight Gateway sunucuları ve etki alanı denetleyicilerinin zamanlarının 5 dakika içinde birbiriyle eşitlenmesi gerekir.
### <a name="network-adapters"></a>Ağ bağdaştırıcıları
ATA Lightweight Gateway etki alanı denetleyicisinin ağ bağdaştırıcılarının hepsindeki yerel trafiği izler. <br>
Dağıtımdan sonra, hangi ağ bağdaştırıcılarının izlendiğini değiştirmek isterseniz ATA Konsolu’nu kullanabilirsiniz.

### <a name="ports"></a>Bağlantı noktaları
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

### <a name="certificates"></a>Sertifikalar
ATA Center’ın CRL dağıtım noktanıza erişimi olduğundan emin olun. ATA Lightweight Gateway bileşenlerinin İnternet erişimi yoksa, CRL’yi el ile içeri aktarma yordamını izleyin ve tüm zincir için CRL dağıtım noktalarının tümünü yükleme işlemini gerçekleştirin.
ATA’nın yüklenmesini kolaylaştırmak için, işlem sırasında otomatik olarak imzalanan sertifikalar yükleyebilirsiniz. Dağıtım sonrasında otomatik olarak imzalanan sertifikayı ATA Lightweight Gateway tarafından kullanılacak bir iç Sertifika Yetkilisi’nin sertifikasıyla değiştirebilirsiniz.
> [!NOTE]
> Sertifikanın Sağlayıcı Türü, Şifreleme Hizmeti Sağlayıcısı (CSP) olmalıdır.

Yerel Bilgisayar deposunda yer alan ATA Lightweight Gateway’in Bilgisayar deposunda Sunucu Kimlik Doğrulaması’nı destekleyen bir sertifikanın yüklenmesi gerekir. ATA Center tarafından bu sertifikaya güvenilmelidir.

## <a name="ata-console"></a>ATA Konsolu
ATA Konsolu’na tarayıcı yoluyla erişilir ve aşağıdakiler desteklenir:

-   Internet Explorer sürüm 10 ve üstü

-   Microsoft Edge

-   Google Chrome 40 ve üstü

-   Minimum ekran genişliği çözünürlüğü 1700 piksel

## <a name="see-also"></a>Ayrıca bkz.

- [ATA mimarisi](ata-architecture.md)
- [ATA’yı yükleme](/advanced-threat-analytics/deploy-use/install-ata)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)





<!--HONumber=Dec16_HO2-->


