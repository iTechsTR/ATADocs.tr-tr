---
title: Advanced Threat Analytics’i Yükleme - 1. Adım | Microsoft Docs
description: ATA’yı yüklemenin ilk adımı, seçtiğiniz sunucuya ATA Center’ı indirmeyi ve yüklemeyi kapsar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: b3cceb18-0f3c-42ac-8630-bdc6b310f1d6
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 27a016fe71d08dd8e8852fc44d5dea142f914d9e
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
ms.locfileid: "30010100"
---
*Uygulandığı öğe: Advanced Threat Analytics sürüm 1.9*


# <a name="install-ata---step-1"></a>ATA’yı Yükleme - 1. Adım

>[!div class="step-by-step"]
[2. Adım »](install-ata-step2.md)

Bu yükleme yordamında sıfırdan bir ATA 1.8 yüklemesi gerçekleştirmeye yönelik yönergeler sağlanmaktadır. Var olan bir ATA dağıtımını önceki bir sürümünden güncelleştirme hakkında daha fazla bilgi için bkz: [sürüm 1.9 için ATA Geçiş Kılavuzu](ata-update-1.9-migration-guide.md).

> [!IMPORTANT] 
> Windows 2012 R2 kullanıyorsanız, yükleme başlamadan önce ATA Center sunucusunda ve ATA Gateway sunucularında KB2934520 yükleyebilirsiniz, aksi takdirde ATA yüklemesi bu güncelleştirmeyi yükler ve ATA yüklemesinin ortasında bir yeniden başlatma gerektirir.

## <a name="step-1-download-and-install-the-ata-center"></a>1. Adım ATA Center’ı indirme ve yükleme
Sunucunun gereksinimleri karşıladığını doğruladıktan sonra, ATA Center’ın yüklemesiyle devam edebilirsiniz.
    
> [!NOTE]
>Doğrudan Office 365 portalı aracılığıyla veya Cloud Solution Partner (CSP) lisans modelinden Enterprise Mobility + Security (EMS) lisansı aldıysanız ve Microsoft Toplu Lisanslama Merkezi’nden (VLSC) ATA’ya erişiminiz yoksa Microsoft Müşteri Desteği ile iletişime geçerek Advanced Threat Analytics’i (ATA) etkinleştirme işlemini edinin.

ATA Center sunucusunda aşağıdaki adımları gerçekleştirin.

