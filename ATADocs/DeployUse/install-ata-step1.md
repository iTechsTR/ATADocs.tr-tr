---
title: "ATA’yı Yükleme - 1. Adım | Microsoft ATA"
description: "ATA’yı yüklemenin ilk adımı, seçtiğiniz sunucuya ATA Center’ı indirmeyi ve yüklemeyi kapsar."
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: b3cceb18-0f3c-42ac-8630-bdc6b310f1d6
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d89f6c5e0ac9712ce2fde057c9ef8e4025e8a144
ms.openlocfilehash: 41d538039a8fa0511a74dd6cd5d840a1dea516e8


---

# ATA’yı Yükleme - 1. Adım

>[!div class="step-by-step"]
[2. Adım »](install-ata-step2.md)

Bu yükleme yordamı, sıfırdan bir ATA 1.6 yüklemesi gerçekleştirme yönergeleri sağlar. Var olan bir ATA dağıtımını önceki bir sürümünden güncelleştirme hakkında daha fazla bilgi için bkz. [Sürüm 1.6 için ATA geçiş kılavuzu](/advanced-threat-analytics/understand-explore/ata-update-1.6-migration-guide).

> [!IMPORTANT] 
> Yüklemeye başlamadan önce ATA Center sunucusunda ve ATA Gateway sunucularında KB2934520’yi yükleyin. Bunu yüklemezseniz, ATA yüklemesi bu güncelleştirmeyi yükler ve ATA yüklemesinin ortasında bir yeniden başlatma gerektirir.

## 1. Adım ATA Center’ı indirme ve yükleme
Sunucunun gereksinimleri karşıladığını doğruladıktan sonra, ATA Center’ın yüklemesiyle devam edebilirsiniz.

ATA Center sunucusunda aşağıdaki adımları gerçekleştirin.

