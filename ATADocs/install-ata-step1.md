---
title: Advanced Threat Analytics’i Yükleme - 1. Adım | Microsoft Docs
description: ATA’yı yüklemenin ilk adımı, seçtiğiniz sunucuya ATA Center’ı indirmeyi ve yüklemeyi kapsar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: b3cceb18-0f3c-42ac-8630-bdc6b310f1d6
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: ea20c87fe7990542ad68de7ae6dfeefad062e378
ms.sourcegitcommit: b283bf66e63d76e6dba4564a229e804792794c6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47454165"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*


# <a name="install-ata---step-1"></a>ATA’yı Yükleme - 1. Adım

> [!div class="step-by-step"]
> [2. Adım »](install-ata-step2.md)

Bu yükleme yordamında sıfırdan bir ATA 1.8 yüklemesi gerçekleştirmeye yönelik yönergeler sağlanmaktadır. Mevcut bir ATA dağıtımını önceki bir sürümünden güncelleştirme hakkında daha fazla bilgi için bkz: [1.9 sürümü için ATA Geçiş Kılavuzu](ata-update-1.9-migration-guide.md).

> [!IMPORTANT] 
> Windows 2012 R2 kullanıyorsanız, yüklemeye başlamadan önce ATA Center sunucusunda ve ATA Gateway sunucularında KB2934520 yükleyebilirsiniz, aksi takdirde ATA yüklemesi bu güncelleştirmeyi yükler ve ATA yüklemesinin ortasında bir yeniden başlatma gerektirir.

## <a name="step-1-download-and-install-the-ata-center"></a>1. Adım ATA Center’ı indirme ve yükleme
Sunucunun gereksinimleri karşıladığını doğruladıktan sonra, ATA Center’ın yüklemesiyle devam edebilirsiniz.
    
> [!NOTE]
>Doğrudan Office 365 portalı aracılığıyla veya Cloud Solution Partner (CSP) lisans modelinden Enterprise Mobility + Security (EMS) lisansı aldıysanız ve Microsoft Toplu Lisanslama Merkezi’nden (VLSC) ATA’ya erişiminiz yoksa Microsoft Müşteri Desteği ile iletişime geçerek Advanced Threat Analytics’i (ATA) etkinleştirme işlemini edinin.

ATA Center sunucusunda aşağıdaki adımları gerçekleştirin.

