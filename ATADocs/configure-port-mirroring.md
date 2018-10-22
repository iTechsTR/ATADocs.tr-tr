---
title: Advanced Threat Analytics dağıtımında Bağlantı Noktası Yansıtmayı yapılandırma | Microsoft Docs
description: Bağlantı noktası yansıtma seçenekleri ve bunların ATA için nasıl yapılandırılacağı açıklanır.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: cdaddca3-e26e-4137-b553-8ed3f389c460
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: b8b9f3b1eeb36e3a4af949d7165ce0a46225b858
ms.sourcegitcommit: 59ed430fa0cd8ac34a70609026ec5fc2f5972f57
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2018
ms.locfileid: "49480659"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*



# <a name="configure-port-mirroring"></a>Bağlantı Noktası Yansıtmayı Yapılandırma
> [!NOTE] 
> Bu makale yalnızca ATA Lightweight Gateway bileşenleri yerine ATA Gateway bileşenleri dağıttığınızda geçerlidir. ATA Gateway’ler kullanmanız gerekip gerekmediğini belirlemek için bkz. [Dağıtımınız için doğru ağ geçitlerini seçme](ata-capacity-planning.md#choosing-the-right-gateway-type-for-your-deployment).
 
ATA tarafından kullanılan ana veri kaynağı, etki alanı denetleyicilerinizden gelen ve giden ağ trafiğinin derin paket incelemesidir. ATA’nın ağ trafiğini görebilmesi için, bağlantı noktası yansıtmayı yapılandırmanız veya bir Ağ TAP kullanmanız gerekir.

Bağlantı noktası yansıtma için, izlenecek her etki alanı denetleyicisinde **bağlantı noktası yansıtmayı** ağ trafiğinin **kaynağı** olarak yapılandırın. Genellikle, bağlantı noktası yansıtmasını yapılandırmak için ağ veya sanallaştırma ekibiyle çalışmanız gerekir.
Daha fazla bilgi için satıcınızın belgelerine bakın.

Etki alanı denetleyicileriniz ve ATA Gateway sunucularınız fiziksel veya sanal olabilir. Aşağıda, bağlantı noktası yansıtma için sık kullanılan yöntemler ve dikkat edilmesi gereken bazı noktalar verilmiştir. Daha fazla bilgi için anahtar veya sanallaştırma sunucunuzun ürün belgelerine bakın. Anahtar üreticiniz farklı bir terminoloji kullanıyor olabilir.

**Anahtarlamalı Bağlantı Noktası Çözümleyicisi (SPAN)** – Bir veya birden çok anahtar bağlantı noktasındaki ağ trafiğini, aynı anahtar üzerindeki başka bir anahtar bağlantı noktasına kopyalar. Hem ATA Gateway hem de etki alanı denetleyicileri aynı fiziksel anahtara bağlı olmalıdır.

**Uzak Anahtar Bağlantı Noktası Çözümleyicisi (RSPAN)**  – Birden çok fiziksel anahtar üzerine dağılmış kaynak bağlantı noktalarından ağ trafiğini izlemenize olanak tanır. RSPAN, kaynak trafiği özel RSPAN yapılandırmalı VLAN’a kopyalar. Bu VLAN, işleme katılan diğer anahtarlara santral oluşturması gerekir. RSPAN, Katman 2’de çalışır.

**Kapsüllenen Uzak Anahtar Bağlantı Noktası Çözümleyicisi (ERSPAN)** – Katman 3’te çalışan Cisco’ya özel bir teknolojidir. ERSPAN, VLAN santrallerine gerek kalmadan anahtarlar arasındaki trafiği izlemenize olanak tanır. ERSPAN izlenen ağ trafiğini kopyalamak için genel yönlendirme kapsüllemesini (GRE) kullanır. ATA şu anda ERSPAN trafiğini doğrudan alamamaktadır. ERSPAN trafiğiyle çalışması Ata'nın bir anahtar veya kapsülden trafiği için yönlendiricinin ERSPAN trafiğini kapsülden çıkarılan olduğu hedef olarak yapılandırılması gerekir. Ardından anahtar veya yönlendirici SPAN veya RSPAN kullanarak ATA Gateway'e kapsülden çıkarılan trafiği iletecek şekilde yapılandırın.

> [!NOTE]
> Bağlantı noktası yansıtılan etki alanı denetleyicisi bir WAN bağlantısı üzerinden bağlanıyorsa, WAN bağlantısının ERSPAN trafiğinden gelen ek yükü işleyebileceğinden emin olun.
> ATA yalnızca, trafik NIC’ye ve etki alanı denetleyicisine aynı şekilde ulaştığında trafik izlemeyi destekler. Trafik farklı bağlantı noktalarına bölündüğünde ATA trafik izlemeyi desteklemez.

## <a name="supported-port-mirroring-options"></a>Desteklenen bağlantı noktası yansıtma seçenekleri

|ATA Gateway|Etki Alanı Denetleyicisi|Dikkat Edilecekler|
|---------------|---------------------|------------------|
|Sanal|Aynı ana bilgisayarda sanal|Sanal anahtarın bağlantı noktası yansıtmayı desteklemesi gerekir.<br /><br />Sanal makinelerden birinin kendi başına başka bir ana bilgisayara taşınması, bağlantı noktası yansıtmanın kesilmesine neden olabilir.|
|Sanal|Farklı ana bilgisayarlarda sanal|Sanal anahtarınızın bu senaryoyu desteklediğinden emin olun.|
|Sanal|Fiziksel|Aksi takdirde ATA tüm giriş ve çıkış konağın, ATA Center'a gönderdiği trafiği bile gelen trafiği gördüğü özel bir ağ bağdaştırıcısı gerektirir.|
|Fiziksel|Sanal|Sanal anahtarınızın bu senaryoyu desteklediğinden ve fiziksel anahtarlarınızdaki bağlantı noktası yansıtmanın senaryoyu temel aldığından emin olun:<br /><br />Sanal ana bilgisayar aynı fiziksel anahtardaysa, bir anahtar düzeyi yayılması yapılandırmanız gerekir.<br /><br />Sanal ana bilgisayar farklı bir anahtardaysa, ERSPAN ya da rspan'ı yapılandırmanıza gerek&#42;.|
|Fiziksel|Aynı anahtarda fiziksel|Fiziksel anahtar SPAN/Bağlantı Noktası Yansıtma’yı desteklemelidir.|
|Fiziksel|Farklı anahtarda fiziksel|Fiziksel anahtarların ERSPAN&#42; veya RSPAN’ı desteklemesi gerekir.|

&#42; ERSPAN’ın desteklenmesi için, trafik ATA tarafından çözümlenmeden önce kapsüllemeyi açma işlemi yapılmalıdır.

> [!NOTE]
> Etki alanı denetleyicileri ve onların bağlandığı ATA Gateway'ler için beş dakika içinde birbiriyle eşitlenmesi sahip olduğunuzdan emin olun.

**Sanallaştırma kümeleriyle çalışıyorsanız:**

-   ATA Gateway’in bulunduğu bir sanal makinedeki sanallaştırma kümesinde çalışan her etki alanı denetleyicisi için, etki alanı denetleyicisiyle ATA Gateway arasında benzeşimi yapılandırın. Etki alanı denetleyicisi ATA Gateway kümedeki başka bir konağa taşındığında bu şekilde, izler. Bu, az sayıda etki alanı denetleyicisi olduğunda iyi çalışır.

> [!NOTE]
> Ortamınız farklı ana bilgisayarlarda Sanal-Sanal (RSPAN) iletişimi destekliyorsa benzeşim hakkında endişelenmeniz gerekmez.

-   ATA Gateway’lerin kendi başlarına tüm DC’leri izleme işlemini yapabilecek şekilde doğru boyutlarda olduğundan emin olmak için şu seçeneği deneyin: Her sanallaştırma ana bilgisayarına bir sanal makine yükleyin ve her ana bilgisayara bir ATA Gateway yükleyin. Her ATA Gateway’i, kümede çalışan etki alanı denetleyicilerinin tümü izleyecek şekilde yapılandırın. Bu şekilde, etki alanı denetleyicilerinin çalıştığı her ana bilgisayar izlenir.

Bağlantı noktası yansıtma yapılandırıldıktan sonra, ATA Gateway’i yüklemeden önce bağlantı noktası yansıtmanın çalışır durumda olduğunu doğrulayın.

## <a name="see-also"></a>Ayrıca Bkz.
- [Bağlantı noktası yansıtmayı doğrulama](validate-port-mirroring.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
