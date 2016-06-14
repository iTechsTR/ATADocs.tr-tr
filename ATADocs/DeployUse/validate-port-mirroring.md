---
# required metadata

title: Bağlantı Noktası Yansıtmayı Doğrulama | Microsoft Advanced Threat Analytics
description: Bağlantı noktası yansıtmanın düzgün yapılandırıldığını nasıl doğrulayabileceğiniz açıklanır
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: ebd41719-c91a-4fdd-bcab-2affa2a2cace

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Bağlantı Noktası Yansıtmayı Doğrulama
> [!NOTE] Bu makale yalnızca ATA Lightweight Gateway bileşenleri yerine ATA Gateway bileşenleri dağıttığınızda geçerlidir. ATA Gateway bileşenleri kullanmanız gerekip gerekmediğini belirlemek için bkz. [Dağıtımınız için doğru ağ geçitlerini seçme](/advanced-threat-analytics/plan-design/ata-capacity-planning#Choosing-the-right-gateway-type-for-your-deployment)
 
Aşağıdaki adımlar, bağlantı noktası yansıtmanın düzgün yapılandırıldığını doğrulama işleminde size yol gösterir. ATA’nın düzgün çalışması için, ATA Gateway’in etki alanı denetleyicisinden gelen ve giden trafiği görebilmesi gerekir. ATA tarafından kullanılan ana veri kaynağı, etki alanı denetleyicilerinizden gelen ve giden ağ trafiğinin derin paket incelemesidir. ATA’nın ağ trafiğini görebilmesi için, bağlantı noktası yansıtma yapılandırılmalıdır. Bağlantı noktası yansıtma, bir bağlantı noktasındaki trafiği (kaynak bağlantı noktası) başka bir bağlantı noktasına (hedef bağlantı noktası) kopyalar.

## Windows PowerShell betiği kullanarak bağlantı noktası yansıtmayı doğrulama

1. Bu betiğin metnini ATAdiag.ps1 adlı bir dosyaya kaydedin.
2. ATA Gateway’den bu betiği çalıştırın.
Betik ATA Gateway’den etki alanı denetleyicisine ICMP trafiği oluşturur ve etki alanı denetleyicisindeki Yakalama NIC’te bu trafiği arar.
ATA Gateway, ATA Konsolu’na girdiğiniz etki alanı IP adresiyle aynı hedef IP adresine sahip ICMP trafiği görürse, bağlantı noktası yansıtmanın yapılandırıldığını kabul eder. 

Betiğin çalıştırılmasına örnek:

    # ATAdiag.ps1 -CaptureIP n.n.n.n -DCIP n.n.n.n -TestCount n
    
    param([parameter(Mandatory=$true)][string]$CaptureIP, [parameter(Mandatory=$true)][string]$DCIP, [int]$PingCount = 10)

    # Set variables
    
        $ErrorActionPreference = "stop"
    $starttime = get-date
    $byteIn = new-object byte[] 4
    $byteOut = new-object byte[] 4
    $byteData = new-object byte[] 4096  # size of data
    
    $byteIn[0] = 1  # for promiscuous mode
    $byteIn[1-3] = 0
    $byteOut[0-3] = 0



    # Convert network data to host format
        function NetworkToHostUInt16 ($value)
        {
        [Array]::Reverse($value)
        [BitConverter]::ToUInt16($value,0)
        }
    
    function NetworkToHostUInt32 ($value)
        {
        [Array]::Reverse($value)
        [BitConverter]::ToUInt32($value,0)
        }
    
    function ByteToString ($value)
        {
        $AsciiEncoding = new-object system.text.asciiencoding
        $AsciiEncoding.GetString($value)
            }
    
    Write-Host "Testing Port Mirroring..." -ForegroundColor Yellow
    Write-Host ""
    Write-Host "Here is a summary of the connection we will test." -ForegroundColor Yellow

    # Initialize a first ping connection
    Test-Connection -Count 1 -ComputerName $DCIP -ea SilentlyContinue
    Write-Host ""
    
    Write-Host "Press any key to continue..." -ForegroundColor Red
    [void][System.Console]::ReadKey($true)
    Write-Host ""
    Write-Host "Sending ICMP and Capturing data..." -ForegroundColor Yellow
    
    # Open a socket
    
    $socket = new-object system.net.sockets.socket([Net.Sockets.AddressFamily]::InterNetwork,[Net.Sockets.SocketType]::Raw,[Net.Sockets.ProtocolType]::IP)
    
    # Include the IP header
    $socket.setsocketoption("IP","HeaderIncluded",$true)
    
    $socket.ReceiveBufferSize = 10000
    
    $ipendpoint = new-object system.net.ipendpoint([net.ipaddress]"$CaptureIP",0)
    $socket.bind($ipendpoint)
    
    # Enable promiscuous mode
    [void]$socket.iocontrol([net.sockets.iocontrolcode]::ReceiveAll,$byteIn,$byteOut)
    
    # Initialize test variables
    $tests = 0
    $TestResult = "Noise"
    $OneSuccess = 0
    
    while ($tests -le $PingCount)
        {
        if (!$socket.Available)  # see if any packets are in the queue
            {
            start-sleep -milliseconds 500
            continue
            }
    
    # Capture traffic
        $rcv = $socket.receive($byteData,0,$byteData.length,[net.sockets.socketflags]::None)
    
    # Decode the header so we can read ICMP
    
        $MemoryStream = new-object System.IO.MemoryStream($byteData,0,$rcv)
        $BinaryReader = new-object System.IO.BinaryReader($MemoryStream)
    
    # Set IP version & header length
        $VersionAndHeaderLength = $BinaryReader.ReadByte()
    
        # TOS
        $TypeOfService= $BinaryReader.ReadByte()
    
        # More values, and the Protocol Number for ICMP traffic
        # Convert network format of big-endian to host format of little-endian 
        $TotalLength = NetworkToHostUInt16 $BinaryReader.ReadBytes(2)
    
        $Identification = NetworkToHostUInt16 $BinaryReader.ReadBytes(2)
        $FlagsAndOffset = NetworkToHostUInt16 $BinaryReader.ReadBytes(2)
        $TTL = $BinaryReader.ReadByte()
        $ProtocolNumber = $BinaryReader.ReadByte()
        $Checksum = [Net.IPAddress]::NetworkToHostOrder($BinaryReader.ReadInt16())
    
        # The source and destination IP addresses
        $SourceIPAddress = $BinaryReader.ReadUInt32()
        $DestinationIPAddress = $BinaryReader.ReadUInt32()
    
        # The source and destimation ports
        $sourcePort = [uint16]0
        $destPort = [uint16]0
            
        # Close the stream reader
        $BinaryReader.Close()
        $memorystream.Close()
    
        # Cast DCIP into an IPaddress type
        $DCIPP = [ipaddress] $DCIP
        $DestinationIPAddressP = [ipaddress] $DestinationIPAddress
    
        #Ping the DC at the end after starting the capture
        Test-Connection -Count 1 -ComputerName $DCIP -ea SilentlyContinue | Out-Null
            
        # This is the match logic - check to see if Destination IP from the Ping sent matches the DCIP entered by in the ATA Console  
        # The only way the ATA Gateway should see a destination of the DC is if Port Spanning is configured
        
            if ($DestinationIPAddressP -eq $DCIPP)  # is the destination IP eq to the DC IP? 
            {
            $TestResult = "Port Spanning success!"
            $OneSuccess = 1
            } else {
                $TestResult = "Noise"
            }
        
        # Put source, destination, test result in Powershell object
        
        new-object psobject | add-member -pass noteproperty CaptureSource $([system.net.ipaddress]$SourceIPAddress) | add-member -pass noteproperty CaptureDestination $([system.net.ipaddress]$DestinationIPAddress) | Add-Member -pass NoteProperty Result $TestResult | Format-List | Out-Host
        #Count tests
        $tests ++
        }
    
        If ($OneSuccess -eq 1){
            Write-Host "Port Spanning Success!" -ForegroundColor Green
            Write-Host ""
            Write-Host "At least one packet which was addressed to the DC, was picked up by the Gateway." -ForegroundColor Yellow
            Write-Host "A little noise is OK, but if you don't see a majority of successes, you might want to re-run." -ForegroundColor Yellow
        } Else {
            Write-Host "No joy, all noise.  You may want to re-run, increase the number of Ping Counts, or check your config." -ForegroundColor Red
        }
    
    Write-Host ""
    Write-Host "Press any key to continue..." -ForegroundColor Red
    [void][System.Console]::ReadKey($true)
    
    
## Net Mon kullanarak bağlantı noktası yansıtmayı doğrulama
1.  [Microsoft Network Monitor 3.4](http://www.microsoft.com/download/details.aspx?id=4865)’ü yükleme.

    > [!IMPORTANT]
    > ATA Gateway’e Microsoft Message Analyzer’ı veya başka herhangi bir trafik yakalama yazılımını yüklemeyin.

2.  Ağ İzleyicisi'ni açın ve yeni bir yakalama sekmesi oluşturun.

    1.  Yalnızca **Yakalama** ağ bağdaştırıcısını veya bağlantı noktası yansıtma hedefi için yapılandırılmış anahtar bağlantı noktasına bağlı ağ bağdaştırıcısını seçin.

    2.  P-Modu’nun etkinleştirildiğinden emin olun.

    3.  **Yeni Yakalama**’ya tıklayın..

        ![Yeni yakalama sekmesi oluşturma resmi](media/ATA-Port-Mirroring-Capture.jpg)

3.  Görüntüleme Filtresi penceresinde **KerberosV5 VEYA LDAP** filtresini girin ve ardından **Uygula**’ya tıklayın..

    ![KerberosV5 veya LDAP filtresini uygulama resmi](media/ATA-Port-Mirroring-filter-settings.jpg)

4.  Yakalama oturumunu başlatmak için **Başlat**’a tıklayın. Etki alanı denetleyicisinden gelen veya giden trafiği görmüyorsanız, bağlantı noktası yansıtma yapılandırmanızı gözden geçirin.

    ![Yakalama oturumunu başlatma resmi](media/ATA-Port-Mirroring-Capture-traffic.jpg)

    > [!NOTE]
    > Etki alanı denetleyicilerinden gelen ve giden trafiği gördüğünüzden emin olmanız önemlidir.
    

5.  Yalnızca bir yöndeki trafiği görüyorsanız, bağlantı noktası yansıtma yapılandırmanızdaki sorunları gidermeye yardımcı olmaları için ağ veya sanallaştırma ekiplerinizle birlikte çalışın.

## Ayrıca Bkz.

- [Bağlantı noktası yansıtmayı yapılandırma](configure-port-mirroring.md)
- [ATA forumuna bakın!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=May16_HO1-->


