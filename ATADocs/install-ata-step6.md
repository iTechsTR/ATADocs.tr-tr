---
title: Advanced Threat Analytics’i Yükleme - 6. Adım | Microsoft Docs
description: ATA yüklemesinin bu adımında veri kaynaklarını yapılandıracaksınız.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 8980e724-06a6-40b0-8477-27d4cc29fd2b
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 6361cf277d1b27ab6792e4780827377835c9abd3
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
ms.locfileid: "30010382"
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*



# <a name="install-ata---step-6"></a>ATA’yı Yükleme - 6. Adım

>[!div class="step-by-step"]
[«5. Adım](install-ata-step5.md)
[7. Adım»](vpn-integration-install-step.md)

## <a name="step-6-configure-event-collection"></a>6. Adım. Olay koleksiyonunu yapılandırma
### <a name="configure-event-collection"></a>Olay Koleksiyonunu Yapılandırma
Algılama yeteneklerini geliştirmek için aşağıdaki Windows olaylarını ATA'ya gerekir: 4776, 4732, 4733, 4728, 4729, 4756, 4757 ve 7045. Bunlar, ATA Lightweight Gateway tarafından otomatik olarak okunabilir veya ATA Lightweight Gateway’in dağıtılmamış olduğu durumlarda şu iki yöntemden biriyle ATA Gateway’e iletilebilir: ATA Gateway’i SIEM olaylarını dinleyecek şekilde yapılandırarak ya da [Windows Olay İletme’yi yapılandırarak](configure-event-collection.md). 

> [!NOTE]
> ATA 1.8 ve üzeri sürümlerde artık ATA Lightweight Gateway’ler için olay koleksiyonu yapılandırması gerekli değildir. ATA Lightweight Gateway artık olay iletmeyi yapılandırmaya gerek kalmadan olayları yerel olarak okuyabilir.

Etki alanı denetleyicilerine gelen ve denetleyicilerden giden ağ trafiğini toplamaya ve çözümlemeye ek olarak ATA, Windows olaylarını kullanarak algılamaları geliştirebilir. Olay 4776 çeşitli algılama ve olayları 4732, 4733, 4728, 4729, 4756 ve hassas grubu değişiklikleri geliştirerek algılanması için 4757 geliştirir NTLM kullanır. Bu, SIEM sistemlerinizden alınabileceği gibi etki alanı denetleyicinizden Windows Olay İletme’yi ayarlayarak da alınabilir. Toplanan olaylar ATA’ya etki alanı denetleyicisi ağ trafiği yoluyla sağlanmayan ek bilgiler sağlar.

#### <a name="siemsyslog"></a>SIEM/Syslog
ATA Syslog sunucusundan verileri kullanamayabilir aşağıdaki adımlar gerçekleştirmeniz gerekir:

-   ATA Gateway sunucularınızı SIEM/Syslog sunucusundan iletilen olayları dinleyecek ve kabul edecek şekilde yapılandırın.
> [!NOTE]
> ATA yalnızca IPv4 dinler; IPv6 dinlemez. 
-   SIEM/Syslog sunucunuzu belirli olayları ATA Gateway’e iletecek şekilde yapılandırın.

> [!IMPORTANT]
> -   Syslog verilerinin tümünü ATA Gateway’e iletmeyin.
> -   ATA, SIEM/Syslog sunucusundan UDP trafiğini destekler.

Belirli olayları başka bir sunucuya iletme işlemini yapılandırma hakkında bilgi edinmek için, SIEM/Syslog sunucunuzun ürün belgelerine bakın. 

> [!NOTE]
>SIEM/Syslog sunucusunu kullanmazsanız, Windows etki alanı denetleyicilerinizi Windows Olay Kimliği 4776’yı ATA tarafından toplanması ve çözümlenmesi için iletecek şekilde yapılandırabilirsiniz. Windows Olay Kimliği 4776, NTLM kimlik doğrulamalarıyla ilgili verileri sağlar.

#### <a name="configuring-the-ata-gateway-to-listen-for-siem-events"></a>ATA Gateway’i SIEM olaylarını dinleyecek şekilde yapılandırma

1.  ATA Yapılandırması’nda **Veri kaynakları** altında **SIEM**’e tıklayın, **Syslog**’u açın ve **Kaydet**’i seçin.

    ![Syslog dinleyicisi UDP’yi etkinleştirme görüntüsü](media/ATA-enable-siem-forward-events.png)

2.  SIEM veya Syslog sunucunuzu, Windows Olay Kimliği 4776’yı ATA Gateway’lerinden birinin IP adresine iletecek şekilde yapılandırın. SIEM çevrimiçi yardımına veya teknik destek seçenekleri için her SIEM sunucusuna özgü belirli biçimlendirme yönergeleriyle SIEM sunucunuzu yapılandırma hakkında ek bilgi için bkz.

