---
title: "Kuşkulu Etkinliklerle Çalışma | Microsoft ATA"
description: "ATA tarafından belirlenen kuşkulu etkinliklerin nasıl gözden geçirileceğini açıklar"
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 44d7c899-816c-4f7f-91d3-84a09d291a24
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 050f1ef0b39d69b64ede53243a7fa2d33d0e4813
ms.openlocfilehash: 30fbeb0682bd4b253d7a6eb52b8b31e487b363cb


---

*Uygulama hedefi: Advanced Threat Analytics sürüm 1.7*



# Kuşkulu Etkinliklerle Çalışma
Bu konu başlığı altında, Advanced Threat Analytics ile çalışmanın temelleri açıklanır.

## Saldırı zaman çizelgesinde kuşkulu etkinlikleri gözden geçirme
ATA Konsolu’nda oturum açtıktan sonra, otomatik olarak açık **Kuşkulu Etkinlikler Zaman Çizelgesi**’ne gelirsiniz. Kuşkulu etkinlikler, en yenileri zaman çizelgesinin en üstünde olacak şekilde kronolojik sırayla listelenir.
Her kuşkulu etkinliğin aşağıdaki bilgileri bulunur:

-   Katılan varlıklar; örneğin kullanıcılar, bilgisayarlar, sunucular, etki alanı denetleyicileri ve kaynaklar.

-   Kuşkulu etkinliklerin zamanı ve zaman çerçevesi.

-   Kuşkulu etkinliğin önem derecesi; Yüksek, Orta veya Düşük

-   Durum: Açık, çözüldü veya çıkarıldı.

-   Yapılabilecekler

    -   Kuşkulu etkinliği e-postayla kuruluşunuzdaki diğer kişilerle paylaşın.

    -   Kuşkulu etkinliği Excel’e aktarma.

    -   Kuşkulu etkinliğe bir not ekleme.

    -   Kuşkulu etkinlik için giriş sağlama.

-   Kuşkulu etkinliğin nasıl yanıtlanacağına ilişkin öneriler sağlar.

> [!NOTE]
> -   Farenizi bir kullanıcı veya bilgisayarın üzerine getirdiğinizde, varlık hakkında ek bilgi sağlayan bir varlık mini profili görüntülenir ve varlığın bağlantılı olduğu kuşkulu etkinliklerin sayısını içerir.
> -   Varlığın üzerine tıkladığınızda, kullanıcının veya bilgisayarın varlık profiline gidersiniz.

![ATA kuşkulu etkinlikler zaman çizelgesinin resmi](media/ATA-Suspicious-Activity-Timeline.JPG)

## Kuşkulu etkinlikler listesini filtreleme
Kuşkulu etkinlikler listesini filtrelemek için:

1.  Ekranın sol tarafındaki **Filtre ölçütü** bölmesinde şunlardan birini seçin: **Tümü**, **Açık**, **Çözüldü** veya **Çıkarıldı**.

2.  Listeyi daha fazla filtrelemek için, **Yüksek**, **Orta** veya **Düşük** ayarını seçin.

**Kuşkulu etkinliğin önem derecesi**

-   **Düşük**

    Kötü amaçlı kullanıcıların veya yazılımların kuruluş verilerine erişim kazanması için tasarlanmış saldırılara yol açabilecek kuşkulu etkinlikleri gösterir.

-   **Orta**

    Kimlik hırsızlığı veya ayrıcalık yükseltmeyle sonuçlanabilecek daha ciddi saldırılar için belirli kimlikleri riske atabilecek kuşkulu etkinlikleri gösterir.

-   **Yüksek**

    Kimlik hırsızlığı, ayrıcalık yükseltme ve diğer etkili saldırılara yol açabilecek kuşkulu etkinlikleri gösterir

**Kuşkulu etkinliğin durumu**

-   **Açık**

    Tüm yeni kuşkulu etkinlikler bu listede gösterilir

-   **Çözüldü**

    Belirlediğiniz, araştırdığınız ve düzeltip etkisini azalttığınız kuşkulu etkinlikler için kullanılır.

    > [!NOTE]
    > Kısa bir süre içinde aynı etkinlik yeniden algılanırsa, ATA çözülmüş bir etkinliği yeniden açabilir.

-   **Çıkarıldı**

    Bunlar, el ile çıkardığınız etkinliklerdir. ATA benzer bir kuşkulu etkinlik algılarsa, yeni bir algılama oluşturulur.

## Kuşkulu etkinlik için giriş sağlama
ATA’nın sizinle ağınız hakkında daha fazla bilgi edinebilmesi için, ileriye dönük olarak kuşkulu etkinliklerin algılanmasını iyileştirmek amacıyla bazı kuşkulu etkinliklerde (DNS keşfi, Anahtar Geçişi, SMB Oturumu Numaralandırma, Anormal Davranış ve Uzaktan Yürütme) sizden giriş istenir.

1.  Giriş sağlamanıza olanak tanıyan kuşkulu etkinlikler için, giriş sorusu otomatik olarak açılır. Ağınızdaki etkinlikler hakkındaki soruları yanıtlamanız istenir ve bunların kuşkulu olarak kabul edilmesinin gerekip gerekmediği sorulur. Aşağıdaki örnekte, belirli bir bilgisayardan tarama araçlarının çalıştırılmasına izin verilip verilmeyeceği sorulmaktadır.

    ![ATA kuşkulu etkinlikler için giriş sağlama resmi](media/ATA-Input.JPG)

2.  Hayır yanıtı verirseniz, bu etkinlik kuşkulu olarak kabul edilir ve ATA herhangi bir anda bu bilgisayardan bu etkinlikle karşılaştığında uyarı alırsınız.

3.  Öte yandan evet yanıtı verirseniz, kuşkulu etkinlik çıkarılabilir ve gelecekte bu bilgisayardan bu tür etkinlikler kuşkulu etkinlik oluşturmayabilir veya otomatik olarak çıkarılan bir etkinlik oluşturabilir.

4.  Bilmiyorsanız, **İptal**’e tıklayabilirsiniz.

## Kuşkulu etkinliğin durumunu değiştirme
Kuşkulu etkinliğin geçerli durumuna tıklayıp **Açık**, **Çözüldü** veya **Çıkarıldı** ayarlarından birini seçerek, kuşkulu etkinliğin durumunu değiştirebilirsiniz.

## Ayrıca Bkz.
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [ATA algılama ayarlarıyla çalışma](working-with-detection-settings.md)
- [ATA yapılandırmasında değişiklik yapma](modifying-ata-configuration.md)



<!--HONumber=Aug16_HO5-->


