---
title: "Advanced Threat Analytics’i Yükleme - 5. Adım | Microsoft Docs"
description: "ATA’yı yükleme işleminin beşinci adımı, ATA Gateway bileşeniniz için ayarları yapılandırmanıza yardımcı olur."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 06/12/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 2a5b6652-2aef-464c-ac17-c7e5f12f920f
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 6952a239eb5f11cdfefc9ce201f9a765e61de8e8
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*



# ATA’yı Yükleme - 5. Adım
<a id="install-ata---step-5" class="xliff"></a>

>[!div class="step-by-step"]
[« 4. Adım](install-ata-step4.md)
[6. Adım »](install-ata-step6.md)


## Adım 5. ATA Gateway ayarlarını yapılandırma
<a id="step-5-configure-the-ata-gateway-settings" class="xliff"></a>
ATA Gateway yüklendikten sonra, ATA Gateway’in ayarlarını yapılandırmak için aşağıdaki adımları gerçekleştirin.

1.  ATA konsolunda, **Yapılandırma**’ya gidin ve **Sistem** altında **Ağ Geçitleri**’ni seçin.
   
     ![Gateway ayarlarını yapılandırma resmi](media/ata-gw-config-1.png)


2.  Yapılandırmak istediğiniz Ağ Geçidine tıklayın ve ardından aşağıdaki bilgileri girin:

    ![Gateway ayarlarını yapılandırma resmi](media/ATA-Gateways-config-2.png)

  - **Açıklama**: ATA Gateway için bir açıklama girin (isteğe bağlı).
  - **Bağlantı Noktası Yansıtılan Etki Alanı Denetleyicileri (FQDN)** (ATA Gateway için gereklidir ve ATA Lightweight Gateway için değiştirilemez): Etki alanı denetleyicinizin tam FQDN’sini girin ve listeye eklemek için artı işaretine tıklayın. Örneğin, **dc01.contoso.com**

      Aşağıdaki bilgiler, **Etki Alanı Denetleyicileri** listesine girdiğiniz sunucular için geçerlidir:
      - ATA Gateway tarafından bağlantı noktası yansıtma yoluyla trafiği izlenmekte olan tüm etki alanı denetleyicilerinin, **Etki Alanı Denetleyicileri** listesinde yer alması gerekir. Bir etki alanı denetleyicisi **Etki Alanı Denetleyicileri** listesinde yer almıyorsa, kuşkulu etkinlikleri algılama özelliği beklendiği gibi çalışmayabilir.
      - Listedeki etki alanı denetleyicilerinden en az biri genel katalog olmalıdır. Bu ATA’nın ormandaki diğer etkin alanlarında yer alan bilgisayar ve kullanıcı nesnelerini çözümleyebilmesine olanak tanır.

  - **Yakalama Ağ bağdaştırıcıları** (gerekli):
  - Ayrılmış bir sunucudaki bir ATA Gateway için, hedef yansıtma bağlantı noktası olarak yapılandırılan ağ bağdaştırıcılarını seçin. Böylece, yansıtılmış etki alanı denetleyicisi trafiği alınır.
  - Bir ATA Lightweight Gateway söz konusu olduğunda bu, kuruluşunuzdaki diğer bilgisayarlarla iletişim için kullanılan tüm ağ bağdaştırıcıları olmalıdır.


  - **Etki alanı eşitleyici adayı**: Etki alanı eşitleyici adayı olarak ayarlanan herhangi bir ATA Gateway, ATA ile Active Directory etki alanınız arasındaki eşitlemeden sorumlu olabilir. Etki alanının büyüklüğüne bağlı olarak, ilk eşitleme biraz zaman alabilir ve yoğun kaynak kullanır. Varsayılan olarak, yalnızca ATA Gateway’ler Etki Alanı eşitleyici adayı olarak ayarlanabilir.
   Uzak yerde bulunan ATA Gateway bileşenlerinin Etki Alanı eşitleyici adayı olmasının engellenmesi önerilir.
   Etki alanı denetleyiciniz salt okunur ise, onu Etki Alanı eşitleyici adayı olarak ayarlamayın. Daha fazla bilgi için bkz. [ATA mimarisi](ata-architecture.md#ata-lightweight-gateway-features).

  > [!NOTE] 
  > ATA Gateway hizmetinin yükleme sonrası ilk kez başlatılması birkaç dakika sürebilir çünkü ağ yakalama ayrıştırıcılarının önbelleğini oluşturur.
  > Yapılandırma değişiklikleri, ATA Gateway ile ATA Center arasındaki bir sonraki zamanlanmış eşitlemede ATA Gateway’e uygulanır.

3. İsterseniz, [Syslog dinleyici ve Windows Olay İletme Koleksiyonu](configure-event-collection.md)’nu ayarlayabilirsiniz. 
4. Gelecek sürümlerde ATA Center’ı güncelleştirirken, bu ATA Gateway’in otomatik olarak güncelleştirilmesi için **ATA Gateway’i otomatik olarak güncelleştir**’i etkinleştirin.

5. **Kaydet**'e tıklayın.


## Yüklemeleri doğrulama
<a id="validate-installations" class="xliff"></a>
ATA Gateway’in başarıyla dağıtıldığını doğrulamak için aşağıdakileri denetleyin:

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

## Ayrıca bkz.
<a id="see-also" class="xliff"></a>

- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [ATA önkoşulları](ata-prerequisites.md)