ATA, aşağıdaki biçimlerde olan SIEM olaylarını destekler:  

#### <a name="rsa-security-analytics"></a>RSA Güvenlik Analizi
&lt;Syslog Üst Bilgisi&gt;RsaSA\n2015-May-19 09:07:09\n4776\nMicrosoft-Windows-Security-Auditing\nSecurity\XXXXX.subDomain.domain.org.il\nYYYYY$\nMMMMM \n0x0

-   Syslog üst bilgisi isteğe bağlıdır.

-   Tüm alanlar arasında “\n” karakter ayırıcısı gereklidir.

-   Alanlar, sırasıyla şöyledir:

    1.  RsaSA sabiti (gösterilmesi gerekir).

    2.  Gerçek olayın zaman damgası (SIEM’e ulaşma veya ATA’ya gönderilme zaman damgası olmadığından emin olun). Tercihen milisaniye hassaslığında bu önemlidir.

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

    -   RT = gerçek olayın zaman damgası (sıem'e ulaşma veya ATA'ya gönderilme zaman damgası olmadığından emin olun). Tercihen milisaniye hassaslığında bu önemlidir.

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

-   Aşağıdaki anahtarlar var ve bir değere sahip olması gerekir:

    -   EventCode = Windows olay kimliği

    -   Logfile = Windows olay günlüğü adı

    -   SourceName = Windows olay sağlayıcısı adı

    -   TimeGenerated = Gerçek olayın zaman damgası (SIEM’e ulaşma veya ATA’ya gönderilme zaman damgası olmadığından emin olun). Biçim, yyyyaaggssddss.ffffff milisaniye hassaslığında, bu önemlidir eşleşmelidir.

    -   ComputerName = kaynak ana bilgisayar adı

    -   Message = Windows olayından alınan özgün olay metni

-   Message Anahtarı ve değeri en sonda yer almalıdır.

-   Anahtar=değer çiftleri için sıra önemli değildir.

#### <a name="qradar"></a>QRadar
QRadar bir aracı üzerinden olay toplamayı sağlar. Veriler bir aracı kullanarak toplanıyorsa, saat biçimi mili saniye verisi olmadan toplanır. ATA mili saniye verisine ihtiyaç duyduğundan, QRadar’ın aracısız Windows olay toplamayı kullanacak şekilde ayarlanması gerekir. Daha fazla bilgi için bkz: [ http://www-01.ibm.com/support/docview.wss?uid=swg21700170 ] (http://www-01.ibm.com/support/docview.wss?uid=swg21700170 "QRadar: MSRPC protokolünü kullanarak aracısız Windows olayları koleksiyonu").

    <13>Feb 11 00:00:00 %IPADDRESS% AgentDevice=WindowsLog AgentLogFile=Security Source=Microsoft-Windows-Security-Auditing Computer=%FQDN% User= Domain= EventID=4776 EventIDCode=4776 EventType=8 EventCategory=14336 RecordNumber=1961417 TimeGenerated=1456144380009 TimeWritten=1456144380009 Message=The computer attempted to validate the credentials for an account. Authentication Package: MICROSOFT_AUTHENTICATION_PACKAGE_V1_0 Logon Account: Administrator Source Workstation: HOSTNAME Error Code: 0x0

Gerekli alanları şunlardır:

- Koleksiyon için aracı türü
- Windows olay günlüğü sağlayıcısı adı
- Windows olay günlüğü kaynağı
- Tam etki alanı adı
- Windows olay kimliği

TimeGenerated, gerçek olayın zaman damgasıdır (SIEM’e ulaşma veya ATA’ya gönderilme zaman damgası olmadığından emin olun). Biçim, yyyyaaggssddss.ffffff milisaniye hassaslığında, bu önemlidir eşleşmelidir.

Message, Windows olayından alınan özgün olay metnidir

key=value çiftleri arasında \t bulunduğundan emin olun.

>[!NOTE] 
> Windows olay koleksiyonu için WinCollect kullanımı desteklenmez.



>[!div class="step-by-step"]
[«5. Adım](install-ata-step5.md)
[7. Adım»](vpn-integration-install-step.md)



## <a name="related-videos"></a>İlgili videolar
- [ATA dağıtımına genel bakış](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)
- [ATA Gateway türü sağ seçme](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)


## <a name="see-also"></a>Ayrıca bkz:
- [ATA POC Dağıtım Kılavuzu](http://aka.ms/atapoc)
- [ATA boyutlandırma aracı](http://aka.ms/atasizingtool)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)

