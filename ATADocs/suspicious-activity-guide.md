---
title: "ATA şüpheli etkinlik kılavuzu | Microsoft Docs"
d|Description: This article provides a list of the suspicious activities ATA can detect and steps for remediation.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/17/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1fe5fd6f-1b79-4a25-8051-2f94ff6c71c1
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 261b0bf277de97520e4d5473d8a16280f8e4534b
ms.sourcegitcommit: 1c4ccb320e712a180433a7625312862235be66f0
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*


# <a name="advanced-threat-analytics-suspicious-activity-guide"></a>Gelişmiş tehdit analizi şüpheli etkinlik Kılavuzu

Uygun araştırma tüm şüpheli etkinlikleri olarak sınıflandırılabilir:

-   **Doğru pozitif**: ATA tarafından algılanan kötü amaçlı bir eylem.

-   **Zararsız true pozitif**: Gerçek ancak sızma test gibi değil amaçlı ATA tarafından algılanan bir eylem.

-   **Yanlış pozitif**: yanlış alarm etkinlik anlamına durum alamadık.

ATA uyarılarla çalışma hakkında daha fazla bilgi için bkz: [kuşkulu etkinliklerle çalışma](working-with-suspicious-activities.md).

Sorularınız veya Geri bildiriminiz için ATA ekibi ile iletişime geçin [ ATAEval@microsoft.com ](mailto:ATAEval@microsoft.com).

## <a name="abnormal-sensitive-group-modification"></a>Anormal Gizli Grup Değişikliği


**Açıklama**

Saldırganlar kullanıcılar yüksek ayrıcalıklı gruplara ekleyin. Daha fazla kaynaklarına erişim kazanmak için ve kalıcılığı kazanmak için bunu. Algılama, kullanıcıların Grup değiştirme etkinliklerini profil ve hassas grubu olağan dışı bir eklemeyi görülen olduğunda uyarı dayanır. Profil oluşturma ATA tarafından sürekli olarak gerçekleştirilir. Bir uyarıyı tetikleyen önce en az bir ay boyunca her etki alanı denetleyicisi başına noktadır.

