---
title: "ATA’yı Yükleme: 1. Adım | Microsoft Docs"
description: "ATA’yı yüklemenin ilk adımı, seçtiğiniz sunucuya ATA Center’ı indirmeyi ve yüklemeyi kapsar."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/9/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: b3cceb18-0f3c-42ac-8630-bdc6b310f1d6
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b73fb769438a7290053c27766c233010079dca78
ms.openlocfilehash: 313ae02742d4acc68c52d5481fdc24c0aa508681


---

*Şunlar için geçerlidir: Advanced Threat Analytics sürüm 1.7*



# <a name="install-ata---step-1"></a>ATA’yı Yükleme - 1. Adım

>[!div class="step-by-step"]
[2. Adım »](install-ata-step2.md)

Bu yükleme yordamı, sıfırdan bir ATA 1.7 yüklemesi gerçekleştirmeye yönelik yönergeleri sağlar. Mevcut bir ATA dağıtımını önceki bir sürümünden güncelleştirme hakkında daha fazla bilgi için bkz. [Sürüm 1.7 için ATA geçiş kılavuzu](/advanced-threat-analytics/understand-explore/ata-update-1.7-migration-guide).

> [!IMPORTANT] 
> Windows 2012 R2 kullanıyorsanız, yüklemeye başlamadan önce ATA Center sunucusuna ve ATA Gateway sunucularına KB2934520’yi yükleyin. Aksi takdirde ATA yüklemesi bu güncelleştirmeyi yükler ve bu işlem sırasında bir yeniden başlatma gerektirir.

## <a name="step-1-download-and-install-the-ata-center"></a>1. Adım ATA Center’ı indirme ve yükleme
Sunucunun gereksinimleri karşıladığını doğruladıktan sonra, ATA Center’ın yüklemesiyle devam edebilirsiniz.

ATA Center sunucusunda aşağıdaki adımları gerçekleştirin.

