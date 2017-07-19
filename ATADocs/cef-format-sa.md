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
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*


# <a name="ata-siem-log-reference"></a>ATA SIEM günlük başvurusu

ATA, şüpheli etkinlik ve izleme uyarısı olaylarını SIEM'nize iletebilir. Şüpheli etkinlik olayları CEF biçimindedir. Bu başvuru makalesinde, SIEM’nize gönderilen şüpheli etkinlik günlükleri için örnekler sağlanmaktadır.

## <a name="sample-ata-suspicious-activities-in-cef-format"></a>CEF biçiminde örnek ATA şüpheli etkinlikleri
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

## <a name="sample-logs"></a>Örnek günlükler

Öncelikler: 3=Düşük 5=Orta 10=Yüksek

### <a name="bruteforce--ldap"></a>BruteForce – LDAP
05-03-2017          13:35:01               Auth.Warning    192.168.0.220     May  3 10:35:01 CENTER ATA:CEF:0|Microsoft|ATA|.5942.64854|BruteForceSuspiciousActivity|LDAP basit bağlama ile deneme yanılma saldırısı|5|start=2017-05-03T10:34:57.2785534Z app=Ldap suser=Darris Woods shost=CLIENT1 msg=CLIENT1 tarafından Darris Woods (Yazılım Mühendisi) adlı kullanıcıya Ldap protokolü ile bir deneme yanılma saldırısı denendi (76 tahmin denemesi). cnt=76 cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70

05-03-2017          13:35:05               Auth.Warning    192.168.0.220     May  3 10:35:05 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|BruteForceSuspiciousActivity|LDAP basit bağlama ile deneme yanılma saldırısı|5|start=2017-05-03T10:34:58.7004159Z app=Ldap suser=Dino Hopkins shost=CLIENT1 msg=CLIENT1 tarafından Dino Hopkins (Yazılım Mühendisi) adlı kullanıcıya Ldap protokolü ile bir deneme yanılma saldırısı denendi (3 tahmin denemesi). cnt=3 cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70

