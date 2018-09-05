---
title: Advanced Threat Analytics’i Yükleme - 5. Adım | Microsoft Docs
description: ATA’yı yükleme işleminin beşinci adımı, ATA Gateway bileşeniniz için ayarları yapılandırmanıza yardımcı olur.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 2a5b6652-2aef-464c-ac17-c7e5f12f920f
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 50a46bad5f138344cc3e62a3fca236e98e71f904
ms.sourcegitcommit: 6f1406f28c4c2af6a36bc691ebaf4e819adc6b4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43675177"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="install-ata---step-5"></a>ATA’yı Yükleme - 5. Adım

>[!div class="step-by-step"]
[« 4. Adım](install-ata-step4.md)
[6. Adım »](install-ata-step6.md)


## <a name="step-5-configure-the-ata-gateway-settings"></a>Adım 5. ATA Gateway ayarlarını yapılandırma
ATA Gateway yüklendikten sonra, ATA Gateway’in ayarlarını yapılandırmak için aşağıdaki adımları gerçekleştirin.

1.  ATA konsolunda, **Yapılandırma**’ya gidin ve **Sistem** altında **Ağ Geçitleri**’ni seçin.
   
     ![Gateway ayarlarını yapılandırma resmi](media/ata-gw-config-1.png)


2.  Yapılandırmak istediğiniz Ağ Geçidine tıklayın ve ardından aşağıdaki bilgileri girin:

    ![Gateway ayarlarını yapılandırma resmi](media/ATA-Gateways-config-2.png)

  - **Açıklama**: ATA Gateway için bir açıklama girin (isteğe bağlı).
  - **Bağlantı Noktası Yansıtılan Etki Alanı Denetleyicileri (FQDN)** (ATA Gateway için gereklidir ve ATA Lightweight Gateway için değiştirilemez): Etki alanı denetleyicinizin tam FQDN’sini girin ve listeye eklemek için artı işaretine tıklayın. Örneğin, **dc01.contoso.com**

    Aşağıdaki bilgiler, **Etki Alanı Denetleyicileri** listesine girdiğiniz sunucular için geçerlidir:
    - ATA Gateway tarafından bağlantı noktası yansıtma yoluyla trafiği izlenmekte olan tüm etki alanı denetleyicilerinin, **Etki Alanı Denetleyicileri** listesinde yer alması gerekir. Bir etki alanı denetleyicisi **Etki Alanı Denetleyicileri** listesinde yer almıyorsa, kuşkulu etkinlikleri algılama özelliği beklendiği gibi çalışmayabilir.
    - Listedeki etki alanı denetleyicilerinden en az biri genel katalog olmalıdır. Bu, Ata'nın ormandaki diğer etki alanı içinde bilgisayar ve kullanıcı nesneleri çözmek sağlar.

  - **Yakalama Ağ bağdaştırıcıları** (gerekli):
  - Ayrılmış bir sunucudaki bir ATA Gateway için, hedef yansıtma bağlantı noktası olarak yapılandırılan ağ bağdaştırıcılarını seçin. Bunlar, yansıtılmış etki alanı denetleyicisi trafiği alır.
  - Bir ATA Lightweight Gateway söz konusu olduğunda bu, kuruluşunuzdaki diğer bilgisayarlarla iletişim için kullanılan tüm ağ bağdaştırıcıları olmalıdır.
  
  - **Etki alanı eşitleyici adayı**: Etki alanı eşitleyici adayı olarak ayarlanan herhangi bir ATA Gateway, ATA ile Active Directory etki alanınız arasındaki eşitlemeden sorumlu olabilir. Etki alanının büyüklüğüne ilk eşitleme biraz zaman alabilir ve yoğun kaynak sahiptir. Varsayılan olarak, yalnızca ATA Gateway’ler Etki Alanı eşitleyici adayı olarak ayarlanabilir.
   Herhangi bir uzak siteyi ATA Gateway, etki alanı Eşitleyici adayı engeller devre dışı bırakmanız önerilir.
   Etki alanı denetleyiciniz salt okunur ise, onu Etki Alanı eşitleyici adayı olarak ayarlamayın. Daha fazla bilgi için bkz. [ATA mimarisi](ata-architecture.md#ata-lightweight-gateway-features).

  > [!NOTE] 
  > ATA Gateway hizmetinin yükleme sonrası ilk kez başlatılması birkaç dakika sürebilir çünkü ağ yakalama ayrıştırıcılarının önbelleğini oluşturur.
  > Yapılandırma değişiklikleri ATA Gateway ve ATA Center arasındaki bir sonraki zamanlanmış eşitlemede ATA gateway'e uygulanır.

3. İsterseniz, [Syslog dinleyici ve Windows Olay İletme Koleksiyonu](configure-event-collection.md)’nu ayarlayabilirsiniz. 
4. Etkinleştirme **ATA Gateway güncelleştirme otomatik olarak** ATA Center'ı güncelleştirdiğinizde, gelecek sürümlerde bu nedenle, bu ATA Gateway otomatik olarak güncelleştirilir.

5. **Kaydet**'e tıklayın.


## <a name="validate-installations"></a>Yüklemeleri doğrulama
ATA Gateway'in başarıyla dağıtıldığını doğrulamak için aşağıdakileri denetleyin:

1.  **Microsoft Advanced Threat Analytics Gateway** adlı hizmetin çalışıp çalışmadığını denetleyin. ATA Gateway ayarlarını kaydettikten sonra, hizmetin başlatılması birkaç dakika sürebilir.

2.  Hizmet başlatılmazsa, varsayılan “%programfiles%\Microsoft Advanced Threat Analytics\Gateway\Logs” klasöründe yer alan “Microsoft.Tri.Gateway-Errors.log” dosyasına göz atın ve yardım için [ATA Sorunlarını Giderme](troubleshooting-ata-known-errors.md) bölümüne bakın.

3.  Bu yüklenen ilk ATA Gateway ise, birkaç dakika sonra ATA Konsolu’nda oturum açın ve açık ekranın sağ tarafından çekerek bildirim bölmesini açın. Konsolun sağ tarafındaki bildirim çubuğunda **Son Öğrenilen Varlıklar** listesini görmelisiniz.

4.  ATA Konsolu’na bağlanmak için masaüstünde **Microsoft Advanced Threat Analytics** kısayoluna tıklayın. ATA Center’ı yüklerken kullandığınız kullanıcı kimlik bilgileriyle oturum açın.
5.  Konsolda, arama çubuğunda bir şey için (etki alanınızdaki bir kullanıcı veya grup gibi) arama yapın.
6.  Performans İzleyicisi'ni açın. Performans ağacında **Performans İzleyicisi**’ne tıklayın ve ardından **Sayaç Eklemek** için artı simgesine tıklayın. **Microsoft ATA Gateway**’i genişletin, ekranı aşağı kaydırarak **Ağ Dinleyicisi Saniyede Yakalanan PEF İleti Sayısı**’na gelin ve bunu ekleyin. Ardından, etkinliği grafikte gördüğünüzden emin olun.

    ![Performans sayaçlarını ekleme resmi](media/ATA-performance-monitoring-add-counters.png)


>[!div class="step-by-step"]
[« 4. Adım](install-ata-step4.md)
[6. Adım »](install-ata-step6.md)



## <a name="related-videos"></a>İlgili videolar
- [ATA dağıtımı genel bakış](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)
- [ATA Gateway türü sağ seçme](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)


## <a name="see-also"></a>Ayrıca Bkz.
- [ATA POC Dağıtım Kılavuzu](http://aka.ms/atapoc)
- [ATA boyutlandırma aracı](http://aka.ms/atasizingtool)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)

