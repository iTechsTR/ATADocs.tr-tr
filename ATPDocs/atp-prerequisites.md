---
title: Azure Advanced Threat Protection önkoşulları | Microsoft Docs
description: Ortamınızda başarılı bir Azure ATP dağıtımının gereksinimlerini açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/28/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 62c99622-2fe9-4035-9839-38fec0a353da
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 3c8e0b239c335981b2030021d1d4e319b2810fda
ms.sourcegitcommit: 7c9fe4eb781bec71129310a6e0c5e76b022a0213
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="azure-atp-prerequisites"></a>Azure ATP önkoşulları
Bu makalede, ortamınızda başarılı bir Azure ATP dağıtımının gereksinimlerini açıklar.

>[!NOTE]
> Kaynakları ve kapasiteyi planlama hakkında daha fazla bilgi için bkz: [Azure ATP kapasite planlaması](atp-capacity-planning.md).


Çalışma alanı Yönetim Portalı'nı ve bir çalışma alanı portalı, Azure ATP tek başına algılayıcı ve/veya Azure ATP algılayıcı oluşur Azure ATP bulut hizmeti Azure ATP oluşur. Azure ATP bileşenleri hakkında daha fazla bilgi için bkz: [Azure ATP mimarisi](atp-architecture.md).

Her Azure ATP çalışma alanı bir Active Directory orman sınırı ve orman işlev düzeyi (FFL) Windows 2003 ve üstünde destekler. Çok ormanlı dağıtımlar için ayrı bir Azure ATP çalışma her orman için gereklidir.