1.  [Microsoft Toplu Lisanslama Hizmeti Merkezi](https://www.microsoft.com/Licensing/servicecenter/default.aspx)’nden, [TechNet Değerlendirme Merkezi](http://www.microsoft.com/evalcenter/)’nden ya da [MSDN](https://msdn.microsoft.com/subscriptions/downloads)’den ATA’yı indirin.

2.  Açın ATA Center yerel Yöneticiler grubunun bir üyesi olan bir kullanıcı yüklediğiniz bilgisayarda oturum açın.

3.  **Microsoft ATA Center Setup.EXE**’yi çalıştırın ve kurulum sihirbazını izleyin.

> [!NOTE]   
> Yüklemenin yeniden başlatma gerektirmesi durumunda oluşabilecek sorunları önlemek için, yükleme dosyasını bağlı bir ISO dosyasından değil yerel bir sürücüden çalıştırdığınızdan emin olun.   

4.  Microsoft .net Framework yüklü değilse, yüklemeyi başlattığınızda yüklemeniz istenir. .NET Framework yüklemesinden sonra bilgisayarı yeniden başlatmanız istenebilir.
5.  **Hoş Geldiniz** sayfasında, ATA yükleme ekranları için kullanılacak dili seçin ve **İleri**’ye tıklayın.

6.  Microsoft Yazılımı Lisans koşullarını okuyun ve koşulları kabul ediyorsanız, onay kutusuna tıklayın ve ardından **sonraki**.

7.  ATA’yı otomatik olarak güncelleştirmeye ayarlamanız önerilir. Windows bilgisayarınızda bunu yapacak şekilde ayarlanmamışsa, size **bilgisayarınızı güvenli ve güncel tutmaya yardımcı olmak için Microsoft Update'i kullanın** ekran. 
    ![ATA’yı güncel tutma resmi](media/ata_ms_update.png)

8. **Güncelleştirmeleri denetlediğimde Microsoft Update'i kullan (önerilir)** öğesini seçin. Bu Windows ayarları, burada görüldüğü gibi diğer Microsoft ürünleri (ATA dahil) için güncelleştirmeleri etkinleştirecek şekilde ayarlar. 

    ![Windows otomatik güncelleştirme resmi](media/ata_installupdatesautomatically.png)

8.  **Center’ı Yapılandırma** sayfasında, ortamınıza bağlı olarak aşağıdaki bilgileri girin:

    |Alan|Description|Açıklamalar|
    |---------|---------------|------------|
    |Yükleme Yolu|Bu, ATA Center'ın yüklendiği konumdur. Varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Center yoludur.|Varsayılan değeri olduğu gibi bırakın.|
    |Veritabanı Veri Yolu|Bu MongoDB veritabanı dosyalarının bulunduğu konumdur. Varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\data yoludur.|Boyutunuza bağlı olarak büyümek için yeriniz olan başka bir konumla değiştirin. **Not:** <ul><li>Üretim ortamlarında, kapasite planlamasına göre yeterli alana sahip bir sürücü kullanmalısınız.</li><li>Büyük dağıtımlar için veritabanı ayrı bir fiziksel diskte yer almalıdır.</li></ul>Boyutlandırma bilgileri için bkz. [ATA kapasite planlaması](ata-capacity-planning.md).|
    |Center Hizmeti SSL Sertifikası|Bu ATA konsolu ve ATA Center hizmeti tarafından kullanılan sertifika yok.|Yüklü bir sertifika seçmek için anahtar simgesine tıklayın veya laboratuvar ortamında dağıtım yaparken otomatik olarak imzalanan sertifikayı işaretleyin. Otomatik olarak imzalanan sertifika oluşturma seçeneğiniz vardır.|
        
    ![ATA Center yapılandırmasının resmi](media/ATA-Center-Configuration.png)

10.  ATA Center ve bileşenlerini yüklemek için **Yükle**’ye tıklayın.
    ATA Center’ın yüklemesi sırasında aşağıdaki bileşenler yüklenir ve yapılandırılır:

    -   ATA Center hizmeti

    -   MongoDB

    -   Özel Performans İzleyicisi veri koleksiyonu kümesi

    -   Otomatik olarak imzalanan sertifikalar (yükleme sırasında seçildiyse)

11.  Yükleme tamamlandığında **Başlat**’a tıklayarak ATA Konsolu’nu açın ve **Yapılandırma** sayfasında kurulumu tamamlayın.
Bu noktada, otomatik olarak güncelleştirilecektir **genel** yapılandırma ve ATA Gateway bileşenlerinin dağıtımına devam etmek için ayarları sayfası.
Siteye bir IP adresi kullanarak oturum açtığınız için sertifika, bu normaldir ilgili bir uyarı alırsınız ve tıklamanız **bu Web sitesine devam et**.

### <a name="validate-installation"></a>Yüklemeyi doğrulama

1.  **Microsoft Advanced Threat Analytics Center** adlı hizmetin çalışıp çalışmadığını denetleyin.
2.  ATA Konsolu’na bağlanmak için masaüstünde **Microsoft Advanced Threat Analytics** kısayoluna tıklayın. ATA Center’ı yüklerken kullandığınız kullanıcı kimlik bilgileriyle oturum açın.

### <a name="set-anti-virus-exclusions"></a>Set virüsten koruma özel durumlar

ATA Center yüklendikten sonra virüsten koruma uygulamanız tarafından sürekli olarak taranan MongoDB veritabanı dizini bırakmanız gerekir. Veritabanındaki varsayılan konum: **C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\data**.



>[!div class="step-by-step"]
[« Yükleme öncesi](configure-port-mirroring.md)
[2. Adım »](install-ata-step2.md)

## <a name="related-videos"></a>İlgili videolar
- [ATA Gateway türü sağ seçme](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)
- [ATA dağıtımına genel bakış](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)


## <a name="see-also"></a>Ayrıca bkz:
- [ATA POC Dağıtım Kılavuzu](http://aka.ms/atapoc)
- [ATA boyutlandırma aracı](http://aka.ms/atasizingtool)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)