1.  [Microsoft Toplu Lisanslama Hizmeti Merkezi](https://www.microsoft.com/Licensing/servicecenter/default.aspx)’nden, [TechNet Değerlendirme Merkezi](http://www.microsoft.com/evalcenter/)’nden ya da [MSDN](https://msdn.microsoft.com/subscriptions/downloads)’den ATA’yı indirin.

2.  ATA Center yükleyeceğiniz bilgisayarda, yerel yöneticiler grubunun üyesi olan bir kullanıcı olarak oturum açın.

3.  **Microsoft ATA Center Setup.EXE**’yi çalıştırın ve kurulum sihirbazını izleyin.

4.  Microsoft .Net Framework yüklü değilse, yüklemeyi başlattığınızda yüklemeniz istenir. .NET Framework yüklemesinden sonra bilgisayarı yeniden başlatmanız istenebilir.
5.  **Hoş Geldiniz** sayfasında, ATA yükleme ekranları için kullanılacak dili seçin ve **İleri**’ye tıklayın.

6.  Microsoft Yazılım Lisans Koşulları’nı okuyun ve onay kutusuna tıklayıp ardından **İleri**’ye tıklayın.

7.  ATA’yı otomatik olarak güncelleştirmeye ayarlamanız önerilir. Windows bilgisayarınızda bunu yapacak şekilde ayarlanmamışsa, **Bilgisayarınızı güvenli ve güncel tutmaya yardımcı olmak için Microsoft Update'i kullanın** ekranıyla karşılaşırsınız. 
    ![ATA’yı güncel tutma görüntüsü](media/ata_ms_update.png)

8. **Güncelleştirmeleri denetlediğimde Microsoft Update'i kullan (önerilir)** öğesini seçin. Bu, burada görüldüğü gibi, Windows ayarlarını diğer Microsoft ürünleri (ATA dahil) için güncelleştirmeleri etkinleştirecek şekilde ayarlar. 
    ![Windows otomatik güncelleştirme resmi](media/ata_installupdatesautomatically.png)

8.  **ATA Center Yapılandırması** sayfasında, ortamınıza bağlı olarak aşağıdaki bilgileri girin:

    |Alan|Açıklama|Açıklamalar|
    |---------|---------------|------------|
    |Yükleme Yolu|Bu, ATA Center’ın yükleneceği konumdur. Varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Center yoludur.|Varsayılan değeri olduğu gibi bırakın.|
    |Veritabanı Veri Yolu|Bu MongoDB veritabanı dosyalarının yer alacağı konumdur. Varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\data yoludur.|Boyutunuza bağlı olarak büyümek için yeriniz olan başka bir konumla değiştirin. **Not:** <ul><li>Üretim ortamlarında, kapasite planlamasına göre yeterli yeri olan bir sürücü kullanmalısınız.</li><li>Büyük dağıtımlar için veritabanı ayrı bir fiziksel diskte yer almalıdır.</li></ul>Boyutlandırma bilgileri için bkz. [ATA kapasite planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning).|
    |ATA Center Hizmeti IP adresi: Bağlantı Noktası|Bu, ATA Center’ın ATA Gateway bileşenlerinden gelen iletişimi dinleyecekleri IP adresidir.<br /><br />**Varsayılan bağlantı noktası:** 443|ATA Center hizmeti tarafından kullanılacak IP adresini seçmek için aşağı oka tıklayın.<br /><br />ATA Center’ın IP adresi ve bağlantı noktası, ATA Konsolu’nun IP adresi ve bağlantı noktasıyla aynı olamaz. ATA Konsolu’nun bağlantı noktasını değiştirdiğinizden emin olun.|
    |ATA Center Hizmeti SSL Sertifikası|Bu, ATA Center hizmeti tarafından kullanılacak olan sertifikadır.|Yüklü bir sertifika seçmek için anahtar simgesine tıklayın veya laboratuvar ortamında dağıtım yaparken otomatik olarak imzalanan sertifikayı işaretleyin.|
    |ATA Konsolu IP adresi|Bu, IIS tarafından ATA Konsolu için kullanılacak olan IP adresidir.|ATA Konsolu tarafından kullanılan IP adresini seçmek için aşağı oka tıklayın. **Not:** ATA Gateway’den ATA Konsolu’na daha kolay erişmek için bu IP adresini not alın.|
    |ATA Konsolu SSL sertifikası|Bu, IIS tarafından kullanılacak olan sertifikadır.|Yüklü bir sertifika seçmek için anahtar simgesine tıklayın veya laboratuvar ortamında dağıtım yaparken otomatik olarak imzalanan sertifikayı işaretleyin.|

    ![ATA Center yapılandırmasının resmi](media/ATA-Center-Configuration.JPG)

10.  ATA Center ve bileşenlerini yüklemek için **Yükle**’ye tıklayın.
    ATA Center’ın yüklemesi sırasında aşağıdaki bileşenler yüklenir ve yapılandırılır:

    -   Internet Information Services (IIS)

    -   ATA Center hizmeti ve ATA Konsolu IIS sitesi

    -   MongoDB

    -   Özel Performans İzleyicisi veri koleksiyonu kümesi

    -   Otomatik olarak imzalanan sertifikalar (yükleme sırasında seçildiyse)

11.  Yükleme tamamlandığında, ATA Konsolu’na bağlanmak için **Başlat**’a tıklayın.
Bu aşamada, ATA Gateway bileşenlerinin yapılandırma ve dağıtımına devam etmek için otomatik olarak **Genel** sayfasına gidersiniz.
Siteye bir IP adresi kullanarak oturum açtığınız için, sertifikayla ilgili bir uyarı alırsınız; bu normaldir ve **Bu Web sitesine devam et**’e tıklamanız gerekir.

### Yüklemeyi doğrulama

1.  **Microsoft Advanced Threat Analytics Center** adlı hizmetin çalışıp çalışmadığını denetleyin.
2.  ATA Konsolu’na bağlanmak için masaüstünde **Microsoft Advanced Threat Analytics** kısayoluna tıklayın. ATA Center’ı yüklerken kullandığınız kullanıcı kimlik bilgileriyle oturum açın.



>[!div class="step-by-step"]
[« Yükleme öncesi](preinstall-ata.md)
[2. Adım »](install-ata-step2.md)

## Ayrıca Bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)




<!--HONumber=Aug16_HO3-->


