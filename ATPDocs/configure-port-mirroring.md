---
title: Azure Advanced Threat Protection dağıtırken bağlantı noktası yansıtmayı yapılandırma | Microsoft Docs
description: Bağlantı noktası yansıtma seçenekleri ve bunların Azure ATP için nasıl yapılandırılacağı açıklanır
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 9ec7eb4c-3cad-4543-bbf0-b951d8fc8ffe
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 1f59f02f73507fe29b41fd13c96a359dee2e88fc
ms.sourcegitcommit: 324dc941282f2948366afa5a919bda0b029bd59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34444609"
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="configure-port-mirroring"></a>Bağlantı Noktası Yansıtmayı Yapılandırma
> [!NOTE] 
> Bu makalede, Azure ATP tek başına algılayıcı Azure ATP algılayıcı yerine yalnızca dağıttığınızda geçerlidir. Azure ATP tek başına algılayıcı kullanmanız gerekip gerekmediğini belirlemek için bkz: [dağıtımınız için doğru algılayıcılar seçme](atp-capacity-planning.md#choosing-the-right-sensor-type-for-your-deployment).
 
Azure ATP tarafından kullanılan ana veri kaynağı, etki alanı denetleyicilerinden gelen ve giden ağ trafiğinin derin paket incelemesi ' dir. Azure ATP'ın ağ trafiğini görebilmesi bağlantı noktası yansıtmayı yapılandırma, veya bir ağ TAP kullanın.

Bağlantı noktası yansıtma için, izlenecek her etki alanı denetleyicisinde **bağlantı noktası yansıtmayı** ağ trafiğinin **kaynağı** olarak yapılandırın. Genellikle, bağlantı noktası yansıtma yapılandırmak için ağ veya sanallaştırma ekibiyle çalışmanız gerekir.
Daha fazla bilgi için satıcınızın belgelerine bakın.

Etki alanı denetleyicileri ve Azure ATP tek başına algılayıcı fiziksel veya sanal olabilir. Aşağıda, bağlantı noktası yansıtma için sık kullanılan yöntemler ve dikkat edilmesi gereken bazı noktalar verilmiştir. Daha fazla bilgi için anahtar veya sanallaştırma sunucunuzun ürün belgelerine bakın. Anahtar üreticiniz farklı bir terminoloji kullanıyor olabilir.

**Anahtarlamalı Bağlantı Noktası Çözümleyicisi (SPAN)** – Bir veya birden çok anahtar bağlantı noktasındaki ağ trafiğini, aynı anahtar üzerindeki başka bir anahtar bağlantı noktasına kopyalar. Hem Azure ATP tek başına algılayıcı ve etki alanı denetleyicileri aynı fiziksel anahtara bağlı olması gerekir.

**Uzak Anahtar Bağlantı Noktası Çözümleyicisi (RSPAN)**  – Birden çok fiziksel anahtar üzerine dağılmış kaynak bağlantı noktalarından ağ trafiğini izlemenize olanak tanır. RSPAN, kaynak trafiği özel RSPAN yapılandırmalı VLAN’a kopyalar. Bu VLAN, işleme katılan diğer anahtarlara santral oluşturması gerekir. RSPAN, Katman 2’de çalışır.

**Kapsüllenen Uzak Anahtar Bağlantı Noktası Çözümleyicisi (ERSPAN)** – Katman 3’te çalışan Cisco’ya özel bir teknolojidir. ERSPAN, VLAN santrallerine gerek kalmadan anahtarlar arasındaki trafiği izlemenize olanak tanır. ERSPAN izlenen ağ trafiğini kopyalamak için genel yönlendirme kapsüllemesini (GRE) kullanır. Azure ATP şu anda ERSPAN trafiğini doğrudan alamaz. Azure ATP'ın ERSPAN trafiğiyle çalışması bir anahtar veya trafiğin yönlendiricinin ERSPAN trafiğini kapsülden çıkarılan olduğu hedef olarak yapılandırılması gerekir. Ardından anahtar veya yönlendirici SPAN veya rspan'ı kullanarak Azure ATP tek başına algılayıcı kapsülden çıkarılan trafiği iletecek şekilde yapılandırın.

> [!NOTE]
> Bağlantı noktası yansıtılan etki alanı denetleyicisi bir WAN bağlantısı üzerinden bağlanıyorsa, WAN bağlantısının ERSPAN trafiğinden gelen ek yükü işleyebileceğinden emin olun.
> Azure ATP yalnızca trafiği aynı şekilde NIC ve etki alanı denetleyicisi ulaştığında trafiğini izleme destekler. Azure ATP, farklı bağlantı noktaları için ayrılmış trafiği olduğunda trafiği izleme desteklemez.

## <a name="supported-port-mirroring-options"></a>Desteklenen bağlantı noktası yansıtma seçenekleri

|Azure ATP tek başına algılayıcısı|Etki Alanı Denetleyicisi|Dikkat Edilecekler|
|---------------|---------------------|------------------|
|Sanal|Aynı ana bilgisayarda sanal|Sanal anahtarın bağlantı noktası yansıtmayı desteklemesi gerekir.<br /><br />Sanal makinelerden birinin kendi başına başka bir ana bilgisayara taşınması, bağlantı noktası yansıtmanın kesilmesine neden olabilir.|
|Sanal|Farklı ana bilgisayarlarda sanal|Sanal anahtarınızın bu senaryoyu desteklediğinden emin olun.|
|Sanal|Fiziksel|Aksi takdirde Azure ATP Azure ATP bulut hizmetine gönderdiği trafiği bile ana bilgisayar ve gelen tüm trafiği görür özel bir ağ bağdaştırıcısı gerektirir.|
|Fiziksel|Sanal|Sanal anahtarınızın bu senaryoyu desteklediğinden ve fiziksel anahtarlarınızdaki bağlantı noktası yansıtmanın senaryoyu temel aldığından emin olun:<br /><br />Sanal ana bilgisayar aynı fiziksel anahtardaysa, bir anahtar düzeyi yayılması yapılandırmanız gerekir.<br /><br />Sanal ana bilgisayar farklı bir anahtardaysa, RSPAN veya ERSPAN yapılandırmanız gereken&#42;.|
|Fiziksel|Aynı anahtarda fiziksel|Fiziksel anahtar SPAN/Bağlantı Noktası Yansıtma’yı desteklemelidir.|
|Fiziksel|Farklı anahtarda fiziksel|Fiziksel anahtarların ERSPAN&#42; veya RSPAN’ı desteklemesi gerekir.|
&#42;ERSPAN trafiğini ATP tarafından çözümlenmeden önce kapsüllemeyi açma işlemi gerçekleştirildiğinde yalnızca desteklenir.

> [!NOTE]
> Etki alanı denetleyicileri ve onların bağlandığı Azure ATP tek başına algılayıcı için beş dakika içinde birbiriyle eşitlenmesi olduğundan emin olun.

**Sanallaştırma kümeleriyle çalışıyorsanız:**

-   Azure ATP tek başına algılayıcı ile bir sanal makine sanallaştırma kümesinde çalışan her etki alanı denetleyicisi için etki alanı denetleyicisi ve Azure ATP tek başına algılayıcı arasında benzeşimi yapılandırın. Böylece etki alanı denetleyicisi Azure ATP tek başına algılayıcı kümedeki başka bir ana bilgisayara taşındığında, izler. Bu, az sayıda etki alanı denetleyicisi olduğunda iyi çalışır.

 > [!NOTE]
 > Ortamınız farklı ana bilgisayarlarda Sanal-Sanal (RSPAN) iletişimi destekliyorsa benzeşim hakkında endişelenmeniz gerekmez.
 
-   Azure ATP tek başına algılayıcı doğru boyutta tüm DC'leri izleme işlemek için tek başına emin olmak için bu seçeneği deneyin: her sanallaştırma ana bilgisayarına bir sanal makine yükleyin ve bir Azure ATP tek başına algılayıcı her ana bilgisayara yükleyin. Tüm küme üzerinde çalışan etki alanı denetleyicilerini izlemek için her Azure ATP tek başına algılayıcı yapılandırın. Bu şekilde, etki alanı denetleyicilerinin çalıştığı herhangi bir ana bilgisayar izlenir.

Bağlantı noktası yansıtma yapılandırıldıktan sonra bağlantı noktası yansıtma Azure ATP tek başına algılayıcı yüklemeden önce çalışır durumda olduğunu doğrulayın.

## <a name="see-also"></a>Ayrıca bkz:
- [Olay iletme özelliğini yapılandırma](configure-event-forwarding.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)