[Başlamadan önce](#before-you-start): Bu bölümde toplamanız gereken bilgiler, hesapları ve sahip olmanız gereken Azure ATP yüklemeye başlamadan önce ağ varlıkları listelenir.

[Azure ATP çalışma Yönetim Portalı](#azure-atp-workspace-management-portal-and-workspace-portal-requirements): Bu bölümde çalışma Yönetim Portalı tarayıcı gereksinimlerini açıklar.

[Azure ATP çalışma portal](#azure-atp-workspace-management-portal-and-workspace-portal-requirements): Bu bölümde Azure ATP çalışma Portalı'nı çalıştırmak için tarayıcı gereksinimleri açıklanmaktadır.

[Azure ATP tek başına algılayıcı](#azure-atp-sensor-requirements): Bu bölümde Azure ATP tek başına algılayıcı sunucularınızda yapılandırmanız gereken ayarlar yanı sıra Azure ATP tek başına algılayıcı donanım, yazılım gereksinimleri listelenmiştir.

[Azure ATP algılayıcı](#azure-atp-lightweight-sensor-requirements): Bu bölümde Azure ATP algılayıcı donanım ve yazılım gereksinimleri listelenmiştir.

![Azure ATP mimarisi diyagramı](media/ATP-architecture-topology.png)

## <a name="before-you-start"></a>Başlamadan önce
Bu bölümde toplamanız gereken bilgiler, hesapları ve Azure ATP yüklemeye başlamadan önce olmalıdır ağ varlıkları listelenir.


-   Bir **şirket içi** AD kullanıcı hesabı ve parolası ile izlenen etki alanlarındaki tüm nesnelere okuma erişimi.

    > [!NOTE]
    > Etki alanınızdaki çeşitli Kurumsal Birimlerde (OU) özel ACL’ler ayarladıysanız, seçili kullanıcının bu OU’lar üzerinde okuma izinleri olmasına dikkat edin.

-   Azure ATP tek başına algılayıcı üzerinde Wireshark çalıştırırsanız, Wireshark yakalama durdurduktan sonra Azure Advanced Threat Protection algılayıcı hizmetini yeniden başlatmanız gerekir. Aksi durumda, trafik yakalama algılayıcı durdurur.

- Bir NIC ekibi oluşturma bağdaştırıcısı ile yapılandırılmış bir makinede ATP algılayıcı yüklemeye çalışırsanız, bir yükleme hatasını alıyorsunuz. NIC ekibi oluşturma ile yapılandırılmış bir makinede ATP algılayıcı yüklemek istiyorsanız, Azure ATP destek temsilcinize başvurun.

-    Önerilen: Kullanıcının silinmiş nesneler kapsayıcısı üzerinde salt okuma izinleri olmalıdır. Bu etki alanında toplu nesne silme işlemlerini algılamasını Azure ATP sağlar. Silinmiş nesneler kapsayıcısı üzerinde salt okuma izinlerini yapılandırma hakkında daha fazla bilgi için bkz: **Silinmiş nesne kapsayıcısı üzerindeki izinleri değiştirme** bölümüne [görünümü veya bir dizin nesnesiizinleriayarlayın](https://technet.microsoft.com/library/cc816824%28v=ws.10%29.aspx) makalesi.

-   İsteğe bağlı: Ağ etkinlikleri olmayan bir kullanıcının kullanıcı hesabı. Bu hesap Azure ATP Honeytoken kullanıcısı olarak yapılandırılır. Daha fazla bilgi için bkz: [dışarıda kalanları ve Honeytoken kullanıcısını yapılandırmak](install-atp-step7.md).

-   İsteğe bağlı: tek başına algılayıcı dağıtırken, Windows olayları 4776, 4732, 4733, 4728, 4729, 4756, 4757 ve 7045 Azure ATP Pass--Hash, deneme yanılma saldırısı, değişikliği hassas gruplarına bal kapları algılamaların daha fazla geliştirmek için ATP iletmek gerekli olan ve kötü amaçlı hizmeti oluşturma. Azure ATP algılayıcı bu olayları otomatik olarak alınır. Azure ATP tek başına algılayıcı bu olaylar, etki alanı denetleyicinizden Windows Olay iletme'yi ayarlayarak SIEM sistemlerinizden alınabilir. Toplanan olayları Azure ATP etki alanı denetleyicisi ağ trafiğinin kullanılabilir olmayan ek bilgi sağlar.


## <a name="azure-atp-workspace-management-portal-and-workspace-portal-requirements"></a>Azure ATP çalışma Yönetim Portalı ve çalışma alanı portal gereksinimleri
Azure ATP çalışma portalı ve Azure ATP çalışma yönetim portalına erişim aşağıdaki tarayıcılar ve ayarları destekleyen bir tarayıcı yoluyla şöyledir:
-   Microsoft Edge
-   Internet Explorer sürüm 10 ve üstü
-   Google Chrome 4.0 ve üstü
-   Minimum ekran genişliği çözünürlüğü 1700 piksel
-   Güvenlik duvarı/proxy Azure ATP bulut hizmetiyle iletişim kurmak için açık -, açık olması gerekir: *. güvenlik duvarı/proxy'de atp.azure.com bağlantı noktası 443'tür. 

## <a name="azure-atp-standalone-sensor-requirements"></a>Azure ATP tek başına algılayıcı gereksinimleri
Bu bölümde Azure ATP tek başına algılayıcı için gereksinimleri listelenir.
### <a name="general"></a>Genel
Azure ATP tek başına algılayıcı Windows Server 2012 R2 veya Windows Server 2016 (INCLUDE Sunucu Çekirdeği) çalıştıran sunuculara yüklemeyi destekler.
Azure ATP tek başına algılayıcı bir etki alanı veya çalışma grubu üyesi olan bir sunucuya yüklenebilir.
Azure ATP tek başına algılayıcı ve üstü etki alanı işlev düzeyi Windows 2003 ile etki alanı denetleyicilerini izlemek için kullanılabilir.

Etki alanı denetleyicileriniz bulut hizmetiyle iletişim kurmak güvenlik duvarları ve proxy için 443 numaralı bağlantı noktasını açmalısınız *. atp.azure.com.


Sanal makineler Azure ATP tek başına algılayıcı ile kullanma hakkında daha fazla bilgi için bkz: [bağlantı noktası yansıtmayı yapılandırma](configure-port-mirroring.md).

> [!NOTE]
> En az 5 GB alan gereklidir ve 10 GB önerilir. Bu Azure ATP ikili dosyaları, Azure ATP günlüklerini ve performans için gereken alanı içerir günlükleri.

### <a name="server-specifications"></a>Sunucu belirtimleri
En iyi performans için ayarlanmış **güç seçeneği** için Azure ATP tek başına algılayıcı **yüksek performanslı**.<br>
Bir Azure ATP tek başına algılayıcı, etki alanı denetleyicilerinden gelen ve giden ağ trafiği miktarına bağlı olarak, birden çok etki alanı denetleyicisinin izlenmesini destekleyebilir.

>[!NOTE] 
> Sanal makine olarak çalıştırırken Dinamik bellek veya başka bir bellek Balona alınma özelliği desteklenmiyor.

Azure ATP tek başına algılayıcı donanım gereksinimleri hakkında daha fazla bilgi için bkz: [Azure ATP kapasite planlaması](atp-capacity-planning.md).

### <a name="time-synchronization"></a>Zaman eşitleme

Sunucuları ve etki alanı denetleyicileri algılayıcı yüklendiği için beş dakika içinde birbiriyle eşitlenmesi gerekir.


### <a name="network-adapters"></a>Ağ bağdaştırıcıları
Azure ATP tek başına algılayıcı en az bir Yönetim bağdaştırıcısı ve en az bir yakalama bağdaştırıcısı gerekir:

-   **Yönetim bağdaştırıcısı** - şirket ağınızdaki iletişim için kullanılır. Bu bağdaştırıcı aşağıdaki ayarlara sahip yapılandırılmış olması gerekir:

    -   Varsayılan algılayıcı dahil statik IP adresi

    -   Tercih edilen ve alternatif DNS sunucuları

    -   **Bu bağlantı için DNS son eki**, izlenen her etki alanı için etki alanının DNS adı olmalıdır.

        ![Gelişmiş TCP/IP ayarlarında DNS son ekini yapılandırma](media/ATP-DNS-Suffix.png)

        > [!NOTE]
        > Azure ATP tek başına algılayıcı etki alanının bir üyesiyse, bu otomatik olarak yapılandırılabilir.

-   **Yakalama bağdaştırıcısı** - etki alanı denetleyicilerinden gelen ve giden trafiği yakalamak için kullanılan.

    > [!IMPORTANT]
    > -   Etki alanı denetleyicisi ağ trafiğinin hedefi olarak yakalama bağdaştırıcısı için bağlantı noktası yansıtmasını yapılandırın. Daha fazla bilgi için bkz: [bağlantı noktası yansıtmayı yapılandırma](configure-port-mirroring.md). Genellikle, bağlantı noktası yansıtma yapılandırmak için ağ veya sanallaştırma ekibiyle çalışmanız gerekir.
    > -   Hiçbir varsayılan algılayıcı ile ortamınız için bir statik yönlendirilemeyen IP adresi ve hiçbir DNS sunucusu adreslerini yapılandırın. Örneğin, 1.1.1.1/32. Bu yakalama ağ bağdaştırıcısı yüksek miktarda trafiği yakalayabilir ve yönetim ağ bağdaştırıcısı'nın göndermek ve gerekli ağ trafiğini almak için kullanılan sağlar.

### <a name="ports"></a>Bağlantı noktaları
Aşağıdaki tabloda yönetim bağdaştırıcısında yapılandırılması Azure ATP tek başına algılayıcı gereken minimum bağlantı noktaları listelenmektedir:

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
|Netlogon (SMB, CIFS, SAM-R)|TCP ve UDP|445|Etki alanı denetleyicileri|Giden|
|Windows Saati|UDP|123|Etki alanı denetleyicileri|Giden|
|DNS|TCP ve UDP|53|DNS Sunucuları|Giden|
|RPC üzerinden NTLM|TCP|135|Ağdaki tüm cihazlar|Giden|
|NetBIOS|UDP|137|Ağdaki tüm cihazlar|Giden|
|Syslog (isteğe bağlı)|TCP/UDP|yapılandırmasına bağlı olarak 514|SIEM Sunucusu|Gelen|
|RADIUS|UDDP|1813|RADIUS|Gelen|

> [!NOTE]
> - Dizin hizmeti kullanıcı hesabı kullanarak, algılayıcı uç noktaları oluşturmak için SAM-R (ağda oturum açma) kullanarak yerel Yöneticiler için kuruluşunuzdaki sorgular [yanal hareket yolu grafik](use-case-lateral-movement-path.md). Daha fazla bilgi için bkz: [SAM-R yapılandırmak gerekli izinleri](install-atp-step8-samr.md).
> - Aşağıdaki bağlantı noktalarını açık cihazlarda gelen trafik Azure ATP tek başına algılayıcılar ağdan gerekir:
>   -   Çözümleme amacıyla (TCP bağlantı noktası 135) RPC üzerinden NTLM
>   -   Çözümleme amacıyla NetBIOS (UDP bağlantı noktası 137)
>   -   Algılama amacıyla SAM-R sorgular (TCP/UDP bağlantı noktası 445)


## <a name="azure-atp-sensor-requirements"></a>Azure ATP algılayıcı gereksinimleri
Bu bölümde Azure ATP algılayıcı için gereksinimleri listelenir.
### <a name="general"></a>Genel
Azure ATP algılayıcısı (Sunucu Çekirdeği dahil değil) Windows Server 2008 R2 SP1, Windows Server 2012, Windows Server 2012 R2, Windows Server 2016 (çekirdek ancak değil Nano dahil) çalıştıran bir etki alanı denetleyicisi üzerinde yüklemeyi destekler.

Etki alanı denetleyicisi salt okunur etki alanı denetleyicisi (RODC) olabilir.

Etki alanı denetleyicileriniz bulut hizmetiyle iletişim kurmak güvenlik duvarları ve proxy için 443 numaralı bağlantı noktasını açmalısınız *. atp.azure.com.

Yükleme sırasında .net Framework 4.7 yüklenir ve etki alanı denetleyicisini yeniden neden olabilir.


> [!NOTE]
> En az 5 GB alan gereklidir ve 10 GB önerilir. Bu Azure ATP ikili dosyaları, Azure ATP günlüklerini ve performans için gereken alanı içerir günlükleri.

### <a name="server-specifications"></a>Sunucu belirtimleri

Azure ATP algılayıcı en az iki çekirdek ve 6 GB etki alanı denetleyicisinde yüklü RAM gerektirir.
En iyi performans için ayarlanmış **güç seçeneği** Azure ATP algılayıcı **yüksek performanslı**.
Azure ATP algılayıcı çeşitli yük ve büyüklükte etki alanı denetleyicilerinden gelen ve giden ağ trafiği miktarına ve bu etki alanı denetleyicisinde yüklü kaynakları miktarını bağlı olarak, etki alanı denetleyicilerinde dağıtılabilir.

>[!NOTE] 
> Sanal makine olarak çalıştırırken Dinamik bellek veya başka bir bellek Balona alınma özelliği desteklenmiyor.

Azure ATP algılayıcı donanım gereksinimleri hakkında daha fazla bilgi için bkz: [Azure ATP kapasite planlaması](atp-capacity-planning.md).

### <a name="time-synchronization"></a>Zaman eşitleme

Sunucuları ve etki alanı denetleyicileri algılayıcı yüklendiği için beş dakika içinde birbiriyle eşitlenmesi gerekir.

### <a name="network-adapters"></a>Ağ bağdaştırıcıları

Azure ATP algılayıcı etki alanı denetleyicisinin ağ bağdaştırıcılarının hepsindeki yerel trafiği izler. <br>
Dağıtımdan sonra hangi ağ bağdaştırıcılarının izlendiğini değiştirmek istiyorsanız, Azure ATP çalışma Portalı'nı kullanabilirsiniz.

Algılayıcı, etki alanı denetleyicileri Broadcom ağ bağdaştırıcısı grubu oluşturma ile Windows 2008 R2 çalıştıran etkin desteklenmiyor.

### <a name="ports"></a>Bağlantı noktaları
Aşağıdaki tabloda Azure ATP algılayıcı gereken minimum bağlantı noktaları listelenmektedir:

|Protokol|Aktarım|Bağlantı Noktası|Hedef/Kaynak|Yön|
|------------|-------------|--------|-----------|-------------|
|**Internet bağlantı noktaları**|||||
|SSL (*.atp.azure.com)|TCP|443|Azure ATP bulut hizmeti|Giden|
|**İç bağlantı noktaları**|||||
|DNS|TCP ve UDP|53|DNS Sunucuları|Giden|
|RPC üzerinden NTLM|TCP|135|Ağdaki tüm cihazlar|Giden|
|Netlogon (SMB, CIFS, SAM-R)|TCP/UDP|445|Etki alanı denetleyicileri|Giden|
|NetBIOS|UDP|137|Ağdaki tüm cihazlar|Giden|
|Syslog (isteğe bağlı)|TCP/UDP|yapılandırmasına bağlı olarak 514|SIEM Sunucusu|Gelen|
|RADIUS|UDDP|1813|RADIUS|Gelen|

> [!NOTE]
> - Dizin hizmeti kullanıcı hesabı kullanarak, algılayıcı uç noktaları oluşturmak için SAM-R (ağda oturum açma) kullanarak yerel Yöneticiler için kuruluşunuzdaki sorgular [yanal hareket yolu grafik](use-case-lateral-movement-path.md).
> - Aşağıdaki bağlantı noktalarını açık cihazlarda gelen trafik Azure ATP algılayıcılar ağdan gerekir:
>   -   Çözümleme amacıyla (TCP bağlantı noktası 135) RPC üzerinden NTLM
>   -   Çözümleme amacıyla NetBIOS (UDP bağlantı noktası 137)
>   -   Algılama amacıyla SAM-R sorgular (TCP/UDP bağlantı noktası 445)





## <a name="see-also"></a>Ayrıca bkz:
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Azure ATP mimarisi](atp-architecture.md)
- [ATP yükleyin](install-atp-step1.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)

