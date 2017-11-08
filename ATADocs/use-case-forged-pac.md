---
title: "Sahte yetkilendirme verileri kullanan Ayrıcalık yükseltme saldırılarını araştırma | Microsoft Docs"
description: "Bu makalede sahte yetkilendirme verileri kullanan Ayrıcalık yükseltme saldırıları açıklanmakta ve ağınızda bu tehdit algılandığında izlenecek araştırma yönergeleri sağlanmaktadır."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/7/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: f3db435e-9553-40a2-a2ad-278fad4f0ef5
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 1820687d1340dfbef703129e5fad7d7a63cfd632
ms.sourcegitcommit: 4d2ac5b02c682840703edb0661be09055d57d728
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*

# <a name="investigating-privilege-escalation-using-forged-authorization-data-attacks"></a>Sahte yetkilendirme verileri kullanan Ayrıcalık yükseltme saldırılarını araştırma

Microsoft, güvenlik algılama becerilerini ve güvenlik analistlerine neredeyse gerçek zamanlı, eyleme dönüştürülebilir bilgiler sağlama özelliğini sürekli geliştirir. Microsoft Advanced Threat Analytics (ATA), bu değişikliği sağlamaya yardımcı olur. ATA kullanarak bir ayrıcalık yükseltme sahte yetkilendirme verileri, ağınızdaki kuşkulu bir etkinlik ve bu makalede, uyarıları yardımcı olur algılarsa anlamak ve onu araştırın.

## <a name="what-is-a-privileged-attribute-certificate-pac"></a>Ayrıcalıklı Öznitelik Sertifikası (PAC) nedir?

Ayrıcalık öznitelik sertifikası (PAC), grup üyelikleri, güvenlik tanımlayıcılarını ve kullanıcı profili bilgileri de dahil olmak üzere yetkilendirme bilgilerini tutan Kerberos bileti veri yapısıdır. Bu, bir Active Directory etki alanında Etki Alanı Denetleyicisi (DC) tarafından sağlanan yetkilendirme verilerinin diğer üye sunuculara ve iş istasyonlarına kimlik doğrulama ve yetkilendirme amacıyla geçirilmesini sağlar. Üyelik bilgilerine ek olarak PAC, ek kimlik bilgilerini, profil ve ilke bilgilerini ve destekleyici güvenlik meta verilerini içerir. 

PAC Veri Yapısı, kaynaklara erişimi denetleyen yetkilendirme bilgilerini taşımak için kimlik doğrulama protokolleri (kimlikleri doğrulayan protokoller) tarafından kullanılır.

### <a name="pac-validation"></a>PAC doğrulama

