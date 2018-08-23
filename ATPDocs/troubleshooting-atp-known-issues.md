---
title: Azure ATP bilinen sorunları giderme | Microsoft Docs
description: Azure ATP sorunları nasıl giderebileceğinizi açıklar.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/13/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 23386e36-2756-4291-923f-fa8607b5518a
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 986dc057127e8de1e26a78dd7a138b02efeebf99
ms.sourcegitcommit: dc56b9e9533db1a2dc314b199e90191bb25adaba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/14/2018
ms.locfileid: "41734813"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*


# <a name="troubleshooting-azure-atp-known-issues"></a>Azure ATP bilinen sorunlarını giderme 


## <a name="deployment-log-location"></a>Dağıtım günlüğü konumu
 
Azure ATP dağıtım günlükleri ürünü yükleyen kullanıcının temp dizininde yer alır. Varsayılan yükleme konumunda, şu anda bulunabilir: C:\Users\Administrator\AppData\Local\Temp (veya bir dizin yukarıda % temp %). Daha fazla bilgi için [günlüklerini kullanarak ATP sorunlarını giderme](troubleshooting-atp-using-logs.md)

## <a name="proxy-authentication-problem-presents-as-licensing-error"></a>Proxy kimlik doğrulama sorunu lisans hatası sayısını gösterir.

Algılayıcı yükleme sırasında şu hatayı alıyorsunuz: **algılayıcı lisans sorunları nedeniyle kaydedilemedi.**

Dağıtım günlük girişlerini: [1C 60: 1AA8] [2018-03-24T23:59:13] i000: 2018-03-25 02:59:13.1237 bilgisi InteractiveDeploymentManager ValidateCreateSensorAsync döndürülen [\[] validateCreateSensorResult LicenseInvalid = [\]] [1 c 60 : 1AA8] [2018-03-24T23:59:56] i000: 2018-03-25 02:59:56.4856 bilgisi InteractiveDeploymentManager ValidateCreateSensorAsync döndürülen [\[] validateCreateSensorResult LicenseInvalid = [\]] [60 1 C: 1AA8] [2018-03-25T00:27:56] i000: 2018-03-25 03:27:56.7399 SensorBootstrapperApplication Engine.Quit hata ayıklama [\[] deploymentResultStatus 1602 isRestartRequired = False = [\]] [60 1 C: 15B8] [2018-03-25T00:27:56] i500: kapatılıyor, çıkış kodu: 0x642


**Neden:**

Bazı durumlarda, bir ara sunucu iletişim kurarken kimlik doğrulaması sırasında hata 401 veya 403 hatası 407 yerine Azure ATP algılayıcısını yanıt. Azure ATP algılayıcısını 401 veya 403 hatası bir ara sunucu kimlik doğrulama sorunu değil de, bir lisanslama sorunu olarak yorumlayın. 

**Çözüm:**

Algılayıcı göz atabilirsiniz emin olun. *. yapılandırılan proxy kimlik doğrulaması olmadan aracılığıyla atp.azure.com. Daha fazla bilgi edinmek, [iletişimi etkinleştirmek için proxy ayarlarını yapılandırma](configure-proxy.md).




## Azure ATP algılayıcısını NIC ekip oluşturma sorunu <a name="nic-teaming"></a>

NIC grubu oluşturma bağdaştırıcısı ile yapılandırılan bir makinede ATP algılayıcısını yüklemeye çalışırsanız, bir yükleme hatasını alıyorsunuz. NIC grubu oluşturma ile yapılandırılmış bir makine üzerinde ATP algılayıcı yüklemek istiyorsanız, lütfen aşağıdaki yönergeleri izleyin:

Henüz algılayıcı yüklemediyseniz:

1.  Gelen Npcap indirme [ https://nmap.org/npcap/ ](https://nmap.org/npcap/).
2.  Yüklü olduğu, WinPcap kaldırın.
3.  Aşağıdaki seçeneklerle Npcap yükleyin: loopback_support = Hayır & winpcap_mode = Evet
4.  Algılayıcı paketini yükleyin.

Algılayıcı zaten yüklediyseniz:

1.  Gelen Npcap indirme [ https://nmap.org/npcap/ ](https://nmap.org/npcap/).
2.  Algılayıcı kaldırın.
3.  WinPcap kaldırın.
4.  Aşağıdaki seçeneklerle Npcap yükleyin: loopback_support = Hayır & winpcap_mode = Evet
5.  Algılayıcı paketini yeniden yükleyin.

## <a name="windows-defender-atp-integration-issue"></a>Windows Defender ATP tümleştirme sorunu

Azure Gelişmiş tehdit koruması, Azure ATP Windows Defender ATP ile tümleştirmenize olanak tanır. 

## <a name="vmware-virtual-machine-sensor-issue"></a>VMware sanal makine algılayıcı sorunu

VMware sanal makinelerindeki bir Azure ATP algılayıcısını varsa, izleme uyarısı alabilirsiniz **ağ trafiğinin bir kısmı analiz edilmiyor**. Bu, bir VMware yapılandırma uyuşmazlık nedeniyle olur.

Bu sorunu çözmek için:

Aşağıdaki ayarlar **0** veya **devre dışı** sanal makinenin NIC yapılandırması: TsoEnable, LargeSendOffload, tso veri boşaltma, büyük TSO boşaltma.
> [!NOTE]
> Azure ATP algılayıcı için yalnızca devre dışı bırakmanız **IPv4 TSO boşaltma'yı** NIC yapılandırması altında.

 ![VMware algılayıcı sorunu](./media/vm-sensor-issue.png)

## <a name="see-also"></a>Ayrıca Bkz.
- [Azure ATP önkoşulları](atp-prerequisites.md)
- [Azure ATP kapasite planlaması](atp-capacity-planning.md)
- [Olay koleksiyonunu yapılandırma](configure-event-collection.md)
- [Windows olay iletme özelliğini yapılandırma](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [ATP forumuna bakın!](https://aka.ms/azureatpcommunity)