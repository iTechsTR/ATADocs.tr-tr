---
title: Azure Gelişmiş tehdit koruması dağıtırken bağlantı noktası yansıtmayı yapılandırma | Microsoft Docs
description: Bağlantı noktası yansıtma seçenekleri ve bunların Azure ATP için nasıl yapılandırılacağı açıklanmaktadır.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/4/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 9ec7eb4c-3cad-4543-bbf0-b951d8fc8ffe
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 9f23426fca9602d4e9f280b2db1407060bf4db5b
ms.sourcegitcommit: 40dbce8045f689376a50275fb12e3c5c32ca8092
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/04/2018
ms.locfileid: "37799136"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="configure-port-mirroring"></a>Bağlantı noktası yansıtmayı yapılandırma
> [!NOTE] 
> Bu makalede, yalnızca Azure ATP algılayıcısını yerine Azure ATP tek başına algılayıcı dağıttığınızda geçerlidir. Azure ATP tek başına algılayıcı kullanmanız gerekip gerekmediğini belirlemek için bkz: [dağıtımınız için doğru sensörlerden seçme](atp-capacity-planning.md#choosing-the-right-sensor-type-for-your-deployment).
 
Azure ATP tarafından kullanılan ana veri kaynağı, etki alanı denetleyicilerinden gelen ve giden ağ trafiğinin derin paket incelemesi ' dir. Azure ATP'ın ağ trafiğini görebilmesi, bağlantı noktası yansıtmayı yapılandırma veya bir ağ TAP'ı kullanın.

Bağlantı noktası yansıtma için, izlenecek her etki alanı denetleyicisinde **bağlantı noktası yansıtmayı** ağ trafiğinin **kaynağı** olarak yapılandırın. Genellikle, bağlantı noktası yansıtmasını yapılandırmak için ağ veya sanallaştırma ekibiyle çalışmanız gerekir.
Daha fazla bilgi için satıcınızın belgelerine bakın.

Azure ATP tek başına algılayıcı ve etki alanı denetleyicileri, fiziksel veya sanal olabilir. Aşağıda, bağlantı noktası yansıtma için sık kullanılan yöntemler ve dikkat edilmesi gereken bazı noktalar verilmiştir. Daha fazla bilgi için anahtar veya sanallaştırma sunucunuzun ürün belgelerine bakın. Anahtar üreticiniz farklı bir terminoloji kullanıyor olabilir.

**Anahtarlamalı Bağlantı Noktası Çözümleyicisi (SPAN)** – Bir veya birden çok anahtar bağlantı noktasındaki ağ trafiğini, aynı anahtar üzerindeki başka bir anahtar bağlantı noktasına kopyalar. Hem Azure ATP tek başına algılayıcı ve etki alanı denetleyicileri aynı fiziksel anahtara bağlanması gerekir.

**Uzak Anahtar Bağlantı Noktası Çözümleyicisi (RSPAN)**  – Birden çok fiziksel anahtar üzerine dağılmış kaynak bağlantı noktalarından ağ trafiğini izlemenize olanak tanır. RSPAN, kaynak trafiği özel RSPAN yapılandırmalı VLAN’a kopyalar. Bu VLAN, işleme katılan diğer anahtarlara santral oluşturması gerekir. RSPAN, Katman 2’de çalışır.

**Kapsüllenen Uzak Anahtar Bağlantı Noktası Çözümleyicisi (ERSPAN)** – Katman 3’te çalışan Cisco’ya özel bir teknolojidir. ERSPAN, VLAN santrallerine gerek kalmadan anahtarlar arasındaki trafiği izlemenize olanak tanır. ERSPAN izlenen ağ trafiğini kopyalamak için genel yönlendirme kapsüllemesini (GRE) kullanır. Azure ATP şu anda ERSPAN trafiğini doğrudan alamaz. Azure ATP'ın ERSPAN trafiğiyle çalışması bir anahtar veya kapsülden trafiği için yönlendiricinin ERSPAN trafiğini kapsülden çıkarılan olduğu hedef olarak yapılandırılması gerekir. Ardından anahtar veya yönlendirici SPAN veya rspan'ı kullanarak Azure ATP tek başına algılayıcı kapsülden çıkarılan trafiği iletecek şekilde yapılandırın.

> [!NOTE]
> Bağlantı noktası yansıtılan etki alanı denetleyicisi bir WAN bağlantısı üzerinden bağlanıyorsa, WAN bağlantısının ERSPAN trafiğinden gelen ek yükü işleyebileceğinden emin olun.
> Azure ATP, yalnızca, trafik NIC'ye ve etki alanı denetleyicisi aynı şekilde ulaştığında trafik izlemeyi destekler. Azure ATP trafik farklı bağlantı noktalarına bölündüğünde trafik izlemeyi desteklemez.

## <a name="supported-port-mirroring-options"></a>Desteklenen bağlantı noktası yansıtma seçenekleri

|Azure ATP tek başına algılayıcı|Etki Alanı Denetleyicisi|Dikkat Edilecekler|
|---------------|---------------------|------------------|
|Sanal|Aynı ana bilgisayarda sanal|Sanal anahtarın bağlantı noktası yansıtmayı desteklemesi gerekir.<br /><br />Sanal makinelerden birinin kendi başına başka bir ana bilgisayara taşınması, bağlantı noktası yansıtmanın kesilmesine neden olabilir.|
|Sanal|Farklı ana bilgisayarlarda sanal|Sanal anahtarınızın bu senaryoyu desteklediğinden emin olun.|
|Sanal|Fiziksel|Aksi takdirde Azure ATP tüm konak Azure ATP bulut hizmetine gönderdiği trafiği bile içine ve dışına gelen trafiği gördüğü özel bir ağ bağdaştırıcısı gerektirir.|
|Fiziksel|Sanal|Sanal anahtarınızın bu senaryoyu desteklediğinden ve fiziksel anahtarlarınızdaki bağlantı noktası yansıtmanın senaryoyu temel aldığından emin olun:<br /><br />Sanal ana bilgisayar aynı fiziksel anahtardaysa, bir anahtar düzeyi yayılması yapılandırmanız gerekir.<br /><br />Sanal ana bilgisayar farklı bir anahtardaysa, ERSPAN ya da rspan'ı yapılandırmanıza gerek&#42;.|
|Fiziksel|Aynı anahtarda fiziksel|Fiziksel anahtar SPAN/Bağlantı Noktası Yansıtma’yı desteklemelidir.|
|Fiziksel|Farklı anahtarda fiziksel|Fiziksel anahtarların ERSPAN&#42; veya RSPAN’ı desteklemesi gerekir.|

&#42;Trafik ATP tarafından çözümlenmeden önce kapsüllemeyi açma işlemi gerçekleştirildiğinde ERSPAN yalnızca desteklenir.

> [!NOTE]
> Etki alanı denetleyicileri ve onların bağlandığı Azure ATP tek başına algılayıcı için beş dakika içinde birbiriyle eşitlenmesi sahip olduğunuzdan emin olun.

**Sanallaştırma kümeleriyle çalışıyorsanız:**

-   Azure ATP tek başına algılayıcı ile bir sanal makinedeki sanallaştırma kümesinde çalışan her etki alanı denetleyicisi için etki alanı denetleyicisi ve tek başına Azure ATP algılayıcısını arasında benzeşimi yapılandırın. Etki alanı denetleyicisi tek başına Azure ATP algılayıcısını kümedeki başka bir konağa taşındığında bu şekilde, izler. Bu, az sayıda etki alanı denetleyicisi olduğunda iyi çalışır.

 > [!NOTE]
 > Ortamınız farklı ana bilgisayarlarda Sanal-Sanal (RSPAN) iletişimi destekliyorsa benzeşim hakkında endişelenmeniz gerekmez.
 
-   Azure ATP tek başına algılayıcı doğru boyutlarda tüm DC'leri izleme işlemini yapabilecek şekilde başlarına emin olmak için bu seçeneği deneyin: her sanallaştırma ana bilgisayarına bir sanal makine yükleyin ve bir Azure ATP tek başına algılayıcı her ana bilgisayara yükleyin. Tüm küme üzerinde çalışan etki alanı denetleyicilerini izlemek için her bir Azure ATP tek başına algılayıcı yapılandırın. Bu şekilde, etki alanı denetleyicilerinin çalıştığı her ana bilgisayar izlenir.

Bağlantı noktası yansıtmayı yapılandırdıktan sonra bağlantı noktası yansıtma Azure ATP tek başına algılayıcı yüklemeden önce çalışır durumda olduğunu doğrulayın.

## <a name="see-also"></a>Ayrıca bkz:
- [Olay iletme'yi yapılandırma](configure-event-forwarding.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
