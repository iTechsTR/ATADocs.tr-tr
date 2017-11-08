---
title: "DNS kullanarak keşfi araştırma | Microsoft Docs"
description: "Bu makalede, DNS kullanarak yapılan keşif açıklanmakta ve ATA tarafından bu tehdit algılandığında izlenecek araştırma yönergeleri sağlanmaktadır."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/7/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1d186a96-ef70-4787-aa64-c03d1db94ce0
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 5ec554b303a19a6e7b12cd788755604f1aaf43db
ms.sourcegitcommit: 4d2ac5b02c682840703edb0661be09055d57d728
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*

# <a name="investigating-reconnaissance-using-dns"></a>DNS kullanarak keşfi araştırma

ATA, ağınızda bir **DNS kullanarak keşif** algılar ve sizi uyarırsa uyarıyı araştırmanıza ve sorunu nasıl düzelteceğinizi anlamanıza yardımcı olması için bu makaleyi okuyun.

## <a name="what-is-reconnaissance-using-dns"></a>DNS kullanarak keşif nedir?

**DNS kullanarak keşif** uyarısı, iç ağınızda keşif yapmak amacıyla olağan dışı bir konaktan şüpheli Etki Alanı Adı Sistemi (DNS) sorguları yapıldığına işaret eder.

Etki Alanı Adı Sistemi (DNS), hiyerarşik ve dağıtılmış bir veritabanı şeklinde bir hizmettir ve konak adları ile etki alanı adlarının çözümlenmesini sağlar. Bir DNS veritabanında bulunan adlar, etki alanı ad alanı olarak isimlendirilen bir hiyerarşik ağaç yapısı oluşturur.
Bir saldırgan için DNS’niz, iç ağ haritasını oluşturmak adına değerli bilgiler içerir, bu bilgiler arasında tüm sunucuların bir listesi ve genellikle bunların IP adresleriyle eşlenen tüm istemciler de bulunur. Ayrıca, çünkü genellikle belirli ağ ortamında açıklayıcı ana bilgisayar adlarını listeler bu bilgiler değeri olur. Bu bilgileri elde eden bir saldırgan, saldırı esnasında ilgili varlıklara odaklanarak işini kolaylaştırabilir. [Nmap](https://nmap.org/) ve [Fierce](https://github.com/mschwager/fierce) gibi araçlar ile [Nslookup](https://technet.microsoft.com/library/cc725991(v=ws.11).aspx) gibi yerleşik araçlar, DNS keşfi kullanarak konak keşfine olanak sağlar.
Bir iç konağın DNS sorgularını kullanarak keşfin algılanması ciddi bir sorundur ve mevcut konak güvenliğinin tehlikeye atılması, daha geniş çaplı bir ağ güvenlik sorunu veya içeriden bir tehdit olasılığına işaret eder.

## <a name="dns-query-types"></a>DNS sorgu türleri

DNS protokolünde birkaç sorgu türü vardır. ATA, AXFR (Aktarım) isteklerini algılar ve bunlar ortaya çıktığında bir uyarı gönderir. Bu tür bir sorgu yalnızca DNS sunucularından gelmelidir.

## <a name="discovering-the-attack"></a>Saldırıyı bulma

Bir saldırgan, DNS kullanarak keşif gerçekleştirmeyi planladığında ATA bunu algılar ve orta derece önemli olarak işaretler.

![ATA, DNS keşfini algılar](./media/dns-recon.png)
 
ATA, kaynak makinenin adını ve gerçekleştirilen asıl DNS sorgusu hakkında ayrıntıları görüntüler. Örneğin, aynı konaktan yapılan birden çok deneme olabilir.

## <a name="investigating"></a>Araştırma

DNS kullanarak keşfi araştırmak için öncelikle sorguların nedenini belirlemeniz gerekir. Bunlar aşağıdaki kategorilerden biriyle tanımlanabilir: 
-   Doğru pozitif sonuçlar – Ağınızda bir saldırgan veya kötü amaçlı bir yazılım var. Bu, ağ çevresini ihlal eden bir saldırgan veya içeriden bir tehdit olabilir.
-   Zararsız doğru pozitif sonuçlar – Bunlar sızma testi, kırmızı ekip etkinliği, güvenlik tarayıcıları, yeni nesil güvenlik duvarı veya tasdikli etkinlikler gerçekleştiren BT yöneticileri tarafından tetiklenen uyarılar olabilir.
-   Hatalı pozitif sonuçlar: Yanlış yapılandırmadan kaynaklanan uyarılar alabilirsiniz. Örneğin, ATA Gateway ile DNS sunucunuz arasında UDP bağlantı noktası 53 engellendiğinde (veya başka bir ağ sorunu oluştuğunda).

Aşağıdaki grafik, uygulamanız gereken araştırma adımlarının belirlenmesine yardımcı olur:

![ATA ile DNS keşfini çözme](./media/dns-recon-diagram.png)
 
1.  İlk adım aşağıdaki ekran görüntüsünde gösterildiği gibi uyarı kaynaklandığı makine belirlemektir:
 
    ![ATA’da DNS keşfi şüpheli etkinliğini inceleyin](./media/dns-recon.png)
2.  Makinenin ne olduğunu belirleyin. İş istasyonu, sunucu, yönetici iş istasyonu, sızma testi istasyonu vb. mi?
3.  Bilgisayar bir DNS sunucusuysa ve bölgenin ikincil bir kopyasını isteme hakkı varsa o halde bu bir hatalı pozitif sonuçtur. Hatalı pozitif sonuç bulduğunuzda bu makine için aynı uyarıyı tekrar almamak adına **Dışla** seçeneğini kullanın.
4. ATA Gateway ve DNS sunucunuz arasında UDP bağlantı noktası 53’ün açık olduğundan emin olun.
4.  Makine, yönetici işleri veya sızma testi için kullanılıyorsa bu zararsız bir doğru pozitif sonuçtur ve söz konusu makine özel durum olarak yapılandırılabilir.
5.  Sızma testi için kullanılmıyorsa makinenin bir güvenlik tarayıcısı veya yeni nesil güvenlik duvarı çalıştırıp çalıştırmadığını kontrol edin çünkü bunlar, AXFR türünde DNS istekleri yapabilir.
6.  Son olarak, bu ölçütlerin hiçbiri uymadıysa makine bir güvenlik tehdidi altında olabilir ve büyük çaplı bir araştırmaya tabi tutulması gerekir. 
7.  Sorgular belirli makinelere ayrıldıysa ve sorguların zararsız olmadığı belirlendiyse aşağıdaki adımlar izlenmelidir:
    1.  Kullanılabilir günlük kaynaklarını gözden geçirin. 
    2.  Konak tabanlı çözümleme yürütün. 
    3.  Etkinlik şüpheli bir kullanıcıdan değilse adli çözümleme yapılarak makineye kötü amaçlı bir yazılım bulaşıp bulaşmadığı belirlenmelidir.

## <a name="post-investigation"></a>Araştırma sonrası

Konağın güvenliğini aşmak için kullanılan kötü amaçlı yazılımlar, arka kapı becerileri olan truva atları barındırabilir. Güvenliği aşılan konakta başarılı yanal hareketin tespit edildiği durumlarda, düzeltme etkinlikleri bu konakları da kapsayacak şekilde genişletilmeli, yanal harekete dahil olan tüm konaklarda kullanılan bütün parolalar ve kimlik bilgileri değiştirilmelidir. 

Düzeltme adımlarının tamamlanmasının ardından kurban konağın temizlendiği doğrulanamıyorsa veya güvenlik ihlalinin kök nedeni belirlenemiyorsa Microsoft, kritik verileri yedeklemenizi ve konağı yeniden derlemenizi önerir. Buna ek olarak yeni veya yeniden derlenen konaklar, yeniden virüs bulaşmasını önlemek amacıyla ağa katılmadan önce güçlendirilmelidir. 

Microsoft, bir saldırganın ağınızda dağıtılmış kalıcı yöntemleri olup olmadığını belirlemek için Microsoft Hesabı Ekibiniz aracılığıyla erişilebilen, profesyonel bir Olay Yanıt ve Kurtarma ekibi kullanmanızı önerir.

## <a name="mitigation"></a>Risk azaltma

DNS kullanarak keşfi önlemek amacıyla DNS sunucusunu güvenlik altına almak için bölge aktarımlarını yalnızca belirtilen IP adresleriyle kısıtlamak veya devre dışı bırakmak mümkündür. Bölge aktarımlarının kısıtlama daha fazla bilgi için bkz: [kısıtlamak bölge aktarımlarının](https://technet.microsoft.com/library/ee649273(v=ws.10).aspx). Kısıtlı bölge aktarımları, [bölge aktarımlarını IPsec ile güvenlik altına alma](https://technet.microsoft.com/library/ee649192(v=ws.10).aspx) yoluyla tamamen kilitlenebilir. Bölge Aktarımlarını Değiştirmek, [DNS sunucularınızı iç ve dış tehditlere karşı korumak](https://technet.microsoft.com/library/cc770432(v=ws.11).aspx) için yapılması gerekenler listesinde bulunan görevlerden biridir.



## <a name="see-also"></a>Ayrıca Bkz.
- [Şüpheli etkinliklerle çalışma](working-with-suspicious-activities.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
