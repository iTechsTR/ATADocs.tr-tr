---
title: Azure Gelişmiş tehdit Koruması'nı yükleme | Microsoft Docs
description: ATP yükleme Bu adımda, veri kaynaklarını yapılandıracaksınız.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/15/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 88692d1a-45a3-4d54-a549-4b5bba6c037b
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 8f52a8e5851cee9fc0ff15d97cd39e98695f9a83
ms.sourcegitcommit: 121c49d559e71741136db1626455b065e8624ff9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2018
ms.locfileid: "41734720"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="configure-event-collection"></a>Olay koleksiyonunu yapılandırma

Azure ATP algılama yeteneklerini artırmak için aşağıdaki Windows olaylarına ihtiyacı vardır: 4776, 4732, 4733, 4728, 4729, 4756, 4757'yi ve 7045. Bunlar ya da otomatik olarak Azure ATP algılayıcı tarafından okunabilir veya Azure ATP algılayıcısını dağıtılmamış olması durumunda, bu iki yoldan biriyle Azure ATP tek başına algılayıcı Azure ATP tek başına algılayıcı SIEM olaylarını dinleyecek şekilde yapılandırarak veya iletilebilir[Windows Olay iletme özelliğini yapılandırma](configure-event-forwarding.md).

> [!NOTE]
> Etki alanı denetleyicilerinde gerekli olayları kaydetmek için düzgün yapılandırıldığından emin olmak için olay koleksiyonu yapılandırmadan önce betik denetim ATA çalıştırmak önemlidir. 

Azure ATP toplama ve analiz etme ve ağ trafiğini yanı sıra etki alanı denetleyicilerinden Windows olaylarını algılamaları geliştirebilir kullanabilirsiniz. Çeşitli algılamalar ve olay 4732, 4733, 4728, 4729, 4756, 4757'yi ve hizmet oluşturma ve gizli Grup değişikliklerini algılamayı için 7045 geliştiren NTLM için olay 4776'yı kullanır. Bu, SIEM sistemlerinizden alınabileceği gibi etki alanı denetleyicinizden Windows Olay İletme’yi ayarlayarak da alınabilir. Toplanan olaylar, etki alanı denetleyicisi ağ trafiğinin kullanılabilir olmayan ek bilgilerle Azure ATP sağlar.

## <a name="siemsyslog"></a>SIEM/Syslog
Azure ATP'ın bir Syslog sunucusundan verileri kullanabilmesi için almak aşağıdaki adımları tamamlamanız gerekir:

-   Azure ATP algılayıcısı sunucularınızı dinlemek ve SIEM/Syslog sunucusundan iletilen olayları kabul edecek şekilde yapılandırın.

 > [!NOTE]
 > Azure ATP yalnızca IPv4 ve IPv6 dinlemez dinler. 

-   SIEM/Syslog sunucunuzu belirli olayları Azure ATP algılayıcısını iletecek şekilde yapılandırın.

> [!IMPORTANT]
> -   Azure ATP algılayıcısını tüm Syslog verileri iletmeyin.
> -   Azure ATP SIEM/Syslog sunucusundan UDP trafiğini destekler.

Belirli olayları başka bir sunucuya iletme işlemini yapılandırma hakkında bilgi edinmek için, SIEM/Syslog sunucunuzun ürün belgelerine bakın. 

> [!NOTE]
>SIEM/Syslog sunucusunu kullanmazsanız, Windows etki alanı denetleyicilerinizi toplanacağı ve ATP tarafından analiz için gerekli tüm olayları iletecek şekilde yapılandırabilirsiniz.

## <a name="configuring-the-azure-atp-sensor-to-listen-for-siem-events"></a>Azure ATP algılayıcısını SIEM olaylarını dinleyecek şekilde yapılandırma

1.  Azure ATP yapılandırma altında **veri kaynakları** tıklayın **SIEM** ve açma **Syslog** tıklatıp **Kaydet**.

    ![Syslog dinleyicisi UDP’yi etkinleştirme görüntüsü](media/atp-siem-config.png)

2.  SIEM veya Syslog sunucunuzu gerekli tüm olayları Azure ATP algılayıcı birinin IP adresine iletecek şekilde yapılandırın. SIEM çevrimiçi yardımına veya teknik destek seçenekleri için her SIEM sunucusuna özgü belirli biçimlendirme yönergeleriyle SIEM sunucunuzu yapılandırma hakkında ek bilgi için bkz.

Azure ATP SIEM olaylarını aşağıdaki biçimlerde destekler:  

## <a name="rsa-security-analytics"></a>RSA Güvenlik Analizi
&lt;Syslog Üst Bilgisi&gt;RsaSA\n2015-May-19 09:07:09\n4776\nMicrosoft-Windows-Security-Auditing\nSecurity\XXXXX.subDomain.domain.org.il\nYYYYY$\nMMMMM \n0x0

-   Syslog üst bilgisi isteğe bağlıdır.

-   Tüm alanlar arasında “\n” karakter ayırıcısı gereklidir.