05-03-2017          13:35:05               Auth.Warning    192.168.0.220     May  3 10:35:05 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|BruteForceSuspiciousActivity|LDAP basit bağlama ile deneme yanılma saldırısı|5|start=2017-05-03T10:34:59.7269332Z app=Ldap suser=Dino Hopkins shost=CLIENT1 msg=CLIENT1 tarafından Dino Hopkins (Yazılım Mühendisi) adlı kullanıcıya Ldap protokolü ile başarılı bir deneme yanılma saldırısı girişimi oldu. (77 tahmin denemesi). cnt=77 cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70
### <a name="bruteforce"></a>BruteForce
05-14-2017          13:27:05               Auth.Warning    192.168.0.220     1 2017-05- ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|BruteForceSuspiciousActivity|Şüpheli kimlik doğrulama hataları|5|start=2017-05-14T10:27:04.3904739Z app=Kerberos shost=CLIENT1 msg=CLIENT1 adlı istemciden olası bir deneme yanılma saldırısına işaret eden şüpheli kimlik doğrulama hataları tespit edildi. externalId=2023 cs1Label=url cs1=https://center/suspiciousActivity/591830f98ca1ec11d0c0d7f5
### <a name="privilege-escalation"></a>Ayrıcalık yükseltme
#### <a name="silver"></a>Gümüş
05-10-2017          17:14:15               Auth.Error           192.168.0.220     1 2017-05-10T14:14:15.589415+00:00 CENTER ATA 596 ForgedPacSuspiciousActivity ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|ForgedPacSuspiciousActivity|Sahte yetkilendirme verileri ile ayrıcalık yükseltme|10|start=2017-05-10T14:11:51.8053059Z app=Kerberos suser=user1 msg=user1 adlı kullanıcı CLIENT2 adlı istemcide sahte yetkilendirme verileri kullanarak HOST/client1 adlı istemci için ayrıcalık yükseltmeyi denedi. externalId=2013 cs1Label=url cs1=https://center/suspiciousActivity/591320378ca1ec02543e4747
#### <a name="gold"></a>Altın
05-10-2017          17:13:30               Auth.Error           192.168.0.220     1 2017-05-10T14:13:30.244377+00:00 CENTER ATA 596 ForgedPacSuspiciousActivity ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|ForgedPacSuspiciousActivity|Sahte yetkilendirme verileri ile ayrıcalık yükseltme|10|start=2017-05-10T14:11:27.6455273Z app=Kerberos suser=user1 msg=user1 adlı kullanıcı CLIENT1 adlı istemcide sahte yetkilendirme verileri kullanarak DC4 adlı etki alanı denetleyicisine karşı ayrıcalık yükseltmeyi denedi. externalId=2013 cs1Label=url cs1=https://center/suspiciousActivity/5913200a8ca1ec02543e3ea8
### <a name="golden-ticket"></a>Altın Bilet
05-14-2017          15:57:10               Auth.Warning    192.168.0.220     1 2017-05-14T12:57:10.392730+00:00 CENTER ATA 4732 EncryptionDowngradeSuspiciousAct ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|EncryptionDowngradeSuspiciousActivity|Şifrelemeyi düşürme etkinliği|5|start=2017-05-14T12:55:08.6913033Z app=Kerberos msg=CLIENT1 tarafından gönderilen TGS_REQ iletisinin TGT alanında kullanılan şifreleme yöntemi önceden öğrenilen davranışa bağlı olarak düşürüldü. Bu, CLIENT1 adlı istemcide kullanımda olan Altın Anahtarın bir sonucu olabilir. externalId=2009 cs1Label=url cs1=https://center/suspiciousActivity/591854268ca1ec127ceec396
### <a name="honey-token-activity"></a>Honey Token Etkinliği
05-11-2017          16:49:10               Auth.Warning    192.168.0.220     1 2017-05-11T13:49:10.725605+00:00 CENTER ATA 876 HoneytokenActivitySuspiciousActi ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|HoneytokenActivitySuspiciousActivity|Honeytoken etkinliği|5|start=2017-05-11T13:49:09.6455794Z app=Kerberos suser=privtriservice msg=privtriservice tarafından şu etkinlikler gerçekleştirildi:\r\nDC1 üzerinden şirket kaynaklarına karşı NTLM kullanılarak DC1’den yetkilendirme. externalId=2014 cs1Label=url cs1=https://center/suspiciousActivity/59146bd68ca1ec036ce57d29
### <a name="suspicious-replication-of-directory-services"></a>Dizin hizmetlerinin şüpheli çoğaltması
May  3 11:02:28 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|DirectoryServicesReplicationSuspiciousActivity|Dizin hizmetlerinin kötü amaçlı çoğaltması|10|start=2017-05-03T11:00:13.6560919Z suser=user1 shost=CLIENT1 outcome=Failure msg=user1 tarafından DC1 adlı etki alanı denetleyicisine karşı CLIENT1 adlı istemciden kötü amaçlı çoğaltma istekleri denendi. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b8c48ca1ec04d05ed28d
### <a name="malicious-data-protection-private-information-request"></a>Kötü Amaçlı Veri Koruma Özel Bilgi İsteği
May  3 13:39:18 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|RetrieveDataProtectionBackupKeySuspiciousActivity|Kötü Amaçlı Veri Koruması Özel Bilgi İsteği|10|start=2017-05-03T13:37:06.4039886Z app=LsaRpc shost=CLIENT1 suser= outcome=Success msg=Bilinmeyen bir kullanıcı DC1 adlı etki alanı denetleyicisinden DPAPI etki alanı yedek anahtarını almak için CLIENT1 adlı istemciden 4 başarılı deneme yaptı. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909dd868ca1ec04d05fb01d
### <a name="massive-object-deletion"></a>Büyük Çaplı Nesne Silme
05-14-2017          14:38:34               Auth.Warning    192.168.0.220     1 2017-05-14T11:38:34.898810+00:00 CENTER ATA 3748 MassiveObjectDeletionSuspiciousA ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|MassiveObjectDeletionSuspiciousActivity|Büyük çaplı nesne silme|5|start=2017-05-14T11:33:32.0000000Z msg=496 nesne (toplam AD nesnelerinin %9.75’i) domain1.test.local adlı etki alanında belirtilmeyen bir süre içerisinde silindi. cnt=496 externalId=2016 cs1Label=url cs1=https://center/suspiciousActivity/591841ba8ca1ec0ea4ad587a
### <a name="over-pass-the-hash"></a>Over-pass-the-hash
05-14-2017          12:07:46               Auth.Warning    192.168.0.220     1 2017-05-14T09:07:46.652319+00:00 CENTER ATA 1116 EncryptionDowngradeSuspiciousAct ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|EncryptionDowngradeSuspiciousActivity|Şifrelemeyi düşürme etkinliği|5|start=2017-05-14T09:07:44.9933773Z app=Kerberos msg=CLIENT1 tarafından gönderilen AS_REQ iletisinin Encrypted_Timestamp alanında kullanılan şifreleme yöntemi önceden öğrenilen davranışa bağlı olarak düşürüldü. Bu, CLIENT1 adlı istemciden Overpass-the-Hash ile kimlik bilgilerini çalmanın bir sonucu olabilir. externalId=2010 cs1Label=url cs1=https://center/suspiciousActivity/59181e628ca1ec045cdfa929
### <a name="pass-the-hash"></a>Pass-the-hash
05-10-2017          17:48:51               Auth.Error           192.168.0.220     1 2017-05-10T14:48:51.998620+00:00 CENTER ATA 596 PassTheHashSuspiciousActivity ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|PassTheHashSuspiciousActivity|Pass-the-hash saldırısı ile kimlik hırsızlığı|10|start=2017-05-10T14:46:50.9463800Z app=Ntlm suser=user2 msg=user2 adlı kullanıcının karması user2 tarafından daha önce oturum açılan bir bilgisayardan çalındı ve CLIENT1 tarafından kullanıldı. externalId=2017 cs1Label=url cs1=https://center/suspiciousActivity/591328538ca1ec02543f9a1a
### <a name="account-enumeration"></a>Hesap listeleme
05-10-2017          16:44:22               Auth.Warning    192.168.0.220     1 2017-05-10T13:44:22.706381+00:00 CENTER ATA 596 AccountEnumerationSuspiciousActi ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|AccountEnumerationSuspiciousActivity|Hesap listeleme ile keşif|5|start=2017-05-10T13:44:20.9930644Z app=Kerberos shost=CLIENT3 msg=CLIENT3 kaynaklı, Kerberos protokolü kullanan şüpheli bir hesap listeleme etkinliği algılandı. Saldırgan, hesap adları için toplamda 72 tahmin denemesinde bulundu; 2 tahmin denemesi, Active Directory’deki mevcut hesap adlarıyla eşleşti. externalId=2003 cs1Label=url cs1=https://center/suspiciousActivity/591319368ca1ec02543c56ee
### <a name="dns-recon"></a>DNS Keşfi
05-03-2017          13:16:57               Auth.Warning    192.168.0.220     May  3 10:16:57 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|DnsReconnaissanceSuspiciousActivity|DNS ile keşif|5|start=2017-05-03T10:16:41.8297467Z app=Dns shost=CLIENT1 msg=DC1 adlı etki alanı denetleyicisine karşı DNS sunucusu olmayan CLIENT1 adlı istemciden kaynaklı şüpheli DNS etkinliği gözlemlendi. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa 05-03-2017          13:24:21               Auth.Warning    192.168.0.220     May  3 10:24:21 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|DnsReconnaissanceSuspiciousActivity|DNS ile keşif|5|start=2017-05-03T10:24:08.0950753Z app=Dns shost=CLIENT1 request=contoso.com requestMethod=Axfr reason=NameError outcome=Failure msg=DNS sunucusu olmayan CLIENT1 adlı istemciden kaynaklı şüpheli DNS etkinliği gözlemlendi. Sorgu contoso.com içindi (Axfr tipi). Yanıt NameError idi. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa
### <a name="smb-session-enumeration"></a>SMB Oturum listeleme
May  3 11:55:43 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|EnumerateSessionsSuspiciousActivity|SMB Oturum Listeleme ile keşif|5|start=2017-05-03T11:52:02.4360718Z app=SrvSvc shost=CLIENT1 msg=CLIENT1 adlı istemciden DC1 adlı etki alanı denetleyicisine karşı SMB oturum listeleme denemeleri başarıyla gerçekleştirildi, user1 (daf::1) adlı kullanıcı açığa çıkarıldı. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909c53f8ca1ec04d05f1cf1
### <a name="samr-enumeration"></a>SAMR listeleme
May  3 11:44:48 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|SamrReconnaissanceSuspiciousActivity|Dizin hizmetleri listeleme ile keşif|5|start=2017-05-03T11:42:46.5911225Z app=Samr shost=CLIENT1 suser=user1 outcome=Success msg=CLIENT1 adlı istemciden DC1 adlı etki alanı denetleyicisine karşı SAMR protokolü kullanan şu dizin hizmetleri listelemeleri denendi:\r\nuser1 tarafından domain1.test.local adlı etki alanındaki tüm gruplar başarıyla listelendi cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909c2b08ca1ec04d05f0e19
### <a name="remote-execution"></a>Uzaktan Yürütme
May  3 12:36:47 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|RemoteExecutionSuspiciousActivity|Uzaktan yürütme denemesi algılandı|3|start=2017-05-03T12:34:32.3714348Z app=ServiceControl shost=CLIENT1 suser=Administrator outcome=Success msg=CLIENT1 tarafından DC1 adlı etki alanı denetleyicisinde şu uzaktan yürütme denemeleri gerçekleştirildi:\r\nYönetici tarafından PSEXESVC başarıyla uzaktan oluşturuldu. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909cedf8ca1ec04d05f5692
### <a name="skeleton-key"></a>Maymuncuk
05-14-2017          12:13:12               Auth.Warning    192.168.0.220     1 2017-05-14T09:13:12.102468+00:00 CENTER ATA 1116 EncryptionDowngradeSuspiciousAct ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|EncryptionDowngradeSuspiciousActivity|Şifrelemeyi düşürme etkinliği|5|start=2017-05-14T09:13:03.3509467Z app=Kerberos msg=CLIENT2 tarafından gönderilen KRB_ERR iletisinin ETYPE_INFO2 alanında kullanılan şifreleme yöntemi önceden öğrenilen davranışa bağlı olarak düşürüldü. Bu, DC3’teki bir Skeleton Key’in sonucu olabilir. externalId=2011 cs1Label=url cs1=https://center/suspiciousActivity/59181fa88ca1ec045cdfe630
### <a name="unusual-protocol-implementation"></a>Olağan dışı protokol uygulanması
May  3 12:28:19 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|AbnormalProtocolSuspiciousActivity|Olağan dışı protokol uygulaması|5|start=2017-05-03T12:28:05.3561302Z app=Ntlm shost=CLIENT1 suser=Administrator outcome=Success msg=Yönetici olağan dışı bir protokol uygulaması kullanarak CLIENT1 adlı istemciden DC1 adlı etki alanı denetleyicisine karşı başarıyla kimlik doğruladı. Bu, Pass-the-Hash ve deneme yanılma gibi saldırıları yürütmek için kullanılan kötü amaçlı bir aracın sonucu olabilir. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909cce38ca1ec04d05f4ab4
### <a name="sensitive-account-credentials-exposed"></a>Gizli hesap kimlik bilgilerinin açığa çıkarılması
May  3 13:23:18 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|LdapSimpleBindCleartextPasswordSuspiciousActivity|Gizli hesap kimlik bilgileri açığa çıkarıldı|3|start=2017-05-03T13:23:09.7798589Z app=Ldap shost=CLIENT1 suser=Administrator msg=Yöneticinin kimlik bilgileri CLIENT1 adlı istemciden LDAP basit bağlaması kullanılarak düz metin şeklinde açığa çıkarıldı. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909d9c68ca1ec04d05f9918
### <a name="services-exposing-account-credentials"></a>Hesap kimlik bilgilerini açığa çıkaran hizmetler
May  3 13:34:23 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|LdapSimpleBindCleartextPasswordSuspiciousActivity|Hesap kimlik bilgilerini açığa çıkaran hizmetler|3|start=2017-05-03T13:28:36.5159194Z app=Ldap shost=daf::220 msg=daf::220 (daf::220) üzerinde çalışan hizmetler LDAP basit bağlaması kullanarak hesap kimlik bilgilerini düz metin şeklinde açığa çıkarıyor. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909dc5f8ca1ec04d05fa8b1
### <a name="pass-the-ticket"></a>Anahtar geçişi
May  4 13:15:41 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|PassTheTicketSuspiciousActivity|Pass-the-Ticket saldırısı ile kimlik hırsızlığı|10|start=2017-05-04T13:13:44.5160000Z app=Kerberos shost=CLIENT1 suser=Administrator request=krbtgt/DOMAIN1.TEST.LOCAL msg=Yöneticinin Kerberos anahtarları CLIENT2 adlı istemciden çalındı ve CLIENT1 adlı istemcide krbtgt/DOMAIN1.TEST.LOCAL etki alanı anahtarına erişmek için kullanıldı. cs2Label=ticketSourceComputer cs2=CLIENT2 cs3Label=ticketSourceComputerIpAddress cs3= cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/590b29168ca1ec0ba438acf6

## <a name="see-also"></a>Ayrıca bkz:
- [ATA önkoşulları](ata-prerequisites.md)
- [ATA kapasite planlaması](ata-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-collection.md#configuring-windows-event-forwarding)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
