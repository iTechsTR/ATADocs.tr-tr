---
title: Azure ATP SIEM günlük başvurusu | Microsoft Docs
description: Azure ATP SIEM'nize gönderilen şüpheli etkinlik günlüğü örnekleri sağlar.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/20/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 3261155c-3c72-4327-ba29-c113c63a4e6d
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: 88056e1dd7523b77569241ccbe3a967c4b7a26ef
ms.sourcegitcommit: 56886d06abd25035ffc9885c69aca9b0ebf14abc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43039064"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="azure-atp-siem-log-reference"></a>Azure ATP SIEM günlük başvurusu

Azure ATP şüpheli etkinlik ve izleme uyarısı olaylarını sıem'nize iletebilir. Şüpheli etkinlik olayları CEF biçimindedir. Bu başvuru makalesinde, SIEM’nize gönderilen şüpheli etkinlik günlükleri için örnekler sağlanmaktadır.

## <a name="sample-azure-atp-suspicious-activities-in-cef-format"></a>CEF biçiminde örnek Azure ATP şüpheli etkinlikleri
Aşağıdaki alanlar ve bunların değerleri SIEM’nize iletilir:

-   start – uyarının başlangıç saati
-   suser – uyarıda bahsi geçen hesap (genellikle kullanıcı hesabıdır)
-   shost – bu uyarının kaynak makinesi
-   sonucu – uyarılar için bu uyarıda gerçekleşen etkinliğin başarı/başarısızlık olduğu  
-   msg – uyarının açıklaması
-   CNT – (parolalar tahmin edilen bir miktarı sahip oldu örneğin deneme yanılma) uyarı bir sayısı sahip uyarılar için
-   app – uyarıda kullanılan protokol
-   externalID – olay kimliği Azure ATP bu uyarıya karşılık gelen olay günlüğüne yazar.
-   cs #label & cs # – bunlar CEF kullanılacak veren müşteri dizeleri, ' % s'cs #label yeni alanın adıdır ve cs # ise değerdir, örneğin: cs1Label = url cs1 =https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa

Bu örnekte cs1, uyarının URL'sini içeren bir alandır.

## <a name="sample-logs"></a>Örnek günlükler

Aşağıdaki günlükleri örnek RFC 5242 ile uyumludur, ancak Azure ATP mevcut özellikler RFC 3164 da destekler.

Öncelikler:

- 3 = düşük
- 5 = Orta
- 10 = yüksek

### <a name="bruteforce--ldap"></a>BruteForce – LDAP
02 21 2018 16:20:21 Auth.Warning 192.168.0.220 1 2018-02-21T14:20:06.156238 + 00:00 merkezi CEF 6076'ya LdapBruteForceSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | LdapBruteForceSecurityAlert | Basit LDAP bağlama kullanan deneme yanılma saldırısı | 5 | başlangıç 2018 =-02-21T14:19:41.7422810Z app = Ldap suser Wofford Thurston shost = clıent1 msg = Wofford Thurston (yazılım mühendisi) üzerinde Protokolü denendi Ldap kullanarak bir deneme yanılma saldırısı = İSTEMCİ1'den (100 tahmin girişim sayısı). CNT 100 externalID = 2004 cs1Label = url cs1 = =https://contoso-corp.atp.azure.com/securityAlert/57b8ac96-7907-4971-9b27-ec77ad8c029a


