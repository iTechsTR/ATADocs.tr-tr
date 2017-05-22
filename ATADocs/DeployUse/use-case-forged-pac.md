---
title: "Sahte PAC saldırılarını araştırma | Microsoft Docs"
description: "Bu makalede Sahte PAC saldırıları açıklanır ve ağınızda bu tehdit algılandığında uygulanacak araştırma yönergeleri sağlanır."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/16/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: f3db435e-9553-40a2-a2ad-278fad4f0ef5
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 437f387815fbbfbe261a192764a428e0d285ef32
ms.sourcegitcommit: 97aced94f47cf3c1b473d25b77d10a300c3f517e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2017
---
*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*

# <a name="investigating-forged-pac-attacks"></a>Sahte PAC saldırılarını araştırma

Microsoft, güvenlik algılama becerilerini ve güvenlik analistlerine neredeyse gerçek zamanlı, eyleme dönüştürülebilir bilgiler sağlama özelliğini sürekli geliştirir. Microsoft Advanced Threat Analytics (ATA), bu değişikliği sağlamaya yardımcı olur. ATA, ağınızda Sahte PAC şüphesi taşıyan bir etkinlik algılar ve bu konuda sizi uyarırsa, bu makale söz konusu etkinliği anlamanıza ve araştırmanıza yardımcı olur.

## <a name="what-is-a-privileged-access-certificate-pac"></a>Ayrıcalıklı Erişim Sertifikası (PAC) nedir?

Ayrıcalık Öznitelik Sertifikası (PAC); grup üyelikleri, güvenlik tanımlayıcıları ve kullanıcı profili bilgileri gibi yetkilendirme bilgilerini içeren Kerberos Anahtarındaki Veri Yapısıdır. Bu, bir Active Directory etki alanında Etki Alanı Denetleyicisi (DC) tarafından sağlanan yetkilendirme verilerinin diğer üye sunuculara ve iş istasyonlarına kimlik doğrulama ve yetkilendirme amacıyla geçirilmesini sağlar. Üyelik bilgilerine ek olarak PAC, ek kimlik bilgilerini, profil ve ilke bilgilerini ve destekleyici güvenlik meta verilerini içerir. 

PAC Veri Yapısı, kaynaklara erişimi denetleyen yetkilendirme bilgilerini taşımak için kimlik doğrulama protokolleri (kimlikleri doğrulayan protokoller) tarafından kullanılır.

### <a name="pac-validation"></a>PAC doğrulama

