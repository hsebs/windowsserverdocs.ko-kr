---
title: VM 만들기 및 테넌트 가상 네트워크 또는 VLAN에 연결
description: 이 항목에서는 테 넌 트 VM을 만들고이를 Hyper-v 네트워크 가상화를 사용 하 여 만든 가상 네트워크 또는 VLAN (virtual Local Area Network)에 연결 하는 방법을 보여 줍니다.
manager: dougkim
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c62f533-1815-4f08-96b1-dc271f5a2b36
ms.author: lizross
author: eross-msft
ms.date: 08/24/2018
ms.openlocfilehash: ef588cfc93216f13490ef3196ec0990b9e7f48d3
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80309792"
---
# <a name="create-a-vm-and-connect-to-a-tenant-virtual-network-or-vlan"></a>VM 만들기 및 테넌트 가상 네트워크 또는 VLAN에 연결

>적용 대상: Windows Server(반기 채널), Windows Server 2016

이 항목에서는 테 넌 트 VM을 만들고이를 Hyper-v 네트워크 가상화를 사용 하 여 만든 가상 네트워크 또는 VLAN (virtual Local Area Network)에 연결 합니다. Windows PowerShell 네트워크 컨트롤러 cmdlet을 사용 하 여 가상 네트워크 또는 NetworkControllerRESTWrappers에 연결 하 여 VLAN에 연결할 수 있습니다.

이 항목에서 설명 하는 프로세스를 사용 하 여 가상 어플라이언스를 배포 합니다. 몇 가지 추가 단계를 처리 하거나 가상 네트워크에 있는 다른 Vm에서 진행 되는 데이터 패킷 검사 기기를 구성할 수 있습니다.

이 항목의 섹션에는 많은 매개 변수에 대 한 예제 값을 포함 하는 예제 Windows PowerShell 명령이 포함 되어 있습니다. 이러한 명령에 대 한 예제 값은 다음이 명령을 실행 하기 전에 배포에 적합 한 값으로 바꾸는 것을 확인 합니다. 


## <a name="prerequisites"></a>필수 조건

1. VM의 수명 동안 정적 MAC 주소를 사용 하 여 만든 VM 네트워크 어댑터입니다.<p>VM 수명 동안 MAC 주소가 변경 되 면 네트워크 컨트롤러는 네트워크 어댑터에 필요한 정책을 구성할 수 없습니다. 네트워크에 대 한 정책을 구성 하지 않으면 네트워크 어댑터가 네트워크 트래픽을 처리할 수 없으며 네트워크와의 모든 통신이 실패 합니다.  

2. Vm을 시작할 때 네트워크 액세스가 필요한 경우 vm 네트워크 어댑터 포트에서 인터페이스 ID를 설정할 때까지 VM을 시작 하지 마세요. 인터페이스 ID를 설정 하기 전에 VM을 시작 하 고 네트워크 인터페이스가 없는 경우 VM은 네트워크 컨트롤러의 네트워크에서 통신할 수 없으며 모든 정책이 적용 됩니다.

3. 사용자 지정 Acl이 네트워크 인터페이스 필요로 하는 경우 만든 ACL 이제 항목의 지침을 사용 하 여 [사용 하 여 액세스 제어 목록 (Acl) 데이터 센터 네트워크 트래픽 흐름을 관리 하려면](../../sdn/manage/Use-Access-Control-Lists--ACLs--to-Manage-Datacenter-Network-Traffic-Flow.md)

