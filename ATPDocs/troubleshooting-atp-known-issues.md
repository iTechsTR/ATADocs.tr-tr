---
title: Azure bilinen sorunlar ATP sorunlarını giderme | Microsoft Docs
description: Azure ATP sorunları nasıl giderebileceğinizi açıklar.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/10/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 23386e36-2756-4291-923f-fa8607b5518a
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 2112e9fea1f316ff12d87b3a477b78bff4457a5f
ms.sourcegitcommit: e0209c6db649a1ced8303bb1692596b9a19db60d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*


# <a name="troubleshooting-azure-atp-known-issues"></a>Azure ATP bilinen sorunları giderme 


## <a name="deployment-log-location"></a>Dağıtım günlüğü konumu
 
Azure ATP dağıtım günlükleri ürünü yükleyen kullanıcının temp dizininde bulunur. Varsayılan yükleme konumunda, şu anda bulunabilir: C:\Users\Administrator\AppData\Local\Temp (veya bir dizin % temp % yukarıda).

## <a name="azure-atp-sensor-nic-teaming-issue"></a>Azure ATP algılayıcı NIC ekip oluşturma sorunu

Bir NIC ekibi oluşturma bağdaştırıcısı ile yapılandırılmış bir makinede ATP algılayıcı yüklemeye çalışırsanız, bir yükleme hatasını alıyorsunuz. NIC grubu oluşturma ile yapılandırılmış bir makinede ATP algılayıcı yüklemek istiyorsanız, lütfen bu yönergeleri izleyin:

Henüz algılayıcı yüklemediyseniz:

1.  Gelen Npcap karşıdan [ https://nmap.org/npcap/ ](https://nmap.org/npcap/).
2.  Yüklü olduğu şekilde WinPcap, kaldırın.
3.  Aşağıdaki seçenekler Npcap yükleyin: loopback_support = Hayır & winpcap_mode = Evet
4.  Algılayıcı paketini yükleyin.

Algılayıcı zaten yüklü ise:

1.  Gelen Npcap karşıdan [ https://nmap.org/npcap/ ](https://nmap.org/npcap/).
2.  Algılayıcı kaldırın.
3.  WinPcap kaldırın.
4.  Aşağıdaki seçenekler Npcap yükleyin: loopback_support = Hayır & winpcap_mode = Evet
5.  Algılayıcı paketi yeniden yükleyin.

## <a name="windows-defender-atp-integration-issue"></a>Windows Defender ATP tümleştirme sorunu

Azure Advanced Threat Protection, Windows Defender ATP ile Azure ATP tümleştirmenize olanak sağlar. Tümleştirme şu anda yalnızca Windows Defender ATP özel Önizleme müşterisiyseniz etkin. 

## <a name="vmware-virtual-machine-sensor-issue"></a>VMware sanal makine algılayıcı sorunu

VMware sanal makineleri bir Azure ATP algılayıcı varsa izleme uyarı alabilirsiniz **olmayan bazı ağ trafiğini analiz ediliyor**. Bu VMware yapılandırma uyuşmazlık nedeniyle olur.

Bu sorunu çözmek için:

Aşağıdaki ayarları ayarlamak **0** veya **devre dışı** sanal makinenin NIC yapılandırması: TsoEnable LargeSendOffload, TSO boşaltma, çok büyük TSO boşaltma.
> [!NOTE]
> Azure ATP algılayıcılar için devre dışı bırakmak yeterlidir **TSO IPv4 boşaltma** NIC yapılandırması altında.

 ![VMware algılayıcı sorunu](./media/vm-sensor-issue.png)

## <a name="see-also"></a>Ayrıca bkz:
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)