---
title: Azure ATP şüpheli etkinlik Kılavuzu | Microsoft Docs
d|Description: This article provides a list of the suspicious activities Azure ATP can detect and steps for remediation.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/6/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: ca5d1c7b-11a9-4df3-84a5-f53feaf6e561
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 9b28cf2497e1f742416f996e4b2dcaf934dc9142
ms.sourcegitcommit: 39a1ddeb6c9dd0817f92870b711627350b7f6f03
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*


# <a name="azure-advanced-threat-protection-suspicious-activity-guide"></a>Azure Advanced Threat Protection şüpheli etkinlik Kılavuzu

Uygun araştırma tüm şüpheli etkinlikleri olarak sınıflandırılabilir:

-   **Doğru pozitif**: Azure ATP tarafından algılanan kötü amaçlı bir eylem.

-   **Zararsız true pozitif**: Gerçek ancak değil kötü niyetli bir sızma testi gibi Azure ATP tarafından algılanan bir eylem.

-   **Yanlış pozitif**: yanlış alarm etkinlik anlamına durum alamadık.

Azure ATP uyarılarla çalışma hakkında daha fazla bilgi için bkz: [kuşkulu etkinliklerle çalışma](working-with-suspicious-activities.md).


## <a name="abnormal-sensitive-group-modification"></a>Anormal Gizli Grup Değişikliği


**Açıklama**

Saldırganlar kullanıcılar yüksek ayrıcalıklı gruplara ekleyin. Daha fazla kaynaklarına erişim kazanmak için ve kalıcılığı kazanmak için bunu. Algılama, kullanıcıların Grup değiştirme etkinliklerini profil ve hassas grubu olağan dışı bir eklemeyi görülen olduğunda uyarı dayanır. Profil oluşturma ATP tarafından sürekli olarak gerçekleştirilir. Bir uyarıyı tetikleyen önce en az bir ay boyunca her etki alanı denetleyicisi başına noktadır.

Azure ATP hassas gruplara tanımı için bkz: [hassas hesaplarıyla çalışmaya](sensitive-accounts.md).


Algılama dayanan [etki alanı denetleyicilerinde Denetlenen olayları](configure-event-collection.md).
Etki alanınızı emin olmak için gerekli olayları denetleyicileri denetim.

**Araştırma**

1. Grubu değişiklik yasal mi? </br>Nadiren oluşur ve "olarak normal", öğrenilen değil yasal grubu değişiklikleri zararsız true pozitif olarak değerlendirilebilecek bir uyarı neden olabilir.

2. Eklenen nesne bir kullanıcı hesabı varsa, kullanıcı hesabının yönetim grubuna eklendikten sonra geçen hangi eylemleri denetleyin. Daha fazla içerik almak için Azure ATP kullanıcının sayfasına gidin. Diğer vardı önce veya sonra ek hesapla ilişkili kuşkulu etkinlikleri gerçekleşen? Karşıdan **hassas grubu değişiklik** ne olan diğer tüm değişiklikleri görmek için raporu yapılmış ve aynı saat diliminde kim tarafından.

**Düzeltme**

Hassas gruplarını değiştirmek için yetkili kullanıcıların sayısını en aza indirin.