PAC doğrulama, özellikle kullanıcının kimliğine bürünülen uygulamalarda, bir saldırganın bir sistem veya kaynaklarına ortadaki adam saldırısıyla yetkisiz erişim elde etmesini önlemeye yönelik bir güvenlik özelliğidir. Kimliğe bürünme, kaynaklara erişmek ve görevleri yürütmek için yükseltilmiş ayrıcalıklar verilen bir hizmet hesabı gibi güvenilen bir kimlik içerir. PAC doğrulama, kimliğe bürünme etkinliğinin gerçekleştiği Kerberos kimlik doğrulaması ayarlarında daha güvenli bir yetkilendirme ortamı sağlar. [PAC doğrulama](https://blogs.msdn.microsoft.com/openspecification/2009/04/24/understanding-microsoft-kerberos-pac-validation/), bir kullanıcının yetkilendirme verilerini Kerberos anahtarında verildiği gibi eksiksiz olarak sunmasını ve anahtar ayrıcalıklarının değiştirilmemesini sağlar.

PAC doğrulaması yapılırken sunucu, PAC imza türü ve uzunluğunu içeren bir istek iletisi kodlar ve DC'ye iletir. DC, istek kodunu çözer ve sunucu sağlama toplamını ve KDC sağlama toplamı değerlerini ayıklar. Sağlama toplamı doğrulama işlemi başarılı olursa, DC sunucuya bir başarı kodu döndürür. Başarısız bir dönüş kodu, PAC’ın değiştirilmiş olduğunu gösterir. 

Kerberos PAC içeriği iki kez imzalanır: 
- Kötü amaçlı sunucu tarafı hizmetlerin yetkilendirme verilerini değiştirmesini engellemek için ilk imzalama işlemi KDC’nin ana anahtarı ile yapılır
- İkinci imzalama işlemi ise bir kullanıcının PAC içeriğinde değişiklik yapmasını ve kendi yetkilendirme verilerini eklemesini engellemek için hedef kaynak sunucunun ana anahtarı ile yapılır

### <a name="pac-vulnerability"></a>PAC güvenlik açığı
Bir saldırganın geçerli bir Kerberos Anahtarındaki PAC alanında değişiklik yaparak kendisine ek ayrıcalıklar sağlamasını mümkün kılabilecek Kerberos KDC güvenlik açıkları, [MS14 068](https://technet.microsoft.com/library/security/MS14-068.aspx) ve [MS11-013](https://technet.microsoft.com/library/security/ms11-013.aspx) güvenlik bültenlerinde ele alınmıştır.

## <a name="forged-pac-attack"></a>Sahte PAC saldırısı

Sahte PAC saldırısı, bir saldırganın bu güvenlik açıklarından faydalanarak Active Directory Ormanınızda veya Etki Alanınızda kendi ayrıcalıklarını yükseltme girişimidir. Bu saldırıyı gerçekleştirmek için bir saldırganın şunlara sahip olması gerekir:
-    Bir etki alanı kullanıcısının kimlik bilgileri.
-    Güvenliği tehlikede olan etki alanı kimlik bilgilerinin kimlik doğrulamasını yapmak için kullanılabilecek Etki Alanı Denetleyicisine ağ bağlantısı.
-    Doğru araçlar. Python Kerberos Exploitation Kit (PyKEK) sahte PAC'ler oluşturan tanınmış bir araçtır.

Saldırgan gerekli kimlik bilgilerine ve bağlantıya sahipse, mevcut bir Kerberos kullanıcı oturum açma belirtecinin (TGT) Ayrıcalıklı Erişim Sertifikası (PAC) üzerinde değişiklik yapabilir veya bunun sahtesini oluşturabilir. Saldırgan, grup üyeliği talebini daha yüksek ayrıcalıklı bir grup (örneğin "Etki Alanı Yöneticileri" veya "Kuruluş Yöneticileri" gibi) içerecek şekilde değiştirir. Daha sonra saldırgan, Kerberos Anahtarı içindeki değiştirilmiş PAC’yi ekler. Ardından bu Kerberos Anahtarı, yama uygulanmamış bir Etki Alanı Denetleyicisinden (DC) Hizmet anahtarı talep etmek için kullanılır ve saldırgana etki alanında yükseltilmiş ayrıcalıklar ve gerçekleştirmemeleri gereken eylemlere yetki sağlar. Bir saldırgan kaynak erişim belirteçleri (TGS) talep ederek etki alanındaki herhangi bir kaynağa erişim elde etmek için değiştirilmiş kullanıcı oturum açma belirteci (TGT) sunabilir. Bu, bir saldırganın Active Directory'deki herhangi bir kullanıcı için yetki verisini (PAC) taklit ederek ağ üzerindeki erişimi sınırlayan tüm yapılandırılmış kaynak ACL'lerini atlayabileceği anlamına gelir.

## <a name="discovering-the-attack"></a>Saldırıyı bulma
Saldırgan, kendi ayrıcalıklarını yükseltmeyi denediğinde, ATA bunu algılar ve yüksek öneme sahip bir uyarı olarak işaretler.

![Sahte PAC şüpheli etkinliği](./media/forged-pac.png)

ATA, sahte PAC başarılı olsa da olmasa da şüpheli etkinlik uyarısını gösterir. Başarısız saldırılar saldırganın ortamınızda bulunduğunu gösterdiğinden, hem başarılı hem de başarısız uyarıların araştırılması gerekir.

## <a name="investigating"></a>Araştırma
ATA’da Sahte PAC uyarısını aldıktan sonra, saldırının etkilerini hafifletmek için yapılması gerekenleri belirlemeniz gerekir. Bunu yapmak için önce uyarıyı aşağıdakilerden biri olarak sınıflandırmanız gerekir: 
-    Gerçek pozitif sonuç: ATA tarafından algılanan kötü amaçlı bir eylem
-    Hatalı pozitif sonuç: Yanlış bir uyarı – Sahte PAC gerçekten meydana gelmemiştir (Bu, ATA’nın bir etkinliği yanlışlıkla Sahte PAC olarak belirlemesidir)
-    Zararsız gerçek pozitif sonuç: Sızma testi örneğindeki gibi ATA tarafından algılanan gerçek, ancak zararsız bir eylem

Aşağıdaki grafik, uygulamanız gereken adımların belirlenmesine yardımcı olur:

![Sahte PAC diyagramı](./media/forged-pac-diagram.png)

1. Sahte yetkilendirme denemesinin gerçekleşip gerçekleşmediğini veya başarılı olup olmadığını görmek için öncelikle ATA saldırı zaman çizelgesindeki uyarıyı denetleyin (gerçekleşen saldırı denemeleri aynı zamanda başarısız saldırılardır). Hem başarılı hem de başarısız denemeler Gerçek Pozitif olarak sonuçlanabilir, ancak ortamdaki önem dereceleri farklıdır.
 
 ![Sahte PAC şüpheli etkinliği](./media/forged-pac-sa.png)


2.    Algılanan Sahte PAC saldırısı başarılı olduysa:
    -    Uyarının tetiklendiği DC’ye yama düzgün şekilde uygulandıysa, hatalı pozitiftir. Bu durumda, uyarıyı yok sayın ve ATA ekibinin ATAEval@microsoft.com adresine durumu bildiren bir e-posta gönderin. Böylece algılama işlemlerimizi sürekli olarak geliştirebiliriz. 
    -    Uyarıdaki DC’ye yama düzgün şekilde uygulanmadıysa:
        -    Uyarıda listelenen hizmet kendi yetkilendirme mekanizmasına sahip değilse, bu gerçek pozitiftir ve kuruluşunuzun Olay Yanıt (IR) işlemini çalıştırmanız gerekir. 
        -    Uyarıda listelenen hizmetin yetkilendirme verileri isteyen bir iç yetkilendirme mekanizması varsa, hatalı bir şekilde Sahte PAC olarak tanımlanmış olabilir. 

3.    Algılanan saldırı başarısız olduysa:
    -    İşletim sistemi veya uygulamanın PAC’de değişiklik yaptığı biliniyorsa bu büyük olasılıkla bir zararsız gerçek pozitiftir ve bu davranışı düzeltmek için uygulama veya işletim sistemi sahibi ile birlikte çalışmanız gerekir.

    -    İşletim sistemi veya uygulamanın PAC’de değişiklik yaptığı bilinen bir durum değilse: 

        -    Listelenen hizmet kendi yetkilendirme hizmetine sahip değilse, bu gerçek pozitiftir ve kuruluşunuzun Olay Yanıt (IR) işlemini çalıştırmanız gerekir. Saldırgan etki alanındaki ayrıcalıklarını yükseltmekte başarılı olamadıysa bile, ağınızda bir saldırgan olduğunu varsayabilirsiniz ve ayrıcalıklarını yükseltmek için başka bilinen gelişmiş kalıcı saldırılar denemeden önce onları mümkün olan en kısa sürede bulmanız gerekir. 
        -    Uyarıda listelenen hizmet, yetkilendirme verileri isteyen kendi yetkilendirme mekanizmasına sahipse, hatalı bir şekilde Sahte PAC olarak tanımlanmış olabilir.


Microsoft, bir saldırganın ağınızda dağıtılmış kalıcı yöntemleri olup olmadığını belirlemek için Microsoft Hesabı Ekibiniz aracılığıyla erişilebilen, profesyonel bir Olay Yanıt ve Kurtarma ekibi kullanmanızı önerir. Bu, kötü amaçlı yazılımların yanı sıra çalınan kimlik bilgileri ve Altın Anahtar gibi kimlik ihlalleri kullanılarak yapılabilir.


## <a name="see-also"></a>Ayrıca bkz.
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATA yapılandırmasında değişiklik yapma](modifying-ata-configuration.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
