---
title: Azure ATP şüpheli etkinlik Kılavuzu | Microsoft Docs
d|Description: This article provides a list of the suspicious activities Azure ATP can detect and steps for remediation.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/20/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: ca5d1c7b-11a9-4df3-84a5-f53feaf6e561
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 4aa58228ea23f58ea37b10f941467e9dc076992f
ms.sourcegitcommit: f534a318be71b840aecb6a84744d8cd1f251a7aa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2018
ms.locfileid: "41734847"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="azure-advanced-threat-protection-suspicious-activity-guide"></a>Azure Gelişmiş tehdit koruması şüpheli etkinlik Kılavuzu

Uygun araştırma, herhangi bir şüpheli etkinlik olarak sınıflandırılabilir:

-   **Gerçek pozitif sonuç**: Azure ATP tarafından algılanan kötü amaçlı bir eylem.

-   **Zararsız gerçek pozitif sonuç**: Gerçek, ancak zararsız sızma testi örneğindeki gibi Azure ATP tarafından algılanan bir eylem.

-   **Hatalı pozitif sonuç**: etkinlik anlamına gelen bir yanlış alarm gerçekleşmemiştir.

Azure ATP uyarılarla çalışma hakkında daha fazla bilgi için bkz: [kuşkulu etkinliklerle çalışma](working-with-suspicious-activities.md).


## <a name="abnormal-sensitive-group-modification"></a>Anormal Gizli Grup Değişikliği


**Açıklama**

Saldırganlar kullanıcıların yüksek ayrıcalıklı gruplara ekleyin. Daha fazla kaynaklarına erişmek ve kalıcılığı sağlamak için bunu yapın. Algılama, kullanıcıların Grup değişikliği etkinliklerini profilini oluşturup anormal bir hassas Grup eklemeyi ortaya çıktığında üzerinde kullanır. Profil oluşturma ATP tarafından sürekli olarak gerçekleştirilir. Bir uyarı tetiklenebilir önce en az süre, her etki alanı denetleyicisi başına bir aydır.

Azure ATP gizli gruplarda tanımı için bkz [hassas hesaplar ile çalışma](sensitive-accounts.md).


Algılama dayanan [etki alanı denetleyicilerinde Denetlenen olayları](configure-event-collection.md).
Etki alanınızı emin olmak için gerekli olayları denetleyicileri denetim.

**Araştırma**

1. Grup değişikliği yasal mı? </br>Nadiren oluşur ve "olarak normal", öğrenilen değil yasal Grup değişikliklerini zararsız gerçek pozitif sonuç olarak değerlendirilebilecek bir uyarı neden olabilir.

2. Eklenen nesne bir kullanıcı hesabı varsa, kullanıcı hesabının yönetim grubuna eklendikten sonra geçen hangi eylemleri denetleyin. Daha fazla bağlam almak için Azure ATP kullanıcı sayfasına gidin. Diğer vardı önce veya sonra ek hesapla ilişkili şüpheli etkinlikleri gerçekleşen? İndirme **gizli Grup değişikliği** ne olan diğer değişiklikleri görmek için raporu yapılmış ve aynı süre boyunca kim tarafından.

**Düzeltme**

Gizli gruplarda değişiklik yapabilecek kullanıcı sayısını en aza indirin.

