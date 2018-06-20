---
title: E-posta bildirim ayarlarını Azure Advanced Threat Protection içinde ayarlama | Microsoft Docs
description: Azure (e-postayla veya Azure ATP Olay iletme) bildir ATP sahip açıklar kuşkulu etkinlikler algıladığında
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: a2d29c9c-7ecb-4804-b74b-fde899b28648
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 74fe9976df769ae01c58a5d66ca491c3fa8958d9
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2018
ms.locfileid: "29445997"
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*



# <a name="integrate-with-syslog"></a>Syslog ile tümleştirme

Syslog sunucunuza bildirim göndererek kuşkulu etkinlikleri ve sistem durumu uyarıları algıladığında, azure ATP size bildirebilir. Syslog bildirimlerini etkinleştirirseniz, bu uyarılar için aşağıdakileri ayarlayabilirsiniz.

1.  Syslog bildirimlerini yapılandırmadan önce, SIEM yöneticinizle birlikte çalışarak aşağıdaki bilgileri bulun:

    -   SIEM sunucusunun FQDN değeri veya IP adresi

    -   SIEM sunucusunun dinlediği bağlantı noktası

    -   Hangi aktarım kullanılacak: UDP, TCP veya TLS (güvenli Syslog)

    -   Veriler gönderilirken kullanılacak biçim, RFC 3164 veya 5424

2.  Çalışma alanı portal girin URL.

3.  Azure Active Directory kullanıcı adınızı ve parolanızı girin ve tıklayın **oturum**.

4.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![Azure ATP yapılandırma ayarları simgesi](media/ATP-config-menu.png)

5.  Tıklatın **bildirimleri**ve ardından, **Syslog bildirimleri** tıklatın **yapılandırma** ve aşağıdaki bilgileri girin:

    |Alan|Description|
    |---------|---------------|
    |Algılayıcı|Tüm Syslog olayları toplamak ve bunları SIEM sunucunuz iletmek için sorumlu olacak belirlenen algılayıcı seçin.|
    |Hizmet uç noktası|Syslog sunucunuzun FQDN’sini girin ve isteğe bağlı olarak bağlantı noktası numarasını (varsayılan 514) değiştirin|
    |Aktarım|UDP, TCP veya TLS (güvenli Syslog) olabilir|
    |Biçim|Bu olayları SIEM sunucusuna - RFC 5424 veya RFC 3164 göndermek için Azure ATP kullanan biçimidir.|

 ![Azure ATP Syslog sunucu ayarları resmi](media/atp-syslog.png)

6. Syslog sunucunuza göndermek için hangi olayların seçebilirsiniz. Altında **Syslog bildirimleri**, hangi bildirimleri Syslog sunucunuza - yeni güvenlik uyarıları, güncelleştirilmiş güvenlik uyarıları ve yeni sistem durumu sorunları gönderilmesi gerektiğini belirtin.


## <a name="see-also"></a>Ayrıca bkz:

- [Hassas hesaplar ile çalışma](sensitive-accounts.md)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)