### <a name="bruteforce"></a>BruteForce
02 21 2018 16:19:20 Auth.Warning 192.168.0.220 1 2018-02-21T14:19:15.397995 + 00:00 merkezi CEF 6076'ya BruteForceSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | BruteForceSecurityAlert | Şüpheli kimlik doğrulama hataları | 5 | Başlat = 2018-02-21T14:19:03.3831122Z app = Kerberos shost = clıent1 msg = = İSTEMCİ1'den olası bir deneme yanılma saldırısı algılandı gösteren şüpheli kimlik doğrulama hataları. externalID = 2023 cs1Label = url cs1 =https://contoso-corp.atp.azure.com/securityAlert/fea88fc7-4110-454d-816d-349032474fd6
### <a name="privilege-escalation"></a>Ayrıcalık yükseltme
#### <a name="silver"></a>Gümüş
02 21 2018 16:19:20 Auth.Error 192.168.0.220 1 2018-02-21T14:19:15.186167 + 00:00 merkezi CEF 6076'ya ForgedPacSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | ForgedPacSecurityAlert | Sahte yetkilendirme verileri kullanan ayrıcalık yükseltme saldırısı | 10 | Başlangıç = 2018-02-21T14:19:02.8595383Z uygulama Kerberos suser = user1 msg = = user1 İSTEMCİ1'den host/domain1.test.local için sahte yetkilendirme verileri kullanılarak ayrıcalıklar yükseltilmeye çalışıldı. externalID = 2013 cs1Label = url cs1 =https://contoso-corp.atp.azure.com/securityAlert/029189e1-6bb4-490b-bcaf-5fac4457e9f3
#### <a name="gold"></a>Altın
02 21 2018 16:19:20 Auth.Error 192.168.0.220 1 2018-02-21T14:19:14.358037 + 00:00 merkezi CEF 6076'ya ForgedPacSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | ForgedPacSecurityAlert | Sahte yetkilendirme verileri kullanan ayrıcalık yükseltme saldırısı | 10 | Başlangıç = 2018-02-21T14:19:02.8595383Z uygulama Kerberos suser = user1 msg = = user1 tarafından DC1'de ayrıcalıkları host/domain1.test.local için İSTEMCİ1'den sahte yetkilendirme verileri kullanarak yükseltmek için başarısız oldu. externalID = 2013 cs1Label = url cs1 =https://contoso-corp.atp.azure.com/securityAlert/f3359eff-cb59-44b9-82b6-5e82ff06e6c8
### <a name="golden-ticket"></a>Altın Bilet
02 21 2018 16:22:39 Auth.Error 192.168.0.220 1 2018-02-21T14:22:34.274054 + 00:00 merkezi CEF 6076'ya GoldenTicketSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | GoldenTicketSecurityAlert | Kerberos altın anahtar etkinliği | 10 | Başlangıç = 2018-02-21T14:19:03.2416152Z uygulama Kerberos suser = Lanell Campos msg = Lanell Campos (yazılım mühendisi) ın Kerberos anahtarı, olası bir altın bilet saldırısına işaret eden şüpheli kullanım =, algılandı. externalId=2022 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/702c836e-6f49-4479-9892-80e8bccbfac0
### <a name="kerberos-golden-ticket-nonexistent-account"></a>Kerberos altın anahtar var olmayan hesap
07-01-2018'den 14:28:49 Auth.Error 192.168.0.100 1 2018-07-01T11:28:35.546638 + 00:00 merkezi CEF 38768 ForgedPrincipalSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.39.0.0 | ForgedPrincipalSecurityAlert | Kerberos altın bilet - mevcut olmayan hesap | 10 | Başlat 2018 =-07-01T09:48:31.2567987Z app = Kerberos Active Directory'de bulunmayan, suser=domain1.test.local\fake msg=domain1.test.local\fake Kerberos bileti kullanılır. Bilet 3 kaynaklara erişmek için 2 bilgisayarlardan algılandı. Bu, olası bir altın bilet saldırısına işaret edebilir. externalID = 2027 cs1Label = url cs1 =https://contoso-corp.atp.azure.com:13000/securityAlert/98f050d4-9134-429c-8e54-d8eeb19849c4


