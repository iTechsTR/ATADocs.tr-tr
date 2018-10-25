---
title: Azure Gelişmiş tehdit koruması Windows Olay iletme'yi yapılandırma | Microsoft Docs
description: Azure ATP ile Windows Olay iletme'yi yapılandırmaya yönelik seçeneklerinizi açıklar
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/07/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 3547519f-8d9c-40a9-8f0e-c7ba21081203
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 931ea6e4c122ad159e16450546d241c67249b321
ms.sourcegitcommit: 63ec9181f71edce6a950f5cc0d69428405436c48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49963344"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="configuring-windows-event-forwarding"></a>Windows Olay İletme’yi yapılandırma

> [!NOTE]
> Azure ATP algılayıcısını yerel olarak olayları olay iletmeyi yapılandırmaya gerek kalmadan otomatik olarak okur.


Azure ATP algılama yeteneklerini artırmak için aşağıdaki Windows olaylarına ihtiyacı vardır: 4776, 4732, 4733, 4728, 4729, 4756, 4757'yi ve 7045. Bunlar ya da otomatik olarak Azure ATP algılayıcı tarafından okunabilir veya Azure ATP algılayıcısını dağıtılmamış olması durumunda, bu iki yoldan biriyle Azure ATP tek başına algılayıcı Azure ATP tek başına algılayıcı SIEM olaylarını dinleyecek şekilde yapılandırarak veya configuri iletilebilir NG Windows Olay iletme'ı seçin.

> [!NOTE]
> Etki alanı denetleyicisi gerekli olayları yakalamak için düzgün yapılandırıldığından emin olun.

### <a name="wef-configuration-for-azure-atp-standalone-sensors-with-port-mirroring"></a>Bağlantı noktası yansıtma ile Azure ATP tek başına algılayıcı'nın için WEF yapılandırması

Azure ATP tek başına algılayıcı için etki alanı denetleyicilerinden bağlantı noktası yansıtmayı yapılandırdıktan sonra Windows olay iletmeyi kaynak tarafından başlatılan yapılandırmasını kullanarak yapılandırmak için aşağıdaki yönergeleri izleyin. Windows Olay İletme’yi yapılandırmanın bir yolu budur. 

**1. Adım: Ağ hizmeti hesabını etki alanının Event Log Readers grubuna ekleyin.** 

Bu senaryoda, Azure ATP tek başına algılayıcı etki alanının bir üyesi olduğunu varsayın.

1.  Active Directory Kullanıcıları ve Bilgisayarları'nı açın ve gidin **yerleşik** klasörü ve çift **Event Log Readers**. 
2.  **Üyeler**’i seçin.
3.  **Ağ Hizmeti** listede yoksa **Ekle**’ye tıklayın, **Seçilecek nesne adlarını girin** alanına **Ağ Hizmeti** yazın. Sonra, **Adları Denetle**’ye tıklayın ve **Tamam**’a çift tıklayın. 

Ekledikten sonra **ağ hizmeti** için **Event Log Readers** grubunda, değişikliğin etkili olması etki alanı denetleyicileri yeniden başlatın.

**2. Adım: Hedef Abonelik Yöneticisini yapılandır ayarını belirlemek için etki alanı denetleyicilerinde bir ilke oluşturun.** 
> [!Note] 
> Bu ayarlar için bir Grup İlkesi oluşturabilir ve Azure ATP tek başına algılayıcı tarafından izlenen her etki alanı denetleyicisinde Grup İlkesi uygulanır. Aşağıdaki adımlar etki alanı denetleyicisinin yerel ilkesini değiştirin.     

1.  Her etki alanı denetleyicisinde aşağıdaki komutu çalıştırın: *winrm quickconfig*
2.  Bir komut isteminde *gpedit.msc* yazın.
3.  **Bilgisayar Yapılandırması > Yönetim Şablonları > Windows Bileşenleri > Olay İletme**’yi genişletin

 ![Yerel ilke grubu düzenleyicisi resmi](media/wef%201%20local%20group%20policy%20editor.png)

4.  Çift **hedef abonelik yöneticisini Yapılandır**.
   
    1.  **Etkin**’i seçin.
    2.  Altında **seçenekleri**, tıklayın **Göster**.
    3.  Altında **SubscriptionManagers**, şu değeri girin ve tıklayın **Tamam**: * Server =`http://<fqdnATPSensor>:5985/wsman/SubscriptionManager/WEC,Refresh=10` * (örneğin: Server =`http://atpsensor9.contoso.com:5985/wsman/SubscriptionManager/WEC,Refresh=10`)
    
    ![Hedef aboneliği yapılandırma resmi](media/wef%202%20config%20target%20sub%20manager.png)
    
5.  **Tamam**'ı tıklatın.
6.  Yükseltilmiş bir komut isteminden şunu yazın: *gpupdate /force*. 

**3. adım: Azure ATP tek başına algılayıcı üzerinde aşağıdaki adımları gerçekleştirin.** 

1. Yükseltilmiş bir komut istemi açın ve *wecutil qc* yazın
2. **Olay Görüntüleyicisi**’ni açın. 
3. Sağ **abonelikleri** seçip **aboneliği oluşturma**. 
    
    1. Abonelik için bir ad ve açıklama girin. 
    2. İçin **hedef günlük**, onaylayın **iletilen olaylar** seçilir. Azure ATP'ın olayları okuması hedef günlüğün olmalıdır **iletilen olaylar**. 
    3. **Kaynak bilgisayar tarafından başlatılan**’ı seçin ve **Bilgisayar Gruplarını Seç**’e tıklayın.
        1. **Etki Alanı Bilgisayarı Ekle**’ye tıklayın.
        2. Etki alanı denetleyicisinin adını **Seçilecek nesne adını girin** alanına girin. Sonra, **Adları Denetle**’ye ve **Tamam**’a tıklayın. 
        3. **Tamam**'ı tıklatın.
        ![Olay Görüntüleyicisi resmi](media/wef3%20event%20viewer.png)     
    4. **Olayları Seç**’e tıklayın.
        1. **Günlüğe göre**’ye tıklayıp **Güvenlik**’i seçin.
        2. **Olay Kimliklerini Ekler/Dışlar** alanına olay numarasını yazın ve **Tamam**’a tıklayın. Örneğin, 4776 gibi aşağıdaki örnekte yazın:<br/>
        ![Sorgu filtresi resmi](media/wef-4-query-filter.png)
   5. Oluşturulan aboneliğe sağ tıklayıp **çalışma zamanı durumu** durumu ile ilgili olup olmadığını görmek için. 
   6. Birkaç dakika sonra iletilmek koymak olayları görmek için Azure ATP tek başına algılayıcı iletilen olaylar bazılarındaki denetleyin.


Daha fazla bilgi için bkz: [olayları iletmek ve toplamak için bilgisayarları yapılandırma](https://technet.microsoft.com/library/cc748890)

## <a name="see-also"></a>Ayrıca Bkz.

- [Azure ATP yükleyin](install-atp-step1.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
