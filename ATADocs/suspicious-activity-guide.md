---
title: "ATA şüpheli etkinlik kılavuzu | Microsoft Docs"
description: "Bu makalede, ATA’nın algılayabildiği şüpheli etkinliklerin bir listesi ve düzeltme adımları sağlanmaktadır."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 07/3/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1fe5fd6f-1b79-4a25-8051-2f94ff6c71c1
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 8a230f47f0bf0e886ba46c964e2c2121e9ee44a4
ms.sourcegitcommit: fa50f37b134d7579d7c310852dff60e5f1996eaa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*


# <a name="introduction"></a>Giriş

ATA gelişmiş bir tehdidin çeşitli aşamaları için algılama sağlar: keşif, kimlik bilgilerinin tehlikeye atılması, yanal hareket, ayrıcalık yükseltme, etki alanı hakimiyeti ve daha fazlası.

Sonlandırma zincirinde ATA’nın şu anda algılayabildiği aşamalar aşağıdaki resimde vurgulanmıştır.

![ATA, saldırı ölüm zincirindeki yanal etkinliklere odaklanır](media/attack-kill-chain-small.jpg)

Bu makalede, aşamalara göre tüm şüpheli etkinlikler hakkında ayrıntılar sağlanmaktadır.


## <a name="reconnaissance-using-account-enumeration"></a>Hesap numaralandırma kullanarak keşif

| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Hesap numaralandırma saldırısı, saldırganların Kerberos kimlik doğrulaması denemeleri ile ağda bir kullanıcı olup olmadığını öğrenerek farklı hesap adlarını tahmin etmek için kullandığı bir tekniktir. Doğru tahmin edilen hesaplar, saldırının sonraki adımlarında kullanılabilir. | Söz konusu bilgisayara bakın ve bilgisayarın bu kadar fazla Kerberos kimlik doğrulama işlemi başlatması için bir neden olup olmadığını belirlemeye çalışın. Bunlar, hesapları öğrenmeyi denerken kullanıcı mevcut olmadığı için birden çok hesapta başarısız olmuş (Client_Principal_Unknown hatası) ve en az bir başarılı erişim denemesi yapmış işlemlerdir. <br></br>**Özel durumlar:** Bu algılama yöntemi, mevcut olmayan birden çok hesap bularak ve tek bir bilgisayardan kimlik doğrulamayı deneyerek çalışır. Bir kullanıcı el ile kullanıcı veya etki alanı adı girerken hata yaparsa bu kimlik doğrulama denemesi, mevcut olmayan bir hesapta oturum açma denemesi olarak değerlendirilir. Pek çok kullanıcının oturum açmasını gerektiren terminal sunucularında çok sayıda hatalı oturum açma denemesi olması normaldir. |Bu istekleri oluşturan işlemi araştırın.  Kaynak bağlantı noktasına dayanarak işlemleri tanımlama konusunda yardım için bkz. [Hangi Windows işleminin ağa belirli bir paket gönderdiğini görmek ister misiniz?](https://blogs.technet.microsoft.com/nettracer/2010/08/02/have-you-ever-wanted-to-see-which-windows-process-sends-a-certain-packet-out-to-network/)|Orta|

## <a name="reconnaissance-using-directory-services-enumeration-sam-r"></a>Dizin hizmetleri listeleme (SAM-R) kullanarak Keşif

| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Dizin hizmetleri ile keşif, saldırganların saldırının sonraki adımlarında kullanmak üzere dizin yapısı ile hedef ayrıcalıklı hesapları eşlemek için kulladığı bir tekniktir. Güvenlik Hesabı Yöneticisi Uzak (SAM-R) protokolü, dizini sorgulamak için kullanılan yöntemlerden biridir. | Söz konusu bilgisayarın neden Güvenlik Hesabı Yöneticisi - Uzak (MS-SAMR) protokolü gerçekleştirdiğini anlamaya çalışın. Bu, normal olmayan bir yolla, büyük olasılıkla gizli varlıkları sorgulayarak gerçekleştiriliyor. <br></br>**Özel durumlar**: Bu algılama yöntemi, SAM-R sorgusu yapan kullanıcıların normal davranış profilini oluşturup normal olmayan bir sorgu gözlemlendiğinde sizi uyararak çalışır. Kendilerine ait olmayan bilgisayarlarda oturum açan gizli kullanıcılar, normal iş sürecinin bir parçası olduğu halde anormal olarak algılanan bir SAM-R sorgusu tetikleyebilir. Bu genellikle BT ekibi üyelerinin başına gelir. Bir sorgu, normal kullanımın sonucu olduğu halde şüpheli olarak işaretlenmişse bunun sebebi, bu davranışın önceden ATA tarafından gözlemlenmemiş olmasıdır. | Bu durumda her Active Directory ormanı başına, daha uzun bir öğrenme süreci ve daha geniş bir ATA kapsamı önerilir.<br></br>[“SAMRi10” aracını indirin ve çalıştırın](https://gallery.technet.microsoft.com/SAMRi10-Hardening-Remote-48d94b5b). SAMRi10 aracı, ATA ekibi tarafından SAM-R sorgularına karşı ortamınızı güçlendirmek amacıyla kullanıma sunulmuştur. | Orta|

## <a name="reconnaissance-using-dns"></a>DNS kullanarak keşif


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| DNS sunucunuz; ağınızdaki tüm bilgisayarlar, IP adresleri ve hizmetlerin bir haritasını içerir. Saldırganlar bu bilgileri kullanarak ağ yapınızın haritasını çıkarır ve saldırının sonraki adımlarında kullanmak üzere uygun bilgisayarları hedef alır. | Söz konusu bilgisayarın neden DNS etki alanında bulunan tüm kayıtları almak için bir Tam Bölge Aktarımı (AXFR) sorgusu gerçekleştirdiğini anlamaya çalışın. <br></br>**Özel durumlar:** Bu algılama yöntemi, DNS bölge aktarım istekleri yapan DNS dışı sunucuları belirler. DNS sunucularına bu tip istekler yaptığı bilinen birkaç güvenlik tarayıcı çözümü vardır. <br></br>Ayrıca, hatalı pozitif senaryoları önlemek için ATA’nın ATA Gateway’lerinde bağlantı noktası 53 aracılığıyla DNS sunucularıyla iletişim kurabildiğini doğrulayın.| Hangi konakların Bölge Aktarımı isteği yapabileceğini dikkatle seçerek bunu sınırlayın. Daha fazla ayrıntı için bkz. [DNS Güvenliğini Sağlama](https://technet.microsoft.com/library/cc770474(v=ws.11).aspx) ve [Yapılacaklar Listesi: DNS Sunucunuzun Güvenliğini Sağlama](https://technet.microsoft.com/library/cc770432(v=ws.11).aspx). |Orta|

## <a name="reconnaissance-using-smb-session-enumeration"></a>SMB Oturumu Listeleme kullanarak Keşif


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Sunucu İleti Bloğu (SMB) listeleme, bir saldırganın ağınızdaki kullanıcıların yakın zamanda hangi IP adreslerinden oturum açtığını öğrenmesini sağlar. Saldırgan bu bilgiyi elde ettiği zaman bunu, belirli hesapları hedef almak ve ağda yanal olarak hareket etmek için kullanabilir. | Söz konusu bilgisayarın neden SMB Oturum listeleme gerçekleştirdiğini anlamaya çalışın.<br></br>**Özel durumlar**: Bu algılama yöntemi, SMB oturum listelemenin kuruluş ağında güvenli bir kullanımı olmadığı varsayımına dayanır ancak bazı güvenlik tarayıcı çözümleri (Websense gibi) bu tip istekler yapar. | [Ortamınızı güçlendirmek için ağ sonlandırma aracını kullanma](https://gallery.technet.microsoft.com/Net-Cease-Blocking-Net-1e8dcb5b) | Orta   |

## <a name="brute-force-ldap-kerberos-ntlm"></a>Deneme yanılma (LDAP, Kerberos, NTLM)


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Deneme yanılma saldırısında bir saldırgan, pek çok parola deneyerek doğru parolayı bulmaya çalışır. Saldırgan, doğrusu bulunana kadar tüm olası parolaları (veya çok sayıda olası parola gruplarını) sistematik olarak dener. Saldırgan doğru parolayı bulduğunda ise kullanıcı gibi ağda oturum açabilir. Şu anda ATA; Kerberos veya NTLM protokolü kullanarak yatay (birden çok hesap) deneme yanılma ile LDAP basit bağlaması kullanarak yatay ve dikey (tek hesap, birden çok parola denemesi) deneme yanılmayı desteklemektedir. | Söz konusu bilgisayarın neden birden çok kullanıcı hesabının kimliğini doğrulamakta başarısız olduğunu (birden çok kullanıcı için yaklaşık olarak aynı sayıda kimlik doğrulama denemesiyle) veya tek bir kullanıcı için neden çok sayıda kimlik doğrulama hatası olduğunu anlamaya çalışın. <br></br>**Özel durumlar**: Bu algılama yöntemi, farklı kaynaklarda kimlik doğrulayan hesapların normal davranış profilini oluşturup normal olmayan bir hareket gözlemlendiğinde bir uyarı tetikleyerek çalışır. Bu durum, otomatik olarak kimlik doğrulayan ancak eski kimlik bilgilerini (ör. yanlış parola veya kullanıcı adı) kullanan betiklerde görülebilir. | Uzun ve karmaşık bir parola, deneme yanılma saldırılarına karşı alınması gereken ilk güvenlik önlemidir. | Orta   |

## <a name="sensitive-account-exposed-in-plain-text-authentication-and-service-exposing-accounts-in-plain-text-authentication"></a>Düz metin kimlik doğrulamasıyla açığa çıkarılan gizli hesap ve hesapları düz metin kimlik doğrulamasıyla açığa çıkaran Hizmet


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Bilgisayarlardaki bazı hizmetler, gizli hesapların bile hesap kimlik bilgilerini düz metin olarak gönderir. Trafiğinizi izleyen saldırganlar bu kimlik bilgilerini kötü amaçlar için ele geçirebilir. Gizli bir hesabın herhangi bir düz metin parolası bu uyarıyı tetikleyecektir. | Hesabı açığa çıkarmaya çalışan bilgisayarı bulun ve neden LDAP basit bağlamaları kullandığını öğrenin. | Kaynak bilgisayarlarda yapılandırmayı doğrulayın ve LDAP basit bağlaması kullanmadığınızdan emin olun. LDAP basit bağlamaları yerine LDAP SALS veya LDAPS kullanın. Güvenlik Katmanlı Çerçevesi’yi izleyin ve katmanlar arası erişimi kısıtlayarak ayrıcalık yükseltmeyi önleyin. | Açığa çıkaran hizmet için Düşük; gizli hesaplar için Orta |

## <a name="honey-token-account-suspicious-activities"></a>Honey Token hesabının kuşkulu etkinlikleri


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Honey Token hesaplar, içinde bulundukları ağda kötü amaçlı etkinlikleri yakalamak, tanımlamak ve izlemek üzere ayarlanan sahte hesaplardır. Bu hesaplar, ağınızda kullanılmayan ve uykuda bulunan hesaplardır. Bir honey token hesapta aniden bir etkinlik görüldüğünde bu, kötü amaçlı bir kullanıcının hesabı kullanmaya çalıştığı anlamına gelebilir. | Neden bir honey token hesabın bu bilgisayarda kimlik doğrulamayı denediğini anlamaya çalıştığın. | Ortamınızdaki diğer gizli (ayrıcalıklı) hesapların ATA profil sayfalarına göz atarak olası bir şüpheli etkinlik olup olmadığını denetleyin. | Orta   |

## <a name="unusual-protocol-implementation"></a>Olağan dışı protokol uygulanması


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Saldırganlar, SMB/Kerberos protokollerini belirli şekillerde uygulayan araçlar kullanarak ağınızda bazı yetkiler elde edebilirler. Bu, over-pass-the-hash veya deneme yanılma saldırıları için kullanılan kötü amaçlı tekniklere işaret eder. | Söz konusu bilgisayarın neden bir kimlik doğrulama protokolünü veya SMB’yi olağan dışı bir şekilde kullandığını anlamaya çalışın. <br></br>**Özel durumlar:** Bu algılama yöntemi, nadiren de olsa, protokolleri standart dışı bir şekilde uygulayan güvenli araçlar kullanıldığında tetiklenebilir. Bazı sızma testi uygulamalarının bunu yaptığı bilinmektedir. | Ağ trafiğini yakalayın ve hangi işlemin olağan dışı protokol uygulaması trafiğini oluşturduğunu belirleyin.<br></br>Bunun bir WannaCry saldırısı olup olmadığını belirlemek için şunu yapın:<br></br> 1.   Şüpheli etkinliği Excel ile dışarı aktarın.<br></br>
2.  Ağ etkinliği sekmesini açın ve ilgili Smb1SessionSetup ve Ntlm JSON’lerini kopyalamak için “Json” alanına gidin<br></br>
3.  Smb1SessionSetup.OperatingSystem “Windows 2000 2195” ve Smb1SessionSetup.IsEmbeddedNtlm “true” ise ve Ntlm.SourceAccountId “null” ise bu WannaCry’dır.
| Orta   |

## <a name="malicious-data-protection-private-information-request"></a>Kötü Amaçlı Veri Koruma Özel Bilgi İsteği


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Parolaları, şifreleme anahtarlarını ve diğer gizli verileri güvenle depolamak için Windows’un birkaç bileşeni tarafından Veri Koruma API’si (DPAPI) kullanılır. Etki alanı denetleyicileri, etki alanına katılan Windows makineler tarafından DPAPI ile şifrelenen tüm gizli dizilerin şifresini çözmek için kullanılan yedek bir ana anahtar bulundurur. Saldırganlar bu DPAPI etki alanı yedek ana anahtarını kullanarak etki alanındaki makinelerde bulunan tüm gizli dizilerin (tarayıcı parolaları, şifreli dosyalar vb.) şifresini çözebilir. | Bu bilgisayarın neden DPAPI’nin ana anahtarı için bu belgelenmemiş API çağrısı kullanarak istek yaptığını anlamaya çalışın. | [Windows Veri Koruması](https://msdn.microsoft.com/library/ms995355.aspx)’nda DPAPI hakkında daha fazla bilgi edinin. | Yüksek     |

## <a name="suspicion-of-identity-theft-based-on-abnormal-behavior"></a>Anormal davranışa bağlı kimlik hırsızlığı şüphesi


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Bir davranış modeli derlendikten sonra (davranış modeli derlemek için 3 haftalık bir süre içerisinde en az 50 etkin hesap gerekir) herhangi bir anormal davranış uyarıyı tetikleyecektir. Belirli bir kullanıcı hesabı için derlenen modelle eşleşmeyen davranış, kimlik hırsızlığına işaret ediyor olabilir. | Söz konusu kullanıcının neden farklı davrandığını anlamaya çalışın. <br></br>**Özel durumlar:** ATA kısmi kapsama sahipse (tüm etki alanı denetleyicileri bir ATA Gateway’e yönlendirilmemişse) belirli bir kullanıcı için yalnızca kısmi etkinlikler öğrenilir. 3 haftadan uzun bir süre sonra ATA aniden tüm trafiğinizi kapsamaya başlarsa kullanıcının daha önce öğrenilmemiş etkinlikleri uyarıyı tetikleyebilir. | ATA’nın tüm etki alanı denetleyicilerinize dağıtıldığından emin olun. <br></br>1.  Kullanıcının kuruluşta yeni bir konuma geçip geçmediğini denetleyin.<br></br>2.  Kullanıcının mevsimlik çalışan olup olmadığını denetleyin.<br></br>3.  Kullanıcının uzun bir aradan yeni dönüp dönmediğini denetleyin.| Tüm kullanıcılar için Orta ve gizli kullanıcılar için Yüksek |


## <a name="pass-the-ticket"></a>Anahtar geçişi


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Pass-the-Ticket saldırısı, saldırganların bir bilgisayardan Kerberos anahtarını çaldığı ve bunu, ağınızdaki bir varlığın kimliğine bürünerek başka bir bilgisayara erişim kazanmak için kullandığı bir yanal hareket tekniğidir. | Bu algılama yöntemi, iki (veya daha fazla) farklı bilgisayarlarda aynı Kerberos anahtarının kullanılmasıyla çalışır. IP adreslerinizin hızla değiştiği bazı durumlarda ATA, bu adreslerin aynı bilgisayar mı yoksa farklı bilgisayarlar tarafından mı kullanıldığını belirleyemeyebilir. Bu, yetersiz DHCP havuzlarında (VPN, WiFi vb.) ve paylaşılan IP adreslerinde (NAT cihazları) sıkça görülen bir sorundur. | Güvenlik Katmanlı Çerçeve’yi izleyin ve katmanlar arası erişimi kısıtlayarak ayrıcalık yükseltmeyi önleyin. | Yüksek     |

## <a name="pass-the-hash"></a>Karma değer geçişi


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Pass the hash saldırısında, saldırgan normalde olduğu gibi ilgili düz metin parolası yerine kullanıcının parolasını temel aldığı NTLM karmasını kullanarak bir uzak sunucuda veya hizmette kimlik doğrular. | Bu uyarının gönderildiği zaman diliminde hesabın, herhangi bir anormal etkinlik gerçekleştirip gerçekleştirmediğini kontrol edin. | [Pass the Hash](http://aka.ms/PtH)’te açıklanan önerileri uygulayın. Güvenlik Katmanlı Çerçeve’yi izleyin ve katmanlar arası erişimi kısıtlayarak ayrıcalık yükseltmeyi önleyin. | Yüksek|

## <a name="over-pass-the-hash"></a>Karma değeri atlayarak geçiş


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Over pass the hash saldırısı, Kerberos anahtarı oluşturmak için NTLM karması kullanılan Kerberos kimlik doğrulama protokolündeki bir uygulama zayıflığından yararlanır ve saldırganın ağdaki hizmetlerde kullanıcı parolasına gerek duymadan oturum açmasını mümkün kılar. | Şifrelemeyi düşürme: Söz konusu hesabın AES kullanmayı öğrendikten sonra Kerberos’ta neden RC4 kullandığını anlamaya çalışın. <br></br>**Özel durumlar:** Bu algılama yöntemi, etki alanında kullanılan şifreleme yöntemlerinin profilini oluşturup anormal ve daha zayıf bir yöntem gözlemlendiğinde sizi uyararak çalışır. Bazı durumlarda daha zayıf bir şifreleme yöntemi kullanılacaktır ve normal iş sürecinizin bir parçası olmasına rağmen ATA bunu anormal olarak algılayacaktır. Benzer bir davranış, ATA tarafından önceden gözlemlenmediyse bu durum ortaya çıkabilir. ATA’nın etki alanındaki kapsamını artırmak yardımcı olacaktır. | [Pass the Hash](http://aka.ms/PtH)’te açıklanan önerileri uygulayın. Güvenlik Katmanlı Çerçeve’yi izleyin ve katmanlar arası erişimi kısıtlayarak ayrıcalık yükseltmeyi önleyin. | Yüksek     |

## <a name="privilege-escalation-using-forged-authorization-data-ms14-068-exploit-forged-pac--ms11-013-exploit-silver-pac"></a>Sahte yetkilendirme verileri kullanarak ayrıcalık yükseltme saldırısı (MS14-068 açığı (Sahte PAC) / MS11-013 açığı (Gümüş PAC))


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Eski Windows Server sürümlerinin bilinen güvenlik açıkları, saldırganların Kerberos anahtarında kullanıcının yetkilendirme verilerini içeren bir alan olan (bu, Active Directory’de grup üyeliğidir) Ayrıcalıklı Öznitelik Sertifikası’nı (PAC) kullanarak kendilerine ek ayrıcalıklar sağlamalarına imkan verir. | Etkilenen bilgisayarda PAC dışında bir yetkilendirme yöntemi kullanan özel bir hizmetin çalışıp çalışmadığını kontrol edin. <br></br>**Özel durumlar:** Belli başlı bazı senaryolarda kaynaklar, kendi yetkilendirme mekanizmalarını uygular ve bu durum ATA’da bir uyarı tetikleyebilir. | Windows Server 2012 R2 ve altı işletim sistemi sürümleri kullanan etki alanı denetleyicilerinde [KB3011780](https://support.microsoft.com/help/2496930/ms11-013-vulnerabilities-in-kerberos-could-allow-elevation-of-privilege)’in yüklü olduğundan ve tüm üye sunucularla 2012 R2 ve altı sürümlerdeki etki alanı denetleyicilerinin KB2496930 güncel sürümünde olduğundan emin olun. Daha fazla bilgi için bkz. [Gümüş PAC](https://technet.microsoft.com/library/security/ms11-013.aspx) ve [Sahte PAC](https://technet.microsoft.com/library/security/ms14-068.aspx). | Yüksek     |

## <a name="abnormal-sensitive-group-modification"></a>Anormal Gizli Grup Değişikliği


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Eski Windows Server sürümlerinin bilinen güvenlik açıkları, saldırganların Kerberos anahtarında kullanıcının yetkilendirme verilerini içeren bir alan olan (bu, Active Directory’de grup üyeliğidir) Ayrıcalıklı Öznitelik Sertifikası’nı (PAC) kullanarak kendilerine ek ayrıcalıklar sağlamalarına imkan verir. | Grup değişikliğinin güvenli olduğunu doğrulayın. <br></br>**Özel durumlar**: Bu algılama yöntemi, gizli gruplarda değişiklik yapan kullanıcıların normal davranış profilini oluşturup anormal bir değişiklik gözlemlendiğinde sizi uyararak çalışır. Bu davranışın ATA tarafından önceden gözlemlenmediği durumlarda güvenli değişiklikler de uyarıyı tetikleyebilir. Daha uzun bir öğrenme süreci ve etki alanında ATA kapsamının artırılması yardımcı olacaktır. | Gizli gruplarda değişiklik yapabilecek kişi sayısını olabildiğince düşük tutun. Mümkünse Just-I- Time izinlerini kullanın. | Orta   |

## <a name="encryption-downgrade---skeleton-key-malware"></a>Şifrelemeyi düşürme - Skeleton Key Kötü Amaçlı Yazılım


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Skeleton Key, etki alanı denetleyicilerinde çalışan ve etki alanında herhangi bir hesap ile parolaya gerek kalmaksızın kimlik doğrulaması sağlayan kötü amaçlı bir yazılımdır. Bu yazılım genellikle daha zayıf şifreleme algoritmaları kullanarak kullanıcının etki alanı denetleyicisindeki parolalarını şifreler. | Şifrelemeyi düşürme: Söz konusu hesabın AES kullanmayı öğrendikten sonra Kerberos’ta neden RC4 kullandığını anlamaya çalışın. <br></br>**Özel durumlar:** Bu algılama yöntemi, etki alanında kullanılan şifreleme yöntemlerinin profilini çıkararak çalışır. Bazı durumlarda daha zayıf bir şifreleme yöntemi kullanılacaktır ve bu, nadiren kullanılsa bile normal iş sürecinin bir parçası olmasına rağmen ATA bunu anormal olarak algılayacaktır. | [ATA ekibi tarafından yazılan tarayıcıyı](https://gallery.technet.microsoft.com/Aorato-Skeleton-Key-24e46b73) kullanarak etki alanı denetleyicilerinizin Skeleton Key’den etkilenip etkilenmediğini kontrol edebilirsiniz. | Yüksek |

## <a name="golden-ticket"></a>Altın anahtar


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Bir saldırganın etki alanı yönetici hakları varsa saldırgan, ağdaki tüm kaynaklarda yetkilendirme sağlayan ve anahtar süresini isteğe göre ayarlamaya olanak tanıyan bir anahtar veren Kerberos anahtarı (TGT) oluşturabilir. Bu durum, saldırganların ağda kalıcı olmasına yol açar. | Şifrelemeyi düşürme: Söz konusu hesabın AES kullanmayı öğrendikten sonra Kerberos’ta neden RC4 kullandığını anlamaya çalışın. <br></br>**Özel durumlar:** Bu algılama yöntemi, etki alanında kullanılan şifreleme yöntemlerinin profilini oluşturup anormal ve daha zayıf bir yöntem gözlemlendiğinde sizi uyararak çalışır. Bazı durumlarda daha zayıf bir şifreleme yöntemi kullanılır ve nadiren kullanılsa bile normal iş sürecinin bir parçası olmasına rağmen ATA bunu anormal olarak algılayacaktır. Benzer bir davranış, ATA tarafından önceden gözlemlenmediyse bu durum ortaya çıkabilir. ATA’nın etki alanınızı tümüyle kapsadığından olduğundan emin olun. | Aşağıdaki yöntemleri kullanarak Anahtar Veren Kerberos Anahtarı (KRBTGT) ana anahtarı için olabildiğince yüksek güvenlik önlemi alın:<br></br>1.  Fiziksel güvenlik<br></br>2.  Sanal makineler için fiziksel güvenlik<br></br>3. Etki alanı denetleyicisini güçlendirme<br></br>4.  Yerel Güvenlik Yetkilisi (LSA) Yalıtım/Credential Guard<br></br>Altın anahtarlar algılandığında, taktiksel kurtarma gerekip gerekmediğine karar vermek için daha kapsamlı bir araştırma yapmak gerekir.<br></br>[KRBTGT Hesap Parolası Sıfırlama Betikleri artık müşteriler tarafından kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/) Microsoft blogunda bulunan kılavuza göre ve [Krbtgt hesap parolası/anahtarı sıfırlama aracını](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51) kullanarak Anahtar Veren Kerberos Anahtarı’nı (KRBTGT) düzenli olarak iki kere değiştirin. <br></br>Bu [Pass the hash önerilerini](http://aka.ms/PtH) uygulayın. | Orta   |



## <a name="remote-execution"></a>Uzaktan yürütme


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Yönetici kimlik bilgilerini ele geçiren saldırganlar, etki alanı denetleyicinizde uzak komutlar yürütebilirler. Bu komutlar kalıcılık sağlamak, bilgi toplamak, hizmet reddi (DoS) saldırıları ve diğer herhangi bir sebeple kullanılabilir. | Söz konusu hesabın etki alanı denetleyicinizde bu uzaktan yürütmeyi gerçekleştirme izni olup olmadığını öğrenin. <br></br>**Özel durumlar:** Normal yönetim sürecinin bir parçası olmasına rağmen etki alanı denetleyicisinde bazen komut çalıştıran güvenli kullanıcılar da bu uyarıyı tetikleyebilir. Bu durum en çok, BT ekibi üyelerinde veya etki alanı denetleyicilerinde yönetim görevi yürüten hizmet hesaplarında görülür. | Katman 0 olmayan makinelerden etki alanı denetleyicilerine uzaktan erişimi kısıtlayın. Şüpheli, eski ve gerekli olmayan dosya ve klasörleri silin. Güçlü Kullanıcı Hesabı Denetimi (UAC) ilkeleri uygulayın. Yalnızca güçlendirilmiş makinelerin yönetici etki alanı denetleyicilerine bağlanmasına izin vermek için [PAW](https://technet.microsoft.com/en-us/windows-server-docs/security/securing-privileged-access/securing-privileged-access) uygulayın. | Düşük      |

## <a name="malicious-replication-requests"></a>Kötü amaçlı çoğaltma istekleri


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Active Directory çoğaltması, bir etki alanı denetleyicisinde yapılan değişikliklerin aynı verilerin kopyalarını depolayan etki alanıyla veya ormandaki tüm diğer etki alanı denetleyicileriyle eşitlenmesi işlemidir. Uygun izne sahip bir saldırgan, etki alanı denetleyicisiymiş gibi bir çoğaltma isteği yapabilir ve böylece parola karmaları da dahil olmak üzere Active Directory’de depolanan verileri alabilir. | Bilgisayarın neden etki alanı denetleyicisi çoğaltma API’si kullandığını anlamaya çalışın. Bu algılama yöntemi, bir bilgisayarın etki alanı denetleyicisi olup olmadığını anlamak için dizin ormanı yapılandırma bölümünü kullanan ATA’ya bağlı olarak çalışır. <br></br>**Özel durumlar:** Azure AD Dizin Eşitlemesi bu uyarının tetiklenmesine neden olabilir. | Şu izinleri doğrulayın: -   Dizin Değişikliklerini Çoğaltma <br></br>-   Dizin Değişikliklerini Çoğaltma Al<br></br>Daha fazla bilgi için bkz. [Active Directory Domain Services hizmetine SharePoint Server 2013’te profil eşitleme izinleri sağlama](https://technet.microsoft.com/library/hh296982.aspx)<br></br>Etki alanında kimin bu izinlere sahip olduğunu belirlemek için [AD ACL Tarayıcı](https://blogs.technet.microsoft.com/pfesweplat/2013/05/13/take-control-over-ad-permissions-and-the-ad-acl-scanner-tool/)’dan yararlanabilir veya bir PowerShell betiği oluşturabilirsiniz. | Orta   |



## <a name="broken-trust-between-domain-and-computers"></a>Etki alanı ve bilgisayarlar arasındaki güvenin bozulması


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Güvenin bozulması, Active Directory güvenlik gereksinimlerinin etkin olmayabileceği anlamına gelir. Bu, genelde temel bir güvenlik ve uyumluluk hatası olarak değerlendirilir ve saldırganlar için kolay bir hedeftir. 24 saatlik bir zaman diliminde bir bilgisayarda art arda 5’ten fazla Kerberos kimlik doğrulama hatası görülürse bu durum ATA’da bir uyarı tetikleyecektir. Bilgisayar, etki alanı denetleyicisi ile iletişim kurmadığı için (1) güncelleştirilmiş bir grup ilkesi yoktur ve (2) oturum açma, önbelleğe alınmış kimlik bilgileriyle sınırlıdır. | Olay günlüklerini kontrol ederek bilgisayar ile etki alanı arasındaki güvenin iyi durumda olduğundan emin olun. | Gerekirse makineyi yeniden etki alanına dahil edin veya makinenin parolasını sıfırlayın. | Düşük      |

## <a name="massive-object-deletion"></a>Büyük çaplı nesne silme


| Açıklama|Araştırma|Öneri|Önem Derecesi|
|------|----|------|----------|
| Hesapların %5’inden fazlası silindiğinde ATA bu uyarıyı gönderir. Bunun için silinmiş öğe kapsayıcısını okuma izni gerekir. | Hesaplarınızın %5’inin neden aniden silindiğini anlamaya çalışın. | Active Directory'de hesapları silebilen kullanıcıların izinlerini kaldırın. Daha fazla ayrıntı için bkz. [Bir Directory Nesnesindeki İzinleri Görüntüleme veya Ayarlama](https://technet.microsoft.com/library/cc816824%28v=ws.10%29.aspx). | Düşük |

## <a name="see-also"></a>Ayrıca Bkz.
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [Sahte PAC saldırılarını araştırma](use-case-forged-pac.md)
- [Bilinen ATA hatalarını giderme](troubleshooting-ata-known-errors.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
