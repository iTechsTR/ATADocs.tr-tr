---
title: Advanced Threat Analytics’te Windows Olay İletme’yi Yapılandırma | Microsoft Docs
description: ATA ile Windows Olay İletme’yi yapılandırmaya yönelik seçeneklerinizi açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 3f0498f9-061d-40e6-ae07-98b8dcad9b20
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 512e7fa979a6fd5e140d65836b533b720a6dc03b
ms.sourcegitcommit: 1b23381ca4551a902f6343428d98f44480077d30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47403225"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="configuring-windows-event-forwarding"></a>Windows Olay İletme’yi yapılandırma

> [!NOTE]
> ATA 1.8 ve üzeri sürümlerde artık ATA Lightweight Gateway’ler için olay koleksiyonu yapılandırması gerekli değildir. ATA Lightweight Gateway, artık olay iletmeyi yapılandırmaya gerek kalmadan olayları yerel olarak okuyun.

ATA algılama yeteneklerini artırmak için aşağıdaki Windows olaylarına ihtiyacı vardır: 4776, 4732, 4733, 4728, 4729, 4756, 4757, 7045. Bunlar ya da otomatik olarak ATA Lightweight Gateway tarafından okunabilir veya ATA Lightweight Gateway'in dağıtılmamış olması durumunda, bu ATA gateway'e iki yoldan biriyle ATA Gateway'i SIEM olaylarını dinleyecek şekilde yapılandırarak veya Windows olay yapılandırarak iletilebilir İletme.

> [!NOTE]
> Sunucu Çekirdeği kullanıyorsanız [wecutil](https://docs.microsoft.com/windows-server/administration/windows-commands/wecutil) oluşturun ve abonelikleri iletilen olaylar için uzak bilgisayarlardan yönetmek için kullanılabilir.

### <a name="wef-configuration-for-ata-gateways-with-port-mirroring"></a>Bağlantı noktası yansıtma ile ATA Gateway’ler için WEF yapılandırması

Bağlantı noktası etki alanı denetleyicilerinden ATA Gateway'e yansıtmayı yapılandırdıktan sonra Windows olay iletmeyi kaynak tarafından başlatılan yapılandırmasını kullanarak yapılandırmak için aşağıdaki yönergeleri kullanın. Windows Olay İletme’yi yapılandırmanın bir yolu budur. 

**1. Adım: Ağ hizmeti hesabını etki alanının Event Log Readers grubuna ekleyin.** 

Bu senaryoda, ATA Gateway etki alanının bir üyesi olduğunu varsayın.

1.  Active Directory Kullanıcıları ve Bilgisayarları'nı açın ve gidin **yerleşik** klasörü ve çift **Event Log Readers**. 
2.  **Üyeler**’i seçin.
3.  **Ağ Hizmeti** listede yoksa **Ekle**’ye tıklayın, **Seçilecek nesne adlarını girin** alanına **Ağ Hizmeti** yazın. Sonra, **Adları Denetle**’ye tıklayın ve **Tamam**’a çift tıklayın. 

Ekledikten sonra **ağ hizmeti** için **Event Log Readers** grubunda, değişikliğin etkili olması etki alanı denetleyicileri yeniden başlatın.

**2. Adım: Hedef Abonelik Yöneticisini yapılandır ayarını belirlemek için etki alanı denetleyicilerinde bir ilke oluşturun.** 
> [!Note] 
> Bu ayarlar için bir grup ilkesi oluşturabilir ve grup ilkesini ATA Gateway tarafından izlenen her etki alanı denetleyicisine uygulayabilirsiniz. Aşağıdaki adımlar etki alanı denetleyicisinin yerel ilkesini değiştirir.     

1.  Her etki alanı denetleyicisinde aşağıdaki komutu çalıştırın: *winrm quickconfig*
2.  Bir komut isteminde *gpedit.msc* yazın.
3.  **Bilgisayar Yapılandırması > Yönetim Şablonları > Windows Bileşenleri > Olay İletme**’yi genişletin

![Yerel ilke grubu düzenleyicisi resmi](media/wef%201%20local%20group%20policy%20editor.png)

4.  Çift **hedef abonelik yöneticisini Yapılandır**.
   
    1.  **Etkin**’i seçin.
    2.  Altında **seçenekleri**, tıklayın **Göster**.
    3.  Altında **SubscriptionManagers**, şu değeri girin ve tıklayın **Tamam**: *Server = http: / /<fqdnATAGateway>: 5985/wsman/SubscriptionManager/WEC, Refresh = 10* 
    
        *(Örneğin: Server =http://atagateway9.contoso.com:5985/wsman/SubscriptionManager/WEC, Yenile = 10)*
 
    ![Hedef aboneliği yapılandırma resmi](media/wef%202%20config%20target%20sub%20manager.png)
   
    5.  **Tamam**'ı tıklatın.
    6.  Yükseltilmiş bir komut isteminden şunu yazın: *gpupdate /force*. 

**3. Adım: ATA Gateway’de aşağıdaki adımları gerçekleştirin** 

1.  Yükseltilmiş bir komut istemi açın ve *wecutil qc* yazın
2.  **Olay Görüntüleyicisi**’ni açın. 
3.  Sağ **abonelikleri** seçip **aboneliği oluşturma**. 

    1.  Abonelik için bir ad ve açıklama girin. 
    2.  İçin **hedef günlük**, onaylayın **iletilen olaylar** seçilir. ATA’nın olayları okuması için hedef günlüğün **İletilen Olaylar** olması gerekir. 
    3.  **Kaynak bilgisayar tarafından başlatılan**’ı seçin ve **Bilgisayar Gruplarını Seç**’e tıklayın.
        1.  **Etki Alanı Bilgisayarı Ekle**’ye tıklayın.
        2.  Etki alanı denetleyicisinin adını **Seçilecek nesne adını girin** alanına girin. Sonra, **Adları Denetle**’ye ve **Tamam**’a tıklayın.  
          ![Olay Görüntüleyicisi resmi](media/wef3%20event%20viewer.png)  
        3.  **Tamam**'ı tıklatın.
     4. **Olayları Seç**’e tıklayın.

        1. **Günlüğe göre**’ye tıklayıp **Güvenlik**’i seçin.
        2. **Olay Kimliklerini Ekler/Dışlar** alanına olay numarasını yazın ve **Tamam**’a tıklayın. Örneğin, 4776 gibi aşağıdaki örnekte yazın.

        ![Sorgu filtresi resmi](media/wef%204%20query%20filter.png)

    5.  Oluşturulan aboneliğe sağ tıklayıp **çalışma zamanı durumu** durumu ile ilgili olup olmadığını görmek için. 
    6.  Birkaç dakika sonra, iletilmek üzere ayarladığınız olayların ATA Gateway’deki İletilen Olaylar kısmında görünüp görünmediğini kontrol edin.


Daha fazla bilgi için bkz: [olayları iletmek ve toplamak için bilgisayarları yapılandırma](https://technet.microsoft.com/library/cc748890)

## <a name="see-also"></a>Ayrıca Bkz.
- [ATA’yı yükleme](install-ata-step1.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
