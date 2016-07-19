---
title: "ATA’yı Yükleme - 5. Adım | Microsoft Advanced Threat Analytics"
description: "ATA’yı yükleme işleminin beşinci adımı, ATA Gateway bileşeniniz için ayarları yapılandırmanıza yardımcı olur."
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 2a5b6652-2aef-464c-ac17-c7e5f12f920f
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d6e7d7bef97bfc4ffde07959dd9256f0319d685f
ms.openlocfilehash: 6400a0eabefac91b418e00eb670b1329fa1b5fb5


---

# ATA’yı Yükleme - 5. Adım

>[!div class="step-by-step"]
[« 4. Adım](install-ata-step4.md)
[6. Adım »](install-ata-step6.md)


## Adım 5. ATA Gateway ayarlarını yapılandırma
ATA Gateway yüklendikten sonra, ATA Gateway’in ayarlarını yapılandırmak için aşağıdaki adımları gerçekleştirin.

1.  ATA Konsolu’nda **Yapılandırma**’ya tıklayın ve **ATA Gateway Bileşenleri** sayfasını seçin.

2.  Aşağıdaki bilgileri girin.

  - **Açıklama**: <br>ATA Gateway’in açıklamasını girin (isteğe bağlı).
  - **Bağlantı Noktası Yansıtılmış Etki Alanı Denetleyicileri (FQDN)** (ATA Gateway için gerekli olup, ATA Lightweight Gateway için ayarlanamaz): <br>Etki alanı denetleyicinizin tam FQDN değerini girin ve bunu listeye eklemek için artı işaretine tıklayın. Örneğin, **dc01.contoso.com**<br /><br />![Örnek FDQN resmi](media/ATAGWDomainController.png)

Aşağıdaki bilgiler, **Etki Alanı Denetleyicileri** listesine girdiğiniz sunucular için geçerlidir: -   ATA Gateway tarafından bağlantı noktası yansıtma yoluyla trafiği izlenmekte olan tüm etki alanı denetleyicilerinin, **Etki Alanı Denetleyicileri** listesinde yer alması gerekir. Bir etki alanı denetleyicisi **Etki Alanı Denetleyicileri** listesinde yer almıyorsa, kuşkulu etkinlikleri algılama özelliği beklendiği gibi çalışmayabilir.
-   Listedeki en az bir etki alanı denetleyicisi genel katalog sunucusu olmalıdır. Bu ATA’nın ormandaki diğer etkin alanlarında yer alan bilgisayar ve kullanıcı nesnelerini çözümleyebilmesine olanak tanır.

 - **Yakalama Ağ bağdaştırıcıları** (gerekli):<br>
     - Ayrılmış bir sunucudaki bir ATA Gateway için, hedef yansıtma bağlantı noktası olarak yapılandırılan ağ bağdaştırıcılarını seçin. Böylece, yansıtılmış etki alanı denetleyicisi trafiği alınır.
     - Bir ATA Lightweight Gateway söz konusu olduğunda bu, kuruluşunuzdaki diğer bilgisayarlarla iletişim için kullanılan tüm ağ bağdaştırıcıları olmalıdır.

![Gateway ayarlarını yapılandırma resmi](media/ATA-Config-GW-Settings.jpg)

 - **Etki alanı eşitleyici adayı**<br>
Bir etki alanı eşitleyici adayı olarak ayarlanan herhangi bir ATA Gateway bileşeni, ATA ile Active Directory etki alanınız arasında eşitlemeden sorumlu olabilir. Etki alanının büyüklüğüne bağlı olarak, ilk eşitleme biraz zaman alabilir ve yoğun kaynak kullanır. Varsayılan olarak, yalnızca ATA Gateway bileşenleri Etki Alanı eşitleyici adayı olarak ayarlanabilir. <br>Uzak yerde bulunan ATA Gateway bileşenlerinin Etki Alanı eşitleyici adayı olmasının engellenmesi önerilir.<br>Etki alanı denetleyiciniz salt okunur ise, onu Etki Alanı eşitleyici adayı olarak ayarlamayın. Daha fazla bilgi için bkz. [ATA mimarisi](/advanced-threat-analytics/plan-design/ata-architecture#ata-lightweight-gateway-features)

> [!NOTE] 
> ATA Gateway hizmetinin ilk kez başlatılması birkaç dakika sürebilir çünkü ağ yakalama ayrıştırıcılarının önbelleğini oluşturur.<br>
> Yapılandırma değişiklikleri, ATA Gateway ile ATA Center arasındaki bir sonraki zamanlanmış eşitlemede ATA Gateway’e uygulanır.



    

3. İsterseniz, [Syslog dinleyici ve Windows Olay İletme Koleksiyonu](configure-event-collection.md)’nu ayarlayabilirsiniz. 
4. Gelecek sürümlerde ATA Center’ı güncelleştirirken, bu ATA Gateway’in otomatik olarak güncelleştirilmesi için **ATA Gateway’i otomatik olarak güncelleştir**’i etkinleştirin.
3.  **Kaydet**'e tıklayın.


## Yüklemeleri doğrulama
ATA Gateway’in başarıyla dağıtıldığını doğrulamak için aşağıdakileri denetleyin:

1.  **Microsoft Advanced Threat Analytics Gateway** adlı hizmetin çalışıp çalışmadığını denetleyin. ATA Gateway ayarlarını kaydettikten sonra, hizmetin başlatılması birkaç dakika sürebilir.

2.  Hizmet başlatılmazsa, “%programfiles%\Microsoft Advanced Threat Analytics\Gateway\Logs” varsayılan klasöründe yer alan “Microsoft.Tri.Gateway-Errors.log” dosyasını gözden geçirin.

3.  Yardım için bkz. [ATA Sorunlarını Giderme](/advanced-threat-analytics/troubleshoot/troubleshooting-ata-known-errors).

4.  Bu yüklenen ilk ATA Gateway ise, birkaç dakika sonra ATA Konsolu’nda oturum açın ve açık ekranın sağ tarafından çekerek bildirim bölmesini açın. Konsolun sağ tarafındaki bildirim çubuğunda **Son Öğrenilen Varlıklar** listesini görmelisiniz.

5.  ATA Konsolu’na bağlanmak için masaüstünde **Microsoft Advanced Threat Analytics** kısayoluna tıklayın. ATA Center’ı yüklerken kullandığınız kullanıcı kimlik bilgileriyle oturum açın.
6.  Konsolda, arama çubuğunda bir şey için (etki alanınızdaki bir kullanıcı veya grup gibi) arama yapın.
7.  Performans İzleyicisi'ni açın. Performans ağacında **Performans İzleyicisi**’ne tıklayın ve ardından **Sayaç Eklemek** için artı simgesine tıklayın. **Microsoft ATA Gateway**’i genişletin, ekranı aşağı kaydırarak **Ağ Dinleyicisi Saniyede Yakalanan PEF İleti Sayısı**’na gelin ve bunu ekleyin. Ardından, etkinliği grafikte gördüğünüzden emin olun.

    ![Performans sayaçlarını ekleme resmi](media/ATA-performance-monitoring-add-counters.png)


>[!div class="step-by-step"]
[« 4. Adım](install-ata-step4.md)
[6. Adım »](install-ata-step6.md)

## Ayrıca Bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)




<!--HONumber=Jun16_HO4-->