### <a name="honey-token-activity"></a>Honey Token Etkinliği
02 21 2018 16:20:36 Auth.Warning 192.168.0.220 1 2018-02-21T14:20:34.106162 + 00:00 merkezi CEF 6076'ya HoneytokenActivitySecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | HoneytokenActivitySecurityAlert | Honeytoken etkinliği | 5 | başlangıç = 2018-02-21T14:20:26.6705617Z uygulama Kerberos suser = honey msg = aşağıdaki = etkinlikleri tarafından DC1 aracılığıyla CLIENT2 için honey: \r\nLogged içinde gerçekleştirildi. externalID = 2014 cs1Label = url cs1 =https://contoso-corp.atp.azure.com/securityAlert/9249fe9a-c883-46dd-a4da-2a1fca5f211c
### <a name="suspicious-replication-of-directory-services"></a>Dizin hizmetlerinin şüpheli çoğaltması
02 21 2018 16:21:22 Auth.Error 192.168.0.220 1 2018-02-21T14:21:13.978554 + 00:00 merkezi CEF 6076'ya DirectoryServicesReplicationSecu ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | DirectoryServicesReplicationSecurityAlert | Dizin hizmetlerinin kötü amaçlı çoğaltması | 10 | Başlangıç = 2018-02-21T14:19:03.9975656Z uygulama Drsr shost = clıent1 msg = amaçlı çoğaltma istekleri İSTEMCİ1 DC1'de user1 tarafından başarıyla gerçekleştirildi. Sonuç başarılı externalID = 2006 cs1Label = url cs1 = =https://contoso-corp.atp.azure.com/securityAlert/cb95648e-1b6f-4d3b-81b9-7605532787d7
### <a name="suspicious-replication-request-potential-dcshadow-attack"></a>Şüpheli çoğaltma isteği (olası DcShadow saldırı)
07-12-2018'den 11:18:37 Auth.Error 192.168.0.200 1 2018-07-12T08:18:32.265989 + 00:00 DC1 CEF 3868 DirectoryServicesRogueReplicatio ï» ¿0 | Microsoft | Azure ATP | 2.40.0.0 | DirectoryServicesRogueReplicationSecurityAlert | **Şüpheli çoğaltma isteği (olası DcShadow saldırı)**| 10 | Başlangıç 2018 =-07-12T08:17:55.3816102Z **uygulama çoğaltma etkinliği =** shost = clıent1 msg = İSTEMCİ1'de, ama geçerli bir etki alanı değil domain1.test.local, denetleyicisi, DC1'de dizin nesneleri için değişiklikler gönderdi. externalID = 2029 cs1Label = url cs1 =https://contoso-corp.atp.azure.com:13000/securityAlert/1d5d1444-12cf-4db9-be48-39ebc2f51515
### <a name="suspicious-domain-controller-promotion-potential-dcshadow-attack"></a>Şüpheli etki alanı denetleyicisi yükseltme (olası DcShadow saldırı)
07-12-2018'den 11:18:07 Auth.Error 192.168.0.200 1 2018-07-12T08:18:06.883880 + 00:00 DC1 CEF 3868 DirectoryServicesRoguePromotionS ï» ¿0 | Microsoft | Azure ATP | 2.40.0.0 | DirectoryServicesRoguePromotionSecurityAlert | **Şüpheli etki alanı denetleyicisi yükseltme (olası DcShadow saldırı)**| 10 | Başlangıç 2018 =-07-12T08:17:55.4067092Z app = Ldap shost = clıent1 msg = İSTEMCİ1'de, ama bir bilgisayar bir etki alanı denetleyicisi olarak kayıtlı domain1.test.local içinde = DC1'de. externalID = 2028 cs1Label = url cs1 =https://contoso-corp.atp.azure.com:13000/securityAlert/97c59b43-dc18-44ee-9826-8fd5d03bd53

### <a name="malicious-data-protection-private-information-request"></a>Kötü Amaçlı Veri Koruma Özel Bilgi İsteği
02 21 2018 16:22:08 Auth.Error 192.168.0.220 1 2018-02-21T14:21:54.080266 + 00:00 merkezi CEF 6076'ya RetrieveDataProtectionBackupKeyS ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | RetrieveDataProtectionBackupKeySecurityAlert | Kötü amaçlı veri koruma özel bilgi isteği | 10 | Başlangıç 2018 =-02-21T14:19:41.8382786Z app = LsaRpc shost = clıent1 msg = = user1 gerçekleştirilen DC1'den DPAPI etki alanı yedek anahtarını almak için clıent1 1 başarılı çalışır. externalID = 2020 cs1Label = url cs1 =https://contoso-corp.atp.azure.com/securityAlert/b22221d1-764a-4fae-a5ce-e6a0c69dc55a

