---
title: "ATA’yı Yükleme - 5. Adım | Microsoft ATA"
description: "ATA’yı yükleme işleminin beşinci adımı, ATA Gateway bileşeniniz için ayarları yapılandırmanıza yardımcı olur."
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 2a5b6652-2aef-464c-ac17-c7e5f12f920f
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e3b690767e5c6f5561a97a73eccfbf50ddb04148
ms.openlocfilehash: 168a41182128a1fc91d92a4ef11b873c04ecc6b7


---

*Uygulama hedefi: Advanced Threat Analytics sürüm 1.7*



# ATA’yı Yükleme - 5. Adım

>[!div class="step-by-step"]
[« 4. Adım](install-ata-step4.md)
[6. Adım »](install-ata-step6.md)


## Adım 5. ATA Gateway ayarlarını yapılandırma
ATA Gateway yüklendikten sonra, ATA Gateway’in ayarlarını yapılandırmak için aşağıdaki adımları gerçekleştirin.

1.  ATA konsolunda, **Yapılandırma**’ya gidin ve **Sistem** altında **Ağ Geçitleri**’ni seçin.
   
     ![Gateway ayarlarını yapılandırma resmi](media/ATA-Gateways-config-1.png)


2.  Yapılandırmak istediğiniz Ağ Geçidini seçin ve aşağıdaki bilgileri girin:

    ![Gateway ayarlarını yapılandırma resmi](media/ATA-Gateways-config-2.png)

  - **Açıklama**: ATA Gateway için bir açıklama girin (isteğe bağlı).
  - **Bağlantı Noktası Yansıtılan Etki Alanı Denetleyicileri (FQDN)** (ATA Gateway için gereklidir ve ATA Lightweight Gateway için değiştirilemez): Etki alanı denetleyicinizin tam FQDN’sini girin ve listeye eklemek için artı işaretine tıklayın. Örneğin, **dc01.contoso.com**

        The following information applies to the servers you enter in the **Domain Controllers** list:
        - All domain controllers whose traffic is being monitored via port mirroring by the ATA Gateway must be listed in the **Domain Controllers** list. If a domain controller is not listed in the **Domain Controllers** list, detection of suspicious activities might not function as expected.
        - At least one domain controller in the list should be a global catalog. This will enable ATA to resolve computer and user objects in other domains in the forest.

- **Yakalama Ağ bağdaştırıcıları** (gerekli):
  - Ayrılmış bir sunucudaki bir ATA Gateway için, hedef yansıtma bağlantı noktası olarak yapılandırılan ağ bağdaştırıcılarını seçin. Böylece, yansıtılmış etki alanı denetleyicisi trafiği alınır.
  - Bir ATA Lightweight Gateway söz konusu olduğunda bu, kuruluşunuzdaki diğer bilgisayarlarla iletişim için kullanılan tüm ağ bağdaştırıcıları olmalıdır.


 - **Etki alanı eşitleyici adayı**: Etki alanı eşitleyici adayı olarak ayarlanan herhangi bir ATA Gateway, ATA ile Active Directory etki alanınız arasındaki eşitlemeden sorumlu olabilir. Etki alanının büyüklüğüne bağlı olarak, ilk eşitleme biraz zaman alabilir ve yoğun kaynak kullanır. Varsayılan olarak, yalnızca ATA Gateway’ler Etki Alanı eşitleyici adayı olarak ayarlanabilir.
   Uzak yerde bulunan ATA Gateway bileşenlerinin Etki Alanı eşitleyici adayı olmasının engellenmesi önerilir.
   Etki alanı denetleyiciniz salt okunur ise, onu Etki Alanı eşitleyici adayı olarak ayarlamayın. Daha fazla bilgi için bkz. [ATA mimarisi](/advanced-threat-analytics/plan-design/ata-architecture#ata-lightweight-gateway-features).

> [!NOTE] 
> ATA Gateway hizmetinin yükleme sonrası ilk kez başlatılması birkaç dakika sürebilir çünkü ağ yakalama ayrıştırıcılarının önbelleğini oluşturur.
> Yapılandırma değişiklikleri, ATA Gateway ile ATA Center arasındaki bir sonraki zamanlanmış eşitlemede ATA Gateway’e uygulanır.

3. İsterseniz, [Syslog dinleyici ve Windows Olay İletme Koleksiyonu](configure-event-collection.md)’nu ayarlayabilirsiniz. 
4. Gelecek sürümlerde ATA Center’ı güncelleştirirken, bu ATA Gateway’in otomatik olarak güncelleştirilmesi için **ATA Gateway’i otomatik olarak güncelleştir**’i etkinleştirin.
3. **Kaydet**'e tıklayın.


## Yüklemeleri doğrulama
ATA Gateway’in başarıyla dağıtıldığını doğrulamak için aşağıdakileri denetleyin:

1.  **Microsoft Advanced Threat Analytics Gateway** adlı hizmetin çalışıp çalışmadığını denetleyin. ATA Gateway ayarlarını kaydettikten sonra, hizmetin başlatılması birkaç dakika sürebilir.

2.  Hizmet başlatılmazsa, varsayılan “%programfiles%\Microsoft Advanced Threat Analytics\Gateway\Logs” klasöründe yer alan “Microsoft.Tri.Gateway-Errors.log” dosyasına göz atın ve yardım için [ATA Sorunlarını Giderme](/advanced-threat-analytics/troubleshoot/troubleshooting-ata-known-errors) bölümüne bakın.

3.  Bu yüklenen ilk ATA Gateway ise, birkaç dakika sonra ATA Konsolu’nda oturum açın ve açık ekranın sağ tarafından çekerek bildirim bölmesini açın. Konsolun sağ tarafındaki bildirim çubuğunda **Son Öğrenilen Varlıklar** listesini görmelisiniz.

4.  ATA Konsolu’na bağlanmak için masaüstünde **Microsoft Advanced Threat Analytics** kısayoluna tıklayın. ATA Center’ı yüklerken kullandığınız kullanıcı kimlik bilgileriyle oturum açın.
5.  Konsolda, arama çubuğunda bir şey için (etki alanınızdaki bir kullanıcı veya grup gibi) arama yapın.
6.  Performans İzleyicisi'ni açın. Performans ağacında **Performans İzleyicisi**’ne tıklayın ve ardından **Sayaç Eklemek** için artı simgesine tıklayın. **Microsoft ATA Gateway**’i genişletin, ekranı aşağı kaydırarak **Ağ Dinleyicisi Saniyede Yakalanan PEF İleti Sayısı**’na gelin ve bunu ekleyin. Ardından, etkinliği grafikte gördüğünüzden emin olun.

    ![Performans sayaçlarını ekleme resmi](media/ATA-performance-monitoring-add-counters.png)


>[!div class="step-by-step"]
[« 4. Adım](install-ata-step4.md)
[6. Adım »](install-ata-step6.md)

## Ayrıca Bkz.

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)




<!--HONumber=Aug16_HO5-->


