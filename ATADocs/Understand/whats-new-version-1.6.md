---
title: "Advanced Threat Analytics sürüm 1.6’daki yenilikler | Microsoft Docs"
description: "ATA sürüm 1.6’daki yenilikleri ve bilinen sorunları listeler"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 27b139e5-12b9-4953-8f53-eb58e8ce0038
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b28cb3a0da844b7c460c03726222bc775a9e47da
ms.openlocfilehash: e31dabc43ada8eac4ebed86af0ac4b43dc410246


---

# <a name="whats-new-in-ata-version-16"></a>ATA sürüm 1.6’daki yenilikler
Bu sürüm notları, Advanced Threat Analytics’in bu sürümündeki bilinen sorunlar hakkında bilgi sağlar.

## <a name="whats-new-in-the-ata-16-update"></a>ATA 1.6 güncelleştirmesindeki yenilikler
ATA 1.6 güncelleştirmesi aşağıdaki alanlarda geliştirmeler sağlar:

-   Yeni algılamalar

-   Var olan algılamalarda geliştirmeler

-   ATA Lightweight Gateway

-   Otomatik güncelleştirmeler

-   Geliştirilmiş ATA Center performansı

-   Daha az depolama alanı gereksinimleri

-   IBM QRadar desteği

### <a name="new-detections"></a>Yeni algılamalar


- **Kötü Amaçlı Veri Koruma Özel Bilgi İsteği** Veri Koruma API’si (DPAPI) parola tabanlı bir veri koruma hizmetidir. Bu koruma hizmeti web sitesi parolaları ve dosya paylaşımı kimlik bilgileri gibi kullanıcının gizli bilgilerini depolayan çeşitli uygulamalar tarafından kullanılır. Parolanın kaybolması senaryolarını desteklemek için, kullanıcılar parolalarını içermeyen bir kurtarma anahtarı kullanılarak korunan verilerin şifresini çözebilir. Bir etki alanı ortamında, saldırganlar uzaktan kurtarma anahtarını çalabilir ve tüm etki alanına katılmış bilgisayarlarda korunan verilerin şifresini çözmek için kullanabilirler.


- **Ağ Oturumu Numaralandırma** Keşif, gelişmiş saldırı sonlandırma zinciri içindeki önemli bir aşamadır. Etki Alanı Denetleyicileri (DC’ler) Server Message Block (SMB) protokolünü kullanarak Grup İlke Nesnesi dağıtımı amacıyla dosya sunucuları görevi görür. Saldırganlar keşif aşamasının bir parçası olarak, etki alanı denetleyicisinde sunucudaki tüm etkin SMB oturumlarını sorgulayabilir ve bu da onlara bu SMB oturumlarıyla ilişkili tüm kullanıcılara ve IP adreslerine erişme olanağı sağlar. SMB oturumu numaralandırması saldırganlar tarafından hassas hesapları hedeflemek için kullanılabilir ve bu da saldırganların ağda yanal olarak hareket etmelerine yardımcı olur.


- **Kötü amaçlı çoğaltma istekleri** Active Directory ortamlarında, Etki Alanı Denetleyicileri arasında düzenli olarak çoğaltma yapılır. Bir saldırgan (bazen bir Etki Alanı Denetleyicisinin kimliğe bürünerek), Active Directory çoğaltma isteğini taklit edebilir ve bu da saldırganın Birim Gölge Kopyası gibi daha kullanışsız tekniklerden yararlanmadan, parola karmaları dahil olmak üzere Active Directory’de depolanan verileri almasına izin verir.


- **MS11-013 açığının algılanması** Bir Kerberos hizmet biletinin belirli yönlerden sahtesini üretmeye olanak sağlayan Kerberos’taki ayrıcalık güvenlik açığından yararlanma söz konusudur. Bu güvenlik açığından yararlanmayı başaran kötü amaçlı bir kullanıcı veya saldırgan Etki Alanı Denetleyicisinde yükseltilmiş ayrıcalıklarla bir belirteç elde edebilir.


- **Olağan dışı protokol uygulanması** Kimlik doğrulama istekleri (Kerberos veya NTLM) genellikle standart bir dizi yöntem ve protokoller kullanılarak gerçekleştirilir. Ancak başarıyla kimlik doğrulamak için, isteğin yalnızca belirli gereksinimleri karşılaması gerekir. Saldırganlar bu protokolleri, ortamda standart uygulamadan küçük sapmalarla uygulayabilir. Bu sapmalar Karma Değer Geçişi, Deneme Yanılma vb. saldırılar uygulamaya çalışan bir saldırganın varlığına işaret edebilir.


