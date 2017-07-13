---
title: "ATA SIEM günlük başvurusu | Microsoft Docs"
description: "ATA’dan SIEM’nize gönderilen şüpheli etkinlik günlüğü örnekleri sağlar."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/21/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 601b48ba-a327-4aff-a1f9-2377a2bb7a42
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: ca460647fbed07820e8d19083d5aca19a05bc0a8
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*


# ATA SIEM günlük başvurusu
<a id="ata-siem-log-reference" class="xliff"></a>

ATA, şüpheli etkinlik ve izleme uyarısı olaylarını SIEM'nize iletebilir. Şüpheli etkinlik olayları CEF biçimindedir. Bu başvuru makalesinde, SIEM’nize gönderilen şüpheli etkinlik günlükleri için örnekler sağlanmaktadır.

## CEF biçiminde örnek ATA şüpheli etkinlikleri
<a id="sample-ata-suspicious-activities-in-cef-format" class="xliff"></a>
Aşağıdaki alanlar ve bunların değerleri SIEM’nize iletilir:

-   start – uyarının başlangıç saati
-   suser – uyarıda bahsi geçen hesap (genellikle kullanıcı hesabıdır)
-   shost – bu uyarının kaynak makinesi
-   outcome – uyarıda gerçekleşen etkinliğin başarı/başarısızlık durumu söz konusu olduğunda  
-   msg – uyarının açıklaması
-   cnt – uyarının bir gerçekleşme miktarı söz konusu olduğunda (örneğin bir deneme yanılmada parola için kaç tahmin yapıldığı)
-   app – uyarıda kullanılan protokol
-   externalId – ATA’nın olay günlüğüne yazdığı ve uyarıya karşılık gelen olay kimliği
-   cs#label ve cs# – bunlar CEF’in kullanmaya izin verdiği müşteri dizeleridir. cs#label yeni alanın adıdır ve cs# ise değerdir, örneğin: cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa

Bu örnekte cs1, uyarının URL'sini içeren bir alandır.

## Örnek günlükler
<a id="sample-logs" class="xliff"></a>

Öncelikler: 3=Düşük 5=Orta 10=Yüksek

### BruteForce – LDAP
<a id="bruteforce--ldap" class="xliff"></a>
05-03-2017          13:35:01               Auth.Warning    192.168.0.220     May  3 10:35:01 CENTER ATA:CEF:0|Microsoft|ATA|.5942.64854|BruteForceSuspiciousActivity|Brute force attack using LDAP simple bind|5|start=2017-05-03T10:34:57.2785534Z app=Ldap suser=Darris Woods shost=CLIENT1 msg=A brute force attack using the Ldap protocol was attempted on Darris Woods (Software Engineer) from CLIENT1 (76 guess attempts). cnt=76 cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70

05-03-2017          13:35:05               Auth.Warning    192.168.0.220     May  3 10:35:05 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|BruteForceSuspiciousActivity|Brute force attack using LDAP simple bind|5|start=2017-05-03T10:34:58.7004159Z app=Ldap suser=Dino Hopkins shost=CLIENT1 msg=A brute force attack using the Ldap protocol was attempted on Dino Hopkins (Software Engineer) from CLIENT1 (3 guess attempts). cnt=3 cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70

