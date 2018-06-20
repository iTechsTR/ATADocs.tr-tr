---
title: ATA SIEM günlük başvurusu | Microsoft Docs
description: ATA’dan SIEM’nize gönderilen şüpheli etkinlik günlüğü örnekleri sağlar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 601b48ba-a327-4aff-a1f9-2377a2bb7a42
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: 7c6eaba8f80dcc7a8fc767f2bb8168221fbc7207
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
ms.locfileid: "30009879"
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*


# <a name="ata-siem-log-reference"></a>ATA SIEM günlük başvurusu

ATA, şüpheli etkinlik ve izleme uyarısı olaylarını SIEM'nize iletebilir. Şüpheli etkinlik olayları CEF biçimindedir. Bu başvuru makalesinde, SIEM’nize gönderilen şüpheli etkinlik günlükleri için örnekler sağlanmaktadır.

## <a name="sample-ata-suspicious-activities-in-cef-format"></a>CEF biçiminde örnek ATA şüpheli etkinlikleri
Aşağıdaki alanlar ve bunların değerleri SIEM’nize iletilir:

-   start – uyarının başlangıç saati
-   suser – uyarıda bahsi geçen hesap (genellikle kullanıcı hesabıdır)
-   shost – bu uyarının kaynak makinesi
-   outcome – uyarıda gerçekleşen etkinliğin başarı/başarısızlık durumu söz konusu olduğunda  
-   msg – uyarının açıklaması
-   CNT – bir sayısı (tahmin edilen parolaları miktardaki sahip oldu örneğin deneme yanılma saldırısı) uyarı sahip uyarılar
-   app – uyarıda kullanılan protokol
-   externalId – ATA’nın olay günlüğüne yazdığı ve uyarıya karşılık gelen olay kimliği
-   cs#label ve cs# – bunlar CEF’in kullanmaya izin verdiği müşteri dizeleridir. cs#label yeni alanın adıdır ve cs# ise değerdir, örneğin: cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa

Bu örnekte cs1, uyarının URL'sini içeren bir alandır.

## <a name="sample-logs"></a>Örnek günlükler

Öncelikler: 3=Düşük 5=Orta 10=Yüksek

### <a name="bruteforce--ldap"></a>BruteForce – LDAP
05-03-2017          13:35:01               Auth.Warning    192.168.0.220     May  3 10:35:01 CENTER ATA:CEF:0|Microsoft|ATA|.5942.64854|BruteForceSuspiciousActivity|LDAP basit bağlama ile deneme yanılma saldırısı|5|start=2017-05-03T10:34:57.2785534Z app=Ldap suser=Darris Woods shost=CLIENT1 msg=CLIENT1 tarafından Darris Woods (Yazılım Mühendisi) adlı kullanıcıya Ldap protokolü ile bir deneme yanılma saldırısı denendi (76 tahmin denemesi). cnt=76 cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70

05-03-2017          13:35:05               Auth.Warning    192.168.0.220     May  3 10:35:05 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|BruteForceSuspiciousActivity|LDAP basit bağlama ile deneme yanılma saldırısı|5|start=2017-05-03T10:34:58.7004159Z app=Ldap suser=Dino Hopkins shost=CLIENT1 msg=CLIENT1 tarafından Dino Hopkins (Yazılım Mühendisi) adlı kullanıcıya Ldap protokolü ile bir deneme yanılma saldırısı denendi (3 tahmin denemesi). cnt=3 cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70

