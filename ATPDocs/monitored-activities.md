---
title: Azure ATP izlenen etki alanı etkinlikleri | Microsoft Docs
description: Azure Gelişmiş tehdit Koruması tarafından izlenen her bir etkinlik türü açıklar.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 37d1a032-65e7-4a89-be0b-c3f9cc2bacdb
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 5424c997de43ac186564b929ab50c7668333ed06
ms.sourcegitcommit: 63ec9181f71edce6a950f5cc0d69428405436c48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49963310"
---
*İçin geçerlidir: Azure Gelişmiş tehdit koruması*



# <a name="azure-atp-monitored-activities"></a>Azure ATP izlenen etkinlikler

Azure Gelişmiş tehdit koruması, kuruluşunuzun Active Directory, ağ etkinliği ve olay etkinlikleri şüpheli etkinlikleri algılamak üzere oluşturulan bilgileri izler. Azure ATP, her potansiyel bir tehdit geçerliliğini belirlemek ve doğru bir şekilde değerlendirmenize ve yanıt yardımcı olmak izlenen etkinlik bilgileri sağlar. 

Geçerli bir tehdit söz konusu olduğunda veya **gerçek pozitif sonuç**, Azure ATP, ihlal kapsamına her olay için keşfetmek, hangi varlıkları karmaşıktır ve bunları düzeltme konusunda bilgi araştırmanıza olanak sağlar.

Azure ATP tarafından izlenen bilgi etkinlikleri biçiminde görüntülenir. Azure ATP şu anda aşağıdaki etkinlik türlerini izlenmesini de destekler:

> [!NOTE] 
> - Bu makalede, tüm Azure ATP algılayıcısı türleri için geçerlidir.
>- Azure ATP izlenen etkinlikler, hem kullanıcı hem de makine profil sayfası görüntülenir. 
 

## <a name="monitored-user-activities-user-account-ad-attribute-changes"></a>İzlenen kullanıcı etkinlikleri: kullanıcı hesabı AD öznitelik değişiklikleri

|İzlenen etkinliği|Açıklama|
|---------------------|------------------|
|Kullanıcı posta değiştirildi|Kullanıcıların e-posta özniteliği değiştirildi.|
|Kullanıcı yöneticisini değiştirildi|Kullanıcının yönetici özniteliği değiştirildi.|
|Kullanıcı telefon numarası değişti|Kullanıcının telefon numarası özniteliğini değiştirildi.|
|Değiştirilen kullanıcı başlığı |Kullanıcının başlık özniteliği değiştirildi.|
|Hesap Kısıtlanmış temsilci durumu değişti |Hesap durumu etkin veya temsilci seçme için devre dışı.|
|Hesap kısıtlanmış temsil SPN'leri değiştirildi | Kısıtlanmış temsil, belirtilen sunucunun kullanıcı adına işlem yapabileceği Hizmetleri kısıtlar.|
|Hesap devre dışı değiştirildi |Hesabınız devre dışı veya etkin olup olmadığını gösterir.|
|Hesabın süresi|Hesabın süresinin dolduğu tarih.|
|Değiştirilen hesap sona erme süresi |Hesabın süresinin sona erdiği tarih olarak değiştirin.|
|Değiştirilen hesap kilitlendi|Hesabın süresinin sona erdiği tarih olarak değiştirin.|
|Hesap parolası değiştirildi|Kullanıcı, parola değiştirdi.|
|Hesap parolasının süresi doldu |Kullanıcının parolasının süresi doldu.|
|Parola her zaman geçerli olsun hesabı değiştirildi |Kullanıcı parolasının süresi dolmayacak şekilde değiştirildi.|
|Hesap parolası gerekli değil değiştirildi |Kullanıcı hesabı değiştirildiği boş bir parola oturum izin verin.|
|Akıllı kart gerekli hesabı değiştirildi  |Bir cihazda bir akıllı kart kullanarak oturum açmasını zorunlu tutmak için değişiklikleri hesap.|
|Hesap desteklenen şifreleme türleri değiştirildi |Kerberos desteklenen şifreleme türleri değiştirildi (türleri: Des, AES 129, AES 256)|
|Değiştirilmiş grup üyeliği  |Kullanıcı Ekleme/Kaldırma yapıldığında, başka bir kullanıcı tarafından veya başlarına grubu içine/dışına.|
|Hesap UPN adı değiştirildi  |Kullanıcının asıl adı değiştirildi.|

## <a name="monitored-user-activities-ad-security-principal-operations"></a>İzlenen kullanıcı etkinlikleri: AD güvenlik sorumlusu işlemleri