05-03-2017          13:35:05               Auth.Warning    192.168.0.220     May  3 10:35:05 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|BruteForceSuspiciousActivity|Brute force attack using LDAP simple bind|5|start=2017-05-03T10:34:59.7269332Z app=Ldap suser=Dino Hopkins shost=CLIENT1 msg=A successful brute force attack using the Ldap protocol was attempted on Dino Hopkins (Software Engineer) from CLIENT1 (77 guess attempts). cnt=77 cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70
### BruteForce
<a id="bruteforce" class="xliff"></a>
05-14-2017          13:27:05               Auth.Warning    192.168.0.220     1 2017-05- ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|BruteForceSuspiciousActivity|Suspicious authentication failures|5|start=2017-05-14T10:27:04.3904739Z app=Kerberos shost=CLIENT1 msg=Suspicious authentication failures indicating a potential brute-force attack were detected from CLIENT1. externalId=2023 cs1Label=url cs1=https://center/suspiciousActivity/591830f98ca1ec11d0c0d7f5
### Ayrıcalık yükseltme
<a id="privilege-escalation" class="xliff"></a>
#### Gümüş
<a id="silver" class="xliff"></a>
05-10-2017          17:14:15               Auth.Error           192.168.0.220     1 2017-05-10T14:14:15.589415+00:00 CENTER ATA 596 ForgedPacSuspiciousActivity ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|ForgedPacSuspiciousActivity|Privilege escalation using forged authorization data|10|start=2017-05-10T14:11:51.8053059Z app=Kerberos suser=user1 msg=user1 attempted to escalate privileges to HOST/client1 from CLIENT2 by using forged authorization data. externalId=2013 cs1Label=url cs1=https://center/suspiciousActivity/591320378ca1ec02543e4747
#### Altın
<a id="gold" class="xliff"></a>
05-10-2017          17:13:30               Auth.Error           192.168.0.220     1 2017-05-10T14:13:30.244377+00:00 CENTER ATA 596 ForgedPacSuspiciousActivity ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|ForgedPacSuspiciousActivity|Privilege escalation using forged authorization data|10|start=2017-05-10T14:11:27.6455273Z app=Kerberos suser=user1 msg=user1 attempted to escalate privileges against DC4 from CLIENT1 by using forged authorization data. externalId=2013 cs1Label=url cs1=https://center/suspiciousActivity/5913200a8ca1ec02543e3ea8
### Altın Bilet
<a id="golden-ticket" class="xliff"></a>
05-14-2017          15:57:10               Auth.Warning    192.168.0.220     1 2017-05-14T12:57:10.392730+00:00 CENTER ATA 4732 EncryptionDowngradeSuspiciousAct ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|EncryptionDowngradeSuspiciousActivity|Encryption downgrade activity|5|start=2017-05-14T12:55:08.6913033Z app=Kerberos msg=The encryption method of the TGT field of TGS_REQ message from CLIENT1 has been downgraded based on previously learned behavior. Bu, CLIENT1’de kullanımda olan Altın Anahtarın sonucu olabilir. externalId=2009 cs1Label=url cs1=https://center/suspiciousActivity/591854268ca1ec127ceec396
### Honey Token Etkinliği
<a id="honey-token-activity" class="xliff"></a>
05-11-2017          16:49:10               Auth.Warning    192.168.0.220     1 2017-05-11T13:49:10.725605+00:00 CENTER ATA 876 HoneytokenActivitySuspiciousActi ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|HoneytokenActivitySuspiciousActivity|Honeytoken activity|5|start=2017-05-11T13:49:09.6455794Z app=Kerberos suser=privtriservice msg=The following activities were performed by privtriservice:\r\nAuthenticated from DC1 using NTLM against corporate resources via DC1. externalId=2014 cs1Label=url cs1=https://center/suspiciousActivity/59146bd68ca1ec036ce57d29
### Dizin hizmetlerinin şüpheli çoğaltması
<a id="suspicious-replication-of-directory-services" class="xliff"></a>
May  3 11:02:28 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|DirectoryServicesReplicationSuspiciousActivity|Malicious replication of directory services|10|start=2017-05-03T11:00:13.6560919Z suser=user1 shost=CLIENT1 outcome=Failure msg=Malicious replication requests were attempted by user1, from CLIENT1 against DC1. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b8c48ca1ec04d05ed28d
### Kötü Amaçlı Veri Koruma Özel Bilgi İsteği
<a id="malicious-data-protection-private-information-request" class="xliff"></a>
May  3 13:39:18 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|RetrieveDataProtectionBackupKeySuspiciousActivity|Malicious Data Protection Private Information Request|10|start=2017-05-03T13:37:06.4039886Z app=LsaRpc shost=CLIENT1 suser= outcome=Success msg=An unknown user performed 4 successful attempts from CLIENT1 to retrieve DPAPI domain backup key from DC1. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909dd868ca1ec04d05fb01d
### Büyük Çaplı Nesne Silme
<a id="massive-object-deletion" class="xliff"></a>
05-14-2017          14:38:34               Auth.Warning    192.168.0.220     1 2017-05-14T11:38:34.898810+00:00 CENTER ATA 3748 MassiveObjectDeletionSuspiciousA ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|MassiveObjectDeletionSuspiciousActivity|Massive object deletion|5|start=2017-05-14T11:33:32.0000000Z msg=496 objects (9.75% of total AD objects) were deleted over a period of no time from domain domain1.test.local. cnt=496 externalId=2016 cs1Label=url cs1=https://center/suspiciousActivity/591841ba8ca1ec0ea4ad587a
### Over-pass-the-hash
<a id="over-pass-the-hash" class="xliff"></a>
05-14-2017          12:07:46               Auth.Warning    192.168.0.220     1 2017-05-14T09:07:46.652319+00:00 CENTER ATA 1116 EncryptionDowngradeSuspiciousAct ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|EncryptionDowngradeSuspiciousActivity|Encryption downgrade activity|5|start=2017-05-14T09:07:44.9933773Z app=Kerberos msg=The encryption method of the Encrypted_Timestamp field of AS_REQ message from CLIENT1 has been downgraded based on previously learned behavior. Bu, CLIENT1’den Overpass-the-Hash kullanılarak kimlik bilgilerini çalmanın bir sonucu olabilir. externalId=2010 cs1Label=url cs1=https://center/suspiciousActivity/59181e628ca1ec045cdfa929
### Pass-the-hash
<a id="pass-the-hash" class="xliff"></a>
05-10-2017          17:48:51               Auth.Error           192.168.0.220     1 2017-05-10T14:48:51.998620+00:00 CENTER ATA 596 PassTheHashSuspiciousActivity ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|PassTheHashSuspiciousActivity|Identity theft using Pass-the-Hash attack|10|start=2017-05-10T14:46:50.9463800Z app=Ntlm suser=user2 msg=user2's hash was stolen from one of the computers previously logged into by user2 and used from CLIENT1. externalId=2017 cs1Label=url cs1=https://center/suspiciousActivity/591328538ca1ec02543f9a1a
### Hesap listeleme
<a id="account-enumeration" class="xliff"></a>
05-10-2017          16:44:22               Auth.Warning    192.168.0.220     1 2017-05-10T13:44:22.706381+00:00 CENTER ATA 596 AccountEnumerationSuspiciousActi ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|AccountEnumerationSuspiciousActivity|Reconnaissance using account enumeration|5|start=2017-05-10T13:44:20.9930644Z app=Kerberos shost=CLIENT3 msg=Suspicious account enumeration activity using Kerberos protocol, originating from CLIENT3, was detected. Saldırgan, hesap adları için toplamda 72 tahmin denemesinde bulundu, 2 tahmin denemesi, Active Directory’deki mevcut hesap adlarıyla eşleşti. externalId=2003 cs1Label=url cs1=https://center/suspiciousActivity/591319368ca1ec02543c56ee
### DNS Keşfi
<a id="dns-recon" class="xliff"></a>
05-03-2017          13:16:57               Auth.Warning    192.168.0.220     May  3 10:16:57 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|DnsReconnaissanceSuspiciousActivity|Reconnaissance using DNS|5|start=2017-05-03T10:16:41.8297467Z app=Dns shost=CLIENT1 msg=Suspicious DNS activity was observed, originating from CLIENT1 (which is not a DNS server) against DC1. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa 05-03-2017          13:24:21               Auth.Warning    192.168.0.220     May  3 10:24:21 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|DnsReconnaissanceSuspiciousActivity|Reconnaissance using DNS|5|start=2017-05-03T10:24:08.0950753Z app=Dns shost=CLIENT1 request=contoso.com requestMethod=Axfr reason=NameError outcome=Failure msg=Suspicious DNS activity was observed, originating from CLIENT1 (which is not a DNS server). Sorgu contoso.com’du (Axfr türü). Yanıt NameError’dı. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa
### SMB Oturum listeleme
<a id="smb-session-enumeration" class="xliff"></a>
May  3 11:55:43 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|EnumerateSessionsSuspiciousActivity|Reconnaissance using SMB Session Enumeration|5|start=2017-05-03T11:52:02.4360718Z app=SrvSvc shost=CLIENT1 msg=SMB session enumeration attempts were successfully performed from CLIENT1 against DC1, exposing user1 (daf::1). cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909c53f8ca1ec04d05f1cf1
### SAMR listeleme
<a id="samr-enumeration" class="xliff"></a>
May  3 11:44:48 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|SamrReconnaissanceSuspiciousActivity|Reconnaissance using directory services enumeration|5|start=2017-05-03T11:42:46.5911225Z app=Samr shost=CLIENT1 suser=user1 outcome=Success msg=The following directory services enumerations using SAMR protocol were attempted against DC1 from CLIENT1:\r\nSuccessful enumeration of all groups in domain1.test.local by user1 cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909c2b08ca1ec04d05f0e19
### Uzaktan Yürütme
<a id="remote-execution" class="xliff"></a>
May  3 12:36:47 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|RemoteExecutionSuspiciousActivity|Remote execution attempt detected|3|start=2017-05-03T12:34:32.3714348Z app=ServiceControl shost=CLIENT1 suser=Administrator outcome=Success msg=The following remote execution attempts were performed on DC1 from CLIENT1:\r\nSuccessful remote creation of PSEXESVC by Administrator. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909cedf8ca1ec04d05f5692
### Maymuncuk
<a id="skeleton-key" class="xliff"></a>
05-14-2017          12:13:12               Auth.Warning    192.168.0.220     1 2017-05-14T09:13:12.102468+00:00 CENTER ATA 1116 EncryptionDowngradeSuspiciousAct ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|EncryptionDowngradeSuspiciousActivity|Encryption downgrade activity|5|start=2017-05-14T09:13:03.3509467Z app=Kerberos msg=The encryption method of the ETYPE_INFO2 field of KRB_ERR message from CLIENT2 has been downgraded based on previously learned behavior. Bu, DC3’teki Skeleton Key’in bir sonucu olabilir. externalId=2011 cs1Label=url cs1=https://center/suspiciousActivity/59181fa88ca1ec045cdfe630
### Olağan dışı protokol uygulanması
<a id="unusual-protocol-implementation" class="xliff"></a>
May  3 12:28:19 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|AbnormalProtocolSuspiciousActivity|Unusual protocol implementation|5|start=2017-05-03T12:28:05.3561302Z app=Ntlm shost=CLIENT1 suser=Administrator outcome=Success msg=Administrator successfully authenticated from CLIENT1 against DC1 using an unusual protocol implementation. Bu, Pass-the-Hash ve deneme yanılma gibi saldırıları yürütmek için kullanılan kötü amaçlı bir aracın sonucu olabilir. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909cce38ca1ec04d05f4ab4
### Gizli hesap kimlik bilgilerinin açığa çıkarılması
<a id="sensitive-account-credentials-exposed" class="xliff"></a>
May  3 13:23:18 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|LdapSimpleBindCleartextPasswordSuspiciousActivity|Sensitive account credentials exposed|3|start=2017-05-03T13:23:09.7798589Z app=Ldap shost=CLIENT1 suser=Administrator msg=Administrator's credentials were exposed in clear text using LDAP simple bind from CLIENT1. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909d9c68ca1ec04d05f9918
### Hesap kimlik bilgilerini açığa çıkaran hizmetler
<a id="services-exposing-account-credentials" class="xliff"></a>
May  3 13:34:23 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|LdapSimpleBindCleartextPasswordSuspiciousActivity|Services exposing account credentials|3|start=2017-05-03T13:28:36.5159194Z app=Ldap shost=daf::220 msg=Services running on daf::220 (daf::220) expose account credentials in clear text using LDAP simple bind. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909dc5f8ca1ec04d05fa8b1
### Anahtar geçişi
<a id="pass-the-ticket" class="xliff"></a>
May  4 13:15:41 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|PassTheTicketSuspiciousActivity|Identity theft using Pass-the-Ticket attack|10|start=2017-05-04T13:13:44.5160000Z app=Kerberos shost=CLIENT1 suser=Administrator request=krbtgt/DOMAIN1.TEST.LOCAL msg=Administrator's Kerberos tickets were stolen from CLIENT2 to CLIENT1 and used to access krbtgt/DOMAIN1.TEST.LOCAL. cs2Label=ticketSourceComputer cs2=CLIENT2 cs3Label=ticketSourceComputerIpAddress cs3= cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/590b29168ca1ec0ba438acf6

## Ayrıca bkz:
<a id="see-also" class="xliff"></a>
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