05-03-2017          13:35:05               Auth.Warning    192.168.0.220     May  3 10:35:05 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|BruteForceSuspiciousActivity|LDAP basit bağlama ile deneme yanılma saldırısı|5|start=2017-05-03T10:34:59.7269332Z app=Ldap suser=Dino Hopkins shost=CLIENT1 msg=CLIENT1 tarafından Dino Hopkins (Yazılım Mühendisi) adlı kullanıcıya Ldap protokolü ile başarılı bir deneme yanılma saldırısı girişimi oldu. (77 tahmin denemesi). cnt=77 cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70
### <a name="bruteforce"></a>BruteForce
05-14-2017          13:27:05               Auth.Warning    192.168.0.220     1 2017-05- ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|BruteForceSuspiciousActivity|Suspicious authentication failures|5|start=2017-05-14T10:27:04.3904739Z app=Kerberos shost=CLIENT1 msg=Suspicious authentication failures indicating a potential brute-force attack were detected from CLIENT1. externalId=2023 cs1Label=url cs1=https://center/suspiciousActivity/591830f98ca1ec11d0c0d7f5
### <a name="privilege-escalation"></a>Ayrıcalık yükseltme
#### <a name="silver"></a>Gümüş
05 10 2017 17:14:15 Auth.Error 192.168.0.220 1 2017-05-10T14:14:15.589415 + 00:00 merkezi ATA 596 ForgedPacSuspiciousActivity ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | ForgedPacSuspiciousActivity | Ayrıcalık yükseltme kullanarak sahte yetkilendirme verilerinin | 10 | Başlat 2017 =-05-10T14:11:51.8053059Z uygulama Kerberos suser = Kullanıcı1 msg = ayrıcalıkları, sahte yetkilendirme verileri kullanarak İSTEMCİ2 KONAK/İSTEMCİ1'e yükseltmek için çalıştı Kullanıcı1 =. externalId=2013 cs1Label=url cs1=https://center/suspiciousActivity/591320378ca1ec02543e4747
#### <a name="gold"></a>Altın
05-10-2017          17:13:30               Auth.Error           192.168.0.220     1 2017-05-10T14:13:30.244377+00:00 CENTER ATA 596 ForgedPacSuspiciousActivity ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|ForgedPacSuspiciousActivity|Privilege escalation using forged authorization data|10|start=2017-05-10T14:11:27.6455273Z app=Kerberos suser=user1 msg=user1 attempted to escalate privileges against DC4 from CLIENT1 by using forged authorization data. externalId=2013 cs1Label=url cs1=https://center/suspiciousActivity/5913200a8ca1ec02543e3ea8
### <a name="golden-ticket"></a>Altın Bilet
05-14-2017          15:57:10               Auth.Warning    192.168.0.220     1 2017-05-14T12:57:10.392730+00:00 CENTER ATA 4732 EncryptionDowngradeSuspiciousAct ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|EncryptionDowngradeSuspiciousActivity|Encryption downgrade activity|5|start=2017-05-14T12:55:08.6913033Z app=Kerberos msg=The encryption method of the TGT field of TGS_REQ message from CLIENT1 has been downgraded based on previously learned behavior. Bu, CLIENT1 adlı istemcide kullanımda olan Altın Anahtarın bir sonucu olabilir. externalId=2009 cs1Label=url cs1=https://center/suspiciousActivity/591854268ca1ec127ceec396
### <a name="honey-token-activity"></a>Honey Token Etkinliği
05-11-2017          16:49:10               Auth.Warning    192.168.0.220     1 2017-05-11T13:49:10.725605+00:00 CENTER ATA 876 HoneytokenActivitySuspiciousActi ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|HoneytokenActivitySuspiciousActivity|Honeytoken activity|5|start=2017-05-11T13:49:09.6455794Z app=Kerberos suser=privtriservice msg=The following activities were performed by privtriservice:\r\nAuthenticated from DC1 using NTLM against corporate resources via DC1. externalId=2014 cs1Label=url cs1=https://center/suspiciousActivity/59146bd68ca1ec036ce57d29
### <a name="suspicious-replication-of-directory-services"></a>Dizin hizmetlerinin şüpheli çoğaltması
May  3 11:02:28 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|DirectoryServicesReplicationSuspiciousActivity|Dizin hizmetlerinin kötü amaçlı çoğaltması|10|start=2017-05-03T11:00:13.6560919Z suser=user1 shost=CLIENT1 outcome=Failure msg=user1 tarafından DC1 adlı etki alanı denetleyicisine karşı CLIENT1 adlı istemciden kötü amaçlı çoğaltma istekleri denendi. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b8c48ca1ec04d05ed28d
### <a name="malicious-data-protection-private-information-request"></a>Kötü Amaçlı Veri Koruma Özel Bilgi İsteği
May  3 13:39:18 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|RetrieveDataProtectionBackupKeySuspiciousActivity|Kötü Amaçlı Veri Koruması Özel Bilgi İsteği|10|start=2017-05-03T13:37:06.4039886Z app=LsaRpc shost=CLIENT1 suser= outcome=Success msg=Bilinmeyen bir kullanıcı DC1 adlı etki alanı denetleyicisinden DPAPI etki alanı yedek anahtarını almak için CLIENT1 adlı istemciden 4 başarılı deneme yaptı. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909dd868ca1ec04d05fb01d
### <a name="massive-object-deletion"></a>Büyük Çaplı Nesne Silme
05-14-2017          14:38:34               Auth.Warning    192.168.0.220     1 2017-05-14T11:38:34.898810+00:00 CENTER ATA 3748 MassiveObjectDeletionSuspiciousA ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|MassiveObjectDeletionSuspiciousActivity|Massive object deletion|5|start=2017-05-14T11:33:32.0000000Z msg=496 objects (9.75% of total AD objects) were deleted over a period of no time from domain domain1.test.local. cnt=496 externalId=2016 cs1Label=url cs1=https://center/suspiciousActivity/591841ba8ca1ec0ea4ad587a
### <a name="over-pass-the-hash"></a>Over-pass-the-hash
05 14 2017 12:07:46 Auth.Warning 192.168.0.220 1 2017-05-14T09:07:46.652319 + 00:00 merkezi ATA 1116 EncryptionDowngradeSuspiciousAct ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | EncryptionDowngradeSuspiciousActivity | Şifreleme indirgeme etkinlik | 5 | Başlat 2017 =-05-14T09:07:44.9933773Z uygulama Kerberos msg = şifreleme yöntemini = AS_REQ Encrypted_Timestamp alanının İSTEMCİ1 iletiden daha önceden öğrenilen davranışı temelinde bir alt sürüme. Bu, CLIENT1 adlı istemciden Overpass-the-Hash ile kimlik bilgilerini çalmanın bir sonucu olabilir. externalId=2010 cs1Label=url cs1=https://center/suspiciousActivity/59181e628ca1ec045cdfa929
### <a name="pass-the-hash"></a>Pass-the-hash
05 10 2017 17:48:51 Auth.Error 192.168.0.220 1 2017-05-10T14:48:51.998620 + 00:00 merkezi ATA 596 PassTheHashSuspiciousActivity ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | PassTheHashSuspiciousActivity | Kimlik hırsızlığı Pass--Hash saldırısı | 10 | Başlat 2017 =-05-10T14:46:50.9463800Z uygulama Ntlm suser = kullanıcı2 msg = kullanıcı2'ın = karma çalınırsa önceden kullanıcı2 oturum açmış ve İSTEMCİ1'den kullanılan bilgisayarları birinden. externalId=2017 cs1Label=url cs1=https://center/suspiciousActivity/591328538ca1ec02543f9a1a
### <a name="account-enumeration"></a>Hesap listeleme
05 10 2017 16:44:22 Auth.Warning 192.168.0.220 1 2017-05-10T13:44:22.706381 + 00:00 merkezi ATA 596 AccountEnumerationSuspiciousActi ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | AccountEnumerationSuspiciousActivity | Hesap numaralandırma kullanarak keşif | 5 | Başlat 2017 =-05-10T13:44:20.9930644Z uygulama Kerberos shost = CLIENT3 msg = = şüpheli hesap CLIENT3 kaynaklanan Kerberos protokolünü kullanarak numaralandırması etkinlik algılandı. Saldırgan, hesap adları için toplamda 72 tahmin denemesinde bulundu; 2 tahmin denemesi, Active Directory’deki mevcut hesap adlarıyla eşleşti. externalId=2003 cs1Label=url cs1=https://center/suspiciousActivity/591319368ca1ec02543c56ee
### <a name="dns-recon"></a>DNS Keşfi
05-03-2017          13:16:57               Auth.Warning    192.168.0.220     May  3 10:16:57 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|DnsReconnaissanceSuspiciousActivity|DNS ile keşif|5|start=2017-05-03T10:16:41.8297467Z app=Dns shost=CLIENT1 msg=DC1 adlı etki alanı denetleyicisine karşı DNS sunucusu olmayan CLIENT1 adlı istemciden kaynaklı şüpheli DNS etkinliği gözlemlendi. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa 05-03-2017          13:24:21               Auth.Warning    192.168.0.220     May  3 10:24:21 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|DnsReconnaissanceSuspiciousActivity|DNS ile keşif|5|start=2017-05-03T10:24:08.0950753Z app=Dns shost=CLIENT1 request=contoso.com requestMethod=Axfr reason=NameError outcome=Failure msg=DNS sunucusu olmayan CLIENT1 adlı istemciden kaynaklı şüpheli DNS etkinliği gözlemlendi. Sorgu contoso.com içindi (Axfr tipi). Yanıt NameError idi. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa
### <a name="smb-session-enumeration"></a>SMB Oturum listeleme
May  3 11:55:43 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|EnumerateSessionsSuspiciousActivity|SMB Oturum Listeleme ile keşif|5|start=2017-05-03T11:52:02.4360718Z app=SrvSvc shost=CLIENT1 msg=CLIENT1 adlı istemciden DC1 adlı etki alanı denetleyicisine karşı SMB oturum listeleme denemeleri başarıyla gerçekleştirildi, user1 (daf::1) adlı kullanıcı açığa çıkarıldı. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909c53f8ca1ec04d05f1cf1
### <a name="samr-enumeration"></a>SAMR listeleme
May  3 11:44:48 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|SamrReconnaissanceSuspiciousActivity|Dizin hizmetleri listeleme ile keşif|5|start=2017-05-03T11:42:46.5911225Z app=Samr shost=CLIENT1 suser=user1 outcome=Success msg=CLIENT1 adlı istemciden DC1 adlı etki alanı denetleyicisine karşı SAMR protokolü kullanan şu dizin hizmetleri listelemeleri denendi:\r\nuser1 tarafından domain1.test.local adlı etki alanındaki tüm gruplar başarıyla listelendi cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909c2b08ca1ec04d05f0e19
### <a name="remote-execution"></a>Uzaktan Yürütme
May  3 12:36:47 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|RemoteExecutionSuspiciousActivity|Uzaktan yürütme denemesi algılandı|3|start=2017-05-03T12:34:32.3714348Z app=ServiceControl shost=CLIENT1 suser=Administrator outcome=Success msg=CLIENT1 tarafından DC1 adlı etki alanı denetleyicisinde şu uzaktan yürütme denemeleri gerçekleştirildi:\r\nYönetici tarafından PSEXESVC başarıyla uzaktan oluşturuldu. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909cedf8ca1ec04d05f5692
### <a name="skeleton-key"></a>Maymuncuk
05 14 2017 12:13:12 Auth.Warning 192.168.0.220 1 2017-05-14T09:13:12.102468 + 00:00 merkezi ATA 1116 EncryptionDowngradeSuspiciousAct ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | EncryptionDowngradeSuspiciousActivity | Şifreleme indirgeme etkinlik | 5 | Başlat 2017 =-05-14T09:13:03.3509467Z uygulama Kerberos msg = şifreleme yöntemini = KRB_ERR ETYPE_INFO2 alanının İSTEMCİ2 iletiden daha önceden öğrenilen davranışı temelinde bir alt sürüme. Bu, DC3’teki bir Skeleton Key’in sonucu olabilir. externalId=2011 cs1Label=url cs1=https://center/suspiciousActivity/59181fa88ca1ec045cdfe630
### <a name="unusual-protocol-implementation"></a>Olağan dışı protokol uygulanması
May  3 12:28:19 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|AbnormalProtocolSuspiciousActivity|Olağan dışı protokol uygulaması|5|start=2017-05-03T12:28:05.3561302Z app=Ntlm shost=CLIENT1 suser=Administrator outcome=Success msg=Yönetici olağan dışı bir protokol uygulaması kullanarak CLIENT1 adlı istemciden DC1 adlı etki alanı denetleyicisine karşı başarıyla kimlik doğruladı. Bu, Pass-the-Hash ve deneme yanılma gibi saldırıları yürütmek için kullanılan kötü amaçlı bir aracın sonucu olabilir. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909cce38ca1ec04d05f4ab4
### <a name="pass-the-ticket"></a>Anahtar geçişi
May  4 13:15:41 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|PassTheTicketSuspiciousActivity|Pass-the-Ticket saldırısı ile kimlik hırsızlığı|10|start=2017-05-04T13:13:44.5160000Z app=Kerberos shost=CLIENT1 suser=Administrator request=krbtgt/DOMAIN1.TEST.LOCAL msg=Yöneticinin Kerberos anahtarları CLIENT2 adlı istemciden çalındı ve CLIENT1 adlı istemcide krbtgt/DOMAIN1.TEST.LOCAL etki alanı anahtarına erişmek için kullanıldı. cs2Label=ticketSourceComputer cs2=CLIENT2 cs3Label=ticketSourceComputerIpAddress cs3= cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/590b29168ca1ec0ba438acf6

### <a name="monitoring-alert"></a>İzleme Uyarısı
2018-01-30T10:42:09.102595+00:00 CENTER ATA 4932 CenterDatabaseDisconnectedMonito ï»¿CEF:0|Microsoft|ATA|1.8.6765.50002|CenterDatabaseDisconnectedMonitoringAlert|CenterDatabaseDisconnectedMonitoringAlert|10|externalId=1005 cs1Label=url cs1=https://center/monitoring msg=The database that is used by the Center, CENTER, is down. Son 30/1/2018 üzerinde çalışan görüldü 10:39:39 AM UTC.

> [!NOTE]
> Tüm izleme uyarıları, yukarıdaki aynı şablonu ile gönderilir.



## <a name="see-also"></a>Ayrıca bkz:
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
