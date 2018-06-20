---
title: Azure Gelişmiş tehdit koruması Windows Olay iletme özelliğini yapılandırma | Microsoft Docs
description: Windows Olay iletme ile Azure ATP yapılandırmaya yönelik seçeneklerinizi açıklar
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 02/21/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 3547519f-8d9c-40a9-8f0e-c7ba21081203
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: df06235de3a29051f9ffcd889bb95936ed9fc27d
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
ms.locfileid: "29446095"
---
*Uygulandığı öğe: Azure Advanced Threat Protection sürüm 1.9*



# <a name="configuring-windows-event-forwarding"></a>Windows Olay İletme’yi yapılandırma

> [!NOTE]
> Azure ATP algılayıcı yerel olarak olayları Olay iletme özelliğini yapılandırma gerek otomatik olarak okur.


Algılama yeteneklerini geliştirmek için aşağıdaki Windows olaylarını Azure ATP gerekir: 4776, 4732, 4733, 4728, 4729, 4756, 4757 ve 7045. Bu da otomatik olarak Azure ATP algılayıcı tarafından okunabilen veya Azure ATP algılayıcı dağıtılmaz durumunda bunu iki yoldan biriyle Azure ATP tek başına algılayıcı Azure ATP tek başına algılayıcı SIEM olaylarını dinleyecek şekilde yapılandırarak veya configuri iletilebilir NG Windows Olay iletme özelliğini kullanın.

> [!NOTE]
> Etki alanı denetleyicisi gerekli olaylarını yakalamak için düzgün yapılandırıldığından emin olun.

### <a name="wef-configuration-for-azure-atp-standalone-sensors-with-port-mirroring"></a>Bağlantı noktası yansıtma ile Azure ATP tek başına algılayıcının WEF yapılandırma

Etki alanı denetleyicilerinden Azure ATP tek başına algılayıcı için bağlantı noktası yansıtma yapılandırılmış sonra kaynak başlatılan Yapılandırması'nı kullanarak Windows Olay iletme özelliğini yapılandırmak için aşağıdaki yönergeleri izleyin. Windows Olay İletme’yi yapılandırmanın bir yolu budur. 

**1. Adım: Ağ hizmeti hesabını etki alanının Event Log Readers grubuna ekleyin.** 

Bu senaryoda, Azure ATP tek başına algılayıcı etki alanının bir üyesi olduğunu varsayın.

1.  Active Directory Kullanıcıları ve bilgisayarları açıp **yerleşik** klasörü ve çift **Event Log Readers**. 
2.  **Üyeler**’i seçin.
4.  **Ağ Hizmeti** listede yoksa **Ekle**’ye tıklayın, **Seçilecek nesne adlarını girin** alanına **Ağ Hizmeti** yazın. Sonra, **Adları Denetle**’ye tıklayın ve **Tamam**’a çift tıklayın. 

Ekledikten sonra **ağ hizmeti** için **Event Log Readers** grup, etki alanı denetleyicileri değişikliğin etkili olması yeniden başlatın.

**2. Adım: Hedef Abonelik Yöneticisini yapılandır ayarını belirlemek için etki alanı denetleyicilerinde bir ilke oluşturun.** 
> [!Note] 
> Bu ayarlar için bir grup ilkesi oluşturmak ve Azure ATP tek başına algılayıcı tarafından izlenen her etki alanı denetleyicisinde Grup İlkesi uygulanır. Aşağıdaki adımlar etki alanı denetleyicisinin yerel ilkeyi değiştirin.     

1.  Her etki alanı denetleyicisinde aşağıdaki komutu çalıştırın: *winrm quickconfig*
2.  Bir komut isteminde *gpedit.msc* yazın.
3.  **Bilgisayar Yapılandırması > Yönetim Şablonları > Windows Bileşenleri > Olay İletme**’yi genişletin

 ![Yerel ilke grubu düzenleyicisi resmi](media/wef 1 local group policy editor.png)

4.  Çift **Yapılandır hedef Abonelik Yöneticisi**.
   
    1.  **Etkin**’i seçin.
    2.  Altında **seçenekleri**, tıklatın **Göster**.
    3.  Altında **SubscriptionManagers**, şu değeri girin ve tıklayın **Tamam**: *Server = http: / /<fqdnATPSensor>: 5985/wsman/SubscriptionManager/WEC, yenileme = 10* () For example: sunucu http://atpsensor9.contoso.com:5985/wsman/SubscriptionManager/WEC, yenileme = = 10)
 
   ![Hedef aboneliği yapılandırma resmi](media/wef 2 config target sub manager.png)
   
    5.  **Tamam**'ı tıklatın.
    6.  Yükseltilmiş bir komut isteminden şunu yazın: *gpupdate /force*. 

**3. adım: Azure ATP tek başına algılayıcı üzerinde aşağıdaki adımları uygulayın** 

1.  Yükseltilmiş bir komut istemi açın ve *wecutil qc* yazın
2.  **Olay Görüntüleyicisi**’ni açın. 
3.  Sağ **abonelikleri** seçip **Abonelik Oluştur**. 

   1.   Abonelik için bir ad ve açıklama girin. 
   2.   İçin **hedef günlük**, onaylayın **iletilen olaylar** seçilir. Azure ATP'ın olayları okumak hedef günlük olmalıdır **iletilen olaylar**. 
   3.   **Kaynak bilgisayar tarafından başlatılan**’ı seçin ve **Bilgisayar Gruplarını Seç**’e tıklayın.
        1.  **Etki Alanı Bilgisayarı Ekle**’ye tıklayın.
        2.  Etki alanı denetleyicisinin adını **Seçilecek nesne adını girin** alanına girin. Sonra, **Adları Denetle**’ye ve **Tamam**’a tıklayın. 
       
        ![Olay Görüntüleyicisi resmi](media/wef3 event viewer.png)
   
        
        3.  **Tamam**'ı tıklatın.
   4.   **Olayları Seç**’e tıklayın.

        1. **Günlüğe göre**’ye tıklayıp **Güvenlik**’i seçin.
        2. **Olay Kimliklerini Ekler/Dışlar** alanına olay numarasını yazın ve **Tamam**’a tıklayın. Örneğin, 4776 gibi aşağıdaki örnekte yazın:

 ![Sorgu filtresi resmi](media/wef-4-query-filter.png)

   5.   Oluşturulan abonelik sağ tıklatıp **çalışma zamanı durumu** durumu herhangi bir sorun olup olmadığını görmek için. 
   6.   Birkaç dakika sonra iletilmesine koymak olayları denetleyin Azure ATP tek başına algılayıcı üzerindeki iletilen olaylar başlanan bir uyarıdır.


Daha fazla bilgi için bkz: [olayları iletmek ve toplamak için bilgisayarları yapılandırma](https://technet.microsoft.com/library/cc748890)

## <a name="see-also"></a>Ayrıca bkz:

- [Azure ATP yükleyin](install-atp-step1.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)