1.  [Microsoft Toplu Lisanslama Hizmeti Merkezi](https://www.microsoft.com/Licensing/servicecenter/default.aspx)’nden, [TechNet Değerlendirme Merkezi](http://www.microsoft.com/evalcenter/)’nden ya da [MSDN](https://msdn.microsoft.com/subscriptions/downloads)’den ATA’yı indirin.

2.  Oturum ATA Center yerel Yöneticiler grubunun bir üyesi olan bir kullanıcı yüklüyorsanız bilgisayarda oturum açın.

3.  **Microsoft ATA Center Setup.EXE**’yi çalıştırın ve kurulum sihirbazını izleyin.

> [!NOTE]   
> Yüklemenin yeniden başlatma gerektirmesi durumunda oluşabilecek sorunları önlemek için, yükleme dosyasını bağlı bir ISO dosyasından değil yerel bir sürücüden çalıştırdığınızdan emin olun.   

4.  Microsoft .net Framework yüklü değilse, yüklemeyi başlattığınızda yüklemeniz istenir. .NET Framework yüklemesinden sonra bilgisayarı yeniden başlatmanız istenebilir.
5.  **Hoş Geldiniz** sayfasında, ATA yükleme ekranları için kullanılacak dili seçin ve **İleri**’ye tıklayın.

6.  Microsoft Yazılımı Lisans koşullarını okuyun ve koşulları kabul ediyorsanız, onay kutusuna tıklayın ve ardından **sonraki**.

7.  ATA’yı otomatik olarak güncelleştirmeye ayarlamanız önerilir. Windows bilgisayarınızda bunu şekilde ayarlanmamışsa, size **bilgisayarınızı güvenli ve güncel tutmaya yardımcı olması için Microsoft Update'i kullanın** ekran. 
    ![ATA’yı güncel tutma resmi](media/ata_ms_update.png)

8. **Güncelleştirmeleri denetlediğimde Microsoft Update'i kullan (önerilir)** öğesini seçin. Bu, Windows ayarlarını, burada görüldüğü gibi diğer Microsoft ürünleri (ATA dahil) için güncelleştirmeleri etkinleştirecek şekilde ayarlar. 

    ![Windows otomatik güncelleştirme resmi](media/ata_installupdatesautomatically.png)

8.  **Center’ı Yapılandırma** sayfasında, ortamınıza bağlı olarak aşağıdaki bilgileri girin:

    |Alan|Açıklama|Açıklamalar|
    |---------|---------------|------------|
    |Yükleme Yolu|ATA Center'ın yüklendiği konumun budur. Varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Center yoludur.|Varsayılan değeri olduğu gibi bırakın.|
    |Veritabanı Veri Yolu|Bu MongoDB veritabanı dosyalarının bulunduğu konumdur. Varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\data yoludur.|Boyutunuza bağlı olarak büyümek için yeriniz olan başka bir konumla değiştirin. **Not:** <ul><li>Üretim ortamlarında, kapasite planlamasına göre yeterli yeri olan bir sürücü kullanmalısınız.</li><li>Büyük dağıtımlar için veritabanı ayrı bir fiziksel diskte yer almalıdır.</li></ul>Boyutlandırma bilgileri için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).|
    |Center Hizmeti SSL Sertifikası|Bu ATA konsolu ve ATA Center hizmeti tarafından kullanılan sertifikadır.|Yüklü bir sertifika seçmek için anahtar simgesine tıklayın veya laboratuvar ortamında dağıtım yaparken otomatik olarak imzalanan sertifikayı işaretleyin. Otomatik olarak imzalanan bir sertifika oluşturma seçeneğiniz vardır.|
        
    ![ATA Center yapılandırmasının resmi](media/ATA-Center-Configuration.png)

10.  ATA Center ve bileşenlerini yüklemek için **Yükle**’ye tıklayın.
    ATA Center’ın yüklemesi sırasında aşağıdaki bileşenler yüklenir ve yapılandırılır:

    -   ATA Center hizmeti

    -   MongoDB

    -   Özel Performans İzleyicisi veri koleksiyonu kümesi

    -   Otomatik olarak imzalanan sertifikalar (yükleme sırasında seçildiyse)

11.  Yükleme tamamlandığında **Başlat**’a tıklayarak ATA Konsolu’nu açın ve **Yapılandırma** sayfasında kurulumu tamamlayın.
Bu noktada, otomatik olarak kapsama dahil edilecektir **genel** Ayarları sayfasında, yapılandırma ve ATA Gateway bileşenlerinin dağıtımına devam etmek için.
Siteye bir IP adresi kullanarak oturum açtığınız için bu normaldir için sertifikayla ilgili bir uyarı alırsınız ve tıklatmanız gerekir **bu Web sitesine devam et**.

### <a name="validate-installation"></a>Yüklemeyi doğrulama

1.  **Microsoft Advanced Threat Analytics Center** adlı hizmetin çalışıp çalışmadığını denetleyin.
2.  ATA Konsolu’na bağlanmak için masaüstünde **Microsoft Advanced Threat Analytics** kısayoluna tıklayın. ATA Center’ı yüklerken kullandığınız kullanıcı kimlik bilgileriyle oturum açın.

### <a name="set-anti-virus-exclusions"></a>Kümesi virüsten koruma dışlamaları

ATA Center'ı yükledikten sonra tarafından virüsten koruma uygulamanızı sürekli olarak taranan MongoDB veritabanı dizini bırakmanız gerekir. Veritabanında varsayılan konum: **C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\data**.



> [!div class="step-by-step"]
> [« Yükleme öncesi](configure-port-mirroring.md)
> [2. Adım »](install-ata-step2.md)

## <a name="related-videos"></a>İlgili videolar
- [ATA Gateway türü sağ seçme](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)
- [ATA dağıtımı genel bakış](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA POC Dağıtım Kılavuzu](http://aka.ms/atapoc)
- [ATA boyutlandırma aracı](http://aka.ms/atasizingtool)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)