### <a name="over-pass-the-hash"></a>Over-pass-the-hash
02 21 2018 16:21:07 Auth.Warning 192.168.0.220 1 2018-02-21T14:20:54.145833 + 00:00 merkezi CEF 6076'ya EncryptionDowngradeSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | EncryptionDowngradeSecurityAlert | Şifreleme düşürme etkinliği | 5 | Başlat = 2018-02-21T14:19:41.8737870Z uygulama Kerberos msg = şifreleme yöntemini = AS_REQ Encrypted_Timestamp alanının İSTEMCİ1 iletiden daha önceden öğrenilen davranışına göre hızdan azalttı. Bu, CLIENT1 adlı istemciden Overpass-the-Hash ile kimlik bilgilerini çalmanın bir sonucu olabilir. externalID = 2011 cs1Label = url cs1 =https://contoso-corp.atp.azure.com/securityAlert/6354b9ed-6a39-4f5b-b10e-f51bbee879d2
### <a name="pass-the-hash"></a>Pass-the-hash
02 21 2018 17:04:47 Auth.Error 192.168.0.220 1 2018-02-21T15:04:33.537583 + 00:00 merkezi CEF 6076'ya PassTheHashSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | PassTheHashSecurityAlert | Pass--Hash saldırısı kullanan kimlik hırsızlığı | 10 | Başlangıç = 2018-02-21T15:02:22.2577465Z uygulama Kerberos suser = Eugene Jenkins msg = Eugene Jenkins = (yazılım mühendisi)'ın karma, daha önce (yazılım Eugene Jenkins tarafından oturum açmış bilgisayarların birinden Çalındı Mühendislik) ve İSTEMCİ1'den kullanılır. externalID = 2017 cs1Label = url cs1 =https://contoso-corp.atp.azure.com/securityAlert/511f1487-2915-477d-be2e-04cfba702ccd
### <a name="account-enumeration"></a>Hesap listeleme
02 21 2018 16:19:35 Auth.Warning 192.168.0.220 1 2018-02-21T14:19:27.540731 + 00:00 merkezi CEF 6076'ya AccountEnumerationSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | AccountEnumerationSecurityAlert | Hesap numaralandırma kullanarak keşif | 5 | başlangıç = 2018-02-21T14:19:02.6045416Z app = Kerberos shost = clıent1 suser = LMaldonado msg = = İSTEMCİ1'den kaynaklanan Kerberos protokolünü kullanarak listeleme etkinliği gözlemlendi şüpheli hesap ve başarıyla Lamon Maldonado (yazılım mühendisi) tahmin. externalID = 2003 cs1Label = url cs1 =https://contoso-corp.atp.azure.com/securityAlert/eb6a35da-ff7f-4ab5-a1b5-a07529a89e6d
### <a name="dns-recon"></a>DNS Keşfi
02 21 2018 16:20:06 Auth.Warning 192.168.0.220 1 2018-02-21T14:19:54.063994 + 00:00 merkezi CEF 6076'ya DnsReconnaissanceSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | DnsReconnaissanceSecurityAlert | DNS kullanarak keşif | 5 | Başlat 2018 =-02-21T14:19:41.9417776Z app = Dns shost = = clıent1 istek tanıtım sorgu requestMethod = Axfr nedeni = NoError outcome = Success msg = = şüpheli DNS etkinliği gözlemlendi (Bu, bir DNS sunucusu olmayan) İSTEMCİ1 kaynaklanan. Sorgu tanıtım için sorgu (AXFR tipi) oluştu. Yanıt NoError:. externalID = 2007 cs1Label = url cs1 =https://contoso-corp.atp.azure.com/securityAlert/6f69e1e7-304a-4054-8edf-33f26c1f004c


### <a name="smb-session-enumeration"></a>SMB Oturum listeleme
02 21 2018 16:21:22 Auth.Warning 192.168.0.220 1 2018-02-21T14:21:13.962930 + 00:00 merkezi CEF 6076'ya EnumerateSessionsSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | EnumerateSessionsSecurityAlert | SMB oturumu listeleme kullanarak keşif | 5 | Başlat = 2018-02-21T14:19:03.2071170Z app = SrvSvc shost = clıent1 msg = SMB oturumu listeleme girişimleri hedeflenerek başarıyla gerçekleştirildi Eugene Jenkins (bilgisayar kullanıcı2) gösterme user1 tarafından DC1'de, İSTEMCİ1 = . externalId=2012 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/622c38ab-324f-4c1f-9caa-1fe85db3b440
### <a name="sam-r-enumeration"></a>SAM-R numaralandırması
02 21 2018 16:22:08 Auth.Warning 192.168.0.220 1 2018-02-21T14:21:54.267658 + 00:00 merkezi CEF 6076'ya SamrReconnaissanceSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | SamrReconnaissanceSecurityAlert | Dizin Hizmetleri listelemesi kullanarak keşif | 5 | Başlat = 2018-02-21T14:19:41.9912772Z app = Samr shost = clıent1 suser = user1 outcome = Success msg = DC1'den karşı SAMR protokolü kullanılarak numaralandırmalar denendi şu Dizin Hizmetleri = User1 tarafından domain1.test.local içindeki tüm gruplar listelenmeye CLIENT1:\r\nSuccessful. externalID = 2019 cs1Label = url cs1 =https://contoso-corp.atp.azure.com/securityAlert/f295029a-ffae-408b-9dd0-55424c81eac0
### <a name="remote-execution"></a>Uzaktan Yürütme
02 21 2018 16:22:08 Auth.Warning 192.168.0.220 1 2018-02-21T14:21:54.267658 + 00:00 merkezi CEF 6076'ya RemoteExecutionSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | RemoteExecutionSecurityAlert | Uzaktan yürütme denemesi algılandı | 5 | başlangıç = 2018-02-21T14:19:41.9912772Z uygulama WMI shost = clıent1 suser = user1 outcome = Success msg = CLIENT1:\r\nSuccessful bir veya daha fazla WMI uzaktan yürütme denemesi DC1 yapıldığı şu uzaktan yürütme = user1 olarak yöntemler. externalID = 2019 cs1Label = url cs1 =https://contoso-corp.atp.azure.com/securityAlert/f295029a-ffae-408b-9dd0-55424c81eac0
### <a name="skeleton-key"></a>Maymuncuk
02 21 2018 16:21:07 Auth.Warning 192.168.0.220 1 2018-02-21T14:20:54.145833 + 00:00 merkezi CEF 6076'ya EncryptionDowngradeSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | EncryptionDowngradeSecurityAlert | Şifreleme düşürme etkinliği | 5 | Başlat = 2018-02-21T14:19:41.8737870Z uygulama Kerberos msg = şifreleme yöntemini = KRB_ERR ETYPE_INFO2 alanının İSTEMCİ1 iletiden daha önceden öğrenilen davranışına göre hızdan azalttı. Bu Maymuncuk DC1'de bir sonucu olabilir. externalID = 2011 cs1Label = url cs1 =https://contoso-corp.atp.azure.com/securityAlert/6354b9ed-6a39-4f5b-b10e-f51bbee879d2