PAC doğrulama, özellikle kullanıcının kimliğine bürünülen uygulamalarda, bir saldırganın bir sistem veya kaynaklarına ortadaki adam saldırısıyla yetkisiz erişim elde etmesini önlemeye yönelik bir güvenlik özelliğidir. Kimliğe bürünme, kaynaklara erişmek ve görevleri yürütmek için yükseltilmiş ayrıcalıklar verilen bir hizmet hesabı gibi güvenilen bir kimlik içerir. PAC doğrulama, kimliğe bürünme etkinliğinin gerçekleştiği Kerberos kimlik doğrulaması ayarlarında daha güvenli bir yetkilendirme ortamı sağlar. [PAC doğrulama](https://blogs.msdn.microsoft.com/openspecification/2009/04/24/understanding-microsoft-kerberos-pac-validation/), bir kullanıcının yetkilendirme verilerini Kerberos anahtarında verildiği gibi eksiksiz olarak sunmasını ve anahtar ayrıcalıklarının değiştirilmemesini sağlar.

PAC doğrulaması yapılırken sunucu, PAC imza türü ve uzunluğunu içeren bir istek iletisi kodlar ve DC'ye iletir. DC, istek kodunu çözer ve sunucu sağlama toplamını ve KDC sağlama toplamı değerlerini ayıklar. Sağlama toplamı doğrulama işlemi başarılı olursa, DC sunucuya bir başarı kodu döndürür. Başarısız bir dönüş kodu, PAC’ın değiştirilmiş olduğunu gösterir. 

Kerberos PAC içeriği iki kez imzalanır: 
- Kötü amaçlı sunucu tarafı hizmetlerin yetkilendirme verilerini değiştirmesini engellemek için ilk imzalama işlemi KDC’nin ana anahtarı ile yapılır
- İkinci imzalama işlemi ise bir kullanıcının PAC içeriğinde değişiklik yapmasını ve kendi yetkilendirme verilerini eklemesini engellemek için hedef kaynak sunucunun ana anahtarı ile yapılır

### <a name="pac-vulnerability"></a>PAC güvenlik açığı
Bir saldırganın geçerli bir Kerberos Anahtarındaki PAC alanında değişiklik yaparak kendisine ek ayrıcalıklar sağlamasını mümkün kılabilecek Kerberos KDC güvenlik açıkları, [MS14 068](https://technet.microsoft.com/library/security/MS14-068.aspx) ve [MS11-013](https://technet.microsoft.com/library/security/ms11-013.aspx) güvenlik bültenlerinde ele alınmıştır.

## <a name="privilege-escalation-using-forged-authorization-data-attack"></a>Sahte yetkilendirme verileri kullanan Ayrıcalık yükseltme saldırısı

Sahte yetkilendirme verileri kullanan Ayrıcalık yükseltme saldırısı, bir saldırganın PAC güvenlik açıklarından faydalanarak Active Directory Ormanınızda veya Etki Alanınızda kendi ayrıcalıklarını yükseltme denemesidir. Bu saldırıyı gerçekleştirmek için bir saldırganın şunlara sahip olması gerekir:
-   Bir etki alanı kullanıcısının kimlik bilgileri.
-   Güvenliği tehlikede olan etki alanı kimlik bilgilerinin kimlik doğrulamasını yapmak için kullanılabilecek Etki Alanı Denetleyicisine ağ bağlantısı.
-   Doğru araçlar. Python Kerberos İstismarı (PyKEK) PACs forges bilinen bir araç setidir.

Saldırgan gerekli kimlik bilgilerine ve bağlantıya sahipse mevcut bir Kerberos kullanıcı oturum açma belirtecinin (TGT) Ayrıcalıklı Öznitelik Sertifikası (PAC) üzerinde değişiklik yapabilir veya sahte bir sertifika oluşturabilir. Saldırgan, grup üyeliği talebini daha yüksek ayrıcalıklı bir grup (örneğin "Etki Alanı Yöneticileri" veya "Kuruluş Yöneticileri" gibi) içerecek şekilde değiştirir. Daha sonra saldırgan, Kerberos Anahtarı içindeki değiştirilmiş PAC’yi ekler. Ardından bu Kerberos Anahtarı, yama uygulanmamış bir Etki Alanı Denetleyicisinden (DC) Hizmet anahtarı talep etmek için kullanılır ve saldırgana etki alanında yükseltilmiş ayrıcalıklar ve gerçekleştirmemeleri gereken eylemlere yetki sağlar. Bir saldırgan kaynak erişim belirteçleri (TGS) talep ederek etki alanındaki herhangi bir kaynağa erişim elde etmek için değiştirilmiş kullanıcı oturum açma belirteci (TGT) sunabilir. Bir saldırgan atlayabilir Bunun anlamı tüm kaynak yetkilendirme verilerinin (PAC) Active Directory'de herhangi bir kullanıcı için kimlik sahtekarlığı ağ erişimini sınırlamak ACL'ler yapılandırılmış.

## <a name="discovering-the-attack"></a>Saldırıyı bulma
Saldırgan ayrıcalıklarını yükseltme girişiminde bulunduğunda, ATA algıladığı ve bir yüksek öneme sahip uyarı olarak işaretleyin.

![Sahte PAC şüpheli etkinliği](./media/forged-pac.png)

Ayrıcalık yükseltme kullanarak sahte olup olmadığını ATA şüpheli etkinlik uyarısı yetkilendirme verilerinin başarılı veya başarısız olduysa gösterir. Başarısız saldırılar saldırganın ortamınızda bulunduğunu gösterdiğinden, hem başarılı hem de başarısız uyarıların araştırılması gerekir.

## <a name="investigating"></a>Araştırma
ATA’da sahte yetkilendirme verileri kullanan Ayrıcalık yükseltme saldırısı uyarısını aldıktan sonra, saldırının etkilerini hafifletmek için yapılması gerekenleri belirlemeniz gerekir. Bunu yapmak için ilk uyarı aşağıdaki uyarı türlerinden biri olarak sınıflandırmak gerekir: 
-   Gerçek pozitif sonuç: ATA tarafından algılanan kötü amaçlı bir eylem
-   Hatalı pozitif sonuç: Yanlış bir uyarıdır – sahte yetkilendirme verileri kullanan Ayrıcalık yükseltme saldırısı aslında gerçekleşmemiştir (bu, ATA’nın sahte yetkilendirme verileri kullanan Ayrıcalık yükseltme saldırısı zannettiği bir olaydır)
-   Zararsız gerçek pozitif sonuç: Sızma testi örneğindeki gibi ATA tarafından algılanan gerçek, ancak zararsız bir eylem

Aşağıdaki grafik, uygulamanız gereken adımların belirlenmesine yardımcı olur:

![Sahte PAC diyagramı](./media/forged-pac-diagram.png)

1. Sahte yetkilendirme denemesinin gerçekleşip gerçekleşmediğini veya başarılı olup olmadığını görmek için öncelikle ATA saldırı zaman çizelgesindeki uyarıyı denetleyin (gerçekleşen saldırı denemeleri aynı zamanda başarısız saldırılardır). Hem başarılı hem de başarısız denemeler Gerçek Pozitif olarak sonuçlanabilir, ancak ortamdaki önem dereceleri farklıdır.
 
 ![Sahte PAC şüpheli etkinliği](./media/forged-pac-sa.png)


2.  Algılanan sahte yetkilendirme verileri kullanan Ayrıcalık yükseltme saldırısı başarılı olduysa:
    -   Uyarının tetiklendiği DC’ye yama düzgün şekilde uygulandıysa, hatalı pozitiftir. Bu durumda, uyarıyı yok sayın ve gerekir ATA ekibi bildiren bir e-posta Gönder ATAEval@microsoft.com ATA, algılama sürekli olarak artırabilir şekilde. 
    -   Uyarıdaki DC’ye yama düzgün şekilde uygulanmadıysa:
        -   Uyarıda listelenen hizmet kendi yetkilendirme mekanizmasına sahip değilse, bu gerçek pozitiftir ve kuruluşunuzun Olay Yanıt (IR) işlemini çalıştırmanız gerekir. 
        -   Uyarıda listelenen hizmetin yetkilendirme verileri isteyen bir dahili yetkilendirme mekanizması varsa hatalı bir şekilde sahte yetkilendirme verileri kullanan Ayrıcalık yükseltme saldırısı olarak tanımlanmış olabilir. 

3.  Algılanan saldırı başarısız olduysa:
    -   İşletim sistemi veya uygulamanın PAC’de değişiklik yaptığı biliniyorsa bu büyük olasılıkla bir zararsız gerçek pozitiftir ve bu davranışı düzeltmek için uygulama veya işletim sistemi sahibi ile birlikte çalışmanız gerekir.

    -   İşletim sistemi veya uygulamanın PAC’de değişiklik yaptığı bilinen bir durum değilse: 

        -   Listelenen hizmet kendi yetkilendirme hizmetine sahip değilse, bu gerçek pozitiftir ve kuruluşunuzun Olay Yanıt (IR) işlemini çalıştırmanız gerekir. Saldırgan, kendi etki alanındaki ayrıcalıklarını içinde başarısızdı olsa da, ağınızdaki bir saldırganın yoktur ve diğer yükseltmesine Gelişmiş kalıcı saldırıları bilinen çalışmadan önce bunları mümkün olan en kısa sürede bulmak istediğiniz varsayabilirsiniz kendi ayrıcalıklar. 
        -   Uyarıda listelenen hizmetin yetkilendirme verileri isteyen kendi yetkilendirme mekanizması varsa hatalı bir şekilde sahte yetkilendirme verileri kullanan Ayrıcalık yükseltme saldırısı olarak tanımlanmış olabilir.

## <a name="post-investigation"></a>Araştırma sonrası
Microsoft, bir saldırganın ağınızda dağıtılmış kalıcı yöntemleri olup olmadığını belirlemek için Microsoft Hesabı Ekibiniz aracılığıyla erişilebilen, profesyonel bir Olay Yanıt ve Kurtarma ekibi kullanmanızı önerir.


## <a name="mitigation"></a>Risk azaltma

Kerberos KDC’deki güvenlik açıklarıyla ilgilenen [MS14-068](https://technet.microsoft.com/library/security/MS14-068.aspx) ve [MS11-013](https://technet.microsoft.com/library/security/ms11-013.aspx) güvenlik bültenlerini uygulayın. 


## <a name="see-also"></a>Ayrıca bkz:
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