이 예제에서는 명령을 사용 하기 전에 가상 네트워크를 이미 만든 있는지 확인 합니다. 자세한 내용은 참조 [만들기, 삭제 또는 업데이트 테 넌 트 가상 네트워크](https://technet.microsoft.com/windows-server-docs/networking/sdn/manage/create%2c-delete%2c-or-update-tenant-virtual-networks)합니다.

## <a name="create-a-vm-and-connect-to-a-virtual-network-by-using-the-windows-powershell-network-controller-cmdlets"></a>VM을 만들고 Windows PowerShell 네트워크 컨트롤러 cmdlet을 사용 하 여 가상 네트워크에 연결


1. 정적 MAC 주소가 있는 VM 네트워크 어댑터를 사용 하 여 VM을 만듭니다. 

   ```PowerShell    
   New-VM -Generation 2 -Name "MyVM" -Path "C:\VMs\MyVM" -MemoryStartupBytes 4GB -VHDPath "c:\VMs\MyVM\Virtual Hard Disks\WindowsServer2016.vhdx" -SwitchName "SDNvSwitch" 
    
   Set-VM -Name "MyVM" -ProcessorCount 4
    
   Set-VMNetworkAdapter -VMName "MyVM" -StaticMacAddress "00-11-22-33-44-55" 
   ```

2. 네트워크 어댑터를 연결 하려는 서브넷이 포함 된 가상 네트워크를 가져옵니다.

   ```Powershell 
   $vnet = get-networkcontrollervirtualnetwork -connectionuri $uri -ResourceId “Contoso_WebTier”
   ```

3. 네트워크 컨트롤러에서 네트워크 인터페이스 개체를 만듭니다.

   >[!TIP]
   >이 단계에서는 사용자 지정 ACL을 사용 합니다.

   ```PowerShell
   $vmnicproperties = new-object Microsoft.Windows.NetworkController.NetworkInterfaceProperties
   $vmnicproperties.PrivateMacAddress = "001122334455" 
   $vmnicproperties.PrivateMacAllocationMethod = "Static" 
   $vmnicproperties.IsPrimary = $true 

   $vmnicproperties.DnsSettings = new-object Microsoft.Windows.NetworkController.NetworkInterfaceDnsSettings
   $vmnicproperties.DnsSettings.DnsServers = @("24.30.1.11", "24.30.1.12")
    
   $ipconfiguration = new-object Microsoft.Windows.NetworkController.NetworkInterfaceIpConfiguration
   $ipconfiguration.resourceid = "MyVM_IP1"
   $ipconfiguration.properties = new-object Microsoft.Windows.NetworkController.NetworkInterfaceIpConfigurationProperties
   $ipconfiguration.properties.PrivateIPAddress = “24.30.1.101”
   $ipconfiguration.properties.PrivateIPAllocationMethod = "Static"
    
   $ipconfiguration.properties.Subnet = new-object Microsoft.Windows.NetworkController.Subnet
   $ipconfiguration.properties.subnet.ResourceRef = $vnet.Properties.Subnets[0].ResourceRef
    
   $vmnicproperties.IpConfigurations = @($ipconfiguration)
   New-NetworkControllerNetworkInterface –ResourceID “MyVM_Ethernet1” –Properties $vmnicproperties –ConnectionUri $uri
   ```

4. 네트워크 컨트롤러에서 네트워크 인터페이스에 대 한 InstanceId를 가져옵니다.

   ```PowerShell 
    $nic = Get-NetworkControllerNetworkInterface -ConnectionUri $uri -ResourceId "MyVM-Ethernet1"
   ```

5. Hyper-v VM 네트워크 어댑터 포트에서 인터페이스 ID를 설정 합니다.

   >[!NOTE]
   >Hyper-v 호스트에 VM이 설치 되어 있는 다음이 명령을 실행 해야 있습니다.

   ```PowerShell 
   #Do not change the hardcoded IDs in this section, because they are fixed values and must not change.
    
   $FeatureId = "9940cd46-8b06-43bb-b9d5-93d50381fd56"
    
   $vmNics = Get-VMNetworkAdapter -VMName “MyVM”
    
   $CurrentFeature = Get-VMSwitchExtensionPortFeature -FeatureId $FeatureId -VMNetworkAdapter $vmNics
    
   if ($CurrentFeature -eq $null)
   {
   $Feature = Get-VMSystemSwitchExtensionPortFeature -FeatureId $FeatureId
    
   $Feature.SettingData.ProfileId = "{$($nic.InstanceId)}"
   $Feature.SettingData.NetCfgInstanceId = "{56785678-a0e5-4a26-bc9b-c0cba27311a3}"
   $Feature.SettingData.CdnLabelString = "TestCdn"
   $Feature.SettingData.CdnLabelId = 1111
   $Feature.SettingData.ProfileName = "Testprofile"
   $Feature.SettingData.VendorId = "{1FA41B39-B444-4E43-B35A-E1F7985FD548}"
   $Feature.SettingData.VendorName = "NetworkController"
   $Feature.SettingData.ProfileData = 1
    
   Add-VMSwitchExtensionPortFeature -VMSwitchExtensionFeature  $Feature -VMNetworkAdapter $vmNics
   }
   else
   {
   $CurrentFeature.SettingData.ProfileId = "{$($nic.InstanceId)}"
   $CurrentFeature.SettingData.ProfileData = 1
    
   Set-VMSwitchExtensionPortFeature -VMSwitchExtensionFeature $CurrentFeature  -VMNetworkAdapter $vmNic
   }
   ```

6. VM을 시작 합니다.

   ```PowerShell
    Get-VM -Name “MyVM” | Start-VM 
   ```

Vm을 성공적으로 만들고, 테 넌 트 Virtual Network에 VM을 연결 하 고, 테 넌 트 워크 로드를 처리할 수 있도록 VM을 시작 했습니다.

## <a name="create-a-vm-and-connect-to-a-vlan-by-using-networkcontrollerrestwrappers"></a>VM을 만들고 NetworkControllerRESTWrappers를 사용 하 여 VLAN에 연결


1. VM을 만들고 VM에 정적 MAC 주소를 할당 합니다.

   ```PowerShell
   New-VM -Generation 2 -Name "MyVM" -Path "C:\VMs\MyVM" -MemoryStartupBytes 4GB -VHDPath "c:\VMs\MyVM\Virtual Hard Disks\WindowsServer2016.vhdx" -SwitchName "SDNvSwitch" 

   Set-VM -Name "MyVM" -ProcessorCount 4

   Set-VMNetworkAdapter -VMName "MyVM" -StaticMacAddress "00-11-22-33-44-55" 
   ```

2. VM 네트워크 어댑터에서 VLAN ID를 설정 합니다.

   ```PowerShell
   Set-VMNetworkAdapterIsolation –VMName “MyVM” -AllowUntaggedTraffic $true -IsolationMode VLAN -DefaultIsolationId 123
   ```

3. 논리 네트워크 서브넷을 가져오고 네트워크 인터페이스를 만듭니다. 

   ```PowerShell
    $logicalnet = get-networkcontrollerLogicalNetwork -connectionuri $uri -ResourceId "00000000-2222-1111-9999-000000000002"

    $vmnicproperties = new-object Microsoft.Windows.NetworkController.NetworkInterfaceProperties
    $vmnicproperties.PrivateMacAddress = "00-1D-C8-B7-01-02"
    $vmnicproperties.PrivateMacAllocationMethod = "Static"
    $vmnicproperties.IsPrimary = $true 
    
    $vmnicproperties.DnsSettings = new-object Microsoft.Windows.NetworkController.NetworkInterfaceDnsSettings
    $vmnicproperties.DnsSettings.DnsServers = $logicalnet.Properties.Subnets[0].DNSServers

    $ipconfiguration = new-object Microsoft.Windows.NetworkController.NetworkInterfaceIpConfiguration
    $ipconfiguration.resourceid = "MyVM_Ip1"
    $ipconfiguration.properties = new-object Microsoft.Windows.NetworkController.NetworkInterfaceIpConfigurationProperties
    $ipconfiguration.properties.PrivateIPAddress = “10.127.132.177”
    $ipconfiguration.properties.PrivateIPAllocationMethod = "Static"

    $ipconfiguration.properties.Subnet = new-object Microsoft.Windows.NetworkController.Subnet
    $ipconfiguration.properties.subnet.ResourceRef = $logicalnet.Properties.Subnets[0].ResourceRef

    $vmnicproperties.IpConfigurations = @($ipconfiguration)
    $vnic = New-NetworkControllerNetworkInterface –ResourceID “MyVM_Ethernet1” –Properties $vmnicproperties –ConnectionUri $uri

    $vnic.InstanceId
   ```

4. Hyper-v 포트에서 InstanceId를 설정 합니다.

   ```PowerShell  
   #The hardcoded Ids in this section are fixed values and must not change.
   $FeatureId = "9940cd46-8b06-43bb-b9d5-93d50381fd56"

   $vmNics = Get-VMNetworkAdapter -VMName “MyVM”

   $CurrentFeature = Get-VMSwitchExtensionPortFeature -FeatureId $FeatureId -VMNetworkAdapter $vmNic
        
   if ($CurrentFeature -eq $null)
   {
       $Feature = Get-VMSystemSwitchExtensionFeature -FeatureId $FeatureId
        
       $Feature.SettingData.ProfileId = "{$InstanceId}"
       $Feature.SettingData.NetCfgInstanceId = "{56785678-a0e5-4a26-bc9b-c0cba27311a3}"
       $Feature.SettingData.CdnLabelString = "TestCdn"
       $Feature.SettingData.CdnLabelId = 1111
       $Feature.SettingData.ProfileName = "Testprofile"
       $Feature.SettingData.VendorId = "{1FA41B39-B444-4E43-B35A-E1F7985FD548}"
       $Feature.SettingData.VendorName = "NetworkController"
       $Feature.SettingData.ProfileData = 1
                
       Add-VMSwitchExtensionFeature -VMSwitchExtensionFeature  $Feature -VMNetworkAdapter $vmNic
   }        
   else
   {
       $CurrentFeature.SettingData.ProfileId = "{$InstanceId}"
       $CurrentFeature.SettingData.ProfileData = 1

       Set-VMSwitchExtensionPortFeature -VMSwitchExtensionFeature $CurrentFeature  -VMNetworkAdapter $vmNic
   }
   ```

5. VM을 시작 합니다.

   ```PowerShell
   Get-VM -Name “MyVM” | Start-VM 
   ```

Vm을 성공적으로 만들고, VM을 VLAN에 연결 하 고, 테 넌 트 워크 로드를 처리할 수 있도록 VM을 시작 했습니다.

  

