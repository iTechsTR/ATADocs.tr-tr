---
title: ATA şüpheli etkinlik kılavuzu | Microsoft Docs
d|Description: This article provides a list of the suspicious activities ATA can detect and steps for remediation.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 7/29/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 1fe5fd6f-1b79-4a25-8051-2f94ff6c71c1
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: be809f422e797f08655b7841fc7f9ecb7423a0a6
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133931"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*


# <a name="advanced-threat-analytics-suspicious-activity-guide"></a>Gelişmiş Threat Analytics şüpheli etkinlik Kılavuzu

Uygun araştırma, herhangi bir şüpheli etkinlik olarak sınıflandırılabilir:

-   **Gerçek pozitif sonuç**: ATA tarafından algılanan kötü amaçlı bir eylem.

-   **Zararsız gerçek pozitif sonuç**: Gerçek, ancak zararsız sızma testi örneğindeki gibi ATA tarafından algılanan bir eylem.

-   **Hatalı pozitif sonuç**: etkinlik anlamına gelen bir yanlış alarm gerçekleşmemiştir.

ATA uyarılarını ile çalışma konusunda daha fazla bilgi için bkz. [kuşkulu etkinliklerle çalışma](working-with-suspicious-activities.md).

Sorularınız veya Geri bildiriminiz için ATA ekibi ile iletişime geçin [ ATAEval@microsoft.com ](mailto:ATAEval@microsoft.com).

## <a name="abnormal-sensitive-group-modification"></a>Anormal Gizli Grup Değişikliği


**Açıklama**

Saldırganlar kullanıcıların yüksek ayrıcalıklı gruplara ekleyin. Daha fazla kaynaklarına erişmek ve kalıcılığı sağlamak için bunu yapın. Algılama, kullanıcıların Grup değişikliği etkinliklerini profilini oluşturup anormal bir hassas Grup eklemeyi ortaya çıktığında üzerinde kullanır. Profil ATA tarafından sürekli olarak gerçekleştirilir. Bir uyarı tetiklenebilir önce en az süre, her etki alanı denetleyicisi başına bir aydır.