### <a name="unusual-protocol-implementation"></a>Olağan dışı protokol uygulanması
02 21 2018 16:21:22 Auth.Warning 192.168.0.220 1 2018-02-21T14:21:13.916050 + 00:00 merkezi CEF 6076'ya AbnormalProtocolSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | AbnormalProtocolSecurityAlert | Olağan dışı protokol uygulaması | 5 | başlangıç = 2018-02-21T14:19:03.1981155Z uygulama Ntlm shost = CLIENT2 outcome = Success msg = var olan CLIENT2 DC1'de kimlik doğrulama girişiminde = olağan dışı protokol uygulaması kullanarak. Bu, Pass-the-Hash ve deneme yanılma gibi saldırıları yürütmek için kullanılan kötü amaçlı bir aracın sonucu olabilir. externalID = 2002 cs1Label = url cs1 =https://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs1 =https://192.168.0.220/suspiciousActivity/5909cce38ca1ec04d05f4ab4

### <a name="malicious-service-creation"></a>Kötü amaçlı hizmeti oluşturma
02 21 2018 16:20:06 Auth.Warning 192.168.0.220 1 2018-02-21T14:19:54.254930 + 00:00 merkezi CEF 6076'ya MaliciousServiceCreationSecurity ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | MaliciousServiceCreationSecurityAlert | Şüpheli hizmet oluşturma işlemi | 5 | başlangıç = 2018-02-21T14:19:41.7897808Z uygulama ServiceInstalledEvent shost = clıent1 msg = İSTEMCİ1'de kötü amaçlı olabilecek komutlar yürütmek için oluşturduğunuz user1 MaliciousService =. externalID = 2026 cs1Label = url cs1 =https://contoso-corp.atp.azure.com/securityAlert/179229b6-b791-4895-b5aa-fdf3747a325c

### <a name="pass-the-ticket"></a>Anahtar geçişi
02 21 2018 17:04:47 Auth.Error 192.168.0.220 1 2018-02-21T15:04:33.537583 + 00:00 merkezi CEF 6076'ya PassTheTicketSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.22.4228.22540 | PassTheTicketSecurityAlert | Pass--Ticket saldırısı kullanan kimlik hırsızlığı | 10 | Başlangıç = 2018-02-21T15:02:22.2577465Z uygulama Kerberos suser = Eugene Jenkins msg = Eugene Jenkins (yazılım mühendisi) ın Kerberos biletleri Admin-PC Victim-PC çalınması ve krbtgt/EtkiAlanı1 erişmek için kullanılan =. TEST. YEREL. externalID = 2017 cs1Label = url cs1 =https://contoso-corp.eng.atp.azure.com/securityAlert/511f1487-2915-477d-be2e-04cfba702ccd

### <a name="suspicious-vpn-connection"></a>Şüpheli VPN bağlantısı
07-03-2018 13:13:12 Auth.Warning 192.168.0.200 1 2018-07-03T10:13:06.187834 + 00:00 DC1 CEF 2520 AbnormalVpnSecurityAlert ï» ¿0 | Microsoft | Azure ATP | 2.39.0.0 | AbnormalVpnSecurityAlert | Şüpheli VPN bağlantısı | 5 | başlangıç 2018 =-06-30T15:34:05.3887333Z uygulama VpnConnection suser = user1 msg = = user1 3 konumlardan 3 bilgisayarları kullanarak VPN bağlı.     externalID = 2025 cs1Label = url cs1 =https://contoso-corp.eng.atp.azure.com:13000/securityAlert/88c46b0e-372f-4c06-9935-67bd512c4f68


## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)