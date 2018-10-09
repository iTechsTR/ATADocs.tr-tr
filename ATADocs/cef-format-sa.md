---
title: ATA SIEM günlük başvurusu | Microsoft Docs
description: ATA’dan SIEM’nize gönderilen şüpheli etkinlik günlüğü örnekleri sağlar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 601b48ba-a327-4aff-a1f9-2377a2bb7a42
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: e4dc613ded1234bad931a67af679bb067c2d7719
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46134098"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*


# <a name="ata-siem-log-reference"></a>ATA SIEM günlük başvurusu

ATA, şüpheli etkinlik ve izleme uyarısı olaylarını SIEM'nize iletebilir. Şüpheli etkinlik olayları CEF biçimindedir. Bu başvuru makalesinde, SIEM’nize gönderilen şüpheli etkinlik günlükleri için örnekler sağlanmaktadır.

## <a name="sample-ata-suspicious-activities-in-cef-format"></a>CEF biçiminde örnek ATA şüpheli etkinlikleri
Aşağıdaki alanlar ve bunların değerleri SIEM’nize iletilir:

-   start – uyarının başlangıç saati
-   suser – uyarıda bahsi geçen hesap (genellikle kullanıcı hesabıdır)
-   shost – bu uyarının kaynak makinesi
-   outcome – uyarıda gerçekleşen etkinliğin başarı/başarısızlık durumu söz konusu olduğunda  
-   msg – uyarının açıklaması
-   CNT – (parolalar tahmin edilen bir miktarı sahip oldu örneğin deneme yanılma) uyarı bir sayısı sahip uyarılar için
-   app – uyarıda kullanılan protokol
-   externalId – ATA’nın olay günlüğüne yazdığı ve uyarıya karşılık gelen olay kimliği
-   cs #label & cs # – bunlar cef'in kullanmaya izin #label yeni alanın adıdır ve cs # ise değerdir, örneğin CEF izin verdiğini müşteri dizeleridir: cs1Label = url cs1 = https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa

Bu örnekte cs1, uyarının URL'sini içeren bir alandır.

## <a name="sample-logs"></a>Örnek günlükler

Öncelikler: 3=Düşük 5=Orta 10=Yüksek

### <a name="bruteforce--ldap"></a>BruteForce – LDAP
05-03-2017          13:35:01               Auth.Warning    192.168.0.220     May  3 10:35:01 CENTER ATA:CEF:0|Microsoft|ATA|.5942.64854|BruteForceSuspiciousActivity|LDAP basit bağlama ile deneme yanılma saldırısı|5|start=2017-05-03T10:34:57.2785534Z app=Ldap suser=Darris Woods shost=CLIENT1 msg=CLIENT1 tarafından Darris Woods (Yazılım Mühendisi) adlı kullanıcıya Ldap protokolü ile bir deneme yanılma saldırısı denendi (76 tahmin denemesi). cnt=76 cs1Label=url cs1 = https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70

05-03-2017          13:35:05               Auth.Warning    192.168.0.220     May  3 10:35:05 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|BruteForceSuspiciousActivity|LDAP basit bağlama ile deneme yanılma saldırısı|5|start=2017-05-03T10:34:58.7004159Z app=Ldap suser=Dino Hopkins shost=CLIENT1 msg=CLIENT1 tarafından Dino Hopkins (Yazılım Mühendisi) adlı kullanıcıya Ldap protokolü ile bir deneme yanılma saldırısı denendi (3 tahmin denemesi). CNT 3 cs1Label = url cs1 = https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70