Gizli gruplarda ata'da tanımı için bkz [ATA Konsolu'yla çalışma](working-with-ata-console.md#sensitive-groups).


Algılama dayanan [etki alanı denetleyicilerinde Denetlenen olayları](https://docs.microsoft.com/advanced-threat-analytics/configure-event-collection).
Etki alanı denetleyicilerinizin gerekli olaylarını denetleme emin olmak için başvurulan aracını [ATA denetim (AuditPol, denetim ayarları zorlama Gelişmiş, basit ağ geçidi hizmet bulma)](https://aka.ms/ataauditingblog).

**Araştırma**

1. Grup değişikliği yasal mı? </br>Nadiren oluşur ve "olarak normal", öğrenilen değil yasal Grup değişikliklerini zararsız gerçek pozitif sonuç olarak değerlendirilebilecek bir uyarı neden olabilir.

2. Eklenen nesne bir kullanıcı hesabı varsa, kullanıcı hesabının yönetim grubuna eklendikten sonra geçen hangi eylemleri denetleyin. Daha fazla bağlam almak için Ata kullanıcının sayfasına gidin. Diğer vardı önce veya sonra ek hesapla ilişkili şüpheli etkinlikleri gerçekleşen? İndirme **gizli Grup değişikliği** ne olan diğer değişiklikleri görmek için raporu yapılmış ve aynı süre boyunca kim tarafından.

**Düzeltme**

Gizli gruplarda değişiklik yapabilecek kullanıcı sayısını en aza indirin.

Ayarlanan [Privileged Access Management için Active Directory](https://docs.microsoft.com/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services) varsa.

## <a name="broken-trust-between-computers-and-domain"></a>Bilgisayarlar ve etki alanı arasındaki güvenin Bozulması

> ! [NOT] Bu şüpheli etkinlik, kullanım dışı bırakıldı ve yalnızca ATA sürümlerde 1.9 görüntülenir.

**Açıklama**

Güvenin bozulması, Active Directory güvenlik gereksinimlerinin etkin bilgisayarlar için söz konusu olmayabileceği anlamına gelir. Bu, genelde temel bir güvenlik ve uyumluluk hatası olarak değerlendirilir ve saldırganlar için kolay bir hedeftir. 24 saat içindeki bilgisayar hesabından 5'ten fazla Kerberos kimlik doğrulama hatası görülürse bu algılama, bir uyarı tetiklenir.

**Araştırma**

Söz konusu bilgisayarın etki alanı oturum açmasına izin veriyor mu? 
- Yanıt Evet ise, bu bilgisayara düzeltme adımlarını göz ardı edebilirsiniz.

**Düzeltme**

Gerekirse makineyi etki alanına katın veya makinenin parolasını sıfırlayın.


## <a name="brute-force-attack-using-ldap-simple-bind"></a>Basit LDAP bağlama kullanan deneme yanılma saldırısı

**Açıklama**

>[!NOTE]
> Arasındaki temel fark **şüpheli kimlik doğrulama hataları** ve bu algılama bu algılama, ATA farklı parolalar kullanımda olup olmadığını belirleyebilirsiniz.

Bir deneme yanılma saldırısında, saldırgan doğru parolayı en az bir hesap için bulunana kadar farklı hesaplar için çok sayıda farklı parolaları ile kimlik doğrulaması dener. Bir kez bulundu, bir saldırganın bu hesabı kullanarak oturum açabilir.

Bu algılama, ATA basit bağlama kimlik doğrulamaları devasa bir dizi algıladığında bir uyarı tetiklenir. Bu olabilir *yatay* parolaları; çok sayıda kullanıcı arasında küçük bir dizi veya *dikey "* parolaları yalnızca birkaç kullanıcılar; veya bu iki seçenek herhangi bir bileşimini büyük bir dizi.

**Araştırma**

1. İlgili birçok hesapları varsa, tıklayın **indirme ayrıntıları** bir Excel elektronik tablosunda listesini görüntülemek için.

2. Ayrılmış alt sayfasına gitmek için uyarıyı tıklayın. Tüm oturum açma girişimlerini başarılı bir kimlik doğrulaması ile sona erdi kontrol edin. Deneme olarak görüneceği **hesapları tahmin** bilgi grafiğine sağ tarafında. Yanıt Evet ise, olan **hesapları tahmin** normalde kullanılan kaynak bilgisayardan? Yanıt Evet ise, **bastır** şüpheli etkinlik.

3. Varsa hiçbir **hesapları tahmin**, olan **Saldırıya uğrayan hesaplar** normalde kullanılan kaynak bilgisayardan? Yanıt Evet ise,**bastır** şüpheli etkinlik.

**Düzeltme**

[Uzun ve karmaşık parolalar](https://docs.microsoft.com/windows/device-security/security-policy-settings/password-policy) gerekli ilk deneme yanılma saldırılarına karşı güvenlik düzeyini belirtin.

## <a name="encryption-downgrade-activity"></a>Şifreleme düşürme etkinliği

**Açıklama**

Şifrelemeyi düşürme Kerberos protokolünün genellikle en yüksek düzeyde şifrelemesi kullanılarak şifrelenmiş farklı alanları şifreleme düzeyini eski sürüme düşürme zayıflatmanın bir yöntemdir. Düzeyi düşürülmüş bir şifrelenmiş alan çevrimdışı deneme yanılma girişimleri için daha kolay bir hedef olabilir. Zayıf Kerberos şifreleme cyphers çeşitli saldırı yöntemleri kullanın. Bu algılama, ATA bilgisayarlar ve kullanıcılar tarafından kullanılan Kerberos şifreleme türleri öğrenir ve daha zayıf bir şifreleme olduğunda, kullanılan uyarılar: (1) kaynak bilgisayarı ve/veya kullanıcı; olağandışı bir durumdur ve bilinen saldırı teknikleri (2) eşleşir.

Üç algılama türleri şunlardır:

1.  Etki alanı denetleyicilerinde çalışan ve kimlik doğrulama etki alanına herhangi bir hesap ile parolaya gerek kalmaksızın sağlayan kötü amaçlı yazılım Maymuncuk – var. Bu kötü amaçlı yazılım, etki alanı denetleyicisinde kullanıcının parolalarını karma için genellikle daha zayıf şifreleme algoritmaları kullanır. Bu algılama, daha önceden öğrenilen davranışına göre şifreleme yöntemi için bir bilet isteyen hesabı etki alanı denetleyicisinden KRB_ERR iletisinin indirgenen.

2.  Altın bilet – içinde bir [altın bilet](#golden-ticket) uyarı, şifreleme yöntemi kaynak bilgisayardan TGS_REQ (hizmet isteği) iletisinin TGT alanının kıyasla daha önceden öğrenilen davranıştır indirgenen. Bu bir zaman anomali (olduğu gibi diğer altın bilet algılama) temel almaz. Ayrıca, ATA tarafından algılanan önceki hizmet isteği ile ilişkili hiçbir Kerberos kimlik doğrulama isteği vardı.

3.  Karmayı – bir saldırgan, Kerberos AS isteği ile güçlü bir anahtar oluşturmak için zayıf çalınmış bir karmasını kullanabilir. Bu algılama, kaynak bilgisayardan AS_REQ ileti şifreleme türü daha önceden öğrenilen davranışına göre indirgenen (bilgisayar, AES kullanıyordu).

**Araştırma**

İlk olarak, yukarıdaki üç algılama türleri ile ilgili uyarıya açıklamasını denetleyin. Daha fazla bilgi için Excel elektronik tablosunu indirin.
1.  Maymuncuk – kullanarak etki alanı denetleyicilerinizin Skeleton Key etkilenen, denetleyebilirsiniz [ATA ekibi tarafından yazılan tarayıcıyı](https://gallery.technet.microsoft.com/Aorato-Skeleton-Key-24e46b73). Tarayıcı 1 veya daha fazla etki alanı denetleyicilerinizin kötü amaçlı yazılım bulması halinde, bu gerçek pozitiftir.
2.  Altın bilet – Excel elektronik tablosunda Git **ağ etkinliği** sekmesi. İlgili indirgenmiş alanı olduğunu göreceksiniz **istek anahtarı şifreleme türü**, ve **kaynak bilgisayarı desteklenen şifreleme türlerini** daha güçlü şifreleme yöntemlerini içerir.
  a.    Kaynak bilgisayar ve hesap denetleyin veya varsa birden çok kaynak bilgisayarlar ve hesabı, bir şey (örneğin, tüm tetiklenmesi için uyarıya neden olan belirli bir uygulama pazarlama kullanacağı) ortak sahip olup olmadığınızı denetleyin. Daha düşük bir şifreleme şifreleme kullanarak nadiren kullanılan özel bir uygulama doğrulama durumlar vardır. Kaynak bilgisayar gibi özel uygulamalar olup olmadığını denetleyin. Bu nedenle, bu büyük olasılıkla bir zararsız gerçek pozitiftir ve yapabilecekleriniz **bastır** bu.
  b.    Kaynak denetimi bu anahtarları tarafından erişilen, tüm eriştikleri bir kaynak varsa, doğrulayın, bunlar erişmek için gereken geçerli bir kaynak olduğundan emin olun. Ayrıca, hedef kaynağın güçlü şifreleme yöntemlerini destekleyip desteklemediğini doğrulayın. Öznitelik kontrol ederek bu Active Directory'de denetleyebilirsiniz `msDS-SupportedEncryptionTypes`, kaynak hizmet hesabı.
3.  Karmayı – Excel elektronik tablosunda Git **ağ etkinliği** sekmesi. İlgili indirgenmiş alanı olduğunu göreceksiniz **şifrelenmiş zaman damgası şifreleme türü** ve **kaynak bilgisayarı desteklenen şifreleme türlerini** daha güçlü şifreleme yöntemlerini içerir.
  a.    Akıllı kart kullanarak akıllı kart yapılandırması yakın zamanda değiştirdiyseniz kullanıcılar oturum açtığında, bu uyarı tetiklenebilir durumlar vardır. İlgili hesapları için bunun gibi değişiklikler olup olmadığını denetleyin. Bu nedenle, bu büyük olasılıkla bir zararsız gerçek pozitiftir ve yapabilecekleriniz **bastır** bu.
  b.    Kaynak denetimi bu anahtarları tarafından erişilen, tüm eriştikleri bir kaynak varsa, doğrulayın, bunlar erişmek için gereken geçerli bir kaynak olduğundan emin olun. Ayrıca, hedef kaynağın güçlü şifreleme yöntemlerini destekleyip desteklemediğini doğrulayın. Öznitelik kontrol ederek bu Active Directory'de denetleyebilirsiniz `msDS-SupportedEncryptionTypes`, kaynak hizmet hesabı.

**Düzeltme**

1.  İskelet anahtar – kötü amaçlı yazılımı kaldırın. Daha fazla bilgi için [Skeleton Key kötü amaçlı yazılım Analizine](https://www.virusbulletin.com/virusbulletin/2016/01/paper-digital-bian-lian-face-changing-skeleton-key-malware).

2.  Altın bilet – yönergeleri izleyin [altın bilet](#golden-ticket) kuşkulu etkinlikler.   
    Ayrıca, etki alanı yöneticisi haklarına bir altın anahtar oluşturuluyor gerektirdiği için uygulama [Pass the hash önerilerini](http://aka.ms/PtH).

3.  Karmayı –, ardından ilgili hesabı hassas, değilse o hesabın parolasını sıfırlayın. Mevcut biletleri, süreleri doluncaya kadar hala kullanılabilir olsa da bu saldırgan parola karması, yeni Kerberos biletleri oluşturmanızı engeller. Hassas hesap ise, iki kez altın bilet şüpheli etkinliğin olduğu gibi KRBTGT hesap sıfırlama düşünmelisiniz. İki kez KRBTGT sıfırlama tüm Kerberos biletleri bu etki alanında bunu yapmadan önce plan geçersiz kılar. Kılavuzunda bkz [KRBTGT hesap parolası sıfırlama betikleri artık müşteriler tarafından kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/). Ayrıca bkz [KRBTGT hesap parolası/anahtarı sıfırlama aracını](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51). Yanal hareket tekniğidir olduğundan, en iyi yöntemleri takip [Pass the hash önerilerini](http://aka.ms/PtH).


## <a name="honeytoken-activity"></a>Honeytoken etkinliği


**Açıklama**

Honeytoken hesapları tanımlamak ve bu hesapları içeren kötü amaçlı etkinliği izlemek üzere ayarlanan sahte hesaplardır. Honeytoken hesapları (örneğin, SQL-yönetici) saldırganlar çekici yöntemlerle çekmeye için çekici bir ad yaparken kullanılmamış olarak bırakılmalıdır. Herhangi bir etkinlikten kötü amaçlı davranışları gösterebilir.

Honeytoken hesapları hakkında daha fazla bilgi için bkz. [Ata'yı yükleme - 7. adım](install-ata-step7.md).

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

1. Tıklayın **indirme ayrıntıları** IP adreslerinin dahil tam listesini görüntülemek için düğme. Bir IP adresi yok veya her iki bilgisayar sayıdan bir DHCP havuzundan WiFi veya VPN gibi ayrılmış bir alt ağa ait? IP adresi paylaşılıyor mu? Örneğin, bir NAT cihazının tarafından? Ardından bu soruları hiçbirini yanıt Evet ise, bir hatalı pozitif sonuç olduğunu.

2. Kullanıcılar adına biletleri ileten özel bir uygulama mı? Bu durumda, bunu bir zararsız gerçek pozitiftir.

**Düzeltme**

1. Ardından ilgili hesabı önemli değilse, o hesabın parolasını sıfırlayın. Mevcut biletleri, süreleri doluncaya kadar hala kullanılabilir olsa da bu saldırgan parola karması, yeni Kerberos biletleri oluşturmanızı engeller.  

2. Hassas hesap ise, iki kez altın bilet şüpheli etkinliğin olduğu gibi KRBTGT hesap sıfırlama düşünmelisiniz. İki kez KRBTGT sıfırlama tüm Kerberos biletleri bu etki alanında bunu yapmadan önce plan geçersiz kılar. Kılavuzunda bkz [KRBTGT hesap parolası sıfırlama betikleri artık müşteriler tarafından kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/), ayrıca bkz [KRBTGT hesap parolası/anahtarı sıfırlama aracını](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51).  Yanal hareket tekniğidir olduğundan, en iyi uygulamaları izlemesi [Pass the hash önerilerini](http://aka.ms/PtH).

## Kerberos altın bilet<a name="golden-ticket"></a>

**Açıklama**

Saldırganlar etki alanı yönetici haklarına sahip tehlikeye [KRBTGT hesabı](https://technet.microsoft.com/library/dn745899(v=ws.11).aspx#Sec_KRBTGT). KRBTGT hesabı kullanarak bunların herhangi bir kaynağa yetkilendirme sağlayan ve rastgele dilediğiniz zaman anahtarı süre sonu Ayarla anahtarı (TGT) sağlayan bir Kerberos bilet oluşturabilirsiniz. Bu sahte TGT "Altın" olarak adlandırılır ve saldırganların ağda kalıcılığı elde etmek sağlar.

Bu algılama, ekibi tarafından verilmesinin anahtarı için kullanılan bir Kerberos anahtarı, izin verilen süre belirtildiği şekilde birden fazla izin olduğunda bir uyarı tetiklenir [kullanıcı anahtarının en fazla ömrü](https://technet.microsoft.com/library/jj852169(v=ws.11).aspx) güvenlik ilkesi.

**Araştırma**

1. (Son birkaç saat içinde) son yapılan herhangi bir değişiklik yoktu **kullanıcı anahtarının en fazla ömrü** Grup İlkesi ayarı? Yanıt Evet ise, ardından **Kapat** (Yanlış pozitif olduğu) uyarı.

2. ATA Gateway, bu uyarı bir sanal makine dahil mi? Evet ise, en son kaydedilen durumdan devam mı? Yanıt Evet ise, ardından **Kapat** bu uyarı.

3. Yukarıdaki soruların yanıtlanması gerekirse, Hayır, bu, kötü amaçlı varsayılır.

**Düzeltme**

Kerberos anahtar verme anahtarı (KRBTGT) parolayı iki kez kılavuzunda göre değiştirmek [KRBTGT hesap parolası sıfırlama betikleri artık müşteriler tarafından kullanılabilir](https://blogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/)kullanarak [KRBTGT hesap parolası/anahtarı sıfırlama Aracı](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51). İki kez KRBTGT sıfırlama tüm Kerberos biletleri bu etki alanında bunu yapmadan önce plan geçersiz kılar.  
Ayrıca, etki alanı yöneticisi haklarına bir altın anahtar oluşturuluyor gerektirdiği için uygulama [Pass the hash önerilerini](http://aka.ms/PtH).


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

1.  Söz konusu bilgisayarın bir etki alanı denetleyicisi mi? Örneğin, çoğaltma olan yeni yükseltilen etki alanı denetleyicisi verir. Yanıt Evet ise, **Kapat** şüpheli etkinlik. 
2.  Söz konusu bilgisayarın Active Directory'den veri çoğaltma olması gerekiyor? Örneğin, Azure AD Connect. Yanıt Evet ise, **Kapat ve dışla** şüpheli etkinlik.
3.  Kaynak bilgisayar veya hesap kendi profili sayfasına gitmek için tıklayın. Ne gibi olağan dışı etkinlikler için arama çoğaltma oluştuğu sırada olduğunu kontrol edin: açan, hangi kaynakların erişilebilir olduğunda. 


**Düzeltme**

Şu izinleri doğrulayın: 

- Dizin Değişikliklerini Çoğaltma   

- Tüm dizin değişikliklerini çoğaltma  

Daha fazla bilgi için [SharePoint Server 2013'te profil eşitleme izinleri verme Active Directory Domain Services](https://technet.microsoft.com/library/hh296982.aspx).
Yararlanabileceğiniz [AD ACL tarayıcı](https://blogs.technet.microsoft.com/pfesweplat/2013/05/13/take-control-over-ad-permissions-and-the-ad-acl-scanner-tool/) veya etki alanında kimin bu izinlere sahip olduğunu belirlemek için bir Windows PowerShell Betiği oluşturabilirsiniz.

## <a name="massive-object-deletion"></a>Büyük çaplı nesne silme

**Açıklama**

Bazı senaryolarda, saldırganlar, yalnızca bilgi çalarak yerine hizmet (DoS) gerçekleştirin. Çok sayıda hesapları silme bir DoS tekniğidir.

Birden fazla %5 tüm hesapların silindiğinde bu algılama, bir uyarı tetiklenir. Algılama Silinmiş nesne kapsayıcısı okuma erişimi gerektirir.  
Silinmiş nesne kapsayıcısı üzerinde salt okuma izinlerini yapılandırma hakkında daha fazla bilgi için bkz: **Silinmiş nesne kapsayıcısı üzerindeki izinleri değiştirme** içinde [izinleri görüntüleme veya ayarlama dizin nesnesi üzerindeki](https://technet.microsoft.com/library/cc816824%28v=ws.10%29.aspx).

**Araştırma**

Silinmiş hesap listesini gözden geçirin ve desen veya bu devasa silme Yasla bir iş neden olup olmadığını anlama.

**Düzeltme**

Active Directory'de hesapları silebilen kullanıcıların izinlerini kaldırın. Daha fazla bilgi için [izinleri görüntüleme veya ayarlama dizin nesnesi üzerindeki](https://technet.microsoft.com/library/cc816824%28v=ws.10%29.aspx).

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

Hesap numaralandırma keşfi bir saldırgan, kullanıcı adlarını veya araçları KrbGuess gibi binlerce etki alanınızdaki kullanıcı adlarını tahmin etme girişiminde bir sözlük kullanır. Saldırgan, Kerberos istekleri için geçerli bir kullanıcı adı, etki alanınızda bulmak için bu adlar kullanarak yapar. Bir tahmin başarıyla bir kullanıcı adı belirler, saldırgan Kerberos hatası alırsa **gerekli ön kimlik doğrulaması** yerine **güvenlik sorumlusu bilinmeyen**. 

Bu algılama, ATA saldırı nereden geldiğini, tahmin girişiminde toplam sayısını ve kaç eşleştirilmiş olan algılayabilir. Bilinmeyen çok sayıda kullanıcı varsa, ATA kuşkulu bir etkinlik algılayacaktır. 

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

Bu algılama, ATA dağıtıldıktan sonra ilk ay içinde hiçbir uyarı tetiklenmesi. Hangi bilgisayarlardan hangi SAM-R sorgularına yapılan öğrenme dönemi ATA profilleri sırasında hem sabit listesi hem de hassas hesapların tek sorgular.

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

Kullanım [SAMRi10 aracı](https://gallery.technet.microsoft.com/SAMRi10-Hardening-Remote-48d94b5b) bu tekniği karşı ortamınızı güçlendirmek için.
Araç, DC için geçerli değilse:
1. Bilgisayar bir güvenlik açığı Tarama Aracı çalışıyor mu?  
2. Belirli sorgulanan kullanıcıları ve grupları saldırı ayrıcalıklı veya yüksek değerli hesapları olup olmadığını araştırın (yani, CEO, CFO, BT yönetimi, vs.).  Bu durumda, diğer uç nokta da faaliyete bakmak ve büyük olasılıkla yatay hareket hedefleri oldukları gibi sorgulanan hesapları, oturum açtığı bilgisayarlar izleyin.

## <a name="reconnaissance-using-dns"></a>DNS kullanarak keşif

**Açıklama**

DNS sunucunuzun tüm bilgisayarlar, IP adresleri ve Hizmetleri, ağınızda bir haritasını içerir. Saldırganlar bu bilgileri kullanarak ağ yapınızın haritasını çıkarır ve saldırının sonraki adımlarında kullanmak üzere uygun bilgisayarları hedef alır.

DNS protokolünde birkaç sorgu türü vardır. ATA, AXFR (aktarım) istek olmayan DNS sunucularından kaynaklanan algılar.

**Araştırma**

1. Kaynak makine (**kaynaklanan...** ) bir DNS sunucusu? Yanıt Evet ise, sonra bunun yanlış pozitif olabilir. Doğrulamak için uyarı için Ayrıntılar sayfasını almak için tıklayın. Tabloda, altında **sorgu**, hangi etki alanlarının sorgulandığını denetleyin. Bu var olan etki alanlarında misiniz? Yanıt Evet ise, ardından **Kapat** şüpheli etkinlik (Yanlış pozitif değer). Ayrıca, UDP bağlantı noktası 53 gelecekteki hatalı pozitif sonuçları engellemek için ATA Gateway ile kaynak bilgisayar arasında açık olduğundan emin olun.
2.  Kaynak makine, bir güvenlik tarayıcısı çalışıyor mu? Yanıt Evet ise, **hariç** varlıkların doğrudan ya da Ata **Kapat ve dışla** veya aracılığıyla **dışlama** sayfa (altında **yapılandırma** – kullanılabilir ATA yöneticileri için).
3.  Yukarıdaki tüm sorulara olduğu sorusunu yanıtlamaya Hayır, kaynak bilgisayarda odaklanarak araştırma tutmak. Kaynak bilgisayarda, profili sayfasına gitmek için tıklayın. İsteğin gibi olağan dışı etkinlikler için arama oluştuğu sırada ne olduğunu kontrol edin: açan, hangi kaynakların erişilebilir olduğunda.


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

## <a name="remote-execution-attempt-detected"></a>Uzaktan yürütme denemesi algılandı

**Açıklama**

Yönetici kimlik bilgilerini tehlikeye veya sıfır gün yararlanma kullanmak saldırganların etki alanı denetleyicinizde uzak komutlar yürütebilir. Bu bilgiler, hizmet (DOS) saldırısı reddi veya başka bir nedenle toplama Kalıcılık, kazanmak için kullanılabilir. PSexec ve WMI uzak bağlantıları ATA algılar.

**Araştırma**

1. Bu yönetim iş istasyonları için de BT ekibi üyelerinde ve hizmet hesapları, etki alanı denetleyicilerinde yönetim görevlerini gerçekleştirmek yaygındır. Bu durum budur ve aynı yönetici veya bilgisayar yapmakta olduğunuz çünkü görev ardından uyarı güncelleştirilir **bastır** uyarı.
2.  Söz konusu bilgisayarın etki alanı denetleyicinizde Bu uzaktan yürütmeyi gerçekleştirme izni?
  - Söz konusu hesabın etki alanı denetleyicinizde Bu uzaktan yürütmeyi gerçekleştirme izni?
  - Her iki sorulara yanıt Evet, ardından olup olmadığını **Kapat** uyarı.
3.  Ya da soruların yanıtlanması gerekirse, Hayır, ardından bunu bir doğru pozitif düşünülmelidir. Bilgisayarınızın ve hesabınızın profilleri kontrol ederek deneme kaynağını bulmaya çalışın. Kaynak bilgisayar veya hesap kendi profili sayfasına gitmek için tıklayın. Ne gibi olağan dışı etkinlikler için arama, bu deneme süresini olduğunu kontrol edin: açan, hangi kaynakların erişilebilir olduğunda.


**Düzeltme**

1. Katman 0 olmayan makinelerden etki alanı denetleyicilerine uzaktan erişimi kısıtlayın.

2. Uygulama [ayrıcalıklı erişim](https://technet.microsoft.com/windows-server-docs/security/securing-privileged-access/securing-privileged-access) yalnızca güçlendirilmiş makinelerin yöneticileri için etki alanı denetleyicilerine bağlanmasına izin vermek için.

## <a name="sensitive-account-credentials-exposed--services-exposing-account-credentials"></a>Gizli hesap kimlik bilgileri ifşa & hesap kimlik bilgilerini açığa çıkaran hizmetler

> [!NOTE]
> Bu şüpheli etkinlik, kullanım dışı bırakıldı ve yalnızca ATA sürümlerde 1.9 görüntülenir. Ata'yı 1.9 ve daha sonra bkz [raporları](reports.md).

**Açıklama**

Bazı hizmetler hesap kimlik bilgilerini düz metin olarak gönderir. Bu durum, hassas hesaplar için bile oluşabilir. Saldırganların ağ trafiğini izleme, catch ve daha sonra bu kimlik bilgilerini kötü amaçlar için yeniden kullanabilirsiniz. Hassas olmayan hesaplar için en az beş farklı hesapları düz metin parolaları aynı kaynak bilgisayardan gönderirseniz uyarının tetiklenmesinden sürece herhangi bir düz metin parolası hassas bir hesap için uyarı tetikler. 

**Araştırma**

Uyarı için Ayrıntılar sayfasını almak için tıklayın. Bkz. hangi hesap ifşa edilmedi. Birçok hesapları varsa, tıklayın **indirme ayrıntıları** bir Excel elektronik tablosunda listesini görüntülemek için.

Genellikle basit LDAP bağlama kullanan bir komut dosyası veya eski uygulama kaynak bilgisayarlarda yoktur.

**Düzeltme**

Kaynak bilgisayarlarda yapılandırmayı doğrulayın ve LDAP basit bağlaması kullanmadığınızdan emin olun. LDAP basit bağlamaları yerine LDAP SALS veya LDAPS kullanabilirsiniz.

## <a name="suspicious-authentication-failures"></a>Şüpheli kimlik doğrulaması hataları

**Açıklama**

Bir deneme yanılma saldırısında, saldırgan doğru parolayı en az bir hesap için bulunana kadar farklı hesaplar için çok sayıda farklı parolaları ile kimlik doğrulaması dener. Bir kez bulundu, bir saldırganın bu hesabı kullanarak oturum açabilir.

Bu algılama, Kerberos veya NTLM kullanarak birçok kimlik doğrulama hataları ortaya çıktığında bir uyarı tetiklenir, bu yatay olarak küçük bir parola ile çok sayıda kullanıcı arasında olabilir; veya dikey olarak büyük ile Parolaları yalnızca bazı kullanıcılar ayarlayın; veya bu iki seçenek herhangi bir birleşimi. Bir uyarı tetiklenebilir önce en az bir hafta dönemdir.

**Araştırma**

1.  Tıklayın **indirme ayrıntıları** bir Excel elektronik tablosundaki tüm bilgileri görüntülemek için. Aşağıdaki bilgiler elde edebilirsiniz: 
  - Saldırıya uğrayan hesaplar listesi
  - Başarılı kimlik doğrulaması ile sona erdi hangi oturum açma girişimlerinde tahmin edilen hesaplar listesi
  - NTLM kullanarak kimlik doğrulama girişimleri gerçekleştirildi varsa, ilgili olay etkinlikleri göreceksiniz. 
  - Kerberos kullanarak kimlik doğrulama girişimleri gerçekleştirildi varsa, ilgili ağ etkinlikleri göreceksiniz.
2.  Kaynak bilgisayarda, profili sayfasına gitmek için tıklayın. Ne gibi olağan dışı etkinlikler için arama, bu deneme süresini olduğunu kontrol edin: açan, hangi kaynakların erişilebilir olduğunda. 
3.  NTLM kullanılarak kimlik doğrulaması gerçekleştirildi ve çoğu zaman, uyarıyı oluşur ve yok yeterli bilgi kaynak makine erişmeye sunucusu hakkında etkinleştirmeniz gereken gördüğünüz **NTLM denetim** üzerinde etki alanı denetleyicileri söz konusu. Bunu yapmak için 8004 olayı kapatın. Kaynak bilgisayar, kullanıcı hesabı hakkında bilgi içeren NTLM kimlik doğrulaması olay budur ve **sunucu** , kaynak makinenin erişmeyi denedi. Hangi sunucu kimlik doğrulama gönderilen bulduktan sonra sunucu kimlik doğrulama işlemi 4624 daha iyi anlama gibi olayları kontrol ederek araştırmanız gerekir. 


**Düzeltme**

[Uzun ve karmaşık parolalar](https://docs.microsoft.com/windows/device-security/security-policy-settings/password-policy) gerekli ilk deneme yanılma saldırılarına karşı güvenlik düzeyini belirtin.

## Şüpheli hizmet oluşturma <a name="suspicious-service-creation"></a>

**Açıklama**

Saldırganlar, ağınızdaki kuşkulu hizmetlerini çalıştırmak çalışır. Bir etki alanı denetleyicisinde şüpheli yeni hizmet oluşturulduğunda ATA bir uyarı başlatır. Bu uyarı olayı 7045 kullanır ve her etki alanı denetleyicisinden bir ATA Gateway veya Lightweight Gateway kapsamında algılandı.

**Araştırma**

1. Söz konusu bilgisayarın bir yönetici iş istasyonunda veya hangi BT ekibi üyelerinde ve hizmet hesapları yönetim görevlerini gerçekleştirmek için bir bilgisayar varsa, bu bir hatalı pozitif sonuç olabilir ve gerekebilir **bastır** uyarı ve ekleyin Dışlama listesine gerekirse.

2. Hizmeti bu bilgisayarda tanıyacak bir şey mi?

 - Olan **hesabı** söz konusu bu hizmet yüklemesine izin?

 - Her iki soruların yanıtlanması gerekirse *Evet*, ardından **Kapat** uyarı veya dışlama listesine ekleyin.

3. Ya da soruların yanıtlanması gerekirse *hiçbir*, sonra bunu bir doğru pozitif düşünülmelidir.

**Düzeltme**

- Daha az ayrıcalıklı erişimi yalnızca belirli kullanıcılara yeni hizmetleri oluşturma hakkı izin vermek için etki alanı makinelerde uygulayın.



## <a name="suspicion-of-identity-theft-based-on-abnormal-behavior"></a>Anormal davranışa bağlı kimlik hırsızlığı şüphesi

**Açıklama**

ATA, bir kayan üç hafta boyunca kullanıcılar, bilgisayarlar ve kaynaklar için varlık davranışını öğrenir. Davranış modeli şu etkinlikleri temel alan: makineler varlıkları için oturum, varlık istenen kaynaklara erişim için ve bu işlemleri yerde geçen süre. ATA, makine öğrenimi algoritması üzerinde temel varlığın davranışını bir sapma olduğunda bir uyarı gönderir. 

**Araştırma**

1. Söz konusu kullanıcının bu işlemleri gerçekleştirmeyi gerekiyor?

2. Aşağıdaki durumlarda olası hatalı pozitif sonuç olarak göz önünde bulundurun: tatil, aşırı erişim, vergi (örneğin bir depo içinde Yardım Masası destek belirli gün veya hafta) bir parçası olarak gerçekleştireceğiniz BT personeli Uzak Masaüstü uygulamaları. döndürüldüğü bir kullanıcı + ise, **Kapat ve dışla** kullanıcı artık uyarı algılama bir parçası olması


**Düzeltme**

Ne gerçekleşmesi bu anormal davranışın nedeni bağlı olarak, farklı eylemler gerçekleştirilmelidir. Bu ağ tarama nedeniyle ise (onaylanmadığı sürece) gibi bu durumun oluştuğu makine ağdan engellenmelidir.

## <a name="unusual-protocol-implementation"></a>Olağan dışı protokol uygulanması


**Açıklama**

Saldırganlar, standart olmayan şekilde çeşitli protokolleri (SMB, Kerberos, NTLM) uygulayan araçlarını kullanın. Ağ trafiği bu tür uyarılar olmadan Windows tarafından kabul edilir, ancak ATA olası kötü amaçlı tanıyabilirsiniz. Gelişmiş fidye yazılımı tarafından Örneğin, WannaCry kullanılan açıklara yanı sıra, Kerberos'taki-geçiş karma gibi teknikler simulatorda davranıştır.

**Araştırma**

Alışılmadık şüpheli etkinlik zaman satırından – Protokolü tanımlayın, şüpheli etkinlik için Ayrıntılar sayfasını almak için tıklayın; protokol oku görünür: Kerberos veya NTLM.

- **Kerberos**: büyük olasılıkla bir adlı istemciden Overpass--Hash saldırısı gerçekleştiren Mimikatz kullanılmış gibi bir deşifre etme aracı, bu genellikle tetiklenir. Kaynak bilgisayar Kerberos RFC uygun olmayan kendi Kerberos yığınını uygulayan bir uygulama çalışıp çalışmadığını denetleyin. Böyle, bunu bir zararsız gerçek pozitiftir ve yapabilecekleriniz **Kapat** uyarı. Uyarıyı tetikleyen tutar ve durum hala geçerlidir, yapabilecekleriniz **bastır** uyarı.

- **NTLM**: WannaCry veya Metasploit Medusa ve Hydra gibi araçları olabilir.  

Bunun bir WannaCry saldırısı olup olmadığını belirlemek için aşağıdaki adımları gerçekleştirin:

1. Kaynak bilgisayarda bir saldırı aracı Metasploit, Medusa veya Hydra gibi çalışıp çalışmadığını denetleyin.

2. Hiçbir saldırı araçlarının bulunursa, kaynak bilgisayarın kendi NTLM veya SMB yığınını uygulayan bir uygulama çalışıp çalışmadığını denetleyin.

3. Aksi durumda sonra bu WannaCry tarafından örneğin bir WannaCry tarayıcı betiği çalıştırarak neden olup olmadığını denetleyin. [bu tarayıcı](https://github.com/apkjet/TrustlookWannaCryToolkit/tree/master/scanner) ' teki şüpheli etkinliklerle ilgili kaynak bilgisayara karşı. Tarayıcı, makine makine düzeltme eki uygulama ve kötü amaçlı yazılımı kaldırmak ve ağdan engelleme virüs bulaşmış veya güvenlik açığı, iş olarak bulursa.

4. Betik makine virüs bulaşmış veya güvenlik açığı, ardından yine de etkilenmiş ancak SMBv1 devre dışı olabilir veya makine yama olduğunu bulamadıysanız, Tarama Aracı etkiler.

**Düzeltme**

Özellikle güvenlik güncelleştirmelerini uygulama tüm makinelerinizi, düzeltme eki.

1. [SMBv1 devre dışı bırak](https://blogs.technet.microsoft.com/filecab/2016/09/16/stop-using-smb1/)

2. [WannaCry Kaldır](https://support.microsoft.com/help/890830/remove-specific-prevalent-malware-with-windows-malicious-software-remo)

3. Kullanıcı olmayan yeniden başlatıldı veya bilgisayar oturumunu açık varsa WanaKiwi ancak bazı ransom yazılım kullanımına veri şifresini çözebilir. Daha fazla bilgi için [Cry fidye yazılımı için istediğiniz](https://answers.microsoft.com/en-us/windows/forum/windows_10-security/wanna-cry-ransomware/5afdb045-8f36-4f55-a992-53398d21ed07?auth=1)


>[!NOTE]
> Kuşkulu bir etkinlik devre dışı bırakmak için desteğe başvurun.

## <a name="related-videos"></a>İlgili videolar
- [Güvenlik topluluğuna katılmak](https://channel9.msdn.com/Shows/Microsoft-Security/Join-the-Security-Community)


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA şüpheli etkinlik playbook](http://aka.ms/ataplaybook)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