ATA hassas gruplara tanımı için bkz: [ATA Konsolu'yla çalışma](working-with-ata-console.md#sensitive-groups).


Algılama dayanan [etki alanı denetleyicilerinde Denetlenen olayları](https://docs.microsoft.com/advanced-threat-analytics/configure-event-collection).
Etki alanı denetleyicileriniz gerekli olaylarını denetleme emin olmak için başvurulan aracını [ATA denetleme (AuditPol, denetim ayarlarını zorlama Gelişmiş, Basit Ağ Geçidi Hizmeti Bulma)](https://aka.ms/ataauditingblog).

**Araştırma**

1. Grubu değişiklik yasal mi? </br>Nadiren oluşur ve "olarak normal", öğrenilen değil yasal grubu değişiklikleri zararsız true pozitif olarak değerlendirilebilecek bir uyarı neden olabilir.

2. Eklenen nesne bir kullanıcı hesabı varsa, kullanıcı hesabının yönetim grubuna eklendikten sonra geçen hangi eylemleri denetleyin. Daha fazla içerik almak için ATA kullanıcının sayfasına gidin. Diğer vardı önce veya sonra ek hesapla ilişkili kuşkulu etkinlikleri gerçekleşen? Karşıdan **hassas grubu değişiklik** ne olan diğer tüm değişiklikleri görmek için raporu yapılmış ve aynı saat diliminde kim tarafından.

**Düzeltme**

Hassas gruplarını değiştirmek için yetkili kullanıcıların sayısını en aza indirin.

Ayarlanan [Active Directory için Privileged Access Management](https://docs.microsoft.com/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services) varsa.

## <a name="broken-trust-between-computers-and-domain"></a>Bilgisayarlar ve etki alanı arasında kaldırılmış güven

**Açıklama**

Kaldırılmış güven, Active Directory güvenlik gereksinimlerini yürürlükte bilgisayarlar için söz konusu olmayabileceğini anlamına gelir. Bu, genelde temel bir güvenlik ve uyumluluk hatası olarak değerlendirilir ve saldırganlar için kolay bir hedeftir. 5'ten fazla Kerberos kimlik doğrulama hataları 24 saat içindeki bir bilgisayar hesabını görülüyorsa bu algılama, bir uyarı tetiklenir.

**Araştırma**

Söz konusu bilgisayarın etki alanı kullanıcıların oturum açmasına izin veriyor mu? 
- Yanıt Evet ise, bu bilgisayara düzeltme adımları yoksayabilirsiniz.

**Düzeltme**

Gerekirse, makineyi etki alanına katın veya makinenin parola sıfırlama.

## <a name="brute-force-attack-using-ldap-simple-bind"></a>LDAP basit bağlama kullanarak yanılma saldırısı

**Açıklama**

>[!NOTE]
> Arasındaki temel fark **kuşkulu kimlik doğrulama hataları** ve bu algılama bu algılama, ATA farklı parolalar kullanımda olup olmadığını belirleyebilirsiniz.

Yanılma saldırısında, saldırganın en az bir hesap için doğru parolayı bulunana kadar farklı hesaplar için birçok farklı parolaları ile kimlik doğrulaması dener. Bir kez bulundu, bir saldırganın bu hesabı kullanarak oturum açabilir.

Bu algılama, ATA kullanılan birçok farklı parolalar algıladığında bir uyarı tetiklenir. Bu da olabilir *yatay* parolaları çok sayıda kullanıcı; boyunca küçük bir dizi veya *dikey "* parolaları yalnızca birkaç kullanıcı; veya bu iki seçenek herhangi bir bileşimini büyük bir dizi.

**Araştırma**

1. İlgili birçok hesapları varsa tıklatın **karşıdan ayrıntıları** bir Excel elektronik tabloda listesini görmek için.

2. Ayrılmış sayfasına gitmek için uyarıyı tıklayın. Tüm oturum açma denemesi olursa onay başarılı bir kimlik doğrulaması ile sona erdi. Deneme olarak görüneceği **hesapları tahmin** bilgi grafiği sağ tarafındaki. Yanıt Evet ise, olan **hesapları tahmin** kaynak bilgisayardan normalde kullanılan? Yanıt Evet ise, **bastır** şüpheli etkinlik.

3. Varsa hiçbir **hesapları tahmin**, olan **saldırıya hesapları** kaynak bilgisayardan normalde kullanılan? Yanıt Evet ise,**bastır** şüpheli etkinlik.

**Düzeltme**

[Uzun ve karmaşık parolalar](https://docs.microsoft.com/windows/device-security/security-policy-settings/password-policy) yanılma saldırılarına karşı güvenlik gerekli ilk düzeyi sağlar.

## <a name="encryption-downgrade-activity"></a>Şifreleme indirgeme etkinliği

**Açıklama**

Çeşitli saldırı yöntemleri zayıf Kerberos şifreleme cyphers kullanın. Bu algılama, ATA bilgisayarlar ve kullanıcılar tarafından kullanılan Kerberos şifreleme türlerini öğrenir ve, zayıf bir şifreleme olduğunda kullanılan uyarılar: (1) kaynak bilgisayar ve/veya kullanıcı; olağandışıdır ve saldırı teknikleri bilinen (2) eşleşir.

Üç algılama türleri şunlardır:

1.  İskelet anahtar – etki alanı denetleyicilerinde çalışan ve kendi parolasını bilmeden herhangi bir hesabı etki alanına kimlik doğrulaması sağlayan kötü amaçlı yazılım olur. Bu kötü amaçlı yazılım genellikle kullanıcının parolaları etki alanı denetleyicisinde şifrele için daha zayıf şifreleme algoritmalarını kullanır. Bu algılama, daha önceden öğrenilen davranışı karşılaştırıldığında şifreleme yöntemini kaynak bilgisayardan KRB_ERR iletisinin alt sürüme.

2.  Altın anahtar – içinde bir [altın anahtar](#golden-ticket) uyarı, kaynak bilgisayardan TGS_REQ (hizmet isteği) iletisinin TGT alanının şifreleme yöntemini daha önceden öğrenilen davranışı karşılaştırıldığında alt sürüme. Bu zaman anomali (olduğu gibi diğer altın anahtar algılama) dayanmıyor. Ayrıca, ATA tarafından algılanan önceki hizmet isteği ile ilişkili hiçbir Kerberos kimlik doğrulama isteği vardı.

3.  Karma Karma – kaynak bilgisayardan AS_REQ ileti şifreleme türü bir alt sürüme daha önceden öğrenilen davranışı karşılaştırıldığında (diğer bir deyişle, bilgisayar AES kullanılarak).

**Araştırma**

İlk olarak hangi ile ilgilenen yukarıdaki üç algılama türlerini görmek için uyarı açıklaması denetleyin.

1.  İskelet anahtar – iskelet anahtar kullanarak etki alanı denetleyicileriniz etkilediğini varsa denetleyebilirsiniz [ATA ekibi tarafından yazılan tarayıcı](https://gallery.technet.microsoft.com/Aorato-Skeleton-Key-24e46b73).
    Tarayıcı 1 veya daha fazla etki alanı denetleyicileriniz kötü amaçlı yazılım bulur, doğru pozitif olur.

2.  Altın anahtar –, nadiren kullanılır, özel bir uygulama kimlik doğrulaması daha düşük bir şifreleme şifrelemeyle durumlar vardır. Kaynak bilgisayarda bu tür özel uygulamalar olup olmadığını denetleyin. Öyleyse, bu büyük olasılıkla zararsız true pozitif ve gizlenebilir.

3.  Karma Karma – içinde bu uyarının akıllı kartlarla yapılandırılmış kullanıcılar etkileşimli oturum açma için gerekli olduğunda durumlar vardır ve bu ayarı devre dışı ve ardından etkin. İlgili hesapları için bu gibi değişiklikler olup olmadığını denetleyin. Öyleyse, bu büyük olasılıkla zararsız true pozitif ve gizlenebilir.

**Düzeltme**

1.  İskelet anahtar – kötü amaçlı yazılımı kaldırın. Daha fazla bilgi için bkz: [iskelet anahtar kötü amaçlı yazılım çözümlemesi](https://www.secureworks.com/research/skeleton-key-malware-analysis) SecureWorks tarafından.

2.  Altın bilet – yönergeleri izleyin [altın anahtar](#golden-ticket) kuşkulu etkinlikler.   
    Ayrıca, bir altın anahtar oluşturmak için etki alanı yönetici hakları gerekir çünkü uygulamak [karma önerileri geçirmek](http://aka.ms/PtH).

3.  Söz konusu hesabı hassas, değilse karma karma – sonra bu hesabın parolasını sıfırlayın. Mevcut biletleri, süreleri doluncaya kadar hala kullanılabilmesine karşın bu saldırgan parola karma değerden yeni Kerberos biletleri oluşturmasını engeller. Hassas hesap ise, iki kez altın anahtar şüpheli etkinlik olduğu gibi KRBTGT hesabı sıfırlama düşünmelisiniz. KRBTGT iki kez sıfırlama tüm Kerberos biletleri bu etki alanında, böylece bunu yapmadan önce planlama geçersiz kılar. Kılavuzunda bkz [KRBTGT hesabı parola sıfırlama betikleri müşteriler için artık kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/). Ayrıca bkz [KRBTGT hesabı parola/anahtarları aracı Sıfırla](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51). Yanal hareket teknik olduğundan, en iyi uygulamaları izleyerek [karma önerileri geçirmek](http://aka.ms/PtH).

## Altın anahtar<a name="golden-ticket"></a>

**Açıklama**

Saldırganlar etki alanı yönetici haklarına sahip tehlikeye [KRBTGT hesabı](https://technet.microsoft.com/library/dn745899(v=ws.11).aspx#Sec_KRBTGT). KRBTGT hesabı kullanarak, bunlar herhangi bir rastgele anda bilet sona erme tarihini ayarlayabilir ve herhangi bir kaynak için yetkilendirme sağlayan bilet (TGT) veren bir Kerberos anahtarı oluşturabilir. Bu sahte TGT "Altın anahtar" denir ve ağdaki kalıcılığı elde etmek, saldırganların sağlar.

İzni veriliyor bileti için kullanılan bir Kerberos anahtarı belirtildiği gibi izin verilen süre birden fazla izin verdiğinde bu algılama, bir uyarı tetiklendiğinde [kullanıcı anahtarının en fazla ömrü](https://technet.microsoft.com/library/jj852169(v=ws.11).aspx) güvenlik ilkesi.

**Araştırma**

1. Yapılan en son (son birkaç saat içinde) değişiklik oluştu **kullanıcı anahtarının en fazla ömrü** içinde Grup İlkesi ayarı? Yanıt Evet ise, ardından **Kapat** (Yanlış pozitif olduğu) uyarı.

2. ATA Gateway, bu uyarı bir sanal makine karmaşıktır? Yanıtınız evet ise, en son kaydedilen durumdan sürdürün? Yanıt Evet ise, ardından **Kapat** bu uyarı.

3. Yukarıdaki sorulara yanıt ise Hayır, bu kötü amaçlı olduğunu varsayalım.

**Düzeltme**

Kerberos anahtar verme anahtarı (KRBTGT) parolayı iki kez kılavuzunda göre değiştirmek [KRBTGT hesabı parola sıfırlama betikleri müşteriler için artık kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/)kullanarak [KRBTGT hesabı parola/anahtarlarını sıfırlama Aracı](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51). KRBTGT iki kez sıfırlama tüm Kerberos biletleri bu etki alanında, böylece bunu yapmadan önce planlama geçersiz kılar.  
Ayrıca, bir altın anahtar oluşturmak için etki alanı yönetici hakları gerekir çünkü uygulamak [karma önerileri geçirmek](http://aka.ms/PtH).

## <a name="honeytoken-activity"></a>Honeytoken etkinliği


**Açıklama**

Honeytoken hesapları tanımlamak ve bu hesapları içeren kötü amaçlı etkinliği izlemek için ayarladığınız decoy hesaplarıdır. Honeytoken hesapları saldırganlar (örneğin, SQL-Admin) çekici yöntemlerle çekmeye için çekici adı yaparken kullanılmayan, bırakılmalıdır. Herhangi bir etkinlikten kötü amaçlı davranış gösterebilir.

Honeytoken hesapları hakkında daha fazla bilgi için bkz: [Ata'yı yükleme - adım 7](install-ata-step7.md).

**Araştırma**

1.  Kaynak bilgisayar sahibinin kimliğini doğrulamak için Honeytoken hesabı kullanılıp şüpheli etkinlik sayfasında (örneğin, Kerberos, LDAP, NTLM) açıklanan yöntemi kullanarak denetleyin.

2.  Kaynak bilgisayarlar profili sayfalara göz atın ve bunları kimliği doğrulanmış hangi hesapların denetleyin. Honeytoken hesabı kullandıysanız bu hesapların sahipleri denetleyin.

3.  Bu, etkileşimli olmayan oturum açma olması, böylece uygulamalar veya kaynak bilgisayar üzerinde çalışan komut dosyaları için denetlediğinizden emin olun.

Kanıt zararsız kullanımı ise 1 ile 3 arasındaki adımları gerçekleştirdikten, sonra bu kötü amaçlı varsayalım.

**Düzeltme**

Hesapları yalnızca hedeflenen bunların amaçla kullanılan emin Honeytoken olun, aksi takdirde birçok uyarılar oluşturabilir.

## <a name="identity-theft-using-pass-the-hash-attack"></a>Kimlik hırsızlığı Pass--Hash saldırısı

**Açıklama**

Pass--Hash bir yanal hareket tekniktir saldırganlar bir bilgisayardan kullanıcının NTLM karmasını çalabilir ve başka bir bilgisayara erişim kazanmak için kullanın. 

**Araştırma**

Karma bir bilgisayardan hedeflenen kullanıcı sahibi veya düzenli olarak kullandığı kullanıldı? Yanıt Evet ise, yanlış pozitif budur. Değilse, doğru pozitif olabilir.

**Düzeltme**

1. Söz konusu hesabı hassas değilse, bu hesabın parolasını sıfırlayın. Mevcut biletleri, süreleri doluncaya kadar hala kullanılabilmesine karşın bu saldırgan parola karma değerden yeni Kerberos biletleri oluşturmasını engeller. 

2. Hassas hesap ise, iki kez altın anahtar şüpheli etkinlik olduğu gibi KRBTGT hesabı sıfırlama düşünmelisiniz. KRBTGT iki kez sıfırlama tüm Kerberos biletleri bu etki alanında, böylece bunu yapmadan önce planlama geçersiz kılar. Kılavuzunda bkz [KRBTGT hesabı parola sıfırlama betikleri müşteriler için artık kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/), ayrıca bkz [KRBTGT hesabı parola/anahtarları aracı Sıfırla](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51). Yanal hareket teknik olduğundan, en iyi uygulamaları izleyerek [karma önerileri geçirmek](http://aka.ms/PtH).

## <a name="identity-theft-using-pass-the-ticket-attack"></a>Kimlik hırsızlığı geçişi anahtar saldırısı

**Açıklama**

Geçişi anahtar bir yanal hareket tekniktir saldırganlar bir bilgisayardan Kerberos anahtarını çalabilir ve çalınan bilet yeniden kullanarak başka bir bilgisayara erişim kazanmak için kullanın. Bu algılama, Kerberos bileti iki (veya daha fazla) farklı bilgisayarlarda görülür.

**Araştırma**

1. Tıklatın **karşıdan ayrıntıları** dahil edilen IP adreslerinin tam listesini görmek için düğmesi. Veya her iki bilgisayar undersized bir DHCP havuzundan Örneğin, VPN veya WiFi ayrılmış bir alt ağa ait bir IP adresi mu? IP adresi paylaşılıyor mu? Örneğin, bir NAT cihazı tarafından? Ardından bu soruları hiçbirine yanıt Evet ise, yanlış pozitif olduğu.

2. Kullanıcılar adına biletleri iletir özel bir uygulamayı var mı? Bu nedenle, zararsız true pozitif olması durumunda.

**Düzeltme**

1. Söz konusu hesabı hassas değilse, bu hesabın parolasını sıfırlayın. Mevcut biletleri, süreleri doluncaya kadar hala kullanılabilmesine karşın bu saldırgan parola karma değerden yeni Kerberos biletleri oluşturmasını engeller.  

2. Hassas hesap ise, iki kez altın anahtar şüpheli etkinlik olduğu gibi KRBTGT hesabı sıfırlama düşünmelisiniz. KRBTGT iki kez sıfırlama tüm Kerberos biletleri bu etki alanında, böylece bunu yapmadan önce planlama geçersiz kılar. Kılavuzunda bkz [KRBTGT hesabı parola sıfırlama betikleri müşteriler için artık kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/), ayrıca bkz [KRBTGT hesabı parola/anahtarları aracı Sıfırla](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51).  Bu bir yanal hareket teknik olduğuna göre en iyi uygulamaları izleyin [karma önerileri geçirmek](http://aka.ms/PtH).

## <a name="malicious-data-protection-private-information-request"></a>Kötü Amaçlı Veri Koruma Özel Bilgi İsteği

**Açıklama**

Data Protection API (DPAPI) tarafından Windows tarayıcılar, şifrelenmiş dosyalar ve diğer hassas verileri tarafından kaydedilen parolaları güvenli bir şekilde korumak için kullanılır. Etki alanı denetleyicileri etki alanına katılmış Windows makinelerde DPAPI ile şifrelenmiş tüm gizlilikleri şifresini çözmek için kullanılan bir yedekleme ana anahtarı tutun. Saldırganlar etki alanına katılmış tüm makinelerde DPAPI tarafından korunan gizli şifresini çözmek için ana anahtar kullanabilirsiniz.
DPAPI yedekleme ana anahtarı almak için kullanıldığında, bu algılama, bir uyarı tetiklenir.

**Araştırma**

1. Organizasyon onaylı çalıştıran kaynak bilgisayar güvenlik tarayıcısı Active Directory karşı Gelişmiş?

2. Yanıt Evet ise ve bu her zaman bunu yapmanız gerekenler **kapatın ve dışlama** şüpheli etkinlik.

3. Yanıt Evet ise ve bu, yapmamalısınız **Kapat** şüpheli etkinlik.

**Düzeltme**

DPAPI kullanmak için bir saldırgan etki alanı yönetici hakları gerekir. Uygulama [karma önerileri geçirmek](http://aka.ms/PtH).

## <a name="malicious-replication-requests"></a>Kötü amaçlı çoğaltma istekleri


**Açıklama**

Active Directory çoğaltma bir etki alanı denetleyicisi üzerinde yapılan değişiklikler diğer tüm etki alanı denetleyicileriyle eşitlenir işlemidir. Gerekli izinleri verildiğinde, saldırganlar Active Directory içinde parola karmaları dahil olmak üzere depolanan verileri almak üzere vermeden çoğaltma isteğini başlatabilirsiniz.

Bir çoğaltma isteğini bir etki alanı denetleyicisi olmayan bir bilgisayardan başlatıldığında bu algılama, bir uyarı tetiklenir.

**Araştırma**

1. Söz konusu bilgisayar bir etki alanı denetleyicisi mi? Örneğin, çoğaltma olan yeni yükseltilen etki alanı denetleyicisi verir. Yanıt Evet ise, **kapatın ve dışlama** şüpheli etkinlik.  

2. Söz konusu bilgisayarın verileri Active Directory'den çoğaltma olması gerekiyor? Örneğin, Azure AD Connect. Yanıt Evet ise, **kapatın ve dışlama** şüpheli etkinlik.

**Düzeltme**

Aşağıdaki izinleri doğrulama: 

- Dizin Değişikliklerini Çoğaltma   

- Tüm dizin değişikliklerini çoğaltma  

Daha fazla bilgi için bkz: [profil eşitleme SharePoint Server 2013'te Grant Active Directory etki alanı Hizmetleri izinlerini](https://technet.microsoft.com/library/hh296982.aspx).
Yararlanabileceğiniz [AD ACL tarayıcı](https://blogs.technet.microsoft.com/pfesweplat/2013/05/13/take-control-over-ad-permissions-and-the-ad-acl-scanner-tool/) veya kimin etki alanında bu izinleri olduğunu belirlemek için bir Windows PowerShell Betiği oluşturun.

## <a name="massive-object-deletion"></a>Büyük çaplı nesne silme

**Açıklama**

Bazı senaryolarda, saldırganlar yalnızca bilgileri çalarak yerine (DoS) hizmet reddine gerçekleştirin. Çok sayıda hesapları silme bir DoS tekniktir.

Tüm hesapları % 5'den fazla silindiğinde bu algılama, bir uyarı tetiklenir. Algılama Silinmiş nesne kapsayıcısı için okuma erişimi gerektirir.  
Silinmiş nesne kapsayıcısı üzerinde salt okuma izinlerini yapılandırma hakkında daha fazla bilgi için bkz: **Silinmiş nesne kapsayıcısı üzerindeki izinleri değiştirme** içinde [izinleri görüntüleme veya ayarlama dizin nesnesi üzerindeki](https://technet.microsoft.com/library/cc816824%28v=ws.10%29.aspx).

**Araştırma**

Silinen hesapların listesini gözden geçirin ve bir desen veya bu yoğun silme iki yana yaslamak bir iş neden olup olmadığını anlamak.

**Düzeltme**

Active Directory'de hesapları silebilen kullanıcıların izinlerini kaldırın. Daha fazla bilgi için bkz: [izinleri görüntüleme veya ayarlama dizin nesnesi üzerindeki](https://technet.microsoft.com/library/cc816824%28v=ws.10%29.aspx).

## <a name="privilege-escalation-using-forged-authorization-data"></a>Ayrıcalık yükseltme kullanarak sahte yetkilendirme verileri

**Açıklama**

Windows Server'ın daha eski sürümleri güvenlik açıkları izin ayrıcalıklı öznitelik sertifikası (PAC), bir kullanıcı yetkilendirme verisi içeren Kerberos bileti alanında işlemek saldırganlar bilinen (Active Directory grup üyeliğini budur), verme saldırganlar ek ayrıcalıklar.

**Araştırma**

1. Kendi ayrıntıları sayfasına ulaşmak için uyarıyı tıklayın.

2. Hedef bilgisayar (altında **ACCESSED** sütun) MS14-068 (etki alanı denetleyicisi) veya MS11-013 (sunucu) ile düzeltme eki uygulandı? Yanıt Evet ise, **Kapat** (Yanlış pozitif olması) şüpheli etkinlik.

3. Kaynak bilgisayar çalışmazsa (altında **FROM** sütun) PAC değiştirmek için bilinen bir işletim sistemi/uygulama? Yanıt Evet ise, **bastır** (zararsız true olumlu olduğu) şüpheli etkinlik.

4. Yanıt ise Hayır Yukarıdaki iki sorulara bu kötü amaçlı olduğunu varsayalım.

**Düzeltme**

Windows Server 2012 R2 ve altı işletim sistemi sürümleri kullanan etki alanı denetleyicilerinde [KB3011780](https://support.microsoft.com/help/2496930/ms11-013-vulnerabilities-in-kerberos-could-allow-elevation-of-privilege)’in yüklü olduğundan ve tüm üye sunucularla 2012 R2 ve altı sürümlerdeki etki alanı denetleyicilerinin KB2496930 güncel sürümünde olduğundan emin olun. Daha fazla bilgi için bkz. [Gümüş PAC](https://technet.microsoft.com/library/security/ms11-013.aspx) ve [Sahte PAC](https://technet.microsoft.com/library/security/ms14-068.aspx).

## <a name="reconnaissance-using-account-enumeration"></a>Hesap numaralandırma kullanarak keşif

**Açıklama**

Hesap numaralandırma keşif bir saldırgan, kullanıcı adlarını veya KrbGuess gibi araçları binlerce ile kullanıcı adlarını, etki alanınızdaki tahmin etme girişiminde bir sözlük kullanır. Saldırgan, geçerli bir kullanıcı adı, etki alanınızdaki bulmak için bu adları kullanarak Kerberos istekleri yapıyorsa. Bir tahmin başarılı bir şekilde bir kullanıcı adı belirlerse, saldırganın Kerberos hata iletisiyle karşılaşırsınız **gerekli ön kimlik doğrulama** yerine **güvenlik sorumlusu bilinmeyen**. 

Bu algılama, ATA saldırı nereden geldiğini, tahmin denemeleri toplam sayısı ve kaç tane eşleştirildiklerinden algılayabilir. Bilinmeyen çok sayıda kullanıcı varsa, ATA kuşkulu bir etkinlik algılar. 

**Araştırma**

1. Kendi ayrıntıları sayfasına ulaşmak için uyarıyı tıklayın. 

2. Bu ana bilgisayar makinesi olup hesapları (örneğin, Exchange sunucuları) mevcut için etki alanı denetleyicisi sorgu? <br></br>
Bir komut dosyası veya bu davranış üretebilir ana bilgisayar üzerinde çalışan uygulama var mı? <br></br>
Ya da bu sorulara yanıt Evet ise, **Kapat** şüpheli etkinliğinden konak dışlama ve şüpheli etkinlik (zararsız true pozitif değil).

3. Uygun hesap girişimleri, var olan ve var olmayan hesaplara bölünmüş listesini görmek için bir Excel elektronik tablosuna uyarıda ayrıntılarını indirin. Bakarsanız elektronik tablosuna olmayan var olan hesapları ve hesapları tanıdık, devre dışı bırakılan hesapları veya şirket sol çalışanlar olabilir. Bu durumda, deneme sözlükten geliyor düşüktür. Büyük olasılıkla bir uygulama veya hangi hesapların Active Directory içinde zararsız true pozitif yani hala mevcut görmek için denetimi komut dosyası değil.

3. Adları büyük ölçüde tanımıyorsanız tahmin denemeleri hiçbirini Active Directory'de mevcut hesabı adları eşleşmiyor? Herhangi bir eşleşme varsa, denemesi yararsız ancak, zaman içinde güncelleştirilmiş, uyarının dikkat etmeniz gerekir.

4. Tahmin hiçbirini çalışırsa bulunan kullanıcı adlarını kullanarak, etki alanına erişmek için deneme yanılma saldırısı kullanmayı deneyebilir ve ortamınızdaki hesaplarının varlığı, saldırganın bilir mevcut hesabı adları eşleşmiyor. Ek şüpheli etkinlikler için tahmin edilen hesap adlarını denetleyin. Herhangi bir eşleşen hesaplar hassas hesapları olup olmadığını denetleyin.


**Düzeltme**

[Uzun ve karmaşık parolalar](https://docs.microsoft.com/windows/device-security/security-policy-settings/password-policy) yanılma saldırılarına karşı güvenlik gerekli ilk düzeyi sağlar.


## <a name="reconnaissance-using-directory-services-queries"></a>Dizin hizmetleri sorguları kullanarak keşif

**Açıklama**

Dizin Hizmetleri Keşif, dizin yapısını eşlemeniz ve daha sonraki adımlarda saldırının için ayrıcalıklı hesapları hedef saldırganlar tarafından kullanılır. Güvenlik hesabı yöneticisinin uzaktan (SAM-R) protokolü bu tür eşlemeyi gerçekleştirmek için dizini sorgulamak için kullanılan yöntemleri biridir.

Bu algılama, hiçbir uyarı ATA dağıtıldıktan sonra ilk ay içinde tetiklenen. Hangi SAM-R sorguların hangi bilgisayarlardan yapılan öğrenme dönemi ATA profilleri sırasında numaralandırması ve hassas hesaplarının tek tek sorgular.

**Araştırma**

1. Kendi ayrıntıları sayfasına ulaşmak için uyarıyı tıklayın. Hangi sorguların (örneğin, Enterprise admins veya yönetici) gerçekleştirilen ve desteklemediğini başarılı denetleyin.

2. Bu tür sorgular kaynak bilgisayardan söz konusu yapılması gerekir?

3. Evet ve uyarı güncelleştirdiyseniz, **bastır** şüpheli etkinlik.

4. Yanıt Evet ise ve onu, bunu kullanmayın **Kapat** şüpheli etkinlik.

5. Söz konusu hesabıyla ilgili bilgiler ise: sorgularını o hesap tarafından yapılması gereken ya da bu hesabı normalde kaynak bilgisayarda oturum mu?

 - Evet ve uyarı güncelleştirdiyseniz, **bastır** şüpheli etkinlik.

 - Yanıt Evet ise ve onu, bunu kullanmayın **Kapat** şüpheli etkinlik.

 - Yanıt Hayır tüm olursa yukarıdaki bu kötü amaçlı olduğunu varsayalım.

**Düzeltme**

Kullanım [SAMRi10 aracı](https://gallery.technet.microsoft.com/SAMRi10-Hardening-Remote-48d94b5b) ortamınızı Bu teknik karşı sağlamlaştırmak için.

## <a name="reconnaissance-using-dns"></a>DNS kullanarak keşif

**Açıklama**

DNS sunucunuzu tüm bilgisayarlar, IP adresleri ve Hizmetleri, ağınızda haritasını içerir. Saldırganlar bu bilgileri kullanarak ağ yapınızın haritasını çıkarır ve saldırının sonraki adımlarında kullanmak üzere uygun bilgisayarları hedef alır.

DNS protokolünde birkaç sorgu türü vardır. ATA olmayan DNS sunucularından kaynaklanan AXFR (aktarım) isteği algılar.

**Araştırma**

1. Kaynak makinenin (**kaynaklanan...** ) bir DNS sunucusu? Yanıt Evet ise, bu büyük olasılıkla yanlış pozitif ise. Doğrulamak için ayrıntıları sayfasına ulaşmak için uyarıyı tıklayın. Tabloda, altında **sorgu**, hangi etki alanlarının sorgulanan denetleyin. Bu var olan etki alanları misiniz? Yanıt Evet ise, ardından **Kapat** (Yanlış pozitif olması) şüpheli etkinlik. Ayrıca, UDP bağlantı noktası 53 ATA Gateway ve gelecekteki hatalı pozitif sonuç önlemek için kaynak bilgisayar arasında açık olduğundan emin olun.

2. Kaynak Makine güvenlik tarayıcısı çalışıyor mu? Yanıt Evet ise, **varlıkları dışlama** doğrudan Ata **kapatın ve dışlama** veya aracılığıyla **dışlama** sayfa (altında **yapılandırma** – kullanılabilir ATA yöneticileri için).

3. Bu kötü amaçlı olup tüm yukarıdaki yanıt Hayır, olduğunu varsayarsak.

**Düzeltme**

DNS kullanarak keşfi önlemek amacıyla DNS sunucusunu güvenlik altına almak için bölge aktarımlarını yalnızca belirtilen IP adresleriyle kısıtlamak veya devre dışı bırakmak mümkündür. Bölge aktarımlarının kısıtlama daha fazla bilgi için bkz: [kısıtlamak bölge aktarımlarının](https://technet.microsoft.com/library/ee649273(v=ws.10).aspx).
Bölge aktarımlarının değiştirme olan bir görev için ele alınması gereken bir denetim listesi arasında [, DNS sunucularınızın iç ve dış saldırılara karşı güvenli hale getirme](https://technet.microsoft.com/library/cc770432(v=ws.11).aspx).

## <a name="reconnaissance-using-smb-session-enumeration"></a>SMB Oturumu Listeleme kullanarak Keşif


**Açıklama**

Sunucu İleti Bloğu (SMB) hakkında bilgi almak yere yakın zamanda açmış kullanıcılar saldırganlar etkinleştirir. Saldırganlar bu bilgileri olduktan sonra bunlar ağ için özel bir hassas hesap almak için yanal taşıyabilirsiniz.

Bir etki alanı denetleyicisine karşı bir SMB oturumu numaralandırma gerçekleştirildiğinde bu olmayacak çünkü bu algılama, bir uyarı tetiklenir.

**Araştırma**

1. Kendi ayrıntıları sayfasına ulaşmak için uyarıyı tıklayın. Hangi hesabı/s işlemi gerçekleştirilen ve hangi hesapların ortaya, varsa denetleyin.

 - Kaynak bilgisayarda çalışan güvenlik tarayıcısı çeşit vardır? Yanıt Evet ise, **kapatın ve dışlama** şüpheli etkinlik.

2. Söz konusu hangi kullanıcı/s işlem gerçekleştirilirken denetleyin. Kaynak bilgisayarın normal şekilde oturum açmayın veya bunlar gibi eylemleri gerçekleştirmesi gereken yöneticiler?  

3. Evet ve uyarı güncelleştirdiyseniz, **bastır** şüpheli etkinlik.  

4. Yanıt Evet ise ve onu, bunu kullanmayın **Kapat** şüpheli etkinlik.

5. Bu kötü amaçlı olup tüm yukarıdaki yanıt Hayır, olduğunu varsayarsak.

**Düzeltme**

Kullanım [Net sona aracı](https://gallery.technet.microsoft.com/Net-Cease-Blocking-Net-1e8dcb5b) ortamınızı bu saldırılara karşı sağlamlaştırmak için.

## <a name="remote-execution-attempt-detected"></a>Uzaktan yürütme girişimi algılandı

**Açıklama**

Yönetimsel kimlik bilgilerini tehlikeye veya sıfırıncı gün yararlanma kullanın saldırganlar etki alanı denetleyicinizde uzaktan komutları çalıştırabilirsiniz. Bu komutlar kalıcılık sağlamak, bilgi toplamak, hizmet reddi (DoS) saldırıları ve diğer herhangi bir sebeple kullanılabilir. ATA PSexec ve uzak WMI bağlantıları algılar.

**Araştırma**

1. Bu, yönetim iş istasyonları ve BT ekibi üyeleri ve etki alanı denetleyicilerine karşı yönetim görevlerini gerçekleştirmek hizmet hesapları için yaygındır. Bu ise durum ve uyarı aynı yönetici bu yana güncelleştirilen ve/veya bilgisayar gerçekleştirme görev sonra **bastır** uyarı.

2. Olan **bilgisayar** söz konusu etki alanı denetleyicisine karşı bu uzaktan yürütme gerçekleştirmeye izin?

 - Olan **hesap** söz konusu etki alanı denetleyicisine karşı bu uzaktan yürütme gerçekleştirmeye izin?

 - Her iki soruların yanıtlanması gerekirse *Evet*, ardından **Kapat** uyarı.

3. Her iki sorulara yanıt ise *hiçbir*, bu geçerli bir pozitif gerekenlerin sonra.

**Düzeltme**

1. Katman 0 olmayan makinelerden etki alanı denetleyicilerine uzaktan erişimi kısıtlayın.

2. Uygulama [ayrıcalıklı erişim](https://technet.microsoft.com/windows-server-docs/security/securing-privileged-access/securing-privileged-access) yalnızca sağlamlaştırılmış makinelerin yöneticileri için etki alanı denetleyicilerine bağlanmasına izin vermek için.

## <a name="sensitive-account-credentials-exposed--services-exposing-account-credentials"></a>Hassas hesap kimlik bilgilerini kullanıma sunulan & Hizmetleri hesabı kimlik bilgileri gösterme

**Açıklama**

Bazı hizmetler hesabı kimlik bilgileri düz metin olarak gönderir. Bu durum, hassas hesapları için bile oluşabilir. Ağ trafiğini izleme saldırganlar catch ve bu kimlik bilgileri kötü amaçlı olarak yeniden kullanabilirsiniz. Beş veya daha fazla farklı hesapları aynı kaynak bilgisayardan düz metin parolalarını gönderirseniz hassas olmayan hesaplar için uyarıyı tetikleyen sürece herhangi bir düz metin parolası hassas hesap için uyarı tetikler. 

**Araştırma**

Kendi ayrıntıları sayfasına ulaşmak için uyarıyı tıklayın. Hangi hesapların ortaya bakın. Böyle birçok hesapları varsa tıklatın **karşıdan ayrıntıları** bir Excel elektronik tabloda listesini görmek için.

Genellikle LDAP basit bağlama kullanan komut dosyası veya eski uygulama kaynak bilgisayarlarda yoktur.

**Düzeltme**

Kaynak bilgisayarlarda yapılandırmayı doğrulayın ve LDAP basit bağlaması kullanmadığınızdan emin olun. LDAP basit bağlamalar kullanmak yerine, LDAP SALS veya LDAPS kullanabilirsiniz.

## <a name="suspicious-authentication-failures"></a>Kuşkulu kimlik doğrulama hataları

**Açıklama**

Yanılma saldırısında, saldırganın en az bir hesap için doğru parolayı bulunana kadar farklı hesaplar için birçok farklı parolaları ile kimlik doğrulaması dener. Bir kez bulundu, bir saldırganın bu hesabı kullanarak oturum açabilir.

Bu algılama, birçok kimlik doğrulama hataları oluştuğunda bir uyarının, bu parolalar, küçük bir kümesini yatay ile ya da çok sayıda kullanıcı arasında olması; veya dikey büyük ile Parolaları yalnızca birkaç kullanıcılar ayarlayın; veya bu iki seçenek herhangi bir bileşimini.

**Araştırma**

1. İlgili birçok hesapları varsa tıklatın **karşıdan ayrıntıları** bir Excel elektronik tabloda listesini görmek için.

2. Kendi ayrıntıları sayfasına gitmek için uyarıyı tıklayın. Onay hiçbir oturum açma denemesi olursa başarılı bir kimlik doğrulaması ile sona erdi, bunlar şöyle görünür **hesapları tahmin** bilgi grafiği sağ tarafındaki. Yanıt Evet ise, olan **hesapları tahmin** kaynak bilgisayardan normalde kullanılan? Yanıt Evet ise, **bastır** şüpheli etkinlik.

3. Varsa hiçbir **hesapları tahmin**, olan **saldırıya hesapları** kaynak bilgisayardan normalde kullanılan? Yanıt Evet ise, **bastır** şüpheli etkinlik.

**Düzeltme**

[Uzun ve karmaşık parolalar](https://docs.microsoft.com/windows/device-security/security-policy-settings/password-policy) yanılma saldırılarına karşı güvenlik gerekli ilk düzeyi sağlar.

## <a name="suspicion-of-identity-theft-based-on-abnormal-behavior"></a>Anormal davranışa bağlı kimlik hırsızlığı şüphesi

**Açıklama**

ATA, bir kayan üç hafta dönemi boyunca kullanıcılar, bilgisayarlar ve kaynaklar için varlık davranış öğrenir. Davranış modeli aşağıdaki etkinliklerde dayanır: makineler varlıklar için oturum, varlık istenen kaynaklar erişim için ve bu işlemleri yerine geçen süre. ATA varlığın davranışını learning algoritmaları makineye dayalı sapma olduğunda bir uyarı gönderir. 

**Araştırma**

1. Söz konusu kullanıcı bu işlemleri gerçekleştirmeyi gerekiyor?

2. Aşağıdaki durumlarda olası hatalı pozitif sonuç olarak göz önünde bulundurun: tatil, aşırı erişimi kendi vergi (örneğin bir depo Yardım Masası desteği belirli gün veya hafta), bir parçası olarak gerçekleştirdiği BT personeli gelen Uzak Masaüstü uygulamaları döndürdü. bir kullanıcı + ise, **Kapatın ve dışlama** kullanıcı artık uyarı algılama bir parçası olması


**Düzeltme**

Neyin bu anormal davranışları oluşmasına neden bağlı olarak, farklı eylemler yapılması gerekir. Bu ağ, tarama nedeniyle ise, (onaylanan sürece) Örneğin, bu durumun oluştuğu makine ağdan engellenmelidir.

## <a name="unusual-protocol-implementation"></a>Olağan dışı protokol uygulanması


**Açıklama**

Saldırganlar, standart olmayan yollarla çeşitli protokoller (SMB, Kerberos, NTLM) uygulama araçlarını kullanın. Bu tür ağ trafiği uyarılar olmadan Windows tarafından kabul edilir, ancak ATA olası kötü amaçlı tanıyabilir. Gelişmiş yazılımı, örneğin, WannaCry tarafından kullanılan açıkları yanı sıra, Over-Pass--Hash ve kaba kuvvet gibi teknikler göstergesi davranıştır.

**Araştırma**

Şüpheli etkinlik zaman satırından – olağandışıdır Protokolü tanımlamak, kendi ayrıntıları sayfasına ulaşmak için şüpheli etkinlik tıklayın; Ok Protokolü görünür: Kerberos veya NTLM.

- **Kerberos**: büyük olasılıkla bir karma--Hash saldırısı gerçekleştiren Mimikatz kullanılmış gibi bir korsan aracı, bu genellikle tetiklenir. Kaynak bilgisayar Kerberos RFC uygun olmayan biçimde kendi Kerberos yığınını uygulayan bir uygulama çalışıp çalışmadığını denetleyin. Böyle, zararsız true pozitif ise ve yapabilecekleriniz **Kapat** uyarı. Uyarıyı tetikleyen tutar ve hala durumda ise, yapabilecekleriniz **bastır** uyarı.

- **NTLM**: WannaCry veya Metasploit, Medusa ve Hydra gibi araçları olabilir.  

Bu WannaCry saldırı olup olmadığını belirlemek için aşağıdaki adımları gerçekleştirin:

1. Kaynak bilgisayar bir saldırı aracı Metasploit, Medusa veya Hydra gibi çalışıp çalışmadığını denetleyin.

2. Hiçbir saldırı araçları bulunursa, kaynak bilgisayarın kendi NTLM veya SMB yığınını uygulayan bir uygulama çalışıp çalışmadığını denetleyin.

3. Aksi durumda bu WannaCry tarafından WannaCry tarayıcı komut dosyası, örneğin çalıştırarak neden olup olmadığını denetleyin [bu tarayıcı](https://github.com/apkjet/TrustlookWannaCryToolkit/tree/master/scanner) kuşkulu etkinliğin söz konusu kaynak bilgisayara karşı. Tarayıcı makine makine düzeltme eki uygulama ve kötü amaçlı yazılım kaldırma ve ağdan engelleme etkilenen ya da güvenlik açığı, iş olarak bulursa.

4. Komut dosyası makine virüs bulaşmış veya güvenlik açığı, sonra hala bulaşmış ancak SMBv1 devre dışı olabilir veya makine düzeltme eki, bulamadıysanız, Tarama Aracı etkiler.

**Düzeltme**

Özellikle güvenlik güncelleştirmelerini uygulamak tüm makinelerinizi, düzeltme eki.

1. [SMBv1 devre dışı bırak](https://blogs.technet.microsoft.com/filecab/2016/09/16/stop-using-smb1/)

2. [WannaCry Kaldır](https://support.microsoft.com/help/890830/remove-specific-prevalent-malware-with-windows-malicious-software-remo)

3. Kullanıcı yeniden değil veya olduğu bilgisayarın açık varsa WanaKiwi ancak bazı ransom yazılım eline verilerin şifresini çözebilir. Daha fazla bilgi için bkz: [Cry yazılımı istiyor](https://answers.microsoft.com/en-us/windows/forum/windows_10-security/wanna-cry-ransomware/5afdb045-8f36-4f55-a992-53398d21ed07?auth=1)

## <a name="related-videos"></a>İlgili videolar
- [Güvenlik topluluğu birleştirme](https://channel9.msdn.com/Shows/Microsoft-Security/Join-the-Security-Community)


## <a name="see-also"></a>Ayrıca bkz:
- [ATA kuşkulu etkinlik playbook](http://aka.ms/ataplaybook)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
