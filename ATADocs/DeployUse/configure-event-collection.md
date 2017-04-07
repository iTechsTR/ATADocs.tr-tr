---
title: "Advanced Threat Analytics’te olay koleksiyonunu yapılandırma | Microsoft Docs"
description: "ATA’yla olay koleksiyonunu yapılandırmaya yönelik seçeneklerinizi açıklar"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 3f0498f9-061d-40e6-ae07-98b8dcad9b20
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: f807b428dfcc12a15b814106cc190f2a72fa4254
ms.sourcegitcommit: 49e892a82275efa5146998764e850959f20d3216
translationtype: HT
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.6 ve 1.7*



# <a name="configure-event-collection"></a>Olay Koleksiyonunu Yapılandırma
ATA, algılama yeteneklerini geliştirmek için Windows Olay günlüğü ID 4776’ya gereksinim duyar. Bu ATA Gateway’e iki yoldan biriyle, ATA Gateway’i SIEM olaylarını dinleyecek şekilde yapılandırarak veya [Windows Olay İletme’yi yapılandırarak](#configuring-windows-event-forwarding) iletilebilir.

## <a name="event-collection"></a>Olay koleksiyonu
Etki alanı denetleyicilerinden gelen ve giden ağ trafiğini toplamaya ve çözümlemeye ek olarak, ATA Windows olayı 4776’yı kullanarak ATA Karma Değeri Geçirme algılamasını daha da geliştirir. Bu, SIEM sistemlerinizden alınabileceği gibi etki alanı denetleyicinizden Windows Olay İletme’yi ayarlayarak da alınabilir. Toplanan olaylar ATA’ya etki alanı denetleyicisi ağ trafiği yoluyla sağlanmayan ek bilgiler sağlar.

### <a name="siemsyslog"></a>SIEM/Syslog
ATA’nın Syslog sunucusundan verileri kullanabilmesi için, aşağıdakileri yapmalısınız:

-   ATA Gateway sunucularınızı SIEM/Syslog sunucusundan iletilen olayları dinleyecek ve kabul edecek şekilde yapılandırın.
> [!NOTE]
> ATA yalnızca IPv4 dinler; IPv6 dinlemez. 
-   SIEM/Syslog sunucunuzu belirli olayları ATA Gateway’e iletecek şekilde yapılandırın.

> [!IMPORTANT]
> -   Syslog verilerinin tümünü ATA Gateway’e iletmeyin.
> -   ATA, SIEM/Syslog sunucusundan UDP trafiğini destekler.

Belirli olayları başka bir sunucuya iletme işlemini yapılandırma hakkında bilgi edinmek için, SIEM/Syslog sunucunuzun ürün belgelerine bakın. 

### <a name="windows-event-forwarding"></a>Windows olay iletme
SIEM/Syslog sunucusunu kullanmazsanız, Windows etki alanı denetleyicilerinizi Windows Olay Kimliği 4776’yı ATA tarafından toplanması ve çözümlenmesi için iletecek şekilde yapılandırabilirsiniz. Windows Olay Kimliği 4776, NTLM kimlik doğrulamalarıyla ilgili verileri sağlar.

## <a name="configuring-the-ata-gateway-to-listen-for-siem-events"></a>ATA Gateway’i SIEM olaylarını dinleyecek şekilde yapılandırma

1.  ATA yapılandırmasında, "Olaylar" sekmesi altında **Syslog**’u etkinleştirip **Kaydet**’e basın.

    ![Syslog dinleyicisi UDP’yi etkinleştirme görüntüsü](media/ATA-enable-siem-forward-events.png)

2.  SIEM veya Syslog sunucunuzu, Windows Olay Kimliği 4776’yı ATA Gateway’lerinden birinin IP adresine iletecek şekilde yapılandırın. SIEM sunucunuzu yapılandırma hakkında ek bilgi için, her SIEM sunucusuna özgü belirli biçimlendirme yönergeleriyle ilgili olarak SIEM sunucunuzun çevrimiçi yardımına veya teknik destek seçeneklerine bakın.

### <a name="siem-support"></a>SIEM desteği
ATA, aşağıdaki biçimlerde olan SIEM olaylarını destekler:  

#### <a name="rsa-security-analytics"></a>RSA Güvenlik Analizi
&lt;Syslog Üst Bilgisi&gt;RsaSA\n2015-May-19 09:07:09\n4776\nMicrosoft-Windows-Security-Auditing\nSecurity\XXXXX.subDomain.domain.org.il\nYYYYY$\nMMMMM \n0x0

-   Syslog üst bilgisi isteğe bağlıdır.

-   Tüm alanlar arasında “\n” karakter ayırıcısı gereklidir.

-   Alanlar, sırasıyla şöyledir:

    1.  RsaSA sabiti (gösterilmesi gerekir).

    2.  Gerçek olayın zaman damgası (SIEM’e ulaşma veya ATA’ya gönderilme zaman damgası olmadığından emin olun). Milisaniye hassaslığında olması tercih edilir ve çok önemlidir.

    3.  Windows olay kimliği

    4.  Windows olay sağlayıcısı adı

    5.  Windows olay günlüğü adı

    6.  Olayı alan bilgisayarın adı (bu örnekte DC)

    7.  Kimliği doğrulanan kullanıcının adı

    8.  Kaynak ana bilgisayar adı

    9. NTLM sonuç kodu

-   Bu değerlerin sırası önemlidir ve iletiye başka hiçbir şey eklenmemelidir.

#### <a name="hp-arcsight"></a>HP Arcsight
CEF:0|Microsoft|Microsoft Windows||Microsoft-Windows-Security-Auditing:4776|Etki alanı denetleyicisi bir hesabın kimlik bilgilerini doğrulamaya çalıştı.|Düşük| externalId=4776 cat=Security rt=1426218619000 shost=KKKKKK dhost=YYYYYY.subDomain.domain.com duser=XXXXXX cs2=Security cs3=Microsoft-Windows-Security-Auditing cs4=0x0 cs3Label=EventSource cs4Label=Reason or Error Code

-   Protokol tanımıyla uyumlu olmalıdır.

-   Syslog üstbilgisi yoktur.

-   Üst bilgi bölümü (dikey çubukla ayrılan bölüm) var olmalıdır (protokolde belirtildiği gibi).

-   _Extension_ bölümündeki anahtarlar olayda var olmalıdır:

    -   externalId = Windows olay kimliği

    -   rt = gerçek olayın zaman damgası (SIEM’e ulaşma veya bize gönderilme zaman damgası olmadığından emin olun). Milisaniye hassaslığında olması tercih edilir ve çok önemlidir.

    -   cat = Windows olay günlüğü adı

    -   shost = kaynak ana bilgisayar adı

    -   dhost = olayı alan bilgisayarın adı (bu örnekte DC)

    -   duser = kimliği doğrulanan kullanıcının adı

-   _Extension_ bölümünde sıra önemli değildir

-   Bu iki alan için bir özel key ve keyLable olmalıdır:

    -   “EventSource”

    -   “Reason or Error Code” = NTLM sonuç kodu

#### <a name="splunk"></a>Splunk
&lt;Syslog Üst Bilgisi&gt;\r\nEventCode=4776\r\nLogfile=Security\r\nSourceName=Microsoft-Windows-Security-Auditing\r\nTimeGenerated=20150310132717.784882-000\r\ComputerName=YYYYY\r\nMessage=

Bilgisayar bir hesabın kimlik bilgilerini doğrulamaya çalıştı.

Kimlik Doğrulama Paketi:              MICROSOFT_AUTHENTICATION_PACKAGE_V1_0

Oturum Açma Hesabı: Administrator

Kaynak İş İstasyonu:       SIEM

Hata Kodu:         0x0

-   Syslog üst bilgisi isteğe bağlıdır.

-   Tüm gerekli alanlar arasında "\r\n" karakter ayırıcısı vardır.

-   Alanlar, anahtar=değer biçimindedir.

-   Aşağıdaki anahtarlar var olmalı ve bunların değeri olmalıdır:

    -   EventCode = Windows olay kimliği

    -   Logfile = Windows olay günlüğü adı

    -   SourceName = Windows olay sağlayıcısı adı

    -   TimeGenerated = Gerçek olayın zaman damgası (SIEM’e ulaşma veya ATA’ya gönderilme zaman damgası olmadığından emin olun). Biçim, yyyyAAGGSSddss.FFFFFF ile eşleşmelidir; milisaniye hassaslığında olması tercih edilir ve çok önemlidir.

    -   ComputerName = kaynak ana bilgisayar adı

    -   Message = Windows olayından alınan özgün olay metni

-   Message Anahtarı ve değeri en sonda yer almalıdır.

-   Anahtar=değer çiftleri için sıra önemli değildir.

#### <a name="qradar"></a>QRadar
QRadar bir aracı üzerinden olay toplamayı sağlar. Veriler bir aracı kullanarak toplanıyorsa, saat biçimi mili saniye verisi olmadan toplanır. ATA mili saniye verisine ihtiyaç duyduğundan, QRadar’ın aracısız Windows olay toplamayı kullanacak şekilde ayarlanması gerekir. Daha fazla bilgi için bkz. [http://www-01.ibm.com/support/docview.wss?uid=swg21700170](http://www-01.ibm.com/support/docview.wss?uid=swg21700170 "QRadar: MSRPC Protokolünü kullanarak Aracısız Windows Olayları Koleksiyonu").

    <13>Feb 11 00:00:00 %IPADDRESS% AgentDevice=WindowsLog AgentLogFile=Security Source=Microsoft-Windows-Security-Auditing Computer=%FQDN% User= Domain= EventID=4776 EventIDCode=4776 EventType=8 EventCategory=14336 RecordNumber=1961417 TimeGenerated=1456144380009 TimeWritten=1456144380009 Message=The computer attempted to validate the credentials for an account. Authentication Package: MICROSOFT_AUTHENTICATION_PACKAGE_V1_0 Logon Account: Administrator Source Workstation: HOSTNAME Error Code: 0x0

Gerekli alanları şunlardır:

- Koleksiyon için aracı türü
- Windows olay günlüğü sağlayıcısı adı
- Windows olay günlüğü kaynağı
- Tam etki alanı adı
- Windows olay kimliği

TimeGenerated, gerçek olayın zaman damgasıdır (SIEM’e ulaşma veya ATA’ya gönderilme zaman damgası olmadığından emin olun). Biçim, yyyyAAGGSSddss.FFFFFF ile eşleşmelidir; mili saniye hassaslığında olması tercih edilir ve çok önemlidir.

Message, Windows olayından alınan özgün olay metnidir

key=value çiftleri arasında \t bulunduğundan emin olun.

>[!NOTE] 
> Windows olay koleksiyonu için WinCollect kullanımı desteklenmez.

## <a name="configuring-windows-event-forwarding"></a>Windows Olay İletme’yi yapılandırma

### <a name="wef-configuration-for-ata-gateways-with-port-mirroring"></a>Bağlantı noktası yansıtma ile ATA Gateway’ler için WEF yapılandırması

Etki alanı denetleyicilerinden ATA Gateway’e bağlantı noktası yansıtmayı yapılandırdıktan sonra, Windows Olay iletmeyi Kaynak Tarafından Başlatılan yapılandırmasını kullanarak yapılandırmak için aşağıdaki yönergeleri uygulayın. Windows Olay İletme’yi yapılandırmanın bir yolu budur. 

**1. Adım: Ağ hizmeti hesabını etki alanının Event Log Readers grubuna ekleyin.** 

Bu senaryoda ATA Gateway’in etki alanı üyesi olduğunu varsayıyoruz.

1.    Active Directory Kullanıcıları ve Bilgisayarları’nı açın, **Yerleşik** klasörüne gidin ve **Event Log Readers**’a çift tıklayın. 
2.    **Üyeler**’i seçin.
4.    **Ağ Hizmeti** listede yoksa **Ekle**’ye tıklayın, **Seçilecek nesne adlarını girin** alanına **Ağ Hizmeti** yazın. Sonra, **Adları Denetle**’ye tıklayın ve **Tamam**’a çift tıklayın. 

**Ağ Hizmeti**’ni **Event Log Readers** grubuna kaydettikten sonra, değişikliklerin uygulanması için etki alanı denetleyicilerini yeniden başlatmanız gerekir.

**2. Adım: Hedef Abonelik Yöneticisini yapılandır ayarını belirlemek için etki alanı denetleyicilerinde bir ilke oluşturun.** 
> [!Note] 
> Bu ayarlar için bir grup ilkesi oluşturabilir ve grup ilkesini ATA Gateway tarafından izlenen her etki alanı denetleyicisine uygulayabilirsiniz. Aşağıdaki adımlar etki alanı denetleyicisinin yerel ilkesini değiştirir.     

1.    Her etki alanı denetleyicisinde aşağıdaki komutu çalıştırın: *winrm quickconfig*
2.  Bir komut isteminde *gpedit.msc* yazın.
3.    **Bilgisayar Yapılandırması > Yönetim Şablonları > Windows Bileşenleri > Olay İletme**’yi genişletin

 ![Yerel ilke grubu düzenleyicisi resmi](media/wef 1 local group policy editor.png)

4.    **Hedef Abonelik Yöneticisini yapılandır**’a çift tıklayın.
   
    1.    **Etkin**’i seçin.
    2.    **Seçenekler** altında **Göster**’e tıklayın.
    3.    **SubscriptionManagers** altında şu değeri girin ve **Tamam**’a tıklayın: *Server=http://<fqdnATAGateway>:5985/wsman/SubscriptionManager/WEC,Refresh=10* (Örneğin: Server=http://atagateway9.contoso.com:5985/wsman/SubscriptionManager/WEC,Refresh=10)
 
   ![Hedef aboneliği yapılandırma resmi](media/wef 2 config target sub manager.png)
   
    5.    **Tamam**’a tıklayın.
    6.    Yükseltilmiş bir komut isteminden şunu yazın: *gpupdate /force*. 

**3. Adım: ATA Gateway’de aşağıdaki adımları gerçekleştirin** 

1.    Yükseltilmiş bir komut istemi açın ve *wecutil qc* yazın
2.    **Olay Görüntüleyicisi**’ni açın. 
3.    **Abonelikler**’e sağ tıklayın ve **Abonelik Oluştur**’u seçin. 

   1.    Abonelik için bir ad ve açıklama girin. 
   2.    **Hedef Günlük** için **İletilen Olaylar**’ın seçili olduğunu doğrulayın. ATA’nın olayları okuması için hedef günlüğün **İletilen Olaylar** olması gerekir. 
   3.    **Kaynak bilgisayar tarafından başlatılan**’ı seçin ve **Bilgisayar Gruplarını Seç**’e tıklayın.
        1.    **Etki Alanı Bilgisayarı Ekle**’ye tıklayın.
        2.    Etki alanı denetleyicisinin adını **Seçilecek nesne adını girin** alanına girin. Sonra, **Adları Denetle**’ye ve **Tamam**’a tıklayın. 
       
        ![Olay Görüntüleyicisi resmi](media/wef3 event viewer.png)
   
        
        3.    **Tamam**’a tıklayın.
   4.    **Olayları Seç**’e tıklayın.

        1. **Günlüğe göre**’ye tıklayıp **Güvenlik**’i seçin.
        2. **Olay Kimliklerini Ekler/Dışlar** alanına **4776** yazın ve **Tamam**’a tıklayın. 

 ![Sorgu filtresi resmi](media/wef 4 query filter.png)

   5.    Oluşturulan aboneliğe sağ tıklayın ve durumla ilgili herhangi bir sorun olup olmadığını görmek için **Çalışma Zamanı Durumu**’nu seçin. 
   6.    Birkaç dakika sonra, olay 4776’nın ATA Gateway’deki İletilen Olaylar kısmında görünüp görünmediğine bakın.


### <a name="wef-configuration-for-the-ata-lightweight-gateway"></a>ATA Lightweight Gateway için WEF yapılandırması
ATA Lightweight Gateway’i etki alanı denetleyicilerinize yüklerken, etki alanı denetleyicilerinizi, olayları kendilerine iletecek şekilde ayarlayabilirsiniz. ATA Lightweight Gateway kullanırken Windows Olay İletme’yi yapılandırmak için aşağıdaki adımları uygulayın. Windows Olay İletme’yi yapılandırmanın bir yolu budur.  

**1. Adım: Ağ hizmeti hesabını etki alanının Event Log Readers grubuna ekleyin** 

1.    Active Directory Kullanıcıları ve Bilgisayarları’nı açın, **Yerleşik** klasörüne gidin ve **Event Log Readers**’a çift tıklayın. 
2.    **Üyeler**’i seçin.
3.    **Ağ Hizmeti** listede yoksa **Ekle**’ye tıklayın ve **Seçilecek nesne adlarını girin** alanına **Ağ Hizmeti** yazın. Sonra, **Adları Denetle**’ye tıklayın ve **Tamam**’a çift tıklayın. 

**2. Adım: ATA Lightweight Gateway yüklendikten sonra etki alanı denetleyicisinde aşağıdaki adımları gerçekleştirin** 

1.    Yükseltilmiş bir komut istemi açın ve *winrm quickconfig* ve *wecutil qc* yazın 
2.    **Olay Görüntüleyicisi**’ni açın. 
3.    **Abonelikler**’e sağ tıklayın ve **Abonelik Oluştur**’u seçin. 

   1.    Abonelik için bir ad ve açıklama girin. 
   2.    **Hedef Günlük** için **İletilen Olaylar**’ın seçili olduğunu doğrulayın. ATA’nın olayları okuması için hedef günlüğün İletilen Olaylar olması gerekir.

        1.    **Toplayıcı tarafından başlatılan**’ı seçin ve **Bilgisayarları Seç**’e tıklayın. Ardından **Etki Alanı Bilgisayarı Ekle**’ye tıklayın.
        2.    **Seçilecek nesne adını girin** alanına etki alanı denetleyicisinin adını girin. Sonra, **Adları Denetle**’ye ve **Tamam**’a tıklayın.

            ![Abonelik özellikleri resmi](media/wef 5 sub properties computers.png)

        3.    **Tamam**’a tıklayın.
   3.    **Olayları Seç**’e tıklayın.

        1.    **Günlüğe göre**’ye tıklayıp **Güvenlik**’i seçin.
        2.    **Olay Kimliklerini Ekler/Dışlar** alanına *4776* yazın ve **Tamam**’a tıklayın. 

![Sorgu filtresi resmi](media/wef 4 query filter.png)


  4.    Oluşturulan aboneliğe sağ tıklayın ve durumla ilgili herhangi bir sorun olup olmadığını görmek için **Çalışma Zamanı Durumu**’nu seçin. 

> [!Note] 
> Ayarın etkin hale gelmesi için etki alanı denetleyicisini yeniden başlatmanız gerekebilir. 

Birkaç dakika sonra, olay 4776’nın ATA Gateway’deki İletilen Olaylar kısmında görünüp görünmediğine bakın.



Daha fazla bilgi için bkz. [Olayları iletmek ve toplamak için bilgisayarları yapılandırma](https://technet.microsoft.com/library/cc748890).

## <a name="see-also"></a>Ayrıca bkz.
- [ATA’yı yükleme](install-ata-step1.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