Ayarlanan [Privileged Access Management için Active Directory](https://docs.microsoft.com/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services) varsa.


## <a name="brute-force-attack-using-ldap-simple-bind"></a>Basit LDAP bağlama kullanan deneme yanılma saldırısı

**Açıklama**

>[!NOTE]
> Arasındaki temel fark **şüpheli kimlik doğrulama hataları** ve bu algılama bu algılama, Azure ATP farklı parolalar kullanımda olup olmadığını belirleyebilirsiniz.

Bir deneme yanılma saldırısında, saldırgan doğru parolayı en az bir hesap için bulunana kadar farklı hesaplar için çok sayıda farklı parolaları ile kimlik doğrulaması dener. Bir kez bulundu, bir saldırganın bu hesabı kullanarak oturum açabilir.

Bu algılama, Azure ATP büyük birkaç basit bağlama kimlik doğrulamaları algıladığında bir uyarı tetiklenir. Bu olabilir *yatay* parolaları; çok sayıda kullanıcı arasında küçük bir dizi veya *dikey "* parolaları yalnızca birkaç kullanıcılar; veya bu iki seçenek herhangi bir bileşimini büyük bir dizi.

**Araştırma**

1. İlgili birçok hesapları varsa, tıklayın **indirme ayrıntıları** bir Excel elektronik tablosunda listesini görüntülemek için.

2. Ayrılmış alt sayfasına gitmek için uyarıyı tıklayın. Tüm oturum açma girişimlerini başarılı bir kimlik doğrulaması ile sona erdi kontrol edin. Deneme olarak görüneceği **hesapları tahmin** bilgi grafiğine sağ tarafında. Yanıt Evet ise, olan **hesapları tahmin** normalde kullanılan kaynak bilgisayardan? Yanıt Evet ise, **bastır** şüpheli etkinlik.

3. Varsa hiçbir **hesapları tahmin**, olan **Saldırıya uğrayan hesaplar** normalde kullanılan kaynak bilgisayardan? Yanıt Evet ise, **bastır** şüpheli etkinlik.

**Düzeltme**

[Uzun ve karmaşık parolalar](https://docs.microsoft.com/windows/device-security/security-policy-settings/password-policy) gerekli ilk deneme yanılma saldırılarına karşı güvenlik düzeyini belirtin.

## <a name="encryption-downgrade-activity"></a>Şifreleme düşürme etkinliği

**Açıklama**

Şifrelemeyi düşürme Kerberos protokolünün genellikle en yüksek düzeyde şifrelemesi kullanılarak şifrelenmiş farklı alanları şifreleme düzeyini eski sürüme düşürme zayıflatmanın bir yöntemdir. Düzeyi düşürülmüş bir şifrelenmiş alan çevrimdışı deneme yanılma girişimleri için daha kolay bir hedef olabilir. Zayıf Kerberos şifreleme cyphers çeşitli saldırı yöntemleri kullanın. Bu algılama, Azure ATP bilgisayarlar ve kullanıcılar tarafından kullanılan Kerberos şifreleme türleri öğrenir ve daha zayıf bir şifreleme olduğunda, kullanılan uyarılar: (1) kaynak bilgisayarı ve/veya kullanıcı; olağandışı bir durumdur ve bilinen saldırı teknikleri (2) eşleşir.

Üç algılama türleri şunlardır:

1.  Etki alanı denetleyicilerinde çalışan ve kimlik doğrulama etki alanına herhangi bir hesap ile parolaya gerek kalmaksızın sağlayan kötü amaçlı yazılım Maymuncuk – var. Bu kötü amaçlı yazılım, etki alanı denetleyicisinde kullanıcının parolalarını karma için genellikle daha zayıf şifreleme algoritmaları kullanır. Bu algılama, daha önceden öğrenilen davranışına göre şifreleme yöntemi için bir bilet isteyen hesabı etki alanı denetleyicisinden KRB_ERR iletisinin indirgenen.

2.  Altın bilet – içinde bir [altın bilet](#golden-ticket) uyarı, şifreleme yöntemi kaynak bilgisayardan TGS_REQ (hizmet isteği) iletisinin TGT alanının kıyasla daha önceden öğrenilen davranıştır indirgenen. Bu bir zaman anomali (olduğu gibi diğer altın bilet algılama) temel almaz. Ayrıca, bir ATP tarafından algılanan önceki hizmet isteği ile ilişkili hiçbir Kerberos kimlik doğrulama isteği vardı.

3.  Karmayı – bir saldırgan, Kerberos AS isteği ile güçlü bir anahtar oluşturmak için zayıf çalınmış bir karmasını kullanabilir. Bu algılama, kaynak bilgisayardan AS_REQ ileti şifreleme türü daha önceden öğrenilen davranışına göre indirgenen (bilgisayar, AES kullanıyordu).

**Araştırma**

Önce yukarıda listelenen olan algılama üç ile ilgilenen görmek için uyarı açıklamasına bakın. Daha fazla bilgi için Excel elektronik tablosunu indirin.

1.  Maymuncuk – kullanarak etki alanı denetleyicilerinizin Skeleton Key etkilenen, denetleyebilirsiniz [Azure ATP ekibi tarafından yazılan tarayıcıyı](https://gallery.technet.microsoft.com/Aorato-Skeleton-Key-24e46b73). Tarayıcı 1 veya daha fazla etki alanı denetleyicilerinizin kötü amaçlı yazılım bulması halinde, bu gerçek pozitiftir.

2.  Altın bilet – excel elektronik tablosunda, ağ etkinliği sekmesini gidin. İlgili indirgenmiş alanı olduğunu göreceksiniz **istek anahtarı şifreleme türü**, ve **kaynak bilgisayarı desteklenen şifreleme türlerini** daha güçlü şifreleme yöntemlerini içerir.

  1. Kaynak denetimi bu anahtarları tarafından erişilen, tüm eriştikleri bir kaynak varsa, doğrulayın, bunlar erişmek için gereken geçerli bir kaynak olduğundan emin olun. Ayrıca, hedef kaynağın güçlü şifreleme yöntemlerini destekleyip desteklemediğini doğrulayın. Bu öznitelik msDS-SupportedEncryptionTypes, kaynak hizmet hesabının denetleyerek Active Directory'de denetleyebilirsiniz.
  
  2. Kaynak bilgisayar ve hesap denetleyin veya varsa birden çok kaynak bilgisayarlar ve hesabı, bir ortak olup olmadığını kontrol edin. Örneğin, tüm pazarlama sorumlunuza tetiklenmesi için uyarıya neden olan belirli bir uygulamayı kullanın. Hangi nadiren kullanılır, özel bir uygulama kimlik doğrulaması daha düşük bir şifreleme şifreleme kullanarak durumlar vardır. Kaynak bilgisayar gibi özel uygulamalar olup olmadığını denetleyin. Bu durumda, büyük olasılıkla bir zararsız gerçek pozitiftir ve kaldırılabilir.
  


3.  Karmayı – excel elektronik tablosunda, ağ etkinliği sekmesini gidin. İlgili indirgenmiş alanı olduğunu göreceksiniz **şifrelenmiş zaman damgası şifreleme türü** ve **kaynak bilgisayarı desteklenen şifreleme türlerini** daha güçlü şifreleme yöntemlerini içerir.

  1. Akıllı kart kullanarak akıllı kart yapılandırması yakın zamanda değiştirdiyseniz kullanıcılar oturum açtığında, bu uyarı tetiklenebilir durumlar vardır. İlgili hesapları için bunun gibi değişiklikler olup olmadığını denetleyin. Bu durumda, bu büyük olasılıkla bir zararsız gerçek pozitiftir ve kaldırılabilir.
  2. Kaynak denetimi bu anahtarları tarafından erişilen, tüm eriştikleri bir kaynak varsa, doğrulayın, bunlar erişmek için gereken geçerli bir kaynak olduğundan emin olun. Ayrıca, hedef kaynağın güçlü şifreleme yöntemlerini destekleyip desteklemediğini doğrulayın. Bu öznitelik msDS-SupportedEncryptionTypes, kaynak hizmet hesabının denetleyerek Active Directory'de denetleyebilirsiniz.

**Düzeltme**

1.  İskelet anahtar – kötü amaçlı yazılımı kaldırın. Daha fazla bilgi için [Skeleton Key kötü amaçlı yazılım Analizine](https://www.virusbulletin.com/virusbulletin/2016/01/paper-digital-bian-lian-face-changing-skeleton-key-malware).

2.  Altın bilet – yönergeleri izleyin [altın bilet](#golden-ticket) kuşkulu etkinlikler.   
    Ayrıca, etki alanı yöneticisi haklarına bir altın anahtar oluşturuluyor gerektirdiği için uygulama [Pass the hash önerilerini](http://aka.ms/PtH).

3.  Karmayı –, ardından ilgili hesabı hassas, değilse o hesabın parolasını sıfırlayın. Mevcut biletleri, süreleri doluncaya kadar hala kullanılabilir olsa da bu saldırgan parola karması, yeni Kerberos biletleri oluşturmanızı engeller. Hassas hesap ise, iki kez altın bilet şüpheli etkinliğin olduğu gibi KRBTGT hesap sıfırlama düşünmelisiniz. İki kez KRBTGT sıfırlama tüm Kerberos biletleri bu etki alanında bunu yapmadan önce plan geçersiz kılar. Kılavuzunda bkz [KRBTGT hesap parolası sıfırlama betikleri artık müşteriler tarafından kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/). Ayrıca bkz [KRBTGT hesap parolası/anahtarı sıfırlama aracını](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51). Yanal hareket tekniğidir olduğundan, en iyi yöntemleri takip [Pass the hash önerilerini](http://aka.ms/PtH).

## <a name="honeytoken-activity"></a>Honeytoken etkinliği


**Açıklama**

Honeytoken hesapları tanımlamak ve bu hesapları içeren kötü amaçlı etkinliği izlemek üzere ayarlanan sahte hesaplardır. Honeytoken hesapları (örneğin, SQL-yönetici) saldırganlar çekici yöntemlerle çekmeye için çekici bir ad yaparken kullanılmamış olarak bırakılmalıdır. Herhangi bir etkinlikten kötü amaçlı davranışları gösterebilir.

Honeytoken hesapları hakkında daha fazla bilgi için bkz. [Azure ATP yükleme - 7. adım](install-atp-step7.md).

**Araştırma**

1.  Sahibi kaynak bilgisayarın kimliğini doğrulamak için Honeytoken hesap kullanılıp (örneğin, Kerberos, LDAP, NTLM) şüpheli etkinlik sayfasında açıklanan yöntemi kullanarak denetleyin.

2.  Kaynak bilgisayarlar profili sayfalara göz atın ve bunları kimliği doğrulanmış hangi hesapların denetleyin. Bunlar Honeytoken hesap kullandıysanız bu hesapların sahipleriyle birlikte denetleyin.

3.  Bu, etkileşimli olmayan oturum açma olacaktır, böylece uygulamalar veya kaynak bilgisayarda çalıştırılan betikler için kontrol ettiğinizden emin olun.

Kanıt zararsız kullanım ise 1 ile 3 arasındaki adımları gerçekleştirmeden varsa sonra bu kötü amaçlı olduğu varsayılır.

**Düzeltme**

Emin Honeytoken hesapları yalnızca kullanım amaçları için kullanılan olun, aksi takdirde sayıda uyarı oluşturabilir.

## <a name="identity-theft-using-pass-the-hash-attack"></a>Pass--Hash saldırısı kullanan kimlik hırsızlığı

**Açıklama**

Pass--Hash bir yanal hareket tekniğidir saldırganlar bir bilgisayardan bir kullanıcının NTLM karmasını çalar ve başka bir bilgisayara erişim kazanmak için kullanın. 

**Araştırma**

Karma hedeflenen kullanıcı sahibi veya düzenli olarak kullandığı bir bilgisayardan kullanıldı? Evet, bu bir hatalı pozitif sonuç ise. Aksi takdirde, büyük olasılıkla gerçek pozitiftir.

**Düzeltme**

1. Ardından ilgili hesabı önemli değilse, o hesabın parolasını sıfırlayın. Mevcut biletleri, süreleri doluncaya kadar hala kullanılabilir olsa da bu saldırgan parola karması, yeni Kerberos biletleri oluşturmanızı engeller. 

2. Hassas hesap ise, iki kez altın bilet şüpheli etkinliğin olduğu gibi KRBTGT hesap sıfırlama düşünmelisiniz. İki kez KRBTGT sıfırlama tüm Kerberos biletleri bu etki alanında bunu yapmadan önce plan geçersiz kılar. Kılavuzunda bkz [KRBTGT hesap parolası sıfırlama betikleri artık müşteriler tarafından kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/), ayrıca bkz [KRBTGT hesap parolası/anahtarı sıfırlama aracını](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51). Yanal hareket tekniğidir olduğundan, en iyi yöntemleri takip [Pass the hash önerilerini](http://aka.ms/PtH).

## <a name="identity-theft-using-pass-the-ticket-attack"></a>Pass--Ticket saldırısı kullanan kimlik hırsızlığı

**Açıklama**

Pass--Ticket bir yanal hareket tekniğidir saldırganlar bir bilgisayardan Kerberos anahtarını çalabilir ve çalınan bilet yeniden kullanarak başka bir bilgisayara erişim kazanmak için kullanın. Bu algılama, bir Kerberos anahtarı iki (veya daha fazla) farklı bilgisayarlarda görülür.

**Araştırma**

1. Tıklayın **indirme ayrıntıları** IP adreslerinin dahil tam listesini görüntülemek için düğme. Bir IP adresi yok veya her iki bilgisayar sayıdan bir DHCP havuzundan WiFi veya VPN gibi ayrılmış bir alt ağa ait? IP adresi paylaşılıyor mu? Örneğin, bir NAT cihazının tarafından? Bir veya daha fazla kaynak IP adreslerinin algılayıcı tarafından çözümlenen değil misiniz? (Bu algılayıcı uygun bağlantı noktaları cihazlara değil düzgün bir şekilde açıldı olduğunu gösteriyor olabilir.) Ardından bu soruları hiçbirini yanıt Evet ise, bir hatalı pozitif sonuç olduğunu.

2. Kullanıcılar adına biletleri ileten özel bir uygulama mı? Bu durumda, bunu bir zararsız gerçek pozitiftir.

**Düzeltme**

1. Ardından ilgili hesabı önemli değilse, o hesabın parolasını sıfırlayın. Mevcut biletleri, süreleri doluncaya kadar hala kullanılabilir olsa da bu saldırgan parola karması, yeni Kerberos biletleri oluşturmanızı engeller.  

2. Hassas hesap ise, iki kez altın bilet şüpheli etkinliğin olduğu gibi KRBTGT hesap sıfırlama düşünmelisiniz. İki kez KRBTGT sıfırlama tüm Kerberos biletleri bu etki alanında bunu yapmadan önce plan geçersiz kılar. Kılavuzunda bkz [KRBTGT hesap parolası sıfırlama betikleri artık müşteriler tarafından kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/), ayrıca bkz [KRBTGT hesap parolası/anahtarı sıfırlama aracını](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51).  Yanal hareket tekniğidir olduğundan, en iyi uygulamaları izlemesi [Pass the hash önerilerini](http://aka.ms/PtH).

## Kerberos altın bilet<a name="golden-ticket"></a>

**Açıklama**

Saldırganlar etki alanı yönetici haklarına sahip tehlikeye [KRBTGT hesabı](https://technet.microsoft.com/library/dn745899(v=ws.11).aspx#Sec_KRBTGT). KRBTGT hesabı kullanarak bunların herhangi bir kaynağa yetkilendirme sağlayan ve rastgele dilediğiniz zaman anahtarı süre sonu Ayarla anahtarı (TGT) sağlayan bir Kerberos bilet oluşturabilirsiniz. Bu sahte TGT "goldentTicket" olarak adlandırılır ve saldırganların ağda kalıcılığı elde etmek sağlar.

Bu algılama, ekibi tarafından verilmesinin anahtarı için kullanılan bir Kerberos anahtarı, izin verilen süre belirtildiği şekilde birden fazla izin olduğunda bir uyarı tetiklenir [kullanıcı anahtarının en fazla ömrü](https://technet.microsoft.com/library/jj852169(v=ws.11).aspx), bu bir **zaman anomali**golden ticket saldırısı veya varolmayan bir hesaba göre bu, bir **var olmayan bir hesap** altın bilet saldırısı.


**Araştırma**

- **Zaman anomali**
   1.   Kullanıcı anahtarı ayarı Grup ilkesinde en fazla ömrü yapılan değişiklikleri (son birkaç saat içinde) son vardı? Belirli değerini denetleyin ve anahtarı için kullanılan süresinden düşük olup olmadığına bakın. Yanıt Evet ise, uyarı (Yanlış pozitif olduğu)'ni kapatın.
   2.   Azure ATP algılayıcısını bu uyarı bir sanal makine dahil mi? Evet ise, en son kaydedilen durumdan devam mı? Yanıt Evet ise, ardından bu uyarıyı kapatın.
   3.   Yukarıdaki soruların yanıtlanması gerekirse, Hayır, bu, kötü amaçlı varsayılır.

- **Var olmayan hesap**
   1.   Aşağıdaki sorular sorun:
         - Kullanıcı bir bilinen ve geçerli etki alanı kullanıcısı mıdır? Yanıt Evet ise, uyarı (Yanlış pozitif olduğu)'ni kapatın.
         - Kullanıcının son eklendi? Yanıt Evet ise, ardından uyarıyı kapatın, değişiklik henüz eşitlenmemiş.
         - Kullanıcı AD'den yakın zamanda silinip silinmediğini? Yanıt Evet ise, ardından uyarıyı kapatın.
   2.   Yukarıdaki soruların yanıtlanması gerekirse, Hayır, bu, kötü amaçlı varsayılır.

1. Altın anahtar saldırılarını hem türleri için Git için kaynak bilgisayara tıklayın, **profili** sayfası. Etkinliğin oluştuğu sırada ne olduğunu kontrol edin ve olağan dışı etkinlikleri kimin, günlüğe kaydedilen dahil olmak üzere arayın hangi kaynaklara erişildiğini? 

2.  Günlüğe kaydedilen tüm kullanıcılar, oturum açmış olması beklenen bilgisayara misiniz? Kendi ayrıcalıklarını nelerdir? 

3.  Kullanıcılar bu kaynaklara erişimi gerekir?<br>
Windows Defender ATP tümleştirme etkinleştirilirse, Windows Defender ATP rozet tıklayın ![WD rozet](./media/wd-badge.png).
 
 4. Windows Defender atp'de makine daha fazla araştırmak için hangi işlemleri ve uyarılar, uyarının oluştuğu sırada oluştu denetleyin.

**Düzeltme**


Kerberos anahtar verme anahtarı (KRBTGT) parolayı iki kez kılavuzunda göre değiştirmek [KRBTGT hesap parolası sıfırlama betikleri artık müşteriler tarafından kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/)kullanarak [KRBTGT hesap parolası/anahtarı sıfırlama Aracı](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51). İki kez KRBTGT sıfırlama tüm Kerberos biletleri bu etki alanında bunu yapmadan önce plan geçersiz kılar. Ayrıca, etki alanı yöneticisi haklarına bir altın anahtar oluşturuluyor gerektirdiği için uygulama [Pass the hash önerilerini](http://aka.ms/PtH).




## <a name="malicious-data-protection-private-information-request"></a>Kötü Amaçlı Veri Koruma Özel Bilgi İsteği

**Açıklama**

Veri koruma API'si (DPAPI) tarayıcılar, şifrelenmiş dosyalar ve diğer hassas verileri tarafından kaydedilen parolaları güvenli bir şekilde korumak için Windows tarafından kullanılır. Etki alanı denetleyicileri, etki alanına katılan Windows makineler üzerinde DPAPI ile şifrelenen tüm gizli dizilerin şifresini çözmek için kullanılan yedek bir ana anahtar tutun. Saldırganlar, etki alanına katılmış tüm makinelerde DPAPI tarafından korunan tüm gizli dizilerin şifresini çözmek için ana anahtar kullanabilirsiniz.
DPAPI yedekleme ana anahtarı almak için kullanıldığında, bu algılama, bir uyarı tetiklenir.

**Araştırma**

1. Bir kuruluş tarafından onaylanmış çalıştıran kaynak bilgisayar, Active Directory karşı güvenlik tarayıcısı gelişmişse?

2. Yanıt Evet ise ve bu her zaman bunu yapıyor olmanız gereken **Kapat ve dışla** şüpheli etkinlik.

3. Yanıt Evet ise ve bu, yapmamalısınız **Kapat** şüpheli etkinlik.

**Düzeltme**

DPAPI kullanmak için saldırganın etki alanı yönetici hakları gerekir. Uygulama [Pass the hash önerilerini](http://aka.ms/PtH).

## <a name="malicious-replication-of-directory-services"></a>Dizin hizmetlerinin kötü amaçlı çoğaltması


**Açıklama**

Active Directory çoğaltma tarafından bir etki alanı denetleyicisinde yapılan değişiklikler diğer tüm etki alanı denetleyicileriyle eşitlenmesi işlemidir. Gerekli izinleri göz önünde bulundurulduğunda, saldırganlar bunları Active Directory parola karmaları dahil olmak üzere depolanan verileri almasına izin vererek bir çoğaltma isteği başlatabilirsiniz.

Bir çoğaltma isteği bir etki alanı denetleyicisi olmayan bir bilgisayardan başlatıldığında bu algılama, bir uyarı tetiklenir.

**Araştırma**

> [!NOTE]
> Azure ATP algılayıcı değil yüklendiği etki alanı denetleyiciniz varsa, bu etki alanı denetleyicileri tarafından Azure ATP kapsamında değildir. Bir kaydı veya korumasız bir etki alanı denetleyicisinde yeni bir etki alanı denetleyicisi dağıtırsanız, bu durumda, bunu Azure ATP tarafından ilk etki alanı denetleyicisi olarak tanımlanmamış olabilir. Azure ATP algılayıcısını tam kapsamı almak için her etki alanı denetleyicisine yüklemek için önerilir.

1. Söz konusu bilgisayarın bir etki alanı denetleyicisi mi? Örneğin, çoğaltma olan yeni yükseltilen etki alanı denetleyicisi verir. Yanıt Evet ise, **Kapat** şüpheli etkinlik. 
2.  Söz konusu bilgisayarın Active Directory'den veri çoğaltma olması gerekiyor? Aygıtlar Örneğin, Azure AD Connect veya ağ performansı izleme. Yanıt Evet ise, **Kapat ve dışla** şüpheli etkinlik.
3. Çoğaltma isteği bir NAT veya bir ara sunucu gönderildiği IP mi? Yanıt Evet ise, yeni bir etki alanı denetleyicisi cihazının arkasında ise veya ondan diğer şüpheli etkinlikleri oluşmadıysa denetleyin. 

4. Kaynak bilgisayar veya hesap kendi profili sayfasına gitmek için tıklayın. Ne gibi olağan dışı etkinlikler için arama çoğaltma oluştuğu sırada olduğunu kontrol edin: açan, hangi kaynakların erişilebilir olduğunda. Windows Defender ATP tümleştirme etkinleştirilirse, Windows Defender ATP rozet tıklayın ![Windows Defender ATP rozeti](./media/wd-badge.png) Daha fazla makine araştırmak için. Windows Defender ATP'de uyarı oluştuğu sırada hangi işlemleri ve uyarılar oluştu görebilirsiniz. 


**Düzeltme**

Şu izinleri doğrulayın: 

- Dizin Değişikliklerini Çoğaltma   

- Tüm dizin değişikliklerini çoğaltma  

Daha fazla bilgi için [SharePoint Server 2013'te profil eşitleme izinleri verme Active Directory Domain Services](https://technet.microsoft.com/library/hh296982.aspx).
Yararlanabileceğiniz [AD ACL tarayıcı](https://blogs.technet.microsoft.com/pfesweplat/2013/05/13/take-control-over-ad-permissions-and-the-ad-acl-scanner-tool/) veya etki alanında kimin bu izinlere sahip olduğunu belirlemek için bir Windows PowerShell Betiği oluşturabilirsiniz.


## <a name="privilege-escalation-using-forged-authorization-data"></a>Sahte yetkilendirme verileri kullanan ayrıcalık yükseltme

**Açıklama**

Windows Server'ın eski sürümlerini güvenlik açıkları, saldırganların ayrıcalıklı öznitelik sertifikası (PAC), bir kullanıcının yetkilendirme verilerini içeren Kerberos anahtarındaki bir alan izin bilinen (Active Directory'de Grup üyeliği budur), verme saldırganlar ek ayrıcalık yok.

**Araştırma**

1. Uyarı için Ayrıntılar sayfasını almak için tıklayın.

2. Hedef bilgisayar (altında **ACCESSED** sütun) MS14-068 (etki alanı denetleyicisi) veya MS11-013 (sunucu) ile yama? Yanıt Evet ise, **Kapat** şüpheli etkinlik (Yanlış pozitif değer).

3. Kaynak bilgisayar çalışmazsa (altında **FROM** sütun) PAC'de değişiklik yaptığı bilinen bir işletim sistemini/uygulamayı? Yanıt Evet ise, **bastır** şüpheli etkinlik (zararsız bir doğru pozitif değer).

4. Yanıt varsa bu, kötü amaçlı Yukarıdaki iki sorulara Hayır varsayılır.

**Düzeltme**

Windows Server 2012 R2 ve altı işletim sistemi sürümleri kullanan etki alanı denetleyicilerinde [KB3011780](https://support.microsoft.com/help/2496930/ms11-013-vulnerabilities-in-kerberos-could-allow-elevation-of-privilege)’in yüklü olduğundan ve tüm üye sunucularla 2012 R2 ve altı sürümlerdeki etki alanı denetleyicilerinin KB2496930 güncel sürümünde olduğundan emin olun. Daha fazla bilgi için bkz. [Gümüş PAC](https://technet.microsoft.com/library/security/ms11-013.aspx) ve [Sahte PAC](https://technet.microsoft.com/library/security/ms14-068.aspx).

## <a name="reconnaissance-using-account-enumeration"></a>Hesap numaralandırma kullanarak keşif

**Açıklama**

Hesap numaralandırma keşfi bir saldırgan, kullanıcı adlarını veya araçları KrbGuess gibi binlerce etki alanınızdaki kullanıcı adlarını tahmin etme girişiminde bir sözlük kullanır. Saldırgan, Kerberos istekleri için geçerli bir kullanıcı adı, etki alanınızda bulmak için bu adlar kullanarak yapar. Bir tahmin başarıyla bir kullanıcı adı belirlerse, saldırgan, Kerberos hatasını alır. **gerekli ön kimlik doğrulaması** yerine **güvenlik sorumlusu bilinmeyen**. 

Bu algılama, Azure ATP saldırı nereden geldiğini, tahmin girişiminde toplam sayısını ve kaç eşleştirilmiş olan algılayabilir. Azure ATP bilinmeyen çok sayıda kullanıcı varsa, kuşkulu bir etkinlik algılar. 

**Araştırma**

1. Uyarı için Ayrıntılar sayfasını almak için tıklayın. 

2. Bu konak makine hesapları (örneğin, Exchange sunucuları) mi var için etki alanı denetleyicisi sorgulama? <br></br>
Bir betik veya bu davranışı üretebilir ana bilgisayarında çalışan bir uygulama mı? <br></br>
Ya da bu sorulara yanıt Evet ise **Kapat** şüpheli etkinliği barındıran hariç tutma ve şüpheli etkinlik (zararsız bir doğru pozitif değer).

3. Bir Excel elektronik tablosunda rahatça hesabı girişimleri, var olan ve mevcut olmayan hesaplara ayrılmış listesini görmek için bir uyarının ayrıntılarını indirin. Bakarsanız elektronik tablosunda olmayan mevcut hesapları ve hesapların tanıdık, devre dışı bırakılmış hesapları ya da çalışan şirketten olabilir. Bu durumda, deneme sözlükten geliyor düşüktür. Büyük olasılıkla bir uygulama ya da hangi hesapların Active Directory içinde bir zararsız gerçek pozitif sonuç yani hala mevcut görmek için denetimi betik olduğu.

3. Adlarını büyük ölçüde alışkın değilseniz, tahmin girişiminde Active Directory'deki mevcut hesap adlarıyla hiçbiriyle? Herhangi bir eşleşme varsa, yararsız girişimdi, ancak zaman içinde güncelleştirilir, görmek için uyarı dikkat.

4. Herhangi bir tahmin çalışırsa, ortamınızdaki hesaplarının varlığı, saldırgan bilir mevcut hesap adlarıyla eşleşen ve etki alanınızda bulunan kullanıcı adlarını kullanarak erişmek için deneme yanılma kullanmayı deneyebilir. Ek şüpheli etkinlikler için tahmin edilen hesap adlarını denetleyin. Herhangi bir eşleşen hesaplar hassas hesaplar olup olmadığını denetleyin.


**Düzeltme**

[Uzun ve karmaşık parolalar](https://docs.microsoft.com/windows/device-security/security-policy-settings/password-policy) gerekli ilk deneme yanılma saldırılarına karşı güvenlik düzeyini belirtin.


## <a name="reconnaissance-using-directory-services-queries"></a>Dizin hizmetleri sorguları kullanarak keşif

**Açıklama**

Dizin Hizmetleri ile Keşif, dizin yapısını ve saldırının sonraki adımlarında ayrıcalıklı hesapları hedeflemek için saldırganlar tarafından kullanılır. Güvenlik hesabı Yöneticisi Uzak (SAM-R) Protokolü gibi bir eşleme gerçekleştirmek için dizini sorgulamak için kullanılan yöntemlerden biridir.

Bu algılama, Azure ATP dağıtıldıktan sonra ilk ay içinde hiçbir uyarı tetiklenmesi. Hangi bilgisayarlardan hangi SAM-R sorgularına yapılan öğrenme dönemi Azure ATP profilleri sırasında hem sabit listesi hem de hassas hesapların tek sorgular.

**Araştırma**

1. Uyarı için Ayrıntılar sayfasını almak için tıklayın. Hangi sorguların (örneğin, Enterprise admins veya yönetici için) gerçekleştirilen ve olup olmadığını başarılı denetleyin.

2. Sorgularını kaynak bilgisayardan söz konusu yapılması gerekir?

3. Evet ve uyarı güncelleştirilir, **bastır** şüpheli etkinlik.

4. Yanıt Evet ise ve onu artık yapmamanız gerekir **Kapat** şüpheli etkinlik.

5. İlgili hesabıyla ilgili bilgiler varsa: sorgularını o hesap tarafından yapılması gereken veya o hesabın normalde kaynak bilgisayarda oturum mu?

 - Evet ve uyarı güncelleştirilir, **bastır** şüpheli etkinlik.

 - Yanıt Evet ise ve onu artık yapmamanız gerekir **Kapat** şüpheli etkinlik.

 - Yanıt Hayır tüm olursa yukarıdaki bu kötü amaçlı olduğu varsayılır.

6. Söz konusuydu hesabı hakkında hiçbir bilgi ise bitiş noktasına gidin ve hangi hesabın uyarı zaman günlüğe kaydedilen denetleyin.

**Düzeltme**

Aşağıdaki işlemi kullanarak bu tekniği karşı ortamınızı sağlamlaştırma:
1. Bilgisayar bir güvenlik açığı Tarama Aracı çalışıyor mu?  
2. Belirli sorgulanan kullanıcıları ve grupları saldırı ayrıcalıklı veya yüksek değerli hesapları olup olmadığını araştırmak (diğer bir deyişle, CEO, CFO, BT yönetimi, vs.).  Bu durumda, diğer uç nokta da faaliyete bakmak ve büyük olasılıkla yatay hareket hedefleri oldukları gibi sorgulanan hesapları, oturum açtığı bilgisayarlar izleyin.

## <a name="reconnaissance-using-dns"></a>DNS kullanarak keşif

**Açıklama**

DNS sunucunuzun tüm bilgisayarlar, IP adresleri ve Hizmetleri, ağınızda bir haritasını içerir. Saldırganlar bu bilgileri kullanarak ağ yapınızın haritasını çıkarır ve saldırının sonraki adımlarında kullanmak üzere uygun bilgisayarları hedef alır.

DNS protokolünde birkaç sorgu türü vardır. Azure ATP olmayan DNS sunucularından kaynaklanan AXFR (aktarım) istek algılar.

**Araştırma**

1. Kaynak makine (**kaynaklanan...** ) bir DNS sunucusu? Yanıt Evet ise, sonra bunun yanlış pozitif olabilir. Doğrulamak için uyarı için Ayrıntılar sayfasını almak için tıklayın. Tabloda, altında **sorgu**, hangi etki alanlarının sorgulandığını denetleyin. Bu var olan etki alanlarında misiniz? Yanıt Evet ise, ardından **Kapat** şüpheli etkinlik (Yanlış pozitif değer). Ayrıca, UDP bağlantı noktası 53 Azure ATP tek başına algılayıcı ve gelecekte hatalı pozitif sonuçları engellemek için kaynak bilgisayar arasında açık olduğundan emin olun.

2. Kaynak makine, bir güvenlik tarayıcısı çalışıyor mu? Yanıt Evet ise, **varlıkları dışlayarak** ATP, doğrudan ya da içinde **Kapat ve dışla** veya aracılığıyla **dışlama** sayfası (altında **yapılandırma** – kullanılabilir Azure ATP Yöneticiler için).

3. Yukarıdaki tüm sorulara olduğu sorusunu yanıtlamaya Hayır, kaynak bilgisayarda odaklanarak araştırma tutmak. Kaynak bilgisayarda, profili sayfasına gitmek için tıklayın. İsteğin gibi olağan dışı etkinlikler için arama oluştuğu sırada ne olduğunu kontrol edin: açan, hangi kaynakların erişilebilir olduğunda. Windows Defender ATP tümleştirme etkinleştirilirse, Windows Defender ATP rozet tıklayın ![Windows Defender ATP rozeti](./media/wd-badge.png) Daha fazla makine araştırmak için. Windows Defender ATP'de uyarı oluştuğu sırada hangi işlemleri ve uyarılar oluştu görebilirsiniz. 

**Düzeltme**

DNS kullanarak keşfi önlemek amacıyla DNS sunucusunu güvenlik altına almak için bölge aktarımlarını yalnızca belirtilen IP adresleriyle kısıtlamak veya devre dışı bırakmak mümkündür. Bölge aktarımlarını kısıtlamak hakkında daha fazla bilgi için bkz. [bölge aktarımlarını kısıtlama](https://technet.microsoft.com/library/ee649273(v=ws.10).aspx).
Bölge aktarımlarını değiştirmek, bir denetim listesi için ele alınması gereken görevlerden biridir [DNS sunucularınızı iç ve dış saldırılara karşı güvenli hale getirme](https://technet.microsoft.com/library/cc770432(v=ws.11).aspx).

## <a name="reconnaissance-using-smb-session-enumeration"></a>SMB Oturumu Listeleme kullanarak Keşif


**Açıklama**

Sunucu İleti Bloğu (SMB) hakkında bilgi almak burada son oturum açan kullanıcılar saldırganlar etkinleştirir. Saldırganlar bu bilgileri aldıktan sonra ağdaki belirli bir hassas hesap almak için riskli taşıyabilirsiniz.

Bir etki alanı denetleyicisine karşı bir SMB oturumu listeleme işlemi yapıldığında bu testler bulunmuyor çünkü bu algılama, bir uyarı tetiklenir.

**Araştırma**

1. Uyarı için Ayrıntılar sayfasını almak için tıklayın. Hangi hesabı/sn işlemin gerçekleştirilmesinden ve hangi hesapların ortaya çıktığını, varsa denetleyin.

 - Kaynak bilgisayarda çalışmakta olan güvenlik tarayıcısı tür var mı? Yanıt Evet ise, **Kapat ve dışla** şüpheli etkinlik.

2. İlgili hangi kullanıcı/sn işlemin gerçekleştirilmesinden denetleyin. Bunlar genellikle kaynak bilgisayarda oturum açın yapın ya da yöneticiler gibi işlemleri gerçekleştirmeniz gerekir?  

3. Evet ve uyarı güncelleştirilir, **bastır** şüpheli etkinlik.  

4. Yanıt Evet ise ve onu artık yapmamanız gerekir **Kapat** şüpheli etkinlik.

5. Yukarıdaki olan tüm yanıt Hayır, bu kötü amaçlı olduğunu varsayarsanız.

**Düzeltme**

Kullanım [Net sona ermesi aracı](https://gallery.technet.microsoft.com/Net-Cease-Blocking-Net-1e8dcb5b) bu saldırılara karşı ortamınızı güçlendirmek için.

## <a name="remote-execution-attempt"></a>Uzaktan yürütme denemesi

**Açıklama**

Yönetici kimlik bilgilerini tehlikeye veya sıfır gün yararlanma kullanmak saldırganların etki alanı denetleyicinizde uzak komutlar yürütebilir. Bu komutlar kalıcılık sağlamak, bilgi toplamak, hizmet reddi (DoS) saldırıları ve diğer herhangi bir sebeple kullanılabilir. Azure ATP PSexec ve WMI uzak bağlantıları algılar.

**Araştırma**

1. Bu, yönetim iş istasyonları, BT ekibi üyelerinde ve hizmet hesapları, etki alanı denetleyicilerinde yönetim görevlerini gerçekleştirmek için yaygındır. Bu ise durum ve uyarı itibaren aynı yönetici güncelleştirilir ve/veya bilgisayar yapmakta olduğunuz görev ardından **bastır** uyarı.

2. Olan **bilgisayar** söz konusu etki alanı denetleyicinizde Bu uzaktan yürütmeyi gerçekleştirme izni var?

 - Olan **hesabı** söz konusu etki alanı denetleyicinizde Bu uzaktan yürütmeyi gerçekleştirme izni var?

 - Her iki soruların yanıtlanması gerekirse *Evet*, ardından **Kapat** uyarı.

3. Ya da soruların yanıtlanması gerekirse, Hayır, ardından bunu bir doğru pozitif düşünülmelidir. Bilgisayarınızın ve hesabınızın profilleri kontrol ederek deneme kaynağını bulmaya çalışın. Kaynak bilgisayar veya hesap kendi profili sayfasına gitmek için tıklayın. Ne gibi olağan dışı etkinlikler için arama, bu deneme süresini olduğunu kontrol edin: açan, hangi kaynakların erişilebilir olduğunda. Windows Defender ATPintegration etkinleştirilirse, Windows Defender ATP rozet tıklayın ![Windows Defender ATP rozeti](./media/wd-badge.png) Daha fazla makine araştırmak için. Windows Defender ATPyou, uyarının oluştuğu sırada hangi işlemleri ve uyarılar oluştu görebilirsiniz. 

**Düzeltme**

1. Katman 0 olmayan makinelerden etki alanı denetleyicilerine uzaktan erişimi kısıtlayın.

2. Uygulama [ayrıcalıklı erişim](https://technet.microsoft.com/windows-server-docs/security/securing-privileged-access/securing-privileged-access) yalnızca güçlendirilmiş makinelerin yöneticileri için etki alanı denetleyicilerine bağlanmasına izin vermek için.

## <a name="suspicious-authentication-failures"></a>Şüpheli kimlik doğrulaması hataları

**Açıklama**

Bir deneme yanılma saldırısında, saldırgan doğru parolayı en az bir hesap için bulunana kadar farklı hesaplar için çok sayıda farklı parolaları ile kimlik doğrulaması dener. Bir kez bulundu, bir saldırganın bu hesabı kullanarak oturum açabilir.

Bu algılama, Kerberos veya NTLM kullanarak birçok kimlik doğrulama hataları ortaya çıktığında bir uyarı tetiklenir, bu yatay olarak küçük bir parola ile çok sayıda kullanıcı arasında olabilir; veya dikey olarak büyük ile Parolaları yalnızca bazı kullanıcılar ayarlayın; veya bu iki seçenek herhangi bir birleşimi. Bir uyarı tetiklenebilir önce en az bir hafta dönemdir.

**Araştırma**

1.  Tıklayın **indirme ayrıntıları** bir Excel elektronik tablosundaki tüm bilgileri görüntülemek için. Aşağıdaki bilgiler elde edebilirsiniz: 
   -    Saldırıya uğrayan hesaplar listesi
   -    Başarılı kimlik doğrulaması ile sona erdi hangi oturum açma girişimlerinde tahmin edilen hesaplar listesi
   -    NTLM kullanarak kimlik doğrulama girişimleri gerçekleştirildi varsa, ilgili olay etkinlikleri göreceksiniz. 
   -    Kerberos kullanarak kimlik doğrulama girişimleri gerçekleştirildi varsa, ilgili ağ etkinlikleri göreceksiniz.

2.  Kaynak bilgisayarda, profili sayfasına gitmek için tıklayın. Ne gibi olağan dışı etkinlikler için arama, bu deneme süresini olduğunu kontrol edin: açan, hangi kaynakların erişilebilir olduğunda. Windows Defender ATP tümleştirme etkinleştirilirse, Windows Defender ATP rozet tıklayın ![Windows Defender ATP rozeti](./media/wd-badge.png) Daha fazla makine araştırmak için. Windows Defender ATP'de uyarı oluştuğu sırada hangi işlemleri ve uyarılar oluştu görebilirsiniz. 

3.  NTLM kullanılarak kimlik doğrulaması gerçekleştirildi ve çoğu zaman, uyarıyı oluşur ve yok yeterli bilgi kaynak makine erişmeye sunucusu hakkında etkinleştirmeniz gereken gördüğünüz **NTLM denetim** üzerinde dahil olan etki alanı denetleyicileri. Bunu yapmak için 8004 olayı kapatın. Kaynak bilgisayar, kullanıcı hesabı hakkında bilgi içeren NTLM kimlik doğrulaması olay budur ve **sunucu** , kaynak makinenin erişmeyi denedi. Hangi sunucu kimlik doğrulama gönderilen bulduktan sonra sunucu kimlik doğrulama işlemi 4624 daha iyi anlama gibi olayları kontrol ederek araştırmanız gerekir. 

**Düzeltme**

[Uzun ve karmaşık parolalar](https://docs.microsoft.com/windows/device-security/security-policy-settings/password-policy) gerekli ilk deneme yanılma saldırılarına karşı güvenlik düzeyini belirtin.

## <a name="suspicious-domain-controller-promotion-potential-dcshadow-attack---new"></a>Şüpheli etki alanı denetleyicisi yükseltme (olası DCShadow saldırı) - yeni

**Açıklama**

Bir etki alanı denetleyicisi gölge (DCShadow) saldırısı, kötü amaçlı çoğaltma kullanarak dizin nesneleri değiştirmek için tasarlanmış bir saldırıdır. Bu saldırı, herhangi bir makineden bir dolandırıcı etki alanı denetleyicisi çoğaltma işlemi kullanarak oluşturarak gerçekleştirilebilir.
 
DCShadow RPC ve LDAP kullanır:
1. Makine hesabı (etki alanı yöneticisi haklarına kullanarak), bir etki alanı denetleyicisi olarak kaydedin ve
2. (Verilen çoğaltma hakları kullanarak) çoğaltma üzere DRSUAPI gerçekleştirin ve dizin nesnelere değişiklikleri göndermek.
 
Sahte etki alanı denetleyicisi olarak kaydetmek ağ bir makinede çalışırken bu algılama, bir uyarı tetiklenir. 

**Araştırma**
 
1. Söz konusu bilgisayarın bir etki alanı denetleyicisi mi? Örneğin, çoğaltma olan yeni yükseltilen etki alanı denetleyicisi verir. Yanıt Evet ise, **Kapat** şüpheli etkinlik.
2. Söz konusu bilgisayarın Active Directory'den veri çoğaltma olması gerekiyor? Örneğin, Azure AD Connect. Yanıt Evet ise, **Kapat ve dışla** şüpheli etkinlik.
3. Kaynak bilgisayar veya hesap kendi profili sayfasına gitmek için tıklayın. Ne gibi olağan dışı etkinlikler için arama çoğaltma oluştuğu sırada olduğunu kontrol edin: kimlerin, hangi kaynaklara günlüğe kaydedilen ve bilgisayar kullanıcının işletim sistemi?
   1. İçine oturum açmış olmanız gereken bilgisayara günlüğe kaydedilen tüm kullanıcılar misiniz? Kendi ayrıcalıklarını nelerdir? Bir sunucuyu etki alanı denetleyicisine Yükselt izni var mı? (etki alanı yöneticileri olmaları)?
   2. Bu kaynaklara erişmek için kullanıcıların gerekir?
   3. Bilgisayar, Windows Server işletim sistemi (veya Windows/Linux) çalıştırıyor mu? Verileri çoğaltmak için bir sunucu olmayan makine beklenmiyor.
Windows Defender ATP tümleştirme etkinleştirilirse, Windows Defender ATP rozet tıklayın ![Windows Defender ATP rozet](./media/wd-badge.png) makine daha fazla araştırmak için. Windows Defender ATP'de uyarı oluştuğu sırada hangi işlemleri ve uyarılar oluştu görebilirsiniz.

4. Konum görmek için Olay Görüntüleyicisi ' [Dizin Hizmetleri günlüğünde kayıtları Active Directory olayları](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/cc961809(v=technet.10)). Günlük, Active Directory'deki değişiklikleri izlemek için kullanabilirsiniz. Varsayılan olarak, Active Directory yalnızca ancak bu, kritik hata olaylarını kaydeder. uyarı recurrs, daha fazla bilgi için ilgili etki alanı denetleyicisinde bu denetimi etkinleştirin.

**Düzelt**

Aşağıdaki izinlere sahip olan, kuruluşunuzda denetimi: 
- Dizin Değişikliklerini Çoğaltma 
- Tüm dizin değişikliklerini çoğaltma 
 
 
Daha fazla bilgi için [SharePoint Server 2013'te profil eşitleme izinleri verme Active Directory Domain Services](https://technet.microsoft.com/library/hh296982.aspx). 

Yararlanabileceğiniz [AD ACL tarayıcı](https://blogs.technet.microsoft.com/pfesweplat/2013/05/13/take-control-over-ad-permissions-and-the-ad-acl-scanner-tool/) veya etki alanında kimin bu izinlere sahip olduğunu belirlemek için bir Windows PowerShell Betiği oluşturabilirsiniz.
 
> [!NOTE]
> Şüpheli etki alanı denetleyicisi yükseltme (olası DCShadow saldırı) algılamalar ATP algılayıcı tarafından desteklenir. 


## <a name="suspicious-replication-request-potential-dcshadow-attack---new"></a>Şüpheli çoğaltma isteği (olası DCShadow saldırı) - yeni

**Açıklama** 

Active Directory çoğaltma tarafından bir etki alanı denetleyicisinde yapılan değişiklikler diğer etki alanı denetleyicileriyle eşitlenmesi işlemidir. Gerekli izinleri göz önünde bulundurulduğunda, saldırganların bir etki alanı denetleyicisi almasına olanak kendi makine hesabı hakları verebilirsiniz. Saldırganlar bir kötü amaçlı çoğaltma isteği başlatmak bunları saldırganlar etki alanındaki Kalıcılık verebilir bir orijinal etki alanı denetleyicisinde Active Directory nesneleri değiştirmek izin verme yönelik çalışmalarımızı sürdüreceğiz.
Azure ATP tarafından korunan bir orijinal etki alanı denetleyicisine karşı şüpheli çoğaltma isteği oluşturulduğunda bu algılama, bir uyarı tetiklenir. Etki alanı denetleyicisi gölge saldırılarında kullanılır teknikler simulatorda davranıştır.

**Araştırma** 
 
1. Söz konusu bilgisayarın bir etki alanı denetleyicisi mi? Örneğin, çoğaltma olan yeni yükseltilen etki alanı denetleyicisi verir. Yanıt Evet ise, **Kapat** şüpheli etkinlik.
2. Söz konusu bilgisayarın Active Directory'den veri çoğaltma olması gerekiyor? Örneğin, Azure AD Connect. Yanıt Evet ise, **Kapat ve dışla** şüpheli etkinlik.
3. Kaynak bilgisayarda, profili sayfasına gitmek için tıklayın. Ne olduğunu denetleyin **zamana yakın** gibi olağan dışı etkinlikler için arama çoğaltma: kimin günlüğe kaydedilen, hangi kaynakların kullanılan ve bilgisayarda nedir kullanıcının işletim sistemi?

   1.  İçine oturum açmış olmanız gereken bilgisayara günlüğe kaydedilen tüm kullanıcılar misiniz? Kendi ayrıcalıklarını nelerdir? Çoğaltmalar (etki alanı yöneticileri olmaları) gerçekleştirmek için izni var mı?
   2.  Bu kaynaklara erişmek için kullanıcıların gerekir?
   3. Bilgisayar, Windows Server işletim sistemi (veya Windows/Linux) çalıştırıyor mu? Verileri çoğaltmak için bir sunucu olmayan makine beklenmiyor.
Windows Defender ATP tümleştirme etkinleştirilirse, Windows Defender ATP rozet tıklayın ![Windows Defender ATP rozet](./media/wd-badge.png) makine daha fazla araştırmak için. Windows Defender ATP'de uyarı oluştuğu sırada hangi işlemleri ve uyarılar oluştu görebilirsiniz.
1. Konum görmek için Olay Görüntüleyicisi ' [Dizin Hizmetleri günlüğünde kayıtları Active Directory olayları](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/cc961809(v=technet.10)). Günlük, Active Directory'deki değişiklikleri izlemek için kullanabilirsiniz. Varsayılan olarak, Active Directory yalnızca ancak bu, kritik hata olaylarını kaydeder. uyarı recurrs, daha fazla bilgi için ilgili etki alanı denetleyicisinde bu denetimi etkinleştirin.

**Düzeltme**

Aşağıdaki izinlere sahip olan, kuruluşunuzda denetimi: 
- Dizin Değişikliklerini Çoğaltma 
- Tüm dizin değişikliklerini çoğaltma 

Bunu yapmak için yararlanabileceğiniz [AD ACL tarayıcı](https://blogs.technet.microsoft.com/pfesweplat/2013/05/13/take-control-over-ad-permissions-and-the-ad-acl-scanner-tool/) veya etki alanında kimin bu izinlere sahip olduğunu belirlemek için bir Windows PowerShell Betiği oluşturabilirsiniz.

> [!NOTE]
> Şüpheli çoğaltma isteği (olası DCShadow saldırı) algılamalar ATP algılayıcı tarafından desteklenir. 


## <a name="suspicious-service-creation"></a>Şüpheli hizmet oluşturma

**Açıklama**

Bir etki alanı denetleyicisine, kuruluşunuzda şüpheli bir hizmet oluşturuldu. Bu uyarı olayı 7045 bu şüpheli etkinlikleri belirlemek için kullanır. 

**Araştırma**

1. Söz konusu bilgisayarın bir yönetici iş istasyonunda veya hangi BT ekibi üyelerinde ve hizmet hesapları yönetim görevlerini gerçekleştirmek için bir bilgisayar varsa, bu bir hatalı pozitif sonuç olabilir ve gerekebilir **bastır** uyarı ve ekleyin Dışlama listesine gerekirse.

2. Hizmeti bu bilgisayarda tanıyacak bir şey mi?

 - Olan **hesabı** söz konusu bu hizmet yüklemesine izin?

 - Her iki soruların yanıtlanması gerekirse *Evet*, ardından **Kapat** uyarı veya dışlama listesine ekleyin.

3. Ya da soruların yanıtlanması gerekirse *hiçbir*, sonra bunu bir doğru pozitif düşünülmelidir.

**Düzeltme**

- Daha az ayrıcalıklı erişimi yalnızca belirli kullanıcılara yeni hizmetleri oluşturma hakkı izin vermek için etki alanı makinelerde uygulayın.

## Şüpheli VPN bağlantısı <a name="suspicious-vpn-detection"></a>

**Açıklama**

Azure ATP kayan bir bir aylık dönem boyunca kullanıcılar VPN bağlantıları için varlık davranışını öğrenir. 

VPN davranışı modelini şu etkinlikleri temel alan: makineler kullanıcılar için oturum ve kullanıcıları konumları bağlanabilirsiniz. 

Bir kullanıcının davranışı üzerinde makine öğrenme algoritmasına göre sapma olduğunda bir uyarı açılır.

**Araştırma**

1.  Söz konusu kullanıcının bu işlemleri gerçekleştirmeyi gerekiyor?
2.  Aşağıdaki durumlarda olası hatalı pozitif sonuç olarak göz önünde bulundurun: kendi konumu değiştiren bir kullanıcı, seyahat ve yeni bir CİHAZDAN bağlanma bir kullanıcı.

**Düzeltme**

1.  Bu kullanıcının parolasını sıfırlama göz önünde bulundurun. Bu, saldırgan eski kimlik bilgilerini kullanarak yeni VPN bağlantıları oluşturmanızı engeller.
2.  Bu kullanıcı, VPN üzerinden bağlanmasını engelleyen göz önünde bulundurun.

## <a name="unusual-protocol-implementation"></a>Olağan dışı protokol uygulanması


**Açıklama**

Saldırganlar, standart olmayan şekilde çeşitli protokolleri (SMB, Kerberos, NTLM) uygulayan araçlarını kullanın. Ağ trafiği bu tür uyarılar olmadan Windows tarafından kabul edilir, ancak Azure ATP olası kötü amaçlı tanıyabilirsiniz. Gelişmiş fidye yazılımı tarafından Örneğin, WannaCry kullanılan açıklara yanı sıra, Kerberos'taki-geçiş--Hash ve deneme yanılma zorla gibi teknikler simulatorda davranıştır.

**Araştırma**

Alışılmadık şüpheli etkinlik zaman satırından – Protokolü tanımlayın, şüpheli etkinlik için Ayrıntılar sayfasını almak için tıklayın; protokol oku görünür: Kerberos veya NTLM.

- **Kerberos**: büyük olasılıkla bir adlı istemciden Overpass--Hash saldırısı gerçekleştiren Mimikatz kullanılmış gibi bir deşifre etme aracı, bu genellikle tetiklenir. Kaynak bilgisayar Kerberos RFC uygun olmayan kendi Kerberos yığınını uygulayan bir uygulama çalışıp çalışmadığını denetleyin. Böyle, bunu bir zararsız gerçek pozitiftir ve yapabilecekleriniz **Kapat** uyarı. Uyarıyı tetikleyen tutar ve durum hala geçerlidir, yapabilecekleriniz **bastır** uyarı.

- **NTLM**: WannaCry veya Metasploit Medusa ve Hydra gibi araçları olabilir.  

Bunun bir WannaCry saldırısı olup olmadığını belirlemek için aşağıdaki adımları gerçekleştirin:

1. Kaynak bilgisayarda bir saldırı aracı Metasploit, Medusa veya Hydra gibi çalışıp çalışmadığını denetleyin.

2. Hiçbir saldırı araçlarının bulunursa, kaynak bilgisayarın kendi NTLM veya SMB yığınını uygulayan bir uygulama çalışıp çalışmadığını denetleyin.

3. Kaynak bilgisayarda, profili sayfasına gitmek için tıklayın. Ne gibi olağan dışı etkinlikler için arama uyarının oluştuğu sırada olduğunu kontrol edin: açan, hangi kaynakların erişilebilir olduğunda. Windows Defender ATP tümleştirme etkinleştirilirse, Windows Defender ATP rozet tıklayın ![WD rozeti](./media/wd-badge.png) Daha fazla makine araştırmak için. Windows Defender ATP'de uyarı oluştuğu sırada hangi işlemleri ve uyarılar oluştu görebilirsiniz.



**Düzeltme**

Özellikle güvenlik güncelleştirmelerini uygulama tüm makinelerinizi, düzeltme eki.

1. [SMBv1 devre dışı bırak](https://blogs.technet.microsoft.com/filecab/2016/09/16/stop-using-smb1/)

2. [WannaCry Kaldır](https://support.microsoft.com/help/890830/remove-specific-prevalent-malware-with-windows-malicious-software-remo)

3. Kullanıcı olmayan yeniden başlatıldı veya bilgisayar oturumunu açık varsa WanaKiwi ancak bazı ransom yazılım kullanımına veri şifresini çözebilir. Daha fazla bilgi için [Cry fidye yazılımı için istediğiniz](https://answers.microsoft.com/en-us/windows/forum/windows_10-security/wanna-cry-ransomware/5afdb045-8f36-4f55-a992-53398d21ed07?auth=1)


> [!NOTE]
> Kuşkulu bir etkinlik devre dışı bırakmak için desteğe başvurun.


## <a name="see-also"></a>Ayrıca Bkz.
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
