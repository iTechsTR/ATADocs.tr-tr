---
title: "Olay Koleksiyonunu Yapılandırma | Microsoft Advanced Threat Analytics"
description: "ATA’yla olay koleksiyonunu yapılandırmaya yönelik seçeneklerinizi açıklar"
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 3f0498f9-061d-40e6-ae07-98b8dcad9b20
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d6e7d7bef97bfc4ffde07959dd9256f0319d685f
ms.openlocfilehash: 17f30cbe478a868f3b6887bf48d8084934624191


---

# Olay Koleksiyonunu Yapılandırma
ATA, algılama yeteneklerini geliştirmek için Windows Olay günlüğü ID 4776’ya gereksinim duyar. Bu ATA Gateway’e iki yoldan biriyle, ATA Gateway’i SIEM olaylarını dinleyecek şekilde yapılandırarak veya [Windows Olay İletme’yi yapılandırarak](#configuring-windows-event-forwarding) iletilebilir.

## Olay koleksiyonu
Etki alanı denetleyicilerinden gelen ve giden ağ trafiğini toplamaya ve çözümlemeye ek olarak, ATA Windows olayı 4776’yı kullanarak ATA Karma Değeri Geçirme algılamasını daha da geliştirir. Bu SIEM sistemlerinizden alınabileceği gibi, etki alanı denetleyicinizden Windows Olay İletme’yi ayarlayarak da alınabilir. Toplanan olaylar ATA’ya etki alanı denetleyicisi ağ trafiği yoluyla sağlanmayan ek bilgiler sağlar.

### SIEM/Syslog
ATA’nın Syslog sunucusundan verileri kullanabilmesi için, aşağıdakileri yapmalısınız:

-   ATA Gateway sunucularınızdan birini SIEM/Syslog sunucusundan iletilen olayları dinleyecek ve kabul edecek şekilde yapılandırın.

-   SIEM/Syslog sunucunuzu belirli olayları ATA Gateway’e iletecek şekilde yapılandırın.

> [!IMPORTANT]
> -   Syslog verilerinin tümünü ATA Gateway’e iletmeyin.
> -   ATA, SIEM/Syslog sunucusundan UDP trafiğini destekler.

Belirli olayları başka bir sunucuya iletme işlemini yapılandırma hakkında bilgi edinmek için, SIEM/Syslog sunucunuzun ürün belgelerine bakın. 

### Windows olay iletme
SIEM/Syslog sunucusunu kullanmazsanız, Windows etki alanı denetleyicilerinizi Windows Olay Kimliği 4776’yı ATA tarafından toplanması ve çözümlenmesi için iletecek şekilde yapılandırabilirsiniz. Windows Olay Kimliği 4776, NTLM kimlik doğrulamalarıyla ilgili verileri sağlar.

## ATA Gateway’i SIEM olaylarını dinleyecek şekilde yapılandırma

1.  ATA Gateway yapılandırmasında **Syslog Dinleyicisi UDP**’yi etkinleştirin.

    Dinleyici IP Adresini aşağıdaki resimde açıklandığı gibi ayarlayın. Varsayılan bağlantı noktası 514'tür.

    ![Syslog dinleyicisi UDP’yi etkinleştirme görüntüsü](media/ATA-enable-siem-forward-events.png)

2.  SIEM veya Syslog sunucunuzu, Windows Olay Kimliği 4776’yı yukarıda seçilen IP adresine iletecek şekilde yapılandırın. SIEM sunucunuzu yapılandırma hakkında ek bilgi için, her SIEM sunucusuna özgü belirli biçimlendirme yönergeleriyle ilgili olarak SIEM sunucunuzun çevrimiçi yardımına veya teknik destek seçeneklerine bakın.

### SIEM desteği
ATA, aşağıdaki biçimlerde olan SIEM olaylarını destekler:

#### RSA Güvenlik Analizi
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

#### HP Arcsight
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

#### Splunk
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

#### QRadar
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

## Windows Olay İletme’yi yapılandırma
SIEM sunucunuz yoksa, etki alanı denetleyicilerinizi Windows Olay Kimliği 4776’yı doğrudan ATA Gateway’lerinizden birine iletecek şekilde yapılandırabilirsiniz.

1.  Yönetici ayrıcalıklarına sahip bir etki alanı hesabı kullanarak tüm etki alanı denetleyicilerinden ve ATA Gateway makinelerinde oturum açın.
2. Bağlandığınız ATA Gateway makinelerinin ve tüm etki alanı denetleyicilerinin aynı etki alanına katıldığından emin olun.
3.  Etki alanı denetleyicilerinin her birinde, yükseltilmiş komut istemine şunları yazın:
```
winrm quickconfig
```
4.  ATA Gateway’de, yükseltilmiş komut istemine şunları yazın:
```
wecutil qc
```
5.  Her etki alanı denetleyicisinde, **Active Directory Kullanıcıları ve Bilgisayarları**’nda **Builtin** klasörüne gidin ve **Event Log Readers** grubunu seçin.<br>
![wef_ad_eventlogreaders](media/wef_ad_eventlogreaders.png)<br>
Buna sağ tıklayın ve **Özellikler**’i seçin. **Üyeler** sekmesinde, her ATA Gateway için bilgisayar hesabını ekleyin.
![wef_ad event log reader popup](media/wef_ad-event-log-reader-popup.png)
6.  ATA Gateway’de Olay Görüntüleyicisi’ni açın, **Abonelikler**’e sağ tıklayın ve **Abonelik Oluştur**’u seçin.  

    a. **Abonelik türü ve kaynak bilgisayarlar**’ın altında **Bilgisayarları Seçin** öğesine tıklayın, etki alanı denetleyicilerini ekleyin ve bağlantıyı test edin.
    ![wef_subscription prop](media/wef_subscription-prop.png)

    b. **Toplanacak olaylar**’ın altında **Olay Seç**’e tıklayın. **Günlüğe göre** öğesini seçin ve ekranı aşağı kaydırarak **Güvenlik**’i seçin. Ardından, **Olay Kimliklerini Ekler/Çıkarır** alanına **4776** yazın.<br>
    ![wef_4776](media/wef_4776.png)

    c. **Kullanıcı hesabını değiştir veya gelişmiş ayarları yapılandır** alanında **Gelişmiş**’e tıklayın.
**Protokol** olarak **HTTP**’yi ve **Bağlantı Noktası** olarak **5985**’i ayarlayın.<br>
    ![wef_http](media/wef_http.png)

7.  [İsteğe bağlı] Daha kısa bir yoklama aralığı istiyorsanız, daha yüksek yoklama hızı için ATA Gateway’de abonelik sinyalini 5 saniyeye ayarlayın.
    wecutil ss <CollectionName>/cm:custom wecutil ss <CollectionName> /hi:5000

8. ATA Gateway yapılandırma sayfasında **Windows Olay İletme Koleksiyonu**’nu etkinleştirin.

> [!NOTE]
> Bu ayarı etkinleştirdiğinizde, ATA Gateway İletilen Olaylar günlüğünde etki alanı denetleyicilerinden kendisine iletilmiş olan Windows Olaylarını arar.

Daha fazla bilgi için bkz. [Olayları iletmek ve toplamak için bilgisayarları yapılandırma](https://technet.microsoft.com/library/cc748890).

## Ayrıca Bkz.
- [ATA’yı yükleme](install-ata.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)



<!--HONumber=Jun16_HO4-->


