---
title: Azure Gelişmiş tehdit koruması önkoşulları | Microsoft Docs
description: Azure ATP başarılı bir dağıtımı ortamınızdaki gereksinimleri açıklanır.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 62c99622-2fe9-4035-9839-38fec0a353da
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: f959176ddca045f421af416d5ce9dc3a777cc43a
ms.sourcegitcommit: fdff488c79729035f89897c2ea0771a45b4c3ecf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49401921"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="azure-atp-prerequisites"></a>Azure ATP önkoşulları
Bu makalede, ortamınızda başarılı bir Azure ATP dağıtımının gereksinimlerini açıklar.

>[!NOTE]
> Kaynakları ve kapasiteyi planlama hakkında daha fazla bilgi için bkz: [Azure ATP kapasite planlaması](atp-capacity-planning.md).


Azure ATP portalı, Azure ATP algılayıcısını ve/veya Azure ATP tek başına algılayıcı oluşan Azure ATP bulut hizmeti Azure ATP oluşur. Her bir Azure ATP bileşen hakkında daha fazla bilgi için bkz. [Azure ATP mimarisi](atp-architecture.md).

Azure ATP örneğinizi oluşturmak için en az bir genel/güvenlik Yöneticisi ile bir AAD kiracısı gerekir. Her Azure ATP örneği bir birden çok Active Directory orman sınırının ve orman işlevsel düzeyi (FFL) Windows 2003 ve üstünde destekler. 

Önkoşul bu kılavuzda, Azure ATP başarıyla dağıtmak için ihtiyacınız olan her şeye sahip olmak için aşağıdaki bölümlere ayrılmıştır. 