05-03-2017          13:35:05               Auth.Warning    192.168.0.220     May  3 10:35:05 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|BruteForceSuspiciousActivity|LDAP basit bağlama ile deneme yanılma saldırısı|5|start=2017-05-03T10:34:59.7269332Z app=Ldap suser=Dino Hopkins shost=CLIENT1 msg=CLIENT1 tarafından Dino Hopkins (Yazılım Mühendisi) adlı kullanıcıya Ldap protokolü ile başarılı bir deneme yanılma saldırısı girişimi oldu. (77 tahmin denemesi). CNT 77 cs1Label = url cs1 = https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70
### <a name="bruteforce"></a>BruteForce
14/05--2017 13:27:05 Auth.Warning 192.168.0.220 1 2017-05-ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | BruteForceSuspiciousActivity | Şüpheli kimlik doğrulama hataları | 5 | başlangıç = 2017-05-14T10:27:04.3904739Z app = Kerberos shost = clıent1 msg = İSTEMCİ1'den olası bir deneme yanılma saldırısı algılandı gösteren şüpheli kimlik doğrulama hataları =. externalID = 2023 cs1Label = url cs1 = https://center/suspiciousActivity/591830f98ca1ec11d0c0d7f5
### <a name="privilege-escalation"></a>Ayrıcalık yükseltme
#### <a name="silver"></a>Gümüş
05-10-2017 17:14:15 Auth.Error 192.168.0.220 1 2017-05-10T14:14:15.589415 + 00:00 CENTER ATA 596 ForgedPacSuspiciousActivity ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | ForgedPacSuspiciousActivity | Sahte yetkilendirme verileri kullanan ayrıcalık yükseltme saldırısı | 10 | Başlangıç = 2017-05-10T14:11:51.8053059Z uygulama Kerberos suser = user1 msg = = user1 İSTEMCİ2 ' KONAK/İSTEMCİ1'e sahte yetkilendirme verileri kullanılarak ayrıcalıklar yükseltilmeye çalışıldı. externalID = 2013 cs1Label = url cs1 =https://center/suspiciousActivity/591320378ca1ec02543e4747
#### <a name="gold"></a>Altın
05-10-2017 17:13:30 Auth.Error 192.168.0.220 1 2017-05-10T14:13:30.244377 + 00:00 CENTER ATA 596 ForgedPacSuspiciousActivity ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | ForgedPacSuspiciousActivity | Sahte yetkilendirme verileri kullanan ayrıcalık yükseltme saldırısı | 10 | Başlangıç = 2017-05-10T14:11:27.6455273Z uygulama Kerberos suser = user1 msg = = user1 sahte yetkilendirme verileri kullanılarak ayrıcalıklar karşı clıent1 DC4 yükseltilmeye çalışıldı. externalID = 2013 cs1Label = url cs1 = https://center/suspiciousActivity/5913200a8ca1ec02543e3ea8
### <a name="golden-ticket"></a>Altın Bilet
14/05--2017 15:57:10 Auth.Warning 192.168.0.220 1 2017-05-14T12:57:10.392730 + 00:00 CENTER ATA 4732 EncryptionDowngradeSuspiciousAct ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | EncryptionDowngradeSuspiciousActivity | Şifreleme düşürme etkinliği | 5 | başlangıç = 2017-05-14T12:55:08.6913033Z uygulama Kerberos msg = şifreleme yöntemini = TGS_REQ TGT alanının İSTEMCİ1 iletiden daha önceden öğrenilen davranışına göre hızdan azalttı. Bu, CLIENT1 adlı istemcide kullanımda olan Altın Anahtarın bir sonucu olabilir. externalID = 2009 cs1Label = url cs1 = https://center/suspiciousActivity/591854268ca1ec127ceec396
### <a name="honey-token-activity"></a>Honey Token Etkinliği
05-11-2017 16:49:10 Auth.Warning 192.168.0.220 1 2017-05-11T13:49:10.725605 + 00:00 CENTER ATA 876 HoneytokenActivitySuspiciousActi ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | HoneytokenActivitySuspiciousActivity | Honeytoken etkinliği | 5 | başlangıç = 2017-05-11T13:49:09.6455794Z uygulama Kerberos suser = privtriservice msg = aşağıdaki = etkinlikleri privtriservice:\r\nAuthenticated DC1 aracılığıyla Kurumsal kaynaklarda NTLM kullanılarak DC1'de tarafından gerçekleştirildi. externalID = 2014 cs1Label = url cs1 = https://center/suspiciousActivity/59146bd68ca1ec036ce57d29
### <a name="suspicious-replication-of-directory-services"></a>Dizin hizmetlerinin şüpheli çoğaltması
May  3 11:02:28 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|DirectoryServicesReplicationSuspiciousActivity|Dizin hizmetlerinin kötü amaçlı çoğaltması|10|start=2017-05-03T11:00:13.6560919Z suser=user1 shost=CLIENT1 outcome=Failure msg=user1 tarafından DC1 adlı etki alanı denetleyicisine karşı CLIENT1 adlı istemciden kötü amaçlı çoğaltma istekleri denendi. cs1Label = url cs1 = https://192.168.0.220/suspiciousActivity/5909b8c48ca1ec04d05ed28d
### <a name="malicious-data-protection-private-information-request"></a>Kötü Amaçlı Veri Koruma Özel Bilgi İsteği
May  3 13:39:18 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|RetrieveDataProtectionBackupKeySuspiciousActivity|Kötü Amaçlı Veri Koruması Özel Bilgi İsteği|10|start=2017-05-03T13:37:06.4039886Z app=LsaRpc shost=CLIENT1 suser= outcome=Success msg=Bilinmeyen bir kullanıcı DC1 adlı etki alanı denetleyicisinden DPAPI etki alanı yedek anahtarını almak için CLIENT1 adlı istemciden 4 başarılı deneme yaptı. cs1Label = url cs1 = https://192.168.0.220/suspiciousActivity/5909dd868ca1ec04d05fb01d
### <a name="massive-object-deletion"></a>Büyük Çaplı Nesne Silme
14/05--2017 14:38:34 Auth.Warning 192.168.0.220 1 2017-05-14T11:38:34.898810 + 00:00 CENTER ATA 3748 MassiveObjectDeletionSuspiciousA ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | MassiveObjectDeletionSuspiciousActivity | Büyük çaplı nesne silme | 5 | başlangıç = 2017-05-14T11:33:32.0000000Z msg = 496 nesneleri (toplam AD nesnelerini %9.75), bir süre boyunca hiçbir etki alanı domain1.test.local öğesinden silindi. CNT 496 externalID = 2016 cs1Label = url cs1 = https://center/suspiciousActivity/591841ba8ca1ec0ea4ad587a
### <a name="over-pass-the-hash"></a>Over-pass-the-hash
14/05--2017 12:07:46 Auth.Warning 192.168.0.220 1 2017-05-14T09:07:46.652319 + 00:00 CENTER ATA 1116 EncryptionDowngradeSuspiciousAct ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | EncryptionDowngradeSuspiciousActivity | Şifreleme düşürme etkinliği | 5 | başlangıç = 2017-05-14T09:07:44.9933773Z uygulama Kerberos msg = şifreleme yöntemini = AS_REQ Encrypted_Timestamp alanının İSTEMCİ1 iletiden daha önceden öğrenilen davranışına göre hızdan azalttı. Bu, CLIENT1 adlı istemciden Overpass-the-Hash ile kimlik bilgilerini çalmanın bir sonucu olabilir. externalID = 2010 cs1Label = url cs1 = https://center/suspiciousActivity/59181e628ca1ec045cdfa929
### <a name="pass-the-hash"></a>Pass-the-hash
05-10-2017 17:48:51 Auth.Error 192.168.0.220 1 2017-05-10T14:48:51.998620 + 00:00 CENTER ATA 596 PassTheHashSuspiciousActivity ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | PassTheHashSuspiciousActivity | Pass--Hash saldırısı kullanan kimlik hırsızlığı | 10 | Başlangıç = 2017-05-10T14:46:50.9463800Z uygulama Ntlm suser = kullanıcı2 msg = kullanıcı2'ın = karması daha önce kullanıcı2 tarafından oturum açtığınız ve İSTEMCİ1'den kullanılan bilgisayarların birinden Çalındı. externalID = 2017 cs1Label = url cs1 = https://center/suspiciousActivity/591328538ca1ec02543f9a1a
### <a name="account-enumeration"></a>Hesap listeleme
05-10-2017 16:44:22 Auth.Warning 192.168.0.220 1 2017-05-10T13:44:22.706381 + 00:00 CENTER ATA 596 AccountEnumerationSuspiciousActi ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | AccountEnumerationSuspiciousActivity | Hesap numaralandırma kullanarak keşif | 5 | başlangıç = 2017-05-10T13:44:20.9930644Z app = Kerberos shost = CLIENT3 msg = = şüpheli hesap listeleme etkinliği CLIENT3 kaynaklanan Kerberos protokolü kullanarak algılandı. Saldırgan, hesap adları için toplamda 72 tahmin denemesinde bulundu; 2 tahmin denemesi, Active Directory’deki mevcut hesap adlarıyla eşleşti. externalID = 2003 cs1Label = url cs1 = https://center/suspiciousActivity/591319368ca1ec02543c56ee
### <a name="dns-recon"></a>DNS Keşfi
05-03-2017          13:16:57               Auth.Warning    192.168.0.220     May  3 10:16:57 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|DnsReconnaissanceSuspiciousActivity|DNS ile keşif|5|start=2017-05-03T10:16:41.8297467Z app=Dns shost=CLIENT1 msg=DC1 adlı etki alanı denetleyicisine karşı DNS sunucusu olmayan CLIENT1 adlı istemciden kaynaklı şüpheli DNS etkinliği gözlemlendi. cs1Label = url cs1 = https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa 05-03-2017 13:24:21 Auth.Warning 192.168.0.220 olabilir 3 10:24:21 CENTER ATA:CEF:0 | Microsoft | ATA | 1.8.5942.64854 | DnsReconnaissanceSuspiciousActivity | DNS kullanarak keşif | 5 | Başlat = 2017-05-03T10:24:08.0950753Z uygulama = Dns shost = clıent1 request=contoso.com requestMethod = Axfr nedeni = NameError outcome = Failure msg = = şüpheli DNS etkinliği gözlemlendi (Bu bir DNS İSTEMCİ1 kaynaklanan Sunucu). Sorgu contoso.com içindi (Axfr tipi). Yanıt NameError idi. cs1Label = url cs1 = https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa
### <a name="smb-session-enumeration"></a>SMB Oturum listeleme
May  3 11:55:43 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|EnumerateSessionsSuspiciousActivity|SMB Oturum Listeleme ile keşif|5|start=2017-05-03T11:52:02.4360718Z app=SrvSvc shost=CLIENT1 msg=CLIENT1 adlı istemciden DC1 adlı etki alanı denetleyicisine karşı SMB oturum listeleme denemeleri başarıyla gerçekleştirildi, user1 (daf::1) adlı kullanıcı açığa çıkarıldı. cs1Label = url cs1 = https://192.168.0.220/suspiciousActivity/5909c53f8ca1ec04d05f1cf1
### <a name="samr-enumeration"></a>SAMR listeleme
May 3 11:44:48 CENTER ATA:CEF:0 | Microsoft | ATA | 1.8.5942.64854 | SamrReconnaissanceSuspiciousActivity | Dizin Hizmetleri listelemesi kullanarak keşif | 5 | başlangıç = 2017-05-03T11:42:46.5911225Z app = Samr shost = clıent1 suser = user1 outcome = Success msg = DC1'den karşı SAMR protokolü kullanılarak numaralandırmalar denendi şu Dizin Hizmetleri = CLIENT1:\r\nSuccessful numaralandırma cs1Label user1 tarafından domain1.test.local içindeki tüm gruplar = url cs1 = https://192.168.0.220/suspiciousActivity/5909c2b08ca1ec04d05f0e19
### <a name="remote-execution"></a>Uzaktan Yürütme
May  3 12:36:47 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|RemoteExecutionSuspiciousActivity|Uzaktan yürütme denemesi algılandı|3|start=2017-05-03T12:34:32.3714348Z app=ServiceControl shost=CLIENT1 suser=Administrator outcome=Success msg=CLIENT1 tarafından DC1 adlı etki alanı denetleyicisinde şu uzaktan yürütme denemeleri gerçekleştirildi:\r\nYönetici tarafından PSEXESVC başarıyla uzaktan oluşturuldu. cs1Label = url cs1 = https://192.168.0.220/suspiciousActivity/5909cedf8ca1ec04d05f5692
### <a name="skeleton-key"></a>Maymuncuk
14/05--2017 12:13:12 Auth.Warning 192.168.0.220 1 2017-05-14T09:13:12.102468 + 00:00 CENTER ATA 1116 EncryptionDowngradeSuspiciousAct ï» ¿CEF:0 | Microsoft | ATA | 1.8.6455.41882 | EncryptionDowngradeSuspiciousActivity | Şifreleme düşürme etkinliği | 5 | başlangıç = 2017-05-14T09:13:03.3509467Z uygulama Kerberos msg = şifreleme yöntemini = KRB_ERR ETYPE_INFO2 alanının CLIENT2 iletiden daha önceden öğrenilen davranışına göre hızdan azalttı. Bu, DC3’teki bir Skeleton Key’in sonucu olabilir. externalID = 2011 cs1Label = url cs1 = https://center/suspiciousActivity/59181fa88ca1ec045cdfe630
### <a name="unusual-protocol-implementation"></a>Olağan dışı protokol uygulanması
May  3 12:28:19 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|AbnormalProtocolSuspiciousActivity|Olağan dışı protokol uygulaması|5|start=2017-05-03T12:28:05.3561302Z app=Ntlm shost=CLIENT1 suser=Administrator outcome=Success msg=Yönetici olağan dışı bir protokol uygulaması kullanarak CLIENT1 adlı istemciden DC1 adlı etki alanı denetleyicisine karşı başarıyla kimlik doğruladı. Bu, Pass-the-Hash ve deneme yanılma gibi saldırıları yürütmek için kullanılan kötü amaçlı bir aracın sonucu olabilir. cs1Label = url cs1 = https://192.168.0.220/suspiciousActivity/5909cce38ca1ec04d05f4ab4
### <a name="pass-the-ticket"></a>Anahtar geçişi
May  4 13:15:41 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|PassTheTicketSuspiciousActivity|Pass-the-Ticket saldırısı ile kimlik hırsızlığı|10|start=2017-05-04T13:13:44.5160000Z app=Kerberos shost=CLIENT1 suser=Administrator request=krbtgt/DOMAIN1.TEST.LOCAL msg=Yöneticinin Kerberos anahtarları CLIENT2 adlı istemciden çalındı ve CLIENT1 adlı istemcide krbtgt/DOMAIN1.TEST.LOCAL etki alanı anahtarına erişmek için kullanıldı. cs2Label ticketSourceComputer cs2 = CLIENT2 cs3Label = ticketSourceComputerIpAddress cs3 = cs1Label = url cs1 = = https://192.168.0.220/suspiciousActivity/590b29168ca1ec0ba438acf6

### <a name="monitoring-alert"></a>İzleme Uyarısı
2018-01-30T10:42:09.102595 + 00:00 CENTER ATA 4932 CenterDatabaseDisconnectedMonito ï» ¿CEF:0 | Microsoft | ATA | 1.8.6765.50002 | CenterDatabaseDisconnectedMonitoringAlert | CenterDatabaseDisconnectedMonitoringAlert | 10 | externalID = 1005 cs1Label = url cs1 = https://center/monitoring msg = Merkezi, merkezi tarafından kullanılan veritabanı kullanılamıyor. Son 30/1/2018 tarihinde çalıştıran görülmemiş 10:39:39: 00 UTC.

> [!NOTE]
> Tüm izleme uyarıları, yukarıdakilerle aynı şablonu ile birlikte gönderilir.



## <a name="see-also"></a>Ayrıca Bkz.
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
