---
# required metadata

title: ATA’yı Yükleme - 1. Adım | Microsoft Advanced Threat Analytics
description: ATA’yı yüklemenin ilk adımı, seçtiğiniz sunucuya ATA Center’ı indirmeyi ve yüklemeyi kapsar.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: b3cceb18-0f3c-42ac-8630-bdc6b310f1d6

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ATA’yı Yükleme - 1. Adım

>[!div class="step-by-step"]
[« Yükleme öncesi](install-ata-preinstall.md)
[2. Adım »](install-ata-step2.md)

## 1. Adım ATA Center’ı indirme ve yükleme
Sunucunun gereksinimleri karşıladığını doğruladıktan sonra, ATA Center’ın yüklemesiyle devam edebilirsiniz.

ATA Center sunucusunda aşağıdaki adımları gerçekleştirin.

1.  ATA’yı [TechNet Değerlendirme Merkezi](http://www.microsoft.com/en-us/evalcenter/)’nden indirin..

2.  Yerel Administrators grubunun bir üyesi olarak kullanıcıyla oturum açın.

3.  Yükseltilmiş bir komut isteminde Microsoft ATA Center Setup.EXE’yi çalıştırın ve kurulum sihirbazını izleyin.

4.  **Hoş Geldiniz** sayfasında dilinizi seçin ve **İleri**’ye tıklayın..

5.  Son Kullanıcı Lisans Sözleşmesi’ni okuyun ve koşulları kabul ediyorsanız **İleri**’ye tıklayın..

6.  **Center Yapılandırması** sayfasında, ortamınıza bağlı olarak aşağıdaki bilgileri girin:

    |Alan|Açıklama|Açıklamalar|
    |---------|---------------|------------|
    |Yükleme Yolu|Bu, ATA Center’ın yükleneceği konumdur. Varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Center yoludur.|Varsayılan değeri olduğu gibi bırakın.|
    |Veritabanı Veri Yolu|Bu MongoDB veritabanı dosyalarının yer alacağı konumdur. Varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\data yoludur.|Boyutunuza bağlı olarak büyümek için yeriniz olan başka bir konumla değiştirin. **Not:** <ul><li>Üretim ortamlarında, kapasite planlamasına göre yeterli yeri olan bir sürücü kullanmalısınız.</li><li>Büyük dağıtımlar için veritabanı ayrı bir fiziksel diskte yer almalıdır.</li></ul>Boyutlandırma bilgileri için bkz. [ATA kapasite planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning).|
    |Veritabanı Günlük Yolu|Bu veritabanı günlük dosyalarının yer alacağı konumdur. Varsayılan olarak %programfiles%\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\data\journal yoludur.|Büyük dağıtımlar için, Veritabanı Günlüğü veritabanından ve sistem sürücüsünden ayrı bir fiziksel diskte yer almalıdır. Veritabanı Günlüğünüz için yeriniz olan başka bir konumla değiştirin.|
    |ATA Center Hizmeti IP adresi: Bağlantı Noktası|Bu, ATA Center’ın ATA Gateway bileşenlerinden gelen iletişimi dinleyecekleri IP adresidir.<br /><br />**Varsayılan bağlantı noktası:** 443|ATA Center hizmeti tarafından kullanılacak IP adresini seçmek için aşağı oka tıklayın.<br /><br />ATA Center’ın IP adresi ve bağlantı noktası, ATA Konsolu’nun IP adresi ve bağlantı noktasıyla aynı olamaz. ATA Konsolu’nun bağlantı noktasını değiştirdiğinizden emin olun.|
    |ATA Center Hizmeti SSL Sertifikası|Bu, ATA Center hizmeti tarafından kullanılacak olan sertifikadır.|Yüklü bir sertifika seçmek için anahtar simgesine tıklayın veya laboratuvar ortamında dağıtım yaparken otomatik olarak imzalanan sertifikayı işaretleyin.|
    |ATA Konsolu IP adresi|Bu, IIS tarafından ATA Konsolu için kullanılacak olan IP adresidir.|ATA Konsolu tarafından kullanılan IP adresini seçmek için aşağı oka tıklayın. **Not:** ATA Gateway’den ATA Konsolu’na daha kolay erişmek için bu IP adresini not alın.|
    |ATA Konsolu SSL sertifikası|Bu, IIS tarafından kullanılacak olan sertifikadır.|Yüklü bir sertifika seçmek için anahtar simgesine tıklayın veya laboratuvar ortamında dağıtım yaparken otomatik olarak imzalanan sertifikayı işaretleyin.|
    ![ATA Center yapılandırmasının resmi](media/ATA-Center-Configuration.JPG)

7.  ATA’yı ve bileşenlerini yüklemek ve ATA Center’la ATA Konsolu arasında bağlantı oluşturmak için **Yükle**’ye tıklayın.

8.  Yükleme tamamlandığında, ATA Konsolu’na bağlanmak için **Başlat**’a tıklayın.

    ATA Center’ın yüklemesi sırasında aşağıdaki bileşenler yüklenir ve yapılandırılır:

    -   Internet Information Services (IIS)

    -   MongoDB

    -   ATA Center hizmeti ve ATA Konsolu IIS sitesi

    -   Özel Performans İzleyicisi veri koleksiyonu kümesi

    -   Otomatik olarak imzalanan sertifikalar (yükleme sırasında seçildiyse)

> [!NOTE]
> Sorun giderme ve ürün iyileştirme işlemlerinde yardımcı olması için, MongoVue veya başka bir MongoDB eklentisini ya da tercih ettiğiniz başka bir üçüncü taraf aracını yüklemenizi öneririz. MongoVue’nun yüklenmesi için .Net Framework 3.5 gerekir.

### Yüklemeyi doğrulama

1.  Microsoft Advanced Threat Analytics Center hizmetinin çalışıp çalışmadığını denetleyin.

2.  ATA Konsolu’na bağlanmak için masaüstünde Microsoft Advanced Threat Analytics kısayoluna tıklayın. ATA Center’ı yüklerken kullandığınız kullanıcı kimlik bilgileriyle oturum açın. ATA Konsolu’nda ilk kez oturum açtığınızda, yapılandırmaya ve ATA Gateway bileşenlerinin dağıtımına devam etmek için otomatik olarak **Etki alanı bağlantı ayarları** sayfasına gidersiniz.

3.  %programfiles%\Microsoft Advanced Threat Analytics\Center\Logs varsayılan konumunda yer alan **Microsoft.Tri.Center-Errors.log** dosyasındaki hata dosyasını gözden geçirin.

>[!div class="step-by-step"]
[« Yükleme öncesi](install-ata-preinstall.md)
[2. Adım »](install-ata-step2.md)

## Ayrıca Bkz.

- [Destek için forumumuzu gözden geçirin!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](/advanced-threat-analytics/plan-design/configure-event-collection)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)


<!--HONumber=Apr16_HO4-->