Ayarlanan [Active Directory için Privileged Access Management](https://docs.microsoft.com/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services) varsa.


## <a name="brute-force-attack-using-ldap-simple-bind"></a>LDAP basit bağlama kullanarak yanılma saldırısı

**Açıklama**

>[!NOTE]
> Arasındaki temel fark **kuşkulu kimlik doğrulama hataları** ve bu algılama bu algılama, Azure ATP farklı parolalar kullanımda olup olmadığını belirleyebilirsiniz.

Yanılma saldırısında, saldırganın en az bir hesap için doğru parolayı bulunana kadar farklı hesaplar için birçok farklı parolaları ile kimlik doğrulaması dener. Bir kez bulundu, bir saldırganın bu hesabı kullanarak oturum açabilir.

Bu algılama, Azure ATP yoğun birkaç basit bağı kimlik doğrulamalarını algıladığında bir uyarı tetiklenir. Bu da olabilir *yatay* parolaları çok sayıda kullanıcı; boyunca küçük bir dizi veya *dikey "* parolaları yalnızca birkaç kullanıcı; veya bu iki seçenek herhangi bir bileşimini büyük bir dizi.

**Araştırma**

1. İlgili birçok hesapları varsa tıklatın **karşıdan ayrıntıları** bir Excel elektronik tabloda listesini görmek için.

2. Ayrılmış sayfasına gitmek için uyarıyı tıklayın. Tüm oturum açma denemesi olursa onay başarılı bir kimlik doğrulaması ile sona erdi. Deneme olarak görüneceği **hesapları tahmin** bilgi grafiği sağ tarafındaki. Yanıt Evet ise, olan **hesapları tahmin** kaynak bilgisayardan normalde kullanılan? Yanıt Evet ise, **bastır** şüpheli etkinlik.

3. Varsa hiçbir **hesapları tahmin**, olan **saldırıya hesapları** kaynak bilgisayardan normalde kullanılan? Yanıt Evet ise, **bastır** şüpheli etkinlik.

**Düzeltme**

[Uzun ve karmaşık parolalar](https://docs.microsoft.com/windows/device-security/security-policy-settings/password-policy) yanılma saldırılarına karşı güvenlik gerekli ilk düzeyi sağlar.

## <a name="encryption-downgrade-activity"></a>Şifreleme indirgeme etkinliği

**Açıklama**

Şifreleme indirgeme şifreleme düzeyini genellikle en yüksek düzeyde şifreleme kullanılarak şifrelenir farklı alanları protokolü, eski sürüme düşürmeyi Kerberos zayıflatmanın bir yöntemdir. Zayıf bir şifrelenmiş alan çevrimdışı yanılma denemeleri daha kolay bir hedefe olabilir. Çeşitli saldırı yöntemleri zayıf Kerberos şifreleme cyphers kullanın. Bu algılama Azure ATP bilgisayarlar ve kullanıcılar tarafından kullanılan Kerberos şifreleme türlerini öğrenir ve, zayıf bir şifreleme olduğunda kullanılan uyarılar: (1) kaynak bilgisayar ve/veya kullanıcı; olağandışıdır ve saldırı teknikleri bilinen (2) eşleşir.

Üç algılama türleri şunlardır:

1.  İskelet anahtar – etki alanı denetleyicilerinde çalışan ve kendi parolasını bilmeden herhangi bir hesabı etki alanına kimlik doğrulaması sağlayan kötü amaçlı yazılım olur. Bu kötü amaçlı yazılım, etki alanı denetleyicisinde kullanıcının parolaları karma hale genellikle daha zayıf şifreleme algoritmalarını kullanır. Bu algılama, daha önceden öğrenilen davranışı karşılaştırıldığında şifreleme yöntemi için bir bilet isteyen hesabı için etki alanı denetleyicisinden KRB_ERR iletisinin alt sürüme.

2.  Altın anahtar – içinde bir [altın anahtar](#golden-ticket) uyarı, kaynak bilgisayardan TGS_REQ (hizmet isteği) iletisinin TGT alanının şifreleme yöntemini daha önceden öğrenilen davranışı karşılaştırıldığında alt sürüme. Bu zaman anomali (olduğu gibi diğer altın anahtar algılama) dayanmıyor. Ayrıca, ATP tarafından algılanan önceki hizmet isteği ile ilişkili hiçbir Kerberos kimlik doğrulama isteği vardı.

3.  Karma Karma – bir saldırganın zayıf çalınan karma Kerberos AS isteği ile güçlü bir anahtar oluşturmak için kullanabilirsiniz. Bu algılama, kaynak bilgisayardan AS_REQ ileti şifreleme türü daha önceden öğrenilen davranışı karşılaştırıldığında alt sürüme (bilgisayar, AES kullanıyordu).

**Araştırma**

İlk olarak hangi ile ilgilenen yukarıdaki üç algılama türlerini görmek için uyarı açıklaması denetleyin. Araştırma önce hangi ile ilgilenen yukarıdaki üç algılama türlerini görmek için uyarı açıklaması kontrol edin. Daha fazla bilgi için Excel elektronik tablosu indirin.

1.  İskelet anahtar – iskelet anahtar kullanarak etki alanı denetleyicileriniz etkilediğini varsa denetleyebilirsiniz [Azure ATP ekibi tarafından yazılan tarayıcı](https://gallery.technet.microsoft.com/Aorato-Skeleton-Key-24e46b73). Tarayıcı 1 veya daha fazla etki alanı denetleyicileriniz kötü amaçlı yazılım bulur, doğru pozitif olur.

2.  Altın anahtar – excel elektronik tablodaki ağ etkinliği sekmesine gidin. İlgili branchcache'in alan olduğunu göreceksiniz **istek anahtarı şifreleme türü**, ve **kaynak bilgisayarı desteklenen şifreleme türlerini** daha güçlü şifreleme yöntemi içerir.

  1. Kaynak bilgisayarı ve hesap denetleyin veya varsa birden çok kaynak bilgisayarlar ve hesaplarını bunlar bir şey (örneğin, tüm pazarlama personeli tetiklenmesi için uyarıyı neden belirli bir uygulama kullanma) ortak içinde olup olmadığını denetleyin. İçinde nadiren kullanılır, özel bir uygulama kimlik doğrulaması daha düşük bir şifreleme şifrelemeyle durumlar vardır. Kaynak bilgisayarda bu tür özel uygulamalar olup olmadığını denetleyin. Öyleyse, bu büyük olasılıkla zararsız true pozitif ve gizlenebilir.
  
  2. Kaynak denetimi bu biletleri tarafından erişilen, tüm erişmekte olan bir kaynak ise, doğrulamak, erişim olması geçerli bir kaynak olduğundan emin olun. Ayrıca, hedef kaynak güçlü şifreleme yöntemleri destekleyip desteklemediğini doğrulayın. Bu öznitelik msDS-SupportedEncryptionTypes, kaynak hizmet hesabının denetleyerek Active Directory'de denetleyebilirsiniz.

3.  Karma Karma – excel elektronik tablodaki ağ etkinliği sekmesine gidin. İlgili branchcache'in alan olduğunu göreceksiniz **şifrelenmiş zaman damgası şifreleme türü** ve **kaynak bilgisayarı desteklenen şifreleme türlerini** daha güçlü şifreleme yöntemi içerir.

  1. Bazı kullanıcılar akıllı kart yapılandırması yakın zamanda değiştiyse akıllı kart kullanarak oturum açtığınızda, bu uyarıyı tetikleyen. İlgili hesapları için bu gibi değişiklikler olup olmadığını denetleyin. Öyleyse, bu büyük olasılıkla zararsız true pozitif ve gizlenebilir.
  2. Kaynak denetimi bu biletleri tarafından erişilen, tüm erişmekte olan bir kaynak ise, doğrulamak, erişim olması geçerli bir kaynak olduğundan emin olun. Ayrıca, hedef kaynak güçlü şifreleme yöntemleri destekleyip desteklemediğini doğrulayın. Bu öznitelik msDS-SupportedEncryptionTypes, kaynak hizmet hesabının denetleyerek Active Directory'de denetleyebilirsiniz.

**Düzeltme**

1.  İskelet anahtar – kötü amaçlı yazılımı kaldırın. Daha fazla bilgi için bkz: [iskelet anahtar kötü amaçlı yazılım çözümlemesi](https://www.secureworks.com/research/skeleton-key-malware-analysis) SecureWorks tarafından.

2.  Altın bilet – yönergeleri izleyin [altın anahtar](#golden-ticket) kuşkulu etkinlikler.   
    Ayrıca, bir altın anahtar oluşturmak için etki alanı yönetici hakları gerekir çünkü uygulamak [karma önerileri geçirmek](http://aka.ms/PtH).

3.  Söz konusu hesabı hassas, değilse karma karma – sonra bu hesabın parolasını sıfırlayın. Mevcut biletleri, süreleri doluncaya kadar hala kullanılabilmesine karşın bu saldırgan parola karma değerden yeni Kerberos biletleri oluşturmasını engeller. Hassas hesap ise, iki kez altın anahtar şüpheli etkinlik olduğu gibi KRBTGT hesabı sıfırlama düşünmelisiniz. KRBTGT iki kez sıfırlama tüm Kerberos biletleri bu etki alanında, böylece bunu yapmadan önce planlama geçersiz kılar. Kılavuzunda bkz [KRBTGT hesabı parola sıfırlama betikleri müşteriler için artık kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/). Ayrıca bkz [KRBTGT hesabı parola/anahtarları aracı Sıfırla](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51). Yanal hareket teknik olduğundan, en iyi uygulamaları izleyerek [karma önerileri geçirmek](http://aka.ms/PtH).

## <a name="honeytoken-activity"></a>Honeytoken etkinliği


**Açıklama**

Honeytoken hesapları tanımlamak ve bu hesapları içeren kötü amaçlı etkinliği izlemek için ayarladığınız decoy hesaplarıdır. Honeytoken hesapları saldırganlar (örneğin, SQL-Admin) çekici yöntemlerle çekmeye için çekici adı yaparken kullanılmayan, bırakılmalıdır. Herhangi bir etkinlikten kötü amaçlı davranış gösterebilir.

Honeytoken hesapları hakkında daha fazla bilgi için bkz: [Azure ATP - adım 7'yi yükleme](install-atp-step7.md).

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

1. Tıklatın **karşıdan ayrıntıları** dahil edilen IP adreslerinin tam listesini görmek için düğmesi. Veya her iki bilgisayar undersized bir DHCP havuzundan Örneğin, VPN veya WiFi ayrılmış bir alt ağa ait bir IP adresi mu? IP adresi paylaşılıyor mu? Örneğin, bir NAT cihazı tarafından? Bir veya daha fazla kaynak IP adreslerinin algılayıcı tarafından çözümlenen değil misiniz? (Bu algılayıcı uygun bağlantı noktalarının aygıtlara değil düzgün açıldığından olduğunu gösteriyor olabilir.) Ardından bu soruları hiçbirine yanıt Evet ise, yanlış pozitif olduğu.

2. Kullanıcılar adına biletleri iletir özel bir uygulamayı var mı? Bu nedenle, zararsız true pozitif olması durumunda.

**Düzeltme**

1. Söz konusu hesabı hassas değilse, bu hesabın parolasını sıfırlayın. Mevcut biletleri, süreleri doluncaya kadar hala kullanılabilmesine karşın bu saldırgan parola karma değerden yeni Kerberos biletleri oluşturmasını engeller.  

2. Hassas hesap ise, iki kez altın anahtar şüpheli etkinlik olduğu gibi KRBTGT hesabı sıfırlama düşünmelisiniz. KRBTGT iki kez sıfırlama tüm Kerberos biletleri bu etki alanında, böylece bunu yapmadan önce planlama geçersiz kılar. Kılavuzunda bkz [KRBTGT hesabı parola sıfırlama betikleri müşteriler için artık kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/), ayrıca bkz [KRBTGT hesabı parola/anahtarları aracı Sıfırla](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51).  Bu bir yanal hareket teknik olduğuna göre en iyi uygulamaları izleyin [karma önerileri geçirmek](http://aka.ms/PtH).

## Kerberos altın anahtarı<a name="golden-ticket"></a>

**Açıklama**

Saldırganlar etki alanı yönetici haklarına sahip tehlikeye [KRBTGT hesabı](https://technet.microsoft.com/library/dn745899(v=ws.11).aspx#Sec_KRBTGT). KRBTGT hesabı kullanarak, bunlar herhangi bir rastgele anda bilet sona erme tarihini ayarlayabilir ve herhangi bir kaynak için yetkilendirme sağlayan bilet (TGT) veren bir Kerberos anahtarı oluşturabilir. Bu sahte TGT "Altın anahtar" denir ve ağdaki kalıcılığı elde etmek, saldırganların sağlar.

İzni veriliyor bileti için kullanılan bir Kerberos anahtarı belirtildiği gibi izin verilen süre birden fazla izin verdiğinde bu algılama, bir uyarı tetiklendiğinde [kullanıcı anahtarının en fazla ömrü](https://technet.microsoft.com/library/jj852169(v=ws.11).aspx) güvenlik ilkesi.

**Araştırma**

1. Yapılan en son (son birkaç saat içinde) değişiklik oluştu **kullanıcı anahtarının en fazla ömrü** içinde Grup İlkesi ayarı? Yanıt Evet ise, ardından **Kapat** (Yanlış pozitif olduğu) uyarı.

2. Bu uyarı bir sanal makine Azure ATP tek başına algılayıcı karmaşıktır? Yanıtınız evet ise, en son kaydedilen durumdan sürdürün? Yanıt Evet ise, ardından **Kapat** bu uyarı.

3. Yukarıdaki sorulara yanıt ise Hayır, bu kötü amaçlı olduğunu varsayalım.

**Düzeltme**

Kerberos anahtar verme anahtarı (KRBTGT) parolayı iki kez kılavuzunda göre değiştirmek [KRBTGT hesabı parola sıfırlama betikleri müşteriler için artık kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/)kullanarak [KRBTGT hesabı parola/anahtarlarını sıfırlama Aracı](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51). KRBTGT iki kez sıfırlama tüm Kerberos biletleri bu etki alanında, böylece bunu yapmadan önce planlama geçersiz kılar. Ayrıca, bir altın anahtar oluşturmak için etki alanı yönetici hakları gerekir çünkü uygulamak [karma önerileri geçirmek](http://aka.ms/PtH).

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

## <a name="malicious-replication-of-directory-services"></a>Dizin hizmetlerinin kötü amaçlı çoğaltması


**Açıklama**

Active Directory çoğaltma bir etki alanı denetleyicisi üzerinde yapılan değişiklikler diğer tüm etki alanı denetleyicileriyle eşitlenir işlemidir. Gerekli izinleri verildiğinde, saldırganlar Active Directory içinde parola karmaları dahil olmak üzere depolanan verileri almak üzere vermeden çoğaltma isteğini başlatabilirsiniz.

Bir çoğaltma isteğini bir etki alanı denetleyicisi olmayan bir bilgisayardan başlatıldığında bu algılama, bir uyarı tetiklenir.

**Araştırma**

1.  Söz konusu bilgisayar bir etki alanı denetleyicisi mi? Örneğin, çoğaltma olan yeni yükseltilen etki alanı denetleyicisi verir. Yanıt Evet ise, **Kapat** şüpheli etkinlik. 
2.  Söz konusu bilgisayarın verileri Active Directory'den çoğaltma olması gerekiyor? Örneğin, Azure AD Connect. Yanıt Evet ise, **kapatın ve dışlama** şüpheli etkinlik.
3.  Kaynak bilgisayar ya da kendi profili sayfasına gitmek için hesap tıklayın. Ne gibi olağan dışı etkinlikler için arama çoğaltma gerçekleştiği sırada meydana denetleyin: kimin hangi kaynaklarında oturum erişilen burada. Windows Defender ATP tümleştirme etkinleştirilirse, Windows Defender ATP rozet tıklatın ![Windows Defender ATP rozet](./media/wd-badge.png) Daha fazla makine araştırmak için. Windows Defender ATP uyarının gerçekleştiği sırada hangi işlemleri ve uyarılar oluştu görebilirsiniz. 


**Düzeltme**

Aşağıdaki izinleri doğrulama: 

- Dizin Değişikliklerini Çoğaltma   

- Tüm dizin değişikliklerini çoğaltma  

Daha fazla bilgi için bkz: [profil eşitleme SharePoint Server 2013'te Grant Active Directory etki alanı Hizmetleri izinlerini](https://technet.microsoft.com/library/hh296982.aspx).
Yararlanabileceğiniz [AD ACL tarayıcı](https://blogs.technet.microsoft.com/pfesweplat/2013/05/13/take-control-over-ad-permissions-and-the-ad-acl-scanner-tool/) veya kimin etki alanında bu izinleri olduğunu belirlemek için bir Windows PowerShell Betiği oluşturun.


## <a name="password-exposed-in-cleartext-report"></a>Doğrulamaya raporda gösterilen parola

**Açıklama**

Bazı hizmetler hesabı kimlik bilgileri düz metin olarak gönderir. Bu durum, kullanıcı hesapları için bile oluşabilir. Ağ trafiğini izleme saldırganlar catch ve bu kimlik bilgileri kötü amaçlı olarak yeniden kullanabilirsiniz. 

**Araştırma**

Raporları sayfasında tıklatın ve doğrulamaya raporda gösterilen parola indirin. Hangi hesapların ortaya Excel elektronik tabloya bakın.
Genellikle LDAP basit bağlama kullanan komut dosyası veya eski uygulama kaynak bilgisayarlarda yoktur.

**Düzeltme**

Kaynak bilgisayarlarda yapılandırmayı doğrulayın ve LDAP basit bağlaması kullanmadığınızdan emin olun. LDAP basit bağlamalar kullanmak yerine, LDAP SALS veya LDAPS kullanabilirsiniz.

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

Hesap numaralandırma keşif bir saldırgan, kullanıcı adlarını veya KrbGuess gibi araçları binlerce ile kullanıcı adlarını, etki alanınızdaki tahmin etme girişiminde bir sözlük kullanır. Saldırgan, geçerli bir kullanıcı adı, etki alanınızdaki bulmak için bu adları kullanarak Kerberos istekleri yapıyorsa. Bir tahmin başarılı bir şekilde bir kullanıcı adı belirlerse, saldırganın Kerberos hata alır **gerekli ön kimlik doğrulama** yerine **güvenlik sorumlusu bilinmeyen**. 

Bu algılama, Azure ATP saldırı nereden geldiğini, tahmin denemeleri toplam sayısı ve kaç tane eşleştirildiklerinden algılayabilir. Bilinmeyen çok sayıda kullanıcı varsa, Azure ATP kuşkulu bir etkinlik algılar. 

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

Bu algılama, hiçbir uyarı Azure ATP dağıtıldıktan sonra ilk ay içinde tetiklenen. Hangi SAM-R sorguların hangi bilgisayarlardan yapılan öğrenme dönemi Azure ATP profilleri sırasında numaralandırması ve hassas hesaplarının tek tek sorgular.

**Araştırma**

1. Kendi ayrıntıları sayfasına ulaşmak için uyarıyı tıklayın. Hangi sorguların (örneğin, Enterprise admins veya yönetici) gerçekleştirilen ve desteklemediğini başarılı denetleyin.

2. Bu tür sorgular kaynak bilgisayardan söz konusu yapılması gerekir?

3. Evet ve uyarı güncelleştirdiyseniz, **bastır** şüpheli etkinlik.

4. Yanıt Evet ise ve onu, bunu kullanmayın **Kapat** şüpheli etkinlik.

5. Söz konusu hesabıyla ilgili bilgiler ise: sorgularını o hesap tarafından yapılması gereken ya da bu hesabı normalde kaynak bilgisayarda oturum mu?

 - Evet ve uyarı güncelleştirdiyseniz, **bastır** şüpheli etkinlik.

 - Yanıt Evet ise ve onu, bunu kullanmayın **Kapat** şüpheli etkinlik.

 - Yanıt Hayır tüm olursa yukarıdaki bu kötü amaçlı olduğunu varsayalım.

6. Söz konusu hesap hakkında hiçbir bilgi ise bitiş noktasına gidin ve hangi hesabın uyarı aynı anda oturum açmış denetleyin.

**Düzeltme**

Ortamınızı aşağıdaki işlemi kullanarak bu teknik karşı sağlamlaştırmak:
1. Bilgisayar Tarama Aracı bir güvenlik açığı çalışıyor mu?  
2. Belirli sorgulanan alanındaki kullanıcılar ve gruplar saldırı ayrıcalıklı veya yüksek değer hesapları olup araştırmak (diğer bir deyişle, CEO, CFO, BT yönetimi, vs.).  Öyleyse, diğer uç nokta da faaliyete bakın ve büyük olasılıkla yanal hareket hedefleri oldukları gibi sorgulanan hesapları, oturum açtığınız bilgisayarları izleyin.

## <a name="reconnaissance-using-dns"></a>DNS kullanarak keşif

**Açıklama**

DNS sunucunuzu tüm bilgisayarlar, IP adresleri ve Hizmetleri, ağınızda haritasını içerir. Saldırganlar bu bilgileri kullanarak ağ yapınızın haritasını çıkarır ve saldırının sonraki adımlarında kullanmak üzere uygun bilgisayarları hedef alır.

DNS protokolünde birkaç sorgu türü vardır. Azure ATP olmayan DNS sunucularından kaynaklanan AXFR (aktarım) isteği algılar.

**Araştırma**

1. Kaynak makinenin (**kaynaklanan...** ) bir DNS sunucusu? Yanıt Evet ise, bu büyük olasılıkla yanlış pozitif ise. Doğrulamak için ayrıntıları sayfasına ulaşmak için uyarıyı tıklayın. Tabloda, altında **sorgu**, hangi etki alanlarının sorgulanan denetleyin. Bu var olan etki alanları misiniz? Yanıt Evet ise, ardından **Kapat** (Yanlış pozitif olması) şüpheli etkinlik. Ayrıca, UDP bağlantı noktası 53 Azure ATP tek başına algılayıcı ve gelecekteki hatalı pozitif sonuç önlemek için kaynak bilgisayar arasında açık olduğundan emin olun.

2. Kaynak Makine güvenlik tarayıcısı çalışıyor mu? Yanıt Evet ise, **varlıkları dışlama** doğrudan ATP içinde **kapatın ve dışlama** veya aracılığıyla **dışlama** sayfa (altında **yapılandırma** – kullanılabilir Azure ATP yöneticileri için).

3. Önceki tüm soruları olan yanıt Hayır, kaynak bilgisayarda odaklanan araştırma tutmak ise. Kendi profili sayfasına gitmek için kaynak bilgisayara tıklayın. Ne gibi olağan dışı etkinlikler için arama isteğin gerçekleştiği sırada meydana denetleyin: kimin hangi kaynaklarında oturum erişilen burada. Windows Defender ATP tümleştirme etkinleştirilirse, Windows Defender ATP rozet tıklatın ![Windows Defender ATP rozet](./media/wd-badge.png) Daha fazla makine araştırmak için. Windows Defender ATP uyarının gerçekleştiği sırada hangi işlemleri ve uyarılar oluştu görebilirsiniz. 

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

## <a name="remote-execution-attempt"></a>Uzaktan yürütme girişimi

**Açıklama**

Yönetimsel kimlik bilgilerini tehlikeye veya sıfırıncı gün yararlanma kullanın saldırganlar etki alanı denetleyicinizde uzaktan komutları çalıştırabilirsiniz. Bu komutlar kalıcılık sağlamak, bilgi toplamak, hizmet reddi (DoS) saldırıları ve diğer herhangi bir sebeple kullanılabilir. Azure ATP PSexec ve uzak WMI bağlantıları algılar.

**Araştırma**

1. Bu, yönetim iş istasyonları ve BT ekibi üyeleri ve etki alanı denetleyicilerine karşı yönetim görevlerini gerçekleştirmek hizmet hesapları için yaygındır. Bu ise durum ve uyarı aynı yönetici bu yana güncelleştirilen ve/veya bilgisayar gerçekleştirme görev sonra **bastır** uyarı.

2. Olan **bilgisayar** söz konusu etki alanı denetleyicisine karşı bu uzaktan yürütme gerçekleştirmeye izin?

 - Olan **hesap** söz konusu etki alanı denetleyicisine karşı bu uzaktan yürütme gerçekleştirmeye izin?

 - Her iki soruların yanıtlanması gerekirse *Evet*, ardından **Kapat** uyarı.

3. Her iki sorulara yanıt ise Hayır, daha sonra bu true pozitif düşünülmelidir. Bilgisayarı ve hesap profilleri denetleyerek denemesi kaynağı bulmaya çalışın. Kaynak bilgisayar ya da kendi profili sayfasına gitmek için hesap tıklayın. Ne gibi olağan dışı etkinlikler için arama bu girişimleri gerçekleştiği sırada meydana denetleyin: kimin hangi kaynaklarında oturum erişilen burada. Windows Defender ATPintegration etkinleştirilirse, Windows Defender ATP rozet tıklatın ![Windows Defender ATP rozet](./media/wd-badge.png) Daha fazla makine araştırmak için. Windows Defender ATPyou uyarının gerçekleştiği sırada hangi işlemleri ve uyarılar oluştu görebilirsiniz. 

**Düzeltme**

1. Katman 0 olmayan makinelerden etki alanı denetleyicilerine uzaktan erişimi kısıtlayın.

2. Uygulama [ayrıcalıklı erişim](https://technet.microsoft.com/windows-server-docs/security/securing-privileged-access/securing-privileged-access) yalnızca sağlamlaştırılmış makinelerin yöneticileri için etki alanı denetleyicilerine bağlanmasına izin vermek için.

## <a name="suspicious-authentication-failures"></a>Kuşkulu kimlik doğrulama hataları

**Açıklama**

Yanılma saldırısında, saldırganın en az bir hesap için doğru parolayı bulunana kadar farklı hesaplar için birçok farklı parolaları ile kimlik doğrulaması dener. Bir kez bulundu, bir saldırganın bu hesabı kullanarak oturum açabilir.

Bu algılama, Kerberos veya NTLM kullanarak birçok kimlik doğrulama hataları oluştuğunda bir uyarının, bu parolalar, küçük bir kümesini yatay ile ya da çok sayıda kullanıcı arasında olması; veya dikey büyük ile Parolaları yalnızca birkaç kullanıcılar ayarlayın; veya bu iki seçenek herhangi bir bileşimini. Bir uyarıyı tetikleyen önce en az bir hafta noktadır.

**Araştırma**

1.  Tıklatın **karşıdan ayrıntıları** bir Excel elektronik tabloda tam bilgileri görüntülemek için. Aşağıdaki bilgiler elde edebilirsiniz: 
   -    Saldırıya uğrayan hesaplarının listesi
   -    Başarılı kimlik doğrulaması ile sona erdi hangi oturum açma denemesi tahmin edilen hesaplarında listesi
   -    Kimlik doğrulama girişimlerini NTLM kullanılarak gerçekleştirilen, ilgili olay etkinlikler görürsünüz 
   -    Kimlik doğrulama girişimlerini Kerberos kullanılarak gerçekleştirilen, ilgili ağ etkinliklerini görürsünüz

2.  Kendi profili sayfasına gitmek için kaynak bilgisayara tıklayın. Ne gibi olağan dışı etkinlikler için arama bu girişimleri gerçekleştiği sırada meydana denetleyin: kimin hangi kaynaklarında oturum erişilen burada. Windows Defender ATP tümleştirme etkinleştirilirse, Windows Defender ATP rozet tıklatın ![Windows Defender ATP rozet](./media/wd-badge.png) Daha fazla makine araştırmak için. Windows Defender ATP uyarının gerçekleştiği sırada hangi işlemleri ve uyarılar oluştu görebilirsiniz. 

3.  Kimlik doğrulaması, NTLM kullanılarak yapıldı ve çoğu zaman, uyarıyı oluşur ve yeterli bilgi yok, kaynak makine erişmeye çalıştığınız sunucu hakkında kullanılabilir, etkinleştirmeniz gereken gördüğünüz **NTLM denetim** üzerinde söz konusu etki alanı denetleyicileri. Bunu yapmak için olayı 8004 açın. Bu kaynak bilgisayar, kullanıcı hesabı hakkında bilgi içeren NTLM kimlik doğrulaması olayıdır ve **server** , kaynak makine erişmeyi denedi. Hangi sunucu kimlik doğrulama gönderilen öğrendikten sonra gibi kimlik doğrulama işlemi 4624 daha iyi anlamak olaylarına denetleyerek sunucunun araştırmanız gerekir. 

**Düzeltme**

[Uzun ve karmaşık parolalar](https://docs.microsoft.com/windows/device-security/security-policy-settings/password-policy) yanılma saldırılarına karşı güvenlik gerekli ilk düzeyi sağlar.

## <a name="suspicious-service-creation"></a>Şüpheli hizmet oluşturma

**Açıklama**

Şüpheli bir hizmet, kuruluşunuzdaki bir etki alanı denetleyicisinde oluşturuldu. Bu uyarı olayı 7045 bu şüpheli etkinlik tanımlamak için kullanır. 

**Araştırma**

1. Söz konusu bilgisayarın yönetici iş istasyonu veya hangi BT ekibi üyeleri ve hizmet hesapları yönetim görevlerini gerçekleştirmek bilgisayar ise, bu yanlış pozitif olabilir ve gerekebilir **bastır** uyarı ve ekleyin Dışlama listesine gerekiyorsa.

2. Hizmeti bu bilgisayarda tanıması bir şey mi?

 - Olan **hesap** söz konusu bu hizmet yüklemesine izin?

 - Her iki soruların yanıtlanması gerekirse *Evet*, ardından **Kapat** uyarı ya da özel durumlar listesine ekleyin.

3. Her iki sorulara yanıt ise *hiçbir*, bu geçerli bir pozitif gerekenlerin sonra.

**Düzeltme**

- Daha az ayrıcalıklı erişimi yalnızca belirli kullanıcılara yeni hizmetler oluşturmak üzere sağa izin vermek için etki alanı makinelerde uygulamak.

## <a name="unusual-protocol-implementation"></a>Olağan dışı protokol uygulanması


**Açıklama**

Saldırganlar, standart olmayan yollarla çeşitli protokoller (SMB, Kerberos, NTLM) uygulama araçlarını kullanın. Bu tür ağ trafiği uyarılar olmadan Windows tarafından kabul edilir, ancak Azure ATP olası kötü amaçlı tanıyabilir. Gelişmiş yazılımı, örneğin, WannaCry tarafından kullanılan açıkları yanı sıra, Over-Pass--Hash ve kaba kuvvet gibi teknikler göstergesi davranıştır.

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


> [!NOTE]
> Kuşkulu bir etkinlik devre dışı bırakmak için desteğe başvurun.


## <a name="see-also"></a>Ayrıca bkz:
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
