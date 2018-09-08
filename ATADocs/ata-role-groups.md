---
title: Erişim yönetimi için Advanced Threat Analytics rol grupları | Microsoft Docs
description: ATA rol gruplarıyla çalışma konusunda yol gösterir.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 3715b69e-e631-449b-9aed-144d0f9bcee7
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: b9779476187d22e8fdd35c0958b52de527b3830c
ms.sourcegitcommit: 7f3ded32af35a433d4b407009f87cfa6099f8edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44126527"
---
*İçin geçerlidir: Advanced Threat Analytics sürüm 1.9*




# <a name="ata-role-groups"></a>ATA Rol Grupları

Rol grupları ATA için erişim yönetimini etkinleştirin. Rol gruplarını kullanarak güvenlik ekibinizdeki görevleri ayırabilir ve kullanıcılara sadece işlerini yapması için gereken miktarda erişim izni verebilirsiniz. Bu makalede erişim yönetimi ve ATA rol yetkilendirmesi açıklanır, ATA’daki rol gruplarını kullanmanıza yardımcı olan bilgiler sağlanır.

> [!NOTE]
> ATA Center’daki herhangi bir yerel yönetici, otomatik olarak Microsoft Advanced Threat Analytics Administrator olur.

## <a name="types-of-ata-role-groups"></a>ATA Rol Gruplarının Türleri 

ATA, üç tür rol grubu tanıtır: ATA Administrators, ATA Users ve ATA Viewers. Aşağıdaki tabloda ATA’daki her rol için kullanılabilen erişim türü açıklanır. Hangi role, bağlı olarak ata, çeşitli ekranlar ve menü seçenekleri gibi kullanılabilir:

|Etkinlik |Microsoft Advanced Threat Analytics Administrators|Microsoft Advanced Threat Analytics Users|Microsoft Advanced Threat Analytics Viewers|
|----|----|----|----|
|Oturum aç|Kullanılabilir|Kullanılabilir|Kullanılabilir|
|Kuşkulu Etkinlikler için Giriş sağlama|Kullanılabilir|Kullanılabilir|Yok|
|Kuşkulu Etkinliklerin durumunu değiştirme|Kullanılabilir|Kullanılabilir|Yok|
|E-posta/bağlantı alma üzerinden şüpheli etkinlikleri paylaşma/dışarı aktarma|Kullanılabilir|Kullanılabilir|Yok|
|İzleme Uyarılarının durumunu değiştirme|Kullanılabilir|Kullanılabilir|Yok|
|ATA Yapılandırmasını güncelleştirme|Kullanılabilir|Yok|Yok|
|Ağ Geçidi – Ekleme|Kullanılabilir|Yok|Yok|
|Ağ Geçidi – Silme |Kullanılabilir|Yok|Yok|
|İzlenen DC – Ekleme |Kullanılabilir|Yok|Yok|
|İzlenen DC – Silme|Kullanılabilir|Yok|Yok|
|Uyarıları ve şüpheli etkinlikleri görüntüleme|Kullanılabilir|Kullanılabilir|Kullanılabilir|


Kullanıcılar kendi rol grupları için kullanılabilir olmayan bir sayfaya erişmeye çalıştıklarında, kullanıcılar ATA yetkisiz sayfasına yönlendirilir. 

## <a name="add--remove-users---ata-role-groups"></a>Kullanıcı Ekleme / Kaldırma - ATA Rol Grupları 

ATA, rol grupları için temel olarak yerel Windows gruplarını kullanır. Rol grupları ATA Center sunucusunda yönetilmelidir.
Kullanıcı eklemek veya kaldırmak için **Yerel Kullanıcılar ve Gruplar** MMC’yi kullanın (Lusrmgr.msc). Etki alanına katılmış bir makinede yerel hesapların yanı sıra etki alanı hesapları da ekleyebilirsiniz. 