[Başlamadan önce](#before-you-start): listeler toplamak için bilgi ve hesaplarla ağ varlıkları yüklemeye başlamadan önce olması gerekir.

[Azure ATP portalında](#azure-atp-workspace-management-portal-and-workspace-portal-requirements): portal tarayıcı gereksinimleri Azure ATP açıklar.

[Azure ATP algılayıcısını](#azure-atp-lightweight-sensor-requirements): listeler Azure ATP algılayıcısı donanım ve yazılım gereksinimleri.

[Azure ATP tek başına algılayıcı](#azure-atp-sensor-requirements): Azure ATP tek başına algılayıcı sunucularınızda yapılandırmanız gereken ayarlar yanı sıra Azure ATP listeler tek başına algılayıcı donanım, yazılım gereksinimleri.

## <a name="before-you-start"></a>Başlamadan önce
Bu bölüm, hesaplarının yanı sıra toplamanız gereken bilgiler ve Azure ATP yüklemeye başlamadan önce olmalıdır. ağ varlık bilgilerini listeler.

- Enterprise Mobility + Security (EMS E5) 5 için doğrudan aracılığıyla lisans [Office 365 portalında](https://www.microsoft.com/cloud-platform/enterprise-mobility-security-pricing) veya Cloud Solution Partner (CSP) lisans modeli aracılığıyla.  

- Azure ATP algılayıcı yüklemek istediğiniz etki alanı denetleyicileri Azure ATP bulut hizmeti için Internet bağlantınız doğrulayın. Azure ATP algılayıcısını bir ara sunucu kullanımını destekler. Proxy yapılandırması hakkında daha fazla bilgi için bkz. [Azure ATP için Ara sunucu yapılandırma](configure-proxy.md).  

-   Bir **şirket içi** AD kullanıcı hesabı ve parola ile izlenen etki alanlarındaki tüm nesnelere okuma erişimi.

    > [!NOTE]
    > Etki alanınızdaki çeşitli Kurumsal Birimlerde (OU) özel ACL’ler ayarladıysanız, seçili kullanıcının bu OU’lar üzerinde okuma izinleri olmasına dikkat edin.

-   Azure ATP tek başına algılayıcı üzerinde Wireshark çalıştırırsanız Wireshark yakalamasını durdurduktan sonra Azure Gelişmiş tehdit koruması algılayıcı hizmeti yeniden başlatmanız gerekir. Aksi durumda, trafik yakalama algılayıcı durdurur.

- Azure ATP algılayıcısını NIC grubu oluşturma bağdaştırıcısı ile yapılandırılan bir makinede yüklemeye çalışırsanız, bir yükleme hatasını alıyorsunuz. Azure ATP algılayıcısını NIC ekibi oluşturma ile yapılandırılmış bir makineye yüklemek isterseniz bkz [Azure ATP algılayıcısını NIC ekip oluşturma sorunu](troubleshooting-atp-known-issues.md#nic-teaming).

-    Önerilen: Kullanıcının silinmiş nesneler kapsayıcısı üzerinde salt okuma izinleri olmalıdır. Bu, Azure ATP Active Directory'den kullanıcı silme işlemlerini algılamasını sağlar. Silinmiş nesneler kapsayıcısı üzerinde salt okuma izinlerini yapılandırma hakkında daha fazla bilgi için bkz: **Silinmiş nesne kapsayıcısı üzerindeki izinleri değiştirme** konusundaki [görünümü veyadizinnesnesiüzerindekiizinleriayarlayın](https://technet.microsoft.com/library/cc816824%28v=ws.10%29.aspx) makalesi.

-   İsteğe bağlı: Ağ etkinlikleri olmayan bir kullanıcının kullanıcı hesabı. Bu hesap bir Azure ATP Honeytoken kullanıcısı olarak yapılandırılır. Daha fazla bilgi için [Dışlamalar ve Honeytoken kullanıcısını yapılandırma](install-atp-step7.md).

-   İsteğe bağlı: tek başına algılayıcı dağıtırken Windows olayları 4776, 4732, 4733, 4728, 4729, 4756, 4757'yi ve 7045 Azure ATP Pass--Hash, deneme yanılma, gizli grup, Honey Token değişiklikleri daha da geliştirmek için Azure ATP iletmek gereklidir algılamalar ve kötü amaçlı hizmeti oluşturma. Azure ATP algılayıcısını bu olayları otomatik olarak alır. Azure ATP tek başına algılayıcı bu olayları sıem sistemlerinizden alınabileceği gibi etki alanı denetleyicinizden Windows Olay iletme'yi ayarlayarak alınabilir. Toplanan olaylar, etki alanı denetleyicisi ağ trafiğinin kullanılabilir olmayan ek bilgilerle Azure ATP sağlar.

## <a name="azure-atp-portal-requirements"></a>Azure ATP portalı gereksinimleri
Azure ATP portalına erişim aşağıdaki tarayıcılar ve ayarları destekleyen bir tarayıcı şöyledir:
-   Microsoft Edge
-   Internet Explorer sürüm 10 ve üstü
-   Google Chrome 4.0 ve üzeri
-   Minimum ekran genişliği çözünürlüğü 1700 piksel
-   Güvenlik Duvarı/proxy'si açılmaya - Azure ATP bulut hizmetiyle iletişim kurmak için *. atp.azure.com 443 numaralı bağlantı noktası güvenlik duvarı/proxy'sinde açık olmalıdır.

 ![Azure ATP mimarisi diyagramı](media/ATP-architecture-topology.png)


> [!NOTE]
> Varsayılan olarak, en fazla 100 algılayıcınız Azure ATP destekler. Daha fazla yüklemek istiyorsanız, Azure ATP desteğe başvurun.

## <a name="azure-atp-sensor-requirements"></a>Azure ATP algılayıcısı gereksinimleri
Bu bölümde Azure ATP algılayıcısını ilişkin gereksinimler listelenmiştir.
### <a name="general"></a>Genel
Azure ATP algılayıcısını, Windows Server 2008 R2 SP1 (Server Core içermeyen), Windows Server 2012, Windows Server 2012 R2, Windows Server 2016 (Core içerip Nano içermeyen) çalıştıran bir etki alanı denetleyicisine yüklemeyi destekler.

Etki alanı denetleyicisi salt okunur etki alanı denetleyicisi (RODC) olabilir.

Etki alanı denetleyicilerinizin bulut hizmetiyle iletişim kurmak güvenlik duvarları ve proxy'ler için 443 numaralı bağlantı noktasını açmanız gerekir *. atp.azure.com.

Yükleme sırasında .net Framework 4.7 yüklenir ve yeniden başlatma bekleyen ise etki alanı denetleyicisini yeniden başlatılmasını gerektirebilir.


> [!NOTE]
> En az 5 GB disk alanı gereklidir ve 10 GB önerilir. Bu Azure ATP ikili dosyaları, Azure ATP günlükleri ve performans için gereken alan da dahildir günlükleri.

### <a name="server-specifications"></a>Sunucu belirtimleri

Azure ATP algılayıcısını, en az iki çekirdek ve 6 GB RAM etki alanı denetleyicisinde yüklü olmasını gerektirir.
En iyi performans için ayarlanmış **güç seçeneğini** Azure ATP algılayıcı için **yüksek performanslı**.
Azure ATP algılayıcısını çeşitli yük ve büyüklükte etki alanı denetleyicilerinden gelen ve giden ağ trafiği miktarına ve bu etki alanı denetleyicisi üzerinde kurulu kaynakların miktarına bağlı olarak, etki alanı denetleyicilerinde dağıtılabilir.

>[!NOTE] 
> Sanal makine olarak çalıştırırken Dinamik bellek veya başka bir bellek Balona alınma özelliği desteklenmiyor.

Azure ATP algılayıcısı donanım gereksinimleri hakkında daha fazla bilgi için bkz. [Azure ATP kapasite planlaması](atp-capacity-planning.md).

### <a name="time-synchronization"></a>Zaman eşitleme

Sunucuları ve ileride algılayıcının yüklendiği etki alanı denetleyicileri için beş dakika içinde birbiriyle eşitlenmesi olması gerekir.

### <a name="network-adapters"></a>Ağ bağdaştırıcıları

Azure ATP algılayıcısını etki alanı denetleyicisinin ağ bağdaştırıcılarının hepsindeki yerel trafiği izler. <br>
Dağıtımdan sonra hangi ağ bağdaştırıcılarının izlendiğini değiştirmek isterseniz, Azure ATP çalışma alanı portalı kullanabilirsiniz.

Algılayıcı, etki alanı denetleyicileri Broadcom ağ bağdaştırıcısı ekibi oluşturma ile Windows 2008 R2 çalıştıran etkin üzerinde desteklenmiyor.

### <a name="ports"></a>Bağlantı noktaları
Aşağıdaki tabloda Azure ATP algılayıcısını gereken minimum bağlantı noktaları listelenmektedir:

|Protokol|Aktarım|Bağlantı Noktası|Hedef/Kaynak|Yön|
|------------|-------------|--------|-----------|-------------|
|**Internet bağlantı noktaları**|||||
|SSL (*.atp.azure.com)|TCP|443|Azure ATP bulut hizmeti|Giden|
|**İç bağlantı noktaları**|||||
|DNS|TCP ve UDP|53|DNS Sunucuları|Giden|
|Netlogon (SMB, CIFS, SAM-R)|TCP/UDP|445|Ağdaki tüm cihazlar|Giden|
|RPC üzerinden NTLM|TCP|135|Ağdaki tüm cihazlar|Her İkisi|
|NetBIOS|UDP|137|Ağdaki tüm cihazlar|Her İkisi|
|Syslog (isteğe bağlı)|TCP/UDP|514, yapılandırmasına bağlı olarak|SIEM Sunucusu|Gelen|
|RADIUS|UDP|1813|RADIUS|Gelen|
|TLS RDP bağlantı noktası|TCP|3389|Ağdaki tüm cihazlar|Her İkisi|

> [!NOTE]
> - Dizin hizmeti kullanıcı hesabını kullanarak algılayıcı uç noktaları oluşturmak için SAM-R (ağ oturumu açma) kullanarak Yerel yöneticilerin kuruluşunuzdaki sorgular [yanal hareket yolu graf](use-case-lateral-movement-path.md). Daha fazla bilgi için [SAM-R yapılandırmak gerekli izinler](install-atp-step8-samr.md).
> - Aşağıdaki bağlantı noktalarının açık cihazlarda gelen trafik Azure ATP tek başına algılayıcı ağdan gerekir:
>   -   Çözümleme amacıyla (TCP bağlantı noktası 135) RPC üzerinden NTLM
>   -   Çözümleme amacıyla NetBIOS (UDP bağlantı noktası 137)
>   -   RDP (TCP bağlantı noktası 3389), yalnızca ilk paketi *istemci hello'suna*, çözümleme amacıyla<br> Kimlik doğrulaması olmayan herhangi bir bağlantı noktaları üzerinde gerçekleştirilir unutmayın.

## <a name="azure-atp-standalone-sensor-requirements"></a>Azure ATP tek başına algılayıcı gereksinimleri
Bu bölümde Azure ATP tek başına algılayıcı ilişkin gereksinimler listelenmiştir.
### <a name="general"></a>Genel
Azure ATP tek başına algılayıcı, Windows Server 2012 R2 veya Windows Server 2016 (Sunucu Çekirdeği dahil) çalıştıran sunuculara yüklemeyi destekler.
Azure ATP tek başına algılayıcı bir etki alanı veya çalışma grubu üyesi olan bir sunucuya yüklenebilir.
Azure ATP tek başına algılayıcı ile etki alanı işlevsel düzeyi, Windows 2003 ve üstü etki alanı denetleyicilerini izlemek için kullanılabilir.

Tek başına algılayıcı bulut hizmetiyle iletişim kurmak, güvenlik duvarları ve proxy'ler için 443 numaralı bağlantı noktası *. atp.azure.com açık olmalıdır.


Azure ATP tek başına algılayıcı ile sanal makineleri kullanma hakkında daha fazla bilgi için bkz: [bağlantı noktası yansıtmayı yapılandırma](configure-port-mirroring.md).

> [!NOTE]
> En az 5 GB disk alanı gereklidir ve 10 GB önerilir. Bu Azure ATP ikili dosyaları, Azure ATP günlükleri ve performans için gereken alan da dahildir günlükleri.

### <a name="server-specifications"></a>Sunucu belirtimleri
En iyi performans için ayarlanmış **güç seçeneğini** Azure ATP tek başına algılayıcı için **yüksek performanslı**.<br>
Bir Azure ATP tek başına algılayıcı, etki alanı denetleyicilerinden gelen ve giden ağ trafiği miktarına bağlı olarak birden çok etki alanı denetleyicisinin izlenmesini destekleyebilir.

>[!NOTE] 
> Sanal makine olarak çalıştırırken Dinamik bellek veya başka bir bellek Balona alınma özelliği desteklenmiyor.

Azure ATP tek başına algılayıcı donanım gereksinimleri hakkında daha fazla bilgi için bkz. [Azure ATP kapasite planlaması](atp-capacity-planning.md).

### <a name="time-synchronization"></a>Zaman eşitleme

Sunucuları ve ileride algılayıcının yüklendiği etki alanı denetleyicileri için beş dakika içinde birbiriyle eşitlenmesi olması gerekir.


### <a name="network-adapters"></a>Ağ bağdaştırıcıları
Azure ATP tek başına algılayıcı en az bir Yönetim bağdaştırıcısı ve en az bir yakalama bağdaştırıcısı gerekir:

-   **Yönetim bağdaştırıcısı** - şirket ağınızdaki iletişim için kullanılır. Algılayıcı bu bağdaştırıcı, koruma ve makine hesaplarına çözümlemesinde DC sorgulamak için kullanır. <br>Bu bağdaştırıcı, aşağıdaki ayarlarla yapılandırılması gerekir:

    -   Varsayılan ağ geçidi dahil statik IP adresi

    -   Tercih edilen ve alternatif DNS sunucuları

    -   **Bu bağlantı için DNS son eki**, izlenen her etki alanı için etki alanının DNS adı olmalıdır.

        ![Gelişmiş TCP/IP ayarlarında DNS son ekini yapılandırma](media/ATP-DNS-Suffix.png)

        > [!NOTE]
        > Azure ATP tek başına algılayıcı etki alanının bir üyesi ise, otomatik olarak da yapılandırılabilir.

-   **Yakalama bağdaştırıcısı** - etki alanı denetleyicilerinden gelen ve giden trafiği yakalamak için kullanılır.

    > [!IMPORTANT]
    > -   Etki alanı denetleyicisi ağ trafiğinin hedefi olarak yakalama bağdaştırıcısı için bağlantı noktası yansıtmasını yapılandırın. Daha fazla bilgi için [bağlantı noktası yansıtmayı yapılandırma](configure-port-mirroring.md). Genellikle, bağlantı noktası yansıtmasını yapılandırmak için ağ veya sanallaştırma ekibiyle çalışmanız gerekir.
    > -   Statik yönlendirilemeyen bir IP adresi yapılandırın (özelliğini/32 ile maskesi) varsayılan algılayıcı ağ geçidi ve DNS sunucu adresleri olmadan ortamınız için. Örneğin, 10.10.0.10/32. Bu yakalama ağ bağdaştırıcısının en yüksek miktarda trafiği yakalayabilmesini ve gerekli ağ trafiğini gönderip için yönetim ağ bağdaştırıcısı kullanıldığını sağlar.

### <a name="ports"></a>Bağlantı noktaları
Aşağıdaki tabloda, yönetim bağdaştırıcısında yapılandırılması gereken Azure ATP tek başına algılayıcı minimum bağlantı noktaları listelenmektedir:

|Protokol|Aktarım|Bağlantı Noktası|Hedef/Kaynak|Yön|
|------------|-------------|--------|-----------|-------------|
|**Internet bağlantı noktaları**|||||
|SSL (*.atp.azure.com)|TCP|443|Azure ATP bulut hizmeti|Giden|
|**İç bağlantı noktaları**|||||
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
|Syslog (isteğe bağlı)|TCP/UDP|514, yapılandırmasına bağlı olarak|SIEM Sunucusu|Gelen|
|RADIUS|UDP|1813|RADIUS|Gelen|
|RDP için TLS|TCP|3389|Ağdaki tüm cihazlar|Her İkisi|

> [!NOTE]
> - Dizin hizmeti kullanıcı hesabını kullanarak algılayıcı uç noktaları oluşturmak için SAM-R (ağ oturumu açma) kullanarak Yerel yöneticilerin kuruluşunuzdaki sorgular [yanal hareket yolu graf](use-case-lateral-movement-path.md). Daha fazla bilgi için [SAM-R yapılandırmak gerekli izinler](install-atp-step8-samr.md).
> - Aşağıdaki bağlantı noktalarının açık cihazlarda gelen trafik Azure ATP tek başına algılayıcı ağdan gerekir:
>   -   Çözümleme amacıyla (TCP bağlantı noktası 135) RPC üzerinden NTLM
>   -   Çözümleme amacıyla NetBIOS (UDP bağlantı noktası 137)
>   -   RDP (TCP bağlantı noktası 3389), yalnızca ilk paketi *istemci hello'suna*, çözümleme amacıyla<br> Kimlik doğrulaması olmayan herhangi bir bağlantı noktaları üzerinde gerçekleştirilir unutmayın.



## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Azure ATP mimarisi](atp-architecture.md)
- [Azure ATP yükleyin](install-atp-step1.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)