1.  [Microsoft Toplu Lisanslama Hizmeti Merkezi](https://www.microsoft.com/Licensing/servicecenter/default.aspx)’nden, [TechNet Değerlendirme Merkezi](http://www.microsoft.com/evalcenter/)’nden ya da [MSDN](https://msdn.microsoft.com/subscriptions/downloads)’den ATA’yı indirin.

2.  ATA Center yükleyeceğiniz bilgisayarda, yerel yöneticiler grubunun üyesi olan bir kullanıcı olarak oturum açın.

3.  **Microsoft ATA Center Setup.EXE**’yi çalıştırın ve kurulum sihirbazını izleyin.

> [!NOTE]   
> Yüklemenin yeniden başlatma gerektirmesi durumunda oluşabilecek sorunları önlemek için, yükleme dosyasını bağlı bir ISO dosyasından değil yerel bir sürücüden çalıştırdığınızdan emin olun.   

4.  Microsoft .Net Framework yüklü değilse, yüklemeyi başlattığınızda yüklemeniz istenir. .NET Framework yüklemesinden sonra bilgisayarı yeniden başlatmanız istenebilir.
5.  **Hoş Geldiniz** sayfasında, ATA yükleme ekranları için kullanılacak dili seçin ve **İleri**’ye tıklayın.

6.  Microsoft Yazılım Lisans Koşulları’nı okuyun ve onay kutusuna tıklayıp ardından **İleri**’ye tıklayın.

7.  ATA’yı otomatik olarak güncelleştirmeye ayarlamanız önerilir. Windows bilgisayarınızda bunu yapacak şekilde ayarlanmamışsa, **Bilgisayarınızı güvenli ve güncel tutmaya yardımcı olmak için Microsoft Update'i kullanın** ekranıyla karşılaşırsınız. 
    ![ATA’yı güncel tutma resmi](media/ata_ms_update.png)

8. **Güncelleştirmeleri denetlediğimde Microsoft Update'i kullan (önerilir)** öğesini seçin. Bu, burada görüldüğü gibi, Windows ayarlarını diğer Microsoft ürünleri (ATA dahil) için güncelleştirmeleri etkinleştirecek şekilde ayarlar. 
    ![Windows otomatik güncelleştirme resmi](media/ata_installupdatesautomatically.png)

8.  **ATA Center Yapılandırması** sayfasında, ortamınıza bağlı olarak aşağıdaki bilgileri girin:

    |Alan|Açıklama|Açıklamalar|
    |---------|---------------|------------|
    |Yükleme Yolu|Bu, ATA Center’ın yükleneceği konumdur. Varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Center yoludur.|Varsayılan değeri olduğu gibi bırakın.|
    |Veritabanı Veri Yolu|Bu MongoDB veritabanı dosyalarının yer alacağı konumdur. Varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\data yoludur.|Boyutunuza bağlı olarak büyümek için yeriniz olan başka bir konumla değiştirin. **Not:** <ul><li>Üretim ortamlarında, kapasite planlamasına göre yeterli yeri olan bir sürücü kullanmalısınız.</li><li>Büyük dağıtımlar için veritabanı ayrı bir fiziksel diskte yer almalıdır.</li></ul>Boyutlandırma bilgileri için bkz. [ATA kapasite planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning).|
    |Center Hizmeti IP adresi: Bağlantı Noktası|Bu, ATA Center’ın ATA Gateway bileşenlerinden gelen iletişimi dinleyecekleri IP adresidir.<br /><br />**Varsayılan bağlantı noktası:** 443|ATA Center hizmeti tarafından kullanılacak IP adresini seçmek için aşağı oka tıklayın.<br /><br />ATA Center’ın IP adresi ve bağlantı noktası, ATA Konsolu’nun IP adresi ve bağlantı noktasıyla aynı olamaz. ATA Konsolu’nun bağlantı noktasını değiştirdiğinizden emin olun.|
    |Center Hizmeti SSL Sertifikası|Bu, ATA Konsolu ve ATA Center hizmeti tarafından kullanılacak olan sertifikadır.|Yüklü bir sertifika seçmek için anahtar simgesine tıklayın veya laboratuvar ortamında dağıtım yaparken otomatik olarak imzalanan sertifikayı işaretleyin.|
    |Konsol IP adresi|Bu, ATA Konsolu için kullanılacak olan IP adresidir.|ATA Konsolu tarafından kullanılan IP adresini seçmek için aşağı oka tıklayın. **Not:** ATA Gateway’den ATA Konsolu’na daha kolay erişmek için bu IP adresini not alın.|
    
    ![ATA Center yapılandırmasının resmi](media/ATA-Center-Configuration.png)

10.  ATA Center ve bileşenlerini yüklemek için **Yükle**’ye tıklayın.
    ATA Center’ın yüklemesi sırasında aşağıdaki bileşenler yüklenir ve yapılandırılır:

    -   ATA Center hizmeti

    -   MongoDB

    -   Özel Performans İzleyicisi veri koleksiyonu kümesi

    -   Otomatik olarak imzalanan sertifikalar (yükleme sırasında seçildiyse)

11.  Yükleme tamamlandığında, ATA Konsolu’na bağlanmak için **Başlat**’a tıklayın.
Bu aşamada, ATA Gateway bileşenlerinin yapılandırma ve dağıtımına devam etmek için otomatik olarak **Genel** sayfasına gidersiniz.
Siteye bir IP adresi kullanarak oturum açtığınız için, sertifikayla ilgili bir uyarı alırsınız; bu normaldir ve **Bu Web sitesine devam et**’e tıklamanız gerekir.

### <a name="validate-installation"></a>Yüklemeyi doğrulama

1.  **Microsoft Advanced Threat Analytics Center** adlı hizmetin çalışıp çalışmadığını denetleyin.
2.  ATA Konsolu’na bağlanmak için masaüstünde **Microsoft Advanced Threat Analytics** kısayoluna tıklayın. ATA Center’ı yüklerken kullandığınız kullanıcı kimlik bilgileriyle oturum açın.



>[!div class="step-by-step"]
[« Yükleme öncesi](configure-port-mirroring.md)
[2. Adım »](install-ata-step2.md)

## <a name="see-also"></a>Ayrıca bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)




<!--HONumber=Jan17_HO2-->


