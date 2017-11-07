---
title: "Erişim yönetimi için Advanced Threat Analytics rol grupları | Microsoft Docs"
description: "ATA rol gruplarıyla çalışma konusunda yol gösterir."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 3715b69e-e631-449b-9aed-144d0f9bcee7
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 89666a024821f9e7981eac2c79e95c62adf11088
ms.sourcegitcommit: e2cb3af9c1dbb0b75946dc70cc439b19d654541c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2017
---
*Uygulama hedefi: Advanced Threat Analytics sürüm 1.8*




# <a name="ata-role-groups"></a>ATA Rol Grupları

Rol grupları ATA için erişim yönetimini etkinleştirir. Rol gruplarını kullanarak güvenlik ekibinizdeki görevleri ayırabilir ve kullanıcılara sadece işlerini yapması için gereken miktarda erişim izni verebilirsiniz. Bu makalede erişim yönetimi ve ATA rol yetkilendirmesi açıklanır, ATA’daki rol gruplarını kullanmanıza yardımcı olan bilgiler sağlanır.

> [!NOTE]
> ATA Center’daki herhangi bir yerel yönetici, otomatik olarak Microsoft Advanced Threat Analytics Administrator olur.

## <a name="types-of-ata-role-groups"></a>ATA Rol Gruplarının Türleri 

ATA, 3 tür Rol grubu içerir: ATA Administrators, ATA Users ve ATA Viewers. Aşağıdaki tabloda ATA’daki her rol için kullanılabilen erişim türü açıklanır. Aşağıda gösterildiği gibi, atanan role bağlı olarak ATA’daki çeşitli ekranlar ve menü seçenekleri kullanılamaz:

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


Kendi rol grupları için kullanılabilir olmayan bir sayfaya erişmeye çalışan kullanıcılar ATA yetkisiz sayfasına yönlendirilir. 

## <a name="add--remove-users---ata-role-groups"></a>Kullanıcı Ekleme / Kaldırma - ATA Rol Grupları 

ATA, rol grupları için temel olarak yerel Windows gruplarını kullanır. Rol grupları ATA Center sunucusunda yönetilmelidir.
Kullanıcı eklemek veya kaldırmak için **Yerel Kullanıcılar ve Gruplar** MMC’yi kullanın (Lusrmgr.msc). Etki alanına katılmış bir makinede yerel hesapların yanı sıra etki alanı hesapları da ekleyebilirsiniz. 

