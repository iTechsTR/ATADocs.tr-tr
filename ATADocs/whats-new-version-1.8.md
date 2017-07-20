---
title: "ATA sürüm 1.8’deki yenilikler | Microsoft Docs"
description: "ATA sürüm 1.8’deki yeniliklerin yanında bilinen sorunları da listeler"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/16/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 9592d413-df0e-4cec-8e03-be1ae00ba5dc
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 63dd37548dbf4e150f32880543c3bf421bf3fe71
ms.sourcegitcommit: 3cd268cf353ff8bc3d0b8f9a8c10a34353d1fcf1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2017
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
-   Şüpheli etkinlik uyarılarını takip etme işlemi artık daha etkilidir. Şüpheli etkinlik zaman çizelgesi yeniden tasarlandı. ATA 1.8 ile önceliklendirme ve araştırmaya yönelik pek çok bilgi içeren tek bir ekranda çok daha fazla şüpheli etkinlikle ilgilenebileceksiniz. 

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



## <a name="see-also"></a>Ayrıca Bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

[ATA’yı sürüm 1.8’e güncelleştirme - geçiş kılavuzu](ata-update-1.8-migration-guide.md)

