---
title: "Advanced Threat Analytics’te Windows Olay İletme’yi Yapılandırma | Microsoft Docs"
description: "ATA ile Windows Olay İletme’yi yapılandırmaya yönelik seçeneklerinizi açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/2/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 3f0498f9-061d-40e6-ae07-98b8dcad9b20
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 6469f602d2da833e96bba72003aad3fe2b67eb48
ms.sourcegitcommit: fa50f37b134d7579d7c310852dff60e5f1996eaa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# <a name="configuring-windows-event-forwarding"></a>Windows Olay İletme’yi yapılandırma

Algılama yeteneklerini artırmak için ATA aşağıdaki Windows olaylarına ihtiyaç duymaktadır: 4776, 4732, 4733, 4728, 4729, 4756, 4757. Bunlar, ATA Lightweight Gateway tarafından otomatik olarak okunabilir veya ATA Lightweight Gateway’in dağıtılmamış olduğu durumlarda şu iki yöntemden biriyle ATA Gateway’e iletilebilir: ATA Gateway’i SIEM olaylarını dinleyecek şekilde yapılandırarak ya da [Windows Olay İletme’yi yapılandırarak](#configuring-windows-event-forwarding).

> [!NOTE]
> ATA 1.8 ve üzeri sürümlerde artık ATA Lightweight Gateway’ler için olay koleksiyonu yapılandırması gerekli değildir. ATA Lightweight Gateway artık olay iletmeyi yapılandırmaya gerek kalmadan olayları yerel olarak okuyabilir.

### <a name="wef-configuration-for-ata-gateways-with-port-mirroring"></a>Bağlantı noktası yansıtma ile ATA Gateway’ler için WEF yapılandırması

Etki alanı denetleyicilerinden ATA Gateway’e bağlantı noktası yansıtmayı yapılandırdıktan sonra, Windows Olay iletmeyi Kaynak Tarafından Başlatılan yapılandırmasını kullanarak yapılandırmak için aşağıdaki yönergeleri uygulayın. Windows Olay İletme’yi yapılandırmanın bir yolu budur. 

**1. Adım: Ağ hizmeti hesabını etki alanının Event Log Readers grubuna ekleyin.** 

Bu senaryoda ATA Gateway’in etki alanı üyesi olduğunu varsayıyoruz.

1.  Active Directory Kullanıcıları ve Bilgisayarları’nı açın, **Yerleşik** klasörüne gidin ve **Event Log Readers**’a çift tıklayın. 
2.  **Üyeler**’i seçin.
4.  **Ağ Hizmeti** listede yoksa **Ekle**’ye tıklayın, **Seçilecek nesne adlarını girin** alanına **Ağ Hizmeti** yazın. Sonra, **Adları Denetle**’ye tıklayın ve **Tamam**’a çift tıklayın. 

**Ağ Hizmeti**’ni **Event Log Readers** grubuna kaydettikten sonra, değişikliklerin uygulanması için etki alanı denetleyicilerini yeniden başlatmanız gerekir.

**2. Adım: Hedef Abonelik Yöneticisini yapılandır ayarını belirlemek için etki alanı denetleyicilerinde bir ilke oluşturun.** 
> [!Note] 
> Bu ayarlar için bir grup ilkesi oluşturabilir ve grup ilkesini ATA Gateway tarafından izlenen her etki alanı denetleyicisine uygulayabilirsiniz. Aşağıdaki adımlar etki alanı denetleyicisinin yerel ilkesini değiştirir.     

1.  Her etki alanı denetleyicisinde aşağıdaki komutu çalıştırın: *winrm quickconfig*
2.  Bir komut isteminde *gpedit.msc* yazın.
3.  **Bilgisayar Yapılandırması > Yönetim Şablonları > Windows Bileşenleri > Olay İletme**’yi genişletin

 ![Yerel ilke grubu düzenleyicisi resmi](media/wef 1 local group policy editor.png)

4.  **Hedef Abonelik Yöneticisini yapılandır**’a çift tıklayın.
   
    1.  **Etkin**’i seçin.
    2.  **Seçenekler** altında **Göster**’e tıklayın.
    3.  **SubscriptionManagers** altında şu değeri girin ve **Tamam**’a tıklayın:  *Server=http://<fqdnATAGateway>:5985/wsman/SubscriptionManager/WEC,Refresh=10* (Örneğin: Server=http://atagateway9.contoso.com:5985/wsman/SubscriptionManager/WEC,Refresh=10)
 
   ![Hedef aboneliği yapılandırma resmi](media/wef 2 config target sub manager.png)
   
    5.  **Tamam**’a tıklayın.
    6.  Yükseltilmiş bir komut isteminden şunu yazın: *gpupdate /force*. 

**3. Adım: ATA Gateway’de aşağıdaki adımları gerçekleştirin** 

1.  Yükseltilmiş bir komut istemi açın ve *wecutil qc* yazın
2.  **Olay Görüntüleyicisi**’ni açın. 
3.  **Abonelikler**’e sağ tıklayın ve **Abonelik Oluştur**’u seçin. 

   1.   Abonelik için bir ad ve açıklama girin. 
   2.   **Hedef Günlük** için **İletilen Olaylar**’ın seçili olduğunu doğrulayın. ATA’nın olayları okuması için hedef günlüğün **İletilen Olaylar** olması gerekir. 
   3.   **Kaynak bilgisayar tarafından başlatılan**’ı seçin ve **Bilgisayar Gruplarını Seç**’e tıklayın.
        1.  **Etki Alanı Bilgisayarı Ekle**’ye tıklayın.
        2.  Etki alanı denetleyicisinin adını **Seçilecek nesne adını girin** alanına girin. Sonra, **Adları Denetle**’ye ve **Tamam**’a tıklayın. 
       
        ![Olay Görüntüleyicisi resmi](media/wef3 event viewer.png)
   
        
        3.  **Tamam**’a tıklayın.
   4.   **Olayları Seç**’e tıklayın.

        1. **Günlüğe göre**’ye tıklayıp **Güvenlik**’i seçin.
        2. **Olay Kimliklerini Ekler/Dışlar** alanına olay numarasını yazın ve **Tamam**’a tıklayın. 

 ![Sorgu filtresi resmi](media/wef 4 query filter.png)

   5.   Oluşturulan aboneliğe sağ tıklayın ve durumla ilgili herhangi bir sorun olup olmadığını görmek için **Çalışma Zamanı Durumu**’nu seçin. 
   6.   Birkaç dakika sonra, iletilmek üzere ayarladığınız olayların ATA Gateway’deki İletilen Olaylar kısmında görünüp görünmediğini kontrol edin.


Daha fazla bilgi için bkz. [Olayları iletmek ve toplamak için bilgisayarları yapılandırma](https://technet.microsoft.com/library/cc748890).

## <a name="see-also"></a>Ayrıca bkz.
- [ATA’yı yükleme](install-ata-step1.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
