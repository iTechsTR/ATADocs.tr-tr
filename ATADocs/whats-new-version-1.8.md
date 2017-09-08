---
title: "ATA sürüm 1.8’deki yenilikler | Microsoft Docs"
description: "ATA sürüm 1.8’deki yeniliklerin yanında bilinen sorunları da listeler"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/03/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 9592d413-df0e-4cec-8e03-be1ae00ba5dc
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 2793a602a0cd0fb9902197acd45dd5bdd4612ea4
ms.sourcegitcommit: 654500928025e3cb127e095c17cc1d6444defd3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2017
---
# <a name="whats-new-in-ata-version-18"></a>ATA sürüm 1.8’deki yenilikler

[İndirme Merkezi’nden](https://www.microsoft.com/download/details.aspx?id=55536) ATA’nın son güncelleştirme sürümünü indirebilir veya [Değerlendirme merkezinden](http://www.microsoft.com/evalcenter/evaluate-microsoft-advanced-threat-analytics) tam sürümü indirebilirsiniz.

Bu sürüm notları, Advanced Threat Analytics’in bu sürümündeki güncelleştirmeler, yeni özellikler, hata düzeltmeleri ve bilinen sorunlar hakkında bilgi sağlar.



## <a name="new--updated-detections"></a>Yeni ve güncelleştirilmiş algılamalar

- Olağan dışı protokol uygulaması, WannaCry kötü amaçlı yazılımını algılayacak şekilde iyileştirildi.

- YENİ! **Gizli gruplardaki anormal değişiklikler** – Ayrıcalık yükseltme aşamasının bir parçası olarak saldırganlar, gizli kaynaklara erişebilmek adına yüksek ayrıcalıklara sahip gruplarda değişiklikler yapar. ATA artık yükseltilmiş bir grupta anormal bir değişiklik olduğunda bunu algılar.
- YENİ! **Şüpheli kimlik doğrulama hataları** (Davranışsal deneme yanılma saldırısı) – Saldırganlar, hesapları ele geçirmek için kimlik bilgilerinde deneme yanılma yapmayı dener. ATA artık anormal bir kimlik doğrulama davranışı hatası algıladığında uyarı gönderir.   

- **Uzaktan yürütme denemesi – WMI exec** - Saldırganlar etki alanı denetleyicinizde uzak kod çalıştırarak ağınızı denetleme girişiminde bulunabilir. ATA, kodu uzaktan çalıştırmaya yarayan WMI yöntemlerini kapsayacak şekilde uzaktan yürütme algılamasını geliştirdi.

- Dizin hizmeti sorguları kullanarak keşif – Bu algılama yöntemi, tek bir gizli varlığa yapılan sorguları yakalayacak ve önceki sürüme kıyasla daha az hatalı pozitif sonuç verecek şekilde geliştirildi. Bu yöntemi 1.7 sürümünde devre dışı bıraktıysanız 1.8 sürümü yüklendiğinde otomatik olarak etkinleştirilecektir.

- Kerberos Altın Anahtar etkinliği – ATA 1.8, altın anahtar saldırılarını algılayacak ilave bir teknik barındırır.
    - ATA artık Altın anahtarın süresinin dolduğu şüpheli etkinlikleri algılar. Bir Kerberos anahtarı, izin verilen süresi dolmasına rağmen kullanılmışsa ATA bunu, büyük olasılıkla Altın anahtarın oluşturulduğu şüpheli bir etkinlik olarak algılayacaktır.
- Aşağıdaki algılama yöntemleri geliştirilerek bilinen hatalı pozitif sonuçlar kaldırılmıştır:  
    - Ayrıcalık yükseltme algılama (sahte PAC) 
    - Şifrelemeyi düşürme etkinliği (Skeleton Key)
    - Olağan dışı protokol uygulanması
    - Bozulmuş güven

## <a name="improved-triage-of-suspicious-activities"></a>İyileştirilmiş şüpheli etkinlik önceliklendirmesi

-   YENİ! ATA 1.8 ile önceliklendirme işlemi sırasında şüpheli etkinliklerde şu eylemleri gerçekleştirmeniz mümkündür: 
    - **Varlıkları dışlayarak** ATA’nın gelecekteki şüpheli etkinliklerde zararsız doğru pozitif sonuçlar (uzak kod çalıştıran bir yönetici veya güvenlik tarayıcıları algılamak gibi) aldığı durumlarda sizi uyarmasını önleyebilirsiniz.
    - **Yinelenenleri göstermeyerek** aynı şüpheli etkinlik için tekrar tekrar uyarılmamayı seçebilirsiniz.
    - **Şüpheli etkinlikleri silerek** saldırı zaman çizelgesindeki etkinlikleri temizleyebilirsiniz.
-   Şüpheli etkinlik uyarılarını takip etme işlemi artık daha etkilidir. Şüpheli etkinlik zaman çizelgesi yeniden tasarlandı. ATA 1.8 sürümünde, önceliklendirme ve araştırmaya yönelik daha fazla bilgi ile çok daha fazla şüpheli etkinliği tek bir ekranda görebileceksiniz. 

## <a name="new-reports-to-help-you-investigate"></a>Araştırmanıza yardımcı olacak yeni raporlar 
-   YENİ! **Özet raporu** eklendi, böylece şüpheli etkinlikler ve sistem durumu sorunları gibi tüm ATA verilerinin bir özetine ulaşmanız mümkündür. Artık yinelenerek otomatik olarak oluşturulan özel bir rapor bile tanımlayabilirsiniz.
-   YENİ! **Gizli grup raporu** eklendi, böylece gizli gruplarda belirli bir zaman dilimi içerisinde yapılan değişikliklere göz atabilirsiniz.


## <a name="infrastructure-improvements"></a>Altyapı iyileştirmeleri

-   ATA Center performansı geliştirildi. ATA 1.8 ile ATA Center saniyede 1 milyondan fazla paket işleyebilir.
-   ATA Lightweight Gateway artık olay iletmeyi yapılandırmaya gerek kalmadan olayları yerel olarak okuyabilir.
-   Artık izleme uyarıları ve şüpheli etkinlikler için farklı e-postalar yapılandırabilirsiniz.

## <a name="security-improvements"></a>Güvenlik iyileştirmeleri

-   YENİ! **ATA yönetimi için çoklu oturum açma**. ATA, Windows kimlik doğrulaması ile tümleştirilmiş çoklu oturum açmayı destekler - bilgisayarınızda zaten oturum açtıysanız ATA bu belirteci kullanarak ATA Konsolu’nda sizin için oturum açar. Ayrıca bir akıllı kart kullanarak da oturum açabilirsiniz. ATA Gateway ve ATA Lightweight Gateway sessiz yükleme betikleri artık kimlik bilgileri sağlamaya gerek kalmadan, oturum açmış kullanıcının bağlamını kullanır.
-   Yerel Sistem ayrıcalıkları, ATA Gateway sürecinden kaldırıldı. Böylece ATA Gateway süreci için artık sanal hesaplar (yalnızca tek başına ATA Gateway’lerde kullanılabilir), yönetilen hizmet hesapları ve grup tarafından yönetilen hizmet hesapları kullanabilirsiniz.   
-   ATA Center ve Gateway’lerine denetim günlükleri eklendi ve artık tüm eylemler Windows Olay Günlüğüne kaydediliyor.
-   ATA Center KSP Sertifikaları için destek eklendi.

## <a name="additional-changes"></a>Ek değişiklikler

- Not ekleme seçeneği Kuşkulu Etkinlikler’den kaldırıldı
- Kuşkulu Etkinlikler’i azaltıcı öneriler, Kuşkulu Etkinlikler zaman satırından kaldırıldı.
- ATA sürüm 1.8 ile başlayan Lightweight Gateway ve ATA Gateway bileşenleri kendi sertifikaların yönetilmesine ve bunları yönetmek için bir yönetici etkileşimi gerekiyor.

## <a name="known-issues"></a>Bilinen sorunlar

> [!WARNING]
> Bu bilinen sorunlar Lütfen güncelleştirme önlemenize veya kullanarak dağıtmak için 1 1.8 güncelleştirin.

### <a name="ata-gateway-on-windows-server-core"></a>Windows Server Core’da ATA Gateway

**Belirtiler**: .NET Framework 4.7 ile Windows Server 2012 R2 Core’da ATA Gateway 1.8’e yükseltme işlemi, şu hatayı vererek başarısız olabilir: *Microsoft Advanced Threat Analytics Gateway çalışmayı durdurdu*. 

![Ağ geçidi çekirdek hatası](./media/gateway-core-error.png)

Windows Server 2016 Core’da hatayı görmeyebilirsiniz. Ancak yüklemeye çalıştığınızda işlem başarısız olacak, ayrıca 1000 ve 1001 numaralı olaylar (işlem kilitlenmesi) sunucudaki uygulama Olay Günlüğü’ne kaydedilecektir.

**Açıklama**: WPF teknolojileri kullanan uygulamaların (ATA gibi) yüklenmesini engelleyen bir .NET Framework 4.7 sorunu var. Daha fazla bilgi için [bkz. KB 4034015](https://support.microsoft.com/help/4034015/wpf-window-can-t-be-loaded-after-you-install-the-net-framework-4-7-on). 

**Geçici çözüm**: .NET 4.7’yi kaldırarak [bkz. KB 3186497](https://support.microsoft.com/help/3186497/the-net-framework-4-7-offline-installer-for-windows) .NET sürümünü .NET 4.6.2’ye döndürün ve daha sonra ATA Gateway’i 1.8 sürümüne güncelleştirin. ATA yükseltmesinden sonra .NET 4.7’yi yeniden yükleyebilirsiniz.  Gelecek sürümlerde bu sorunu düzeltmeye yönelik bir güncelleştirme sunulacaktır.

### <a name="lightweight-gateway-event-log-permissions"></a>Lightweight Gateway olay günlüğü izinleri

**Belirtiler**: ATA sürümünüzü 1.8’e yükselttiğinizde, önceden Güvenlik Olay Günlüğü’ne erişim izni olan uygulama veya hizmetler bu izinleri kaybedebilir. 

**Açıklama**: ATA dağıtımının kolaylaştırılması için ATA 1.8, Güvenlik Olay Günlüğünüze Windows Olay İletme yapılandırmasına gerek duymadan doğrudan erişir. ATA aynı zamanda, güvenliği artırmak için düşük düzeyde izinlere sahip bir yerel hizmet olarak da çalışır. ATA’ya olayları okumak üzere erişim sağlamak için ATA hizmeti, kendisine Güvenlik Olay Günlüğü izinleri verir. Bu durumda, önceden diğer hizmetler için ayarlanan izinler devre dışı kalabilir.

**Geçici Çözüm**: Aşağıdaki Windows PowerShell betiğini çalıştırın. Bu betik, kayıt defterinde ATA için eklenen hatalı izinleri kaldırır ve bunları farklı bir API aracılığıyla ekler. Bu yolla diğer uygulamaların izinleri geri yüklenebilir. Yüklenmezse, bu izinler el ile geri yüklenmelidir. Gelecek sürümlerde bu sorunu düzeltmeye yönelik bir güncelleştirme sunulacaktır. 

       $ATADaclEntry = "(A;;0x1;;;S-1-5-80-1717699148-1527177629-2874996750-2971184233-2178472682)"
        try {
        $SecurityDescriptor = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Eventlog\Security -Name CustomSD
        $ATASddl = "O:BAG:SYD:" + $ATADaclEntry 
        if($SecurityDescriptor.CustomSD -eq $ATASddl) {
        Remove-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Eventlog\Security -Name CustomSD
        }
    }
    catch
    {
    # registry key does not exist
    }

    $EventLogConfiguration = New-Object -TypeName System.Diagnostics.Eventing.Reader.EventLogConfiguration("Security")
    $EventLogConfiguration.SecurityDescriptor = $EventLogConfiguration.SecurityDescriptor + $ATADaclEntry

### <a name="proxy-interference"></a>Ara sunucu müdahalesi

**Belirtiler**: ATA sürümünü 1.8’e yükselttikten sonra, ATA Gateway hizmeti başlatılamayabilir. ATA hata günlüğünde şu özel durumu görebilirsiniz: *System.Net.Http.HttpRequestException: İstek gönderilirken bir hata oluştu. ---> System.Net.WebException: Uzak sunucu bir hata döndürdü: (407) Ara Sunucu Kimlik Doğrulaması Gerekli.*

**Açıklama**: ATA 1.8 ve üzeri sürümlerde ATA Gateway ile ATA Center, http protokolünü kullanarak iletişim kurar. ATA Gateway’i yüklediğiniz makine ATA Center’a bağlanmak için bir ara sunucusu kullanıyorsa, bu iletişim bozulabilir. 

**Geçici çözüm**: ATA Gateway hizmet hesabında, ara sunucu kullanımını devre dışı bırakın. Gelecek sürümlerde bu sorunu düzeltmeye yönelik bir güncelleştirme sunulacaktır.

### <a name="report-settings-reset"></a>Rapor ayarlarını sıfırla

**Belirtiler**: 1.8 güncelleştirme 1'ı güncelleştirdiğinizde Zamanlanmış raporlar yapılan herhangi bir ayarı temizlenir.

**Açıklama**: 1.8 sıfırlar 1.8 güncelleştirme 1 için güncelleştirme raporları zamanlaması ayarlar.

**Geçici çözüm**: 1.8 güncelleştirme 1 için güncelleştirme önce rapor ayarların bir kopyasını oluşturmak ve bunları yeniden girin, bu da yapılabilir daha fazla bilgi için bir komut dosyası aracılığıyla bkz [ATA yapılandırmasını içeri ve dışarı aktarmak](ata-configuration-file.md).


## <a name="see-also"></a>Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

[ATA’yı sürüm 1.8’e güncelleştirme - geçiş kılavuzu](ata-update-1.8-migration-guide.md)