### <a name="improvements-to-existing-detections"></a>Var olan algılamalarda geliştirmeler
ATA 1.6 Altın Anahtar, Şanslı Belirteç, Deneme Yanılma ve Uzak Yürütme gibi var olan algılamalar için hatalı pozitif ve hatalı negatif senaryoları azaltan geliştirilmiş bir algılama mantığına sahiptir.

### <a name="the-ata-lightweight-gateway"></a>ATA Lightweight Gateway
ATA’nın bu sürümü ATA Gateway için, doğrudan Etki Alanı Denetleyicisine ATA Gateway yüklenmesine olanak sağlayan yeni bir dağıtım seçeneği sunar. Bu dağıtım seçeneği ATA Gateway’in kritik olmayan işlevlerini kaldırır ve etki alanı denetleyicisindeki kullanılabilir kaynaklara dayalı olarak dinamik kaynak yönetimi sunar ve bu da etki alanı denetleyicisindeki var olan işlemlerin etkilenmemesini sağlar. ATA Lightweight Gateway, ATA dağıtımının maliyetini azaltır. Aynı zamanda, bağlantı noktası yansıtma desteği kurmak için donanım kaynak kapasitesinin veya olanaklarının sınırlı olduğu şubelerde dağıtımı kolaylaştırır.
ATA Lightweight Gateway hakkında daha fazla bilgi için bkz. [ATA mimarisi](/advanced-threat-analytics/plan-design/ata-architecture#ata-gateway-and-ata-lightweight-gateway)

Dağıtım hakkında önemli noktalar ve sizin için doğru türde ağ geçitlerini seçme konusunda daha fazla bilgi için bkz. [ATA kapasite planlaması](/advanced-threat-analytics/plan-design/ata-capacity-planning#choosing-the-right-gateway-type-for-your-deployment)


### <a name="automatic-updates"></a>Otomatik güncelleştirmeler
Sürüm 1.6 ile başlayarak, Microsoft Update kullanarak ATA Center’ı güncelleştirmek mümkündür. Ayrıca, ATA Gateway’ler artık ATA Center’a kendi standart iletişim kanalı kullanılarak otomatik olarak güncelleştirilebilir.
### <a name="improved-ata-center-performance"></a>Geliştirilmiş ATA Center performansı
Bu sürümde daha basit bir veritabanı yükü ve tüm algılamaların daha verimli bir şekilde çalıştırılması, daha pek çok etki alanı denetleyicisin tek bir ATA Center ile izlenmesine olanak sağlar.

### <a name="lower-storage-requirements"></a>Daha az depolama alanı gereksinimleri
ATA 1.6, ATA Veritabanını çalıştırmak için önemli ölçüde daha az depolama alanı gerektirir; şimdi önceki sürümlerde kullanılanın %20’si kadar alan gerekir.

### <a name="support-for-ibm-qradar"></a>IBM QRadar desteği
ATA daha önce desteklenen SIEM çözümlerinin yanı sıra şimdi IBM'in QRadar SIEM çözümünden gelen olayları alabilmektedir.

## <a name="known-issues"></a>Bilinen sorunlar
Bu sürümün bilinen sorunları şunlardır:

### <a name="failure-to-recognize-new-path-in-manually-moved-databases"></a>El ile taşınan veritabanlarında yeni yolu tanıma hatası

Veritabanı yolunun el ile taşındığı dağıtımlarda, ATA dağıtımı güncelleştirme için yeni veritabanı yolunu kullanmaz. Bu aşağıdaki sorunlara neden olabilir:


- ATA eski ağ etkinliklerini döngüsel olarak silmeden ATA Center’ın sistem sürücüsündeki tüm boş alanı kullanabilir.


- ATA’yı 1.6 sürümüne güncelleştirmek, aşağıdaki resimde gösterilen güncelleştirme öncesi Hazırlık Denetimlerinde başarısız olabilir.
    ![Başarısız hazırlık denetimi](media/ata_failed_readinesschecks.png)
    >[!Important]
ATA’yı 1.6 sürümüne güncelleştirmeden önce, aşağıdaki kayıt defteri anahtarını doğru veritabanı yoluyla güncelleştirin: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Advanced Threat Analytics\Center\DatabaseDataPath`

### <a name="migration-failure-when-updating-from-ata-15"></a>ATA 1.5’ten güncelleştirirken geçiş hatası
ATA 1.6’ya güncelleştirirken, güncelleştirme işlemi şu hata koduyla başarısız olabilir:

![ATA’yı 1.6 sürümüne güncelleştirme hatası](http://i.imgur.com/QrLSApr.png) Bu hatayı görürseniz, **C:\Users\<User>\AppData\Local\Temp** konumundaki dağıtım günlüğünü gözden geçirin ve aşağıdaki özel durumu arayın:

    System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> MongoDB.Driver.MongoWriteException: A write operation resulted in an error. E11000 duplicate key error index: ATA.UniqueEntityProfile.$_id_ dup key: { : "<guid>" } ---> MongoDB.Driver.MongoBulkWriteException`1: A bulk write operation resulted in one or more errors.  E11000 duplicate key error index: ATA.UniqueEntityProfile.$_id_ dup key: { : " <guid> " }

Şu hatayı da görebilirsiniz: System.ArgumentNullException: Değer null olamaz.
    
Bu hatalardan herhangi biriyle karşılaşırsanız, aşağıdaki geçici çözümü çalıştırın.

**Geçici çözüm**: 

1.  "data_old" klasörünü, geçici bir klasöre (genellikle %ProgramFiles%\Microsoft Advanced Threat Analytics\Center\MongoDB\bin konumunda bulunur) taşıyın.
2.  ATA Center v1.5’i kaldırın ve tüm veritabanı verilerini silin.
![ATA 1.5’i Kaldırma](http://i.imgur.com/x4nJycx.png)
3.  ATA Center v1.5’i yeniden yükleyin. Önceki ATA 1.5 yüklemesiyle (Sertifikalar, IP adresleri, veritabanı yolu, vs.) aynı yapılandırmayı kullandığınızdan emin olun.
4.  Aşağıdaki sırayla şu işlemleri durdurun:
    1.  Microsoft Advanced Threat Analytics Center
    2.  MongoDB
5.  MongoDB veritabanı dosyalarını “data_old” klasöründeki dosyalarla değiştirin.
6.  Aşağıdaki sırayla şu işlemleri başlatın:
    1.  MongoDB
    2.  Microsoft Advanced Threat Analytics Center
7.  Ürün hatasız çalıştığını doğrulamak için günlükleri gözden geçirin.
8.  [İndir]"RemoveDuplicateProfiles.exe" aracını (http://aka.ms/ataremoveduplicateprofiles "indirin") ve ana yükleme yoluna (%ProgramFiles%\Microsoft Advanced Threat Analytics\Center) kopyalayın
9.  Yükseltilmiş bir komut isteminden "RemoveDuplicateProfiles.exe" aracını çalıştırın ve başarıyla tamamlanana dek bekleyin.
10. Buradan:  …\Microsoft Advanced Threat Analytics\Center\MongoDB\bin directory: **Mongo ATA**, aşağıdaki komutu yazın:

    db.SuspiciousActivities.remove({ "_t" : "RemoteExecutionSuspiciousActivity", "DetailsRecords" : { "$elemMatch" : { "ReturnCode" : null } } }, { "_id" : 1 });

![Güncelleştirme geçici çözümü](http://i.imgur.com/Nj99X2f.png)

Bu bir WriteResult({ "nRemoved" : XX }) döndürebilir; burada “XX” silinen Şüpheli Etkinlik sayısıdır. Sayı 0'dan büyükse, komut isteminden çıkın ve güncelleştirme işlemine devam.


### <a name="net-framework-461-requires-restarting-the-server"></a>NET Framework 4.6.1, sunucunun yeniden başlatılmasını gerektirir

Bazı durumlarda, .Net Framework 4.6.1 yüklemesi sunucuyu yeniden başlatmanızı gerekebilir. **Microsoft Advanced Threat Analytics Center Kurulumu** iletişim kutusunda Tamam düğmesine tıkladığınızda sunucunun otomatik olarak yeniden başlatıldığına dikkat edin. Kurulumdan önce bir bakım penceresi planlamak isteyebileceğinizden, bu özellikle ATA Lightweight Gateway’i bir etki alanı denetleyicisine yüklerken önemlidir.
    ![.NET Framework’ü yeniden başlatma](media/ata-net-framework-restart.png)

### <a name="historical-network-activities-no-longer-migrated"></a>Geçmiş ağ etkinlikleri artık geçirilmez
ATA’nın bu sürümü daha doğru algılama sunan ve özellikle Karma Değer Geçirme için birçok hatalı pozitif senaryosunu azaltan geliştirilmiş bir algılama altyapısı sunar.
Yeni ve geliştirilmiş algılama altyapısı hat içi algılama teknolojisini kullanarak, ATA Center’ın performansını önemli ölçüde artırmak için, geçmiş ağ etkinliğine erişmeksizin algılamaya olanak sağlar. Bu aynı zamanda, güncelleştirme işlemi sırasında geçmiş ağ etkinliğinin aktarılmasına gerek kalmadığı anlamına gelir.
Gelecekte araştırmak amacıyla istemeniz halinde, ATA güncelleştirme yordamı verileri JSON dosyası olarak `<Center Installation Path>\Migration` uygulamasına aktarır.

## <a name="see-also"></a>Ayrıca bkz.
[ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

[ATA’yı 1.6 sürümüne güncelleştirme: geçiş kılavuzu](ata-update-1.6-migration-guide.md)


<!--HONumber=Feb17_HO1-->