-   Alanlar, sırasıyla şöyledir:

    1.  RsaSA sabiti (gösterilmesi gerekir).

    2.  Gerçek olayın zaman damgası (sıem'e ulaşma veya ATP'ye gönderilme zaman damgası olmadığından emin olun). Tercihen milisaniye hassaslığında bu önemlidir.

    3.  Windows olay kimliği

    4.  Windows olay sağlayıcısı adı

    5.  Windows olay günlüğü adı

    6.  Olayı alan bilgisayarın adı (bu örnekte DC)

    7.  Kimliği doğrulanan kullanıcının adı

    8.  Kaynak ana bilgisayar adı

    9. NTLM sonuç kodu

-   Bu değerlerin sırası önemlidir ve iletiye başka hiçbir şey eklenmemelidir.

## <a name="hp-arcsight"></a>HP Arcsight
CEF:0|Microsoft|Microsoft Windows||Microsoft-Windows-Security-Auditing:4776|Etki alanı denetleyicisi bir hesabın kimlik bilgilerini doğrulamaya çalıştı.|Düşük| externalId=4776 cat=Security rt=1426218619000 shost=KKKKKK dhost=YYYYYY.subDomain.domain.com duser=XXXXXX cs2=Security cs3=Microsoft-Windows-Security-Auditing cs4=0x0 cs3Label=EventSource cs4Label=Reason or Error Code

-   Protokol tanımıyla uyumlu olmalıdır.

-   Syslog üstbilgisi yoktur.

-   Üst bilgi bölümü (dikey çubukla ayrılan bölüm) var olmalıdır (protokolde belirtildiği gibi).

-   _Extension_ bölümündeki anahtarlar olayda var olmalıdır:

    -   externalId = Windows olay kimliği

    -   RT = gerçek olayın zaman damgası (sıem'e ulaşma veya ATP'ye gönderilme zaman damgası olmadığından emin olun). Tercihen milisaniye hassaslığında bu önemlidir.

    -   cat = Windows olay günlüğü adı

    -   shost = kaynak ana bilgisayar adı

    -   dhost = olayı alan bilgisayarın adı (bu örnekte DC)

    -   duser = kimliği doğrulanan kullanıcının adı

-   _Extension_ bölümünde sıra önemli değildir

-   Bu iki alan için bir özel key ve keyLable olmalıdır:

    -   “EventSource”

    -   “Reason or Error Code” = NTLM sonuç kodu

## <a name="splunk"></a>Splunk
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

    -   TimeGenerated = gerçek olayın zaman damgası (sıem'e ulaşma veya ATP'ye gönderilme zaman damgası olmadığından emin olun). Biçim, yyyyaaggssddss.ffffff milisaniye hassaslığında, bu önemlidir eşleşmelidir.

    -   ComputerName = kaynak ana bilgisayar adı

    -   Message = Windows olayından alınan özgün olay metni

-   Message Anahtarı ve değeri en sonda yer almalıdır.

-   Anahtar=değer çiftleri için sıra önemli değildir.

## <a name="qradar"></a>QRadar
QRadar bir aracı üzerinden olay toplamayı sağlar. Veriler bir aracı kullanarak toplanıyorsa, saat biçimi mili saniye verisi olmadan toplanır. Azure ATP mili saniye verisi duyduğundan, QRadar aracısız Windows olay toplamayı kullanacak şekilde ayarlanması gerekir. Daha fazla bilgi için [ http://www-01.ibm.com/support/docview.wss?uid=swg21700170 ] (http://www-01.ibm.com/support/docview.wss?uid=swg21700170 "QRadar: MSRPC protokolünü kullanarak aracısız Windows olayları koleksiyonu").

    <13>Feb 11 00:00:00 %IPADDRESS% AgentDevice=WindowsLog AgentLogFile=Security Source=Microsoft-Windows-Security-Auditing Computer=%FQDN% User= Domain= EventID=4776 EventIDCode=4776 EventType=8 EventCategory=14336 RecordNumber=1961417 TimeGenerated=1456144380009 TimeWritten=1456144380009 Message=The computer attempted to validate the credentials for an account. Authentication Package: MICROSOFT_AUTHENTICATION_PACKAGE_V1_0 Logon Account: Administrator Source Workstation: HOSTNAME Error Code: 0x0

Gerekli alanları şunlardır:

- Koleksiyon için aracı türü
- Windows olay günlüğü sağlayıcısı adı
- Windows olay günlüğü kaynağı
- Tam etki alanı adı
- Windows olay kimliği

TimeGenerated olan gerçek olayın zaman damgası (sıem'e ulaşma veya ATP'ye gönderilme zaman damgası olmadığından emin olun). Biçim, yyyyaaggssddss.ffffff milisaniye hassaslığında, bu önemlidir eşleşmelidir.

Message, Windows olayından alınan özgün olay metnidir

key=value çiftleri arasında \t bulunduğundan emin olun.

>[!NOTE] 
> Windows olay koleksiyonu için WinCollect kullanımı desteklenmez.




## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP boyutlandırma aracı](http://aka.ms/aatpsizingtool)
- [Azure ATP SIEM günlük başvurusu](cef-format-sa.md)
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
