---
title: "Azure bilinen sorunlar ATP sorunlarını giderme | Microsoft Docs"
description: "Azure ATP sorunları nasıl giderebileceğinizi açıklar."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 23386e36-2756-4291-923f-fa8607b5518a
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 2895a38e2328fb7de4fe7f47d00c4e40ac854e74
ms.sourcegitcommit: 84556e94a3efdf20ca1ebf89a481550d7f8f0f69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2018
---
*Uygulandığı öğe: Azure Gelişmiş tehdit koruması*


# <a name="troubleshooting-azure-atp-known-issues"></a>Azure ATP bilinen sorunları giderme 

## <a name="azure-atp-sensor-nic-teaming-issue"></a>Azure ATP algılayıcı NIC ekip oluşturma sorunu

Bir NIC ekibi oluşturma bağdaştırıcısı ile yapılandırılmış bir makinede ATP algılayıcı yüklemeye çalışırsanız, bir yükleme hatasını alıyorsunuz. NIC grubu oluşturma ile yapılandırılmış bir makinede ATP algılayıcı yüklemek istiyorsanız, lütfen bu yönergeleri izleyin:

Henüz algılayıcı yüklemediyseniz:

1.  Gelen Npcap karşıdan [https://nmap.org/npcap/](https://nmap.org/npcap/).
2.  Yüklü olduğu şekilde WinPcap, kaldırın.
3.  Aşağıdaki seçenekler Npcap yükleyin: loopback_support = Hayır & winpcap_mode = Evet
4.  Algılayıcı paketini yükleyin.

Algılayıcı zaten yüklü ise:

1.  Gelen Npcap karşıdan [https://nmap.org/npcap/](https://nmap.org/npcap/).
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