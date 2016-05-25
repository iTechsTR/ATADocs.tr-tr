---
# required metadata

title: ATA’yı Yükleme - 5. Adım | Microsoft Advanced Threat Analytics
description: ATA’yı yükleme işleminin beşinci adımı, ATA Gateway bileşeniniz için ayarları yapılandırmanıza yardımcı olur.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 2a5b6652-2aef-464c-ac17-c7e5f12f920f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ATA’yı Yükleme - 5. Adım

>[!div class="step-by-step"]
[« 4. Adım](install-ata-step4.md)
[6. Adım »](install-ata-step6.md)


## 5. Adım ATA Gateway ayarlarını yapılandırma
ATA Gateway yüklendikten sonra, ATA Gateway’in ayarlarını yapılandırmak için aşağıdaki adımları gerçekleştirin.

1.  ATA Gateway makinesinde, ATA Konsolu’nda **Yapılandırma**’ya tıklayın ve **ATA Gateway Bileşenleri** sayfasını seçin.

2.  Aşağıdaki bilgileri girin.



  - **Açıklama**: <br>ATA Gateway’in açıklamasını girin (isteğe bağlı).
  - **Etki alanı denetleyicileri** (gerekli): <br>Denetleyicilerin listesi hakkında ek bilgi için aşağıya bakın.<br>Etki alanı denetleyicinizin tam FQDN değerini girin ve bunu listeye eklemek için artı işaretine tıklayın. Örneğin, **dc01.contoso.com**<br /><br />![Örnek FDQN resmi](media/ATAGWDomainController.png)<br>Listedeki ilk etki alanı denetleyicisinde yer alan nesneler LDAP sorguları yoluyla eşitlenir. Etki alanının boyutuna bağlı olarak bu işlem biraz zaman alabilir.<br>
  **Not:** <br>İlk etki alanı denetleyicisinin salt okunur **olmamasına** dikkat edin. Salt okunur etki alanı denetleyicileri ancak ilk eşitleme tamamlandıktan sonra eklenmelidir.<br>


 - **Yakalama Ağ bağdaştırıcıları** (gerekli):<br>Etki alanı trafiğini almak üzere hedef yansıtma etki alanı olarak yapılandırılmış anahtara bağlanan ağ bağdaştırıcılarını seçin.|Yakalama ağ bağdaştırıcısını seçin.
    ![Gateway ayarlarını yapılandırma resmi](media/ATA-Config-GW-Settings.jpg)

3.  **Kaydet**'e tıklayın..

    > [!NOTE]
    > ATA Gateway hizmetinin ilk kez başlatılması birkaç dakika sürebilir çünkü ATA Gateway tarafından kullanılan ağ yakalama ayrıştırıcılarının önbelleğini oluşturur.

Aşağıdaki bilgiler, **Etki Alanı Denetleyicileri** listesine girdiğiniz sunucular için geçerlidir.

-   Listedeki ilk etki alanı denetleyicisi, ATA Gateway tarafından etki alanındaki nesnelerin LDAP sorguları yoluyla eşitlenmesinde kullanılır. Etki alanının boyutuna bağlı olarak bu işlem biraz zaman alabilir.

-   ATA Gateway tarafından bağlantı noktası yansıtma yoluyla trafiği izlenmekte olan tüm etki alanı denetleyicilerinin, **Etki Alanı Denetleyicileri** listesinde yer alması gerekir. Bir etki alanı denetleyicisi **Etki Alanı Denetleyicileri** listesinde yer almıyorsa, kuşkulu etkinlikleri algılama özelliği beklendiği gibi çalışmayabilir.

-   İlk etki alanı denetleyicisinin salt okunur bir etki alanı denetleyicisi (RODC) **olmamasına** dikkat edin.

    Salt okunur etki alanı denetleyicileri ancak ilk eşitleme tamamlandıktan sonra eklenmelidir.

-   Listedeki en az bir etki alanı denetleyicisi genel katalog sunucusu olmalıdır. Bu ATA’nın ormandaki diğer etkin alanlarında yer alan bilgisayar ve kullanıcı nesnelerini çözümleyebilmesine olanak tanır.

Yapılandırma değişiklikleri, ATA Gateway ile ATA Center arasındaki bir sonraki zamanlanmış eşitlemede ATA Gateway’e uygulanır.

### Yüklemeyi doğrulama:
ATA Gateway’in başarıyla dağıtıldığını doğrulamak için aşağıdakileri denetleyin:

1.  Microsoft Advanced Threat Analytics Gateway hizmetinin çalışıp çalışmadığını denetleyin. ATA Gateway ayarlarını kaydettikten sonra, hizmetin başlatılması birkaç dakika sürebilir.

2.  Hizmet başlatılmazsa, “%programfiles%\Microsoft Advanced Threat Analytics\Gateway\Logs” varsayılan klasöründe yer alan “Microsoft.Tri.Gateway-Errors.log” dosyasını gözden geçirin ve “transfer” veya “service start” girdilerini arayın.

3.  Şu Microsoft ATA Gateway performans sayaçlarını denetleyin:

    -   **AğDinleyicisi Yakalanan İleti Sayısı/Sn**: Bu sayaç ATA tarafından saniyede yakalanan ileti sayısını izler. Değer, izlenen etki alanı denetleyicilerinin sayısına ve her etki alanı denetleyicisinin ne kadar meşgul olduğuna bağlı olarak, 150 dolayında olabileceği gibi binlerce de olabilir. Tek veya çift basamaklı değerler, bağlantı noktası yansıtma yapılandırması bir sorun olduğunu gösteriyor olabilir.

    -   **VarlıkAktarımı Etkinlik Aktarım Sayısı/Sn**: Bu değer, her birkaç saniyede bir birkaç yüz dolayında olmalıdır.

4.  Bu yüklenen ilk ATA Gateway ise, birkaç dakika sonra ATA Konsolu’nda oturum açın ve açık ekranın sağ tarafından çekerek bildirim bölmesini açın. Konsolun sağ tarafındaki bildirim çubuğunda **Son Öğrenilen Varlıklar** listesini görmelisiniz.

5.  Yüklemenin başarıyla tamamlandığını doğrulamak için:

    Konsolda, arama çubuğunda bir şey için (etki alanınızdaki bir kullanıcı veya grup gibi) arama yapın.

    Performans İzleyicisi'ni açın. Performans ağacında **Performans İzleyicisi**’ne tıklayın ve ardından **Sayaç Eklemek** için artı simgesine tıklayın. **Microsoft ATA Gateway**’i genişletin, ekranı aşağı kaydırarak **Ağ Dinleyicisi Saniyede Yakalanan İleti Sayısı**’na gelin ve bunu ekleyin. Ardından, etkinliği grafikte gördüğünüzden emin olun.

    ![Performans sayaçlarını ekleme resmi](media/ATA-performance-monitoring-add-counters.png)


>[!div class="step-by-step"]
[« 4. Adım](install-ata-step4.md)
[6. Adım »](install-ata-step6.md)

## Ayrıca Bkz.

- [Destek için forumumuzu gözden geçirin!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)
- [Olay koleksiyonunu yapılandırma](/advanced-threat-analytics/plan-design/configure-event-collection)
- [ATA önkoşulları](/advanced-threat-analytics/plan-design/ata-prerequisites)


<!--HONumber=Apr16_HO4-->


