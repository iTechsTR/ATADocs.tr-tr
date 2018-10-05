---
title: E-posta bildirim ayarlarını Azure Gelişmiş tehdit koruması ayarlama | Microsoft Docs
description: Azure ATP (e-postayla veya Azure ATP Olay iletme'yi) bildirmek açıklar kuşkulu etkinlikler algıladığında
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: a2d29c9c-7ecb-4804-b74b-fde899b28648
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 18f6d38f871539cf0701b697c9d0c5d9d96a27e4
ms.sourcegitcommit: 27cf312b8ebb04995e4d06d3a63bc75d8ad7dacb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48783551"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="integrate-with-syslog"></a>Syslog ile tümleştirme

Azure ATP, sistem durumu uyarılarını yanı sıra şüpheli etkinlikler ve sorunları güvenlik uyarıları Syslog sunucunuza bildirim göndererek algıladığında size bildirebilir. Syslog bildirimlerini etkinleştirirseniz, aşağıdaki şekilde ayarlayabilirsiniz:

1.  Syslog bildirimlerini yapılandırmadan önce, SIEM yöneticinizle birlikte çalışarak aşağıdaki bilgileri bulun:

    -   SIEM sunucusunun FQDN değeri veya IP adresi

    -   SIEM sunucusunun dinlediği bağlantı noktası

    -   Hangi aktarım kullanılacak: UDP, TCP veya TLS (güvenli Syslog)

    -   Veriler gönderilirken kullanılacak biçim, RFC 3164 veya 5424

2.  Çalışma alanı URL'sini girin.

3.  Azure Active Directory kullanıcı adınızı ve parolanızı girin ve tıklayın **oturum**.

4.  Araç çubuğunda ayarlar seçeneğini belirtin ve **Yapılandırma**’yı seçin.

    ![Azure ATP yapılandırma ayarları simgesi](media/ATP-config-menu.png)

5.  Tıklayın **bildirimleri**ve sonra **Syslog bildirimlerini** tıklayın **yapılandırma** ve aşağıdaki bilgileri girin:

    |Alan|Açıklama|
    |---------|---------------|
    |Algılayıcı|Belirlenen algılayıcı Syslog olaylarını toplamak ve bunları SIEM sunucusuna iletme için sorumlu seçin.|
    |Hizmet uç noktası|Syslog sunucunuzun FQDN’sini girin ve isteğe bağlı olarak bağlantı noktası numarasını (varsayılan 514) değiştirin|
    |Aktarım|UDP, TCP veya TLS (güvenli Syslog) olabilir|
    |Biçim|Bu SIEM sunucusuna - RFC 5424 veya RFC 3164 olayları göndermek için Azure ATP kullandığı biçimdir.|

 ![Azure ATP Syslog sunucusu ayarları resmi](media/atp-syslog.png)

6. Hangi olayların Syslog sunucunuza göndermeyi seçebilirsiniz. Altında **Syslog bildirimlerini**, Syslog sunucunuza - yeni güvenlik uyarıları, güncelleştirilmiş güvenlik uyarıları ve yeni sistem durumu sorunları hangi bildirimlerin gönderilmesi gerektiğini belirtin.


## <a name="see-also"></a>Ayrıca Bkz.

- [Hassas hesaplar ile çalışma](sensitive-accounts.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)