|İzlenen etkinliği|Açıklama|
|---------------------|------------------|
|Güvenlik sorumlusu oluşturuldu |Hesap (kullanıcı ve bilgisayar) oluşturuldu.|
|Güvenlik sorumlusu silindi değiştirildi  |Hesabı silinir ve geri (kullanıcı ve bilgisayar).|
|Güvenlik sorumlusu görünen adı değiştirildi   |Hesap görünen adı X, Y değiştirildi.|
|Güvenlik sorumlusunun adı değiştirildi  |Hesap adı özniteliği değiştirildi.|
|Güvenlik sorumlusu yolu değişti  |Hesap ayırt edici adı X, Y değiştirildi.|
|Güvenlik sorumlusu Sam adı değiştirildi |SAM adı değiştirildi (SAM, istemciler ve sunucular işletim sisteminin önceki sürümlerini çalıştıran desteklemek için kullanılan oturum açma adıdır).|

## <a name="monitored-user-activities-domain-controller-based-user-operations"></a>İzlenen kullanıcı etkinlikleri: etki alanı denetleyicisi tabanlı kullanıcı işlemleri

|İzlenen etkinliği|Açıklama|
|---------------------|------------------|
|Wmi yürütme  |Kullanıcı bir WMI yöntem uzaktan yürütülmeye çalışıldı.|
|Hizmet oluşturma   |Kullanıcı belirli bir hizmete bir uzak makineye uzaktan oluşturulmaya çalışıldı.|
|SMB Oturumu Listeleme   |Kullanıcı, etki alanı denetleyicilerinde açık bir SMB oturumu olan tüm kullanıcılar listelenmeye çalışıldı.|
|Görev zamanlama  |Kullanıcı, uzak makinede uzaktan zamanlama X göreve denedi.|
|SAMR sorgusu   |Kullanıcı SAMR sorgusu gerçekleştirilir.|
|Özel veri alma  |Kullanıcı LSARPC protokolünü kullanarak özel verileri sorgulamak denendi/başarılı.|
|Dizin hizmeti çoğaltmasını  |Kullanılan dizin hizmeti çoğaltmak denedi.|
|DNS sorgusu  |Kullanıcı, bir etki alanı denetleyicisine karşı AXFR sorgu desteklerken.|


## <a name="monitored-user-activities-login-operations"></a>İzlenen kullanıcı etkinlikleri: oturum açma işlemleri

|Oturum açma türü|İzlenen etkinliği|Açıklama|
|---------------------|---------------------|------------------|
|Oturum açma türü 2|Kimlik doğrulama  |NTLM ve Kerberos kimlik doğrulama yöntemleri kullanarak etki alanı hesabı kimlik doğrulama olayı.|
|Oturum açma türü 2|Etkileşimli Oturum Açma  |Kullanıcı adı ve parola (kimlik doğrulama yöntemini Kerberos) girerek ağ erişim elde ettiğini.|
|Oturum açma türü 2|VPN bağlantısı   |VPN - RADIUS protokolü kullanılarak kimlik doğrulaması kullanarak bağlı kullanıcı.|
|Oturum açma türü 3|Kaynak erişimi  |Kullanıcının Kerberos kimlik doğrulaması kullanarak bir kaynağa erişme.|
|Oturum açma türü 8|LDAP düz metin  |LDAP düz metin parola (Basit kimlik doğrulaması) kullanılarak kimliği doğrulanmış bir kullanıcı.|
|10 oturum açma türü|Uzak Masaüstü |Kullanıcı, Kerberos kimlik doğrulaması kullanarak uzak bir bilgisayara bir RDP oturumu gerçekleştirdi.|
| --- |Başarısız oturum açma |Etki alanı hesabını (NTLM ve Kerberos) aracılığıyla aşağıdaki nedeniyle kimlik doğrulama girişimi başarısız oldu: Hesap devre dışı bırakılmış/süresi doldu/kilitli/kullanılan güvenilmeyen bir sertifika veya son idi geçersiz oturum açma saatleri/eski parola/süresi dolmuş parola/yanlış parola.|


## <a name="monitored-machine-activities-machine-account"></a>İzlenen makine etkinlikleri: Makine hesabı

|İzlenen etkinliği|Açıklama|
|---------------------|------------------|
|Bilgisayar işletim sistemi değiştirildi|Bilgisayar işletim sistemi olarak değiştirin.


## <a name="see-also"></a>Ayrıca Bkz.
- [Güvenlik uyarılarını yönetme](working-with-suspicious-activities.md)
- [Güvenlik uyarısı kılavuzu](suspicious-activity-guide.md)
- [Varlıkları araştırma](investigate-entity.md)
- [Azure ATP forumuna bakın!](https://aka.ms/azureatpcommunity)
