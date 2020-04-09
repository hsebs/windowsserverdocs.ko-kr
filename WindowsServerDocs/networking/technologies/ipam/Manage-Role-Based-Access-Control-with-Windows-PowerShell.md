---
title: Windows PowerShell 을 사용하여 역할 기반 액세스 제어 관리
description: 이 항목은 Windows Server 2016의 IPAM (IP 주소 관리) 관리 가이드의 일부입니다.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ipam
ms.topic: article
ms.assetid: 4f13f78e-0114-4e41-9a28-82a4feccecfc
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 8fd8a0780e18324748e0352b124b2e3182bca13b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80860646"
---
# <a name="manage-role-based-access-control-with-windows-powershell"></a>Windows PowerShell 을 사용하여 역할 기반 액세스 제어 관리

>적용 대상: Windows Server(반기 채널), Windows Server 2016

이 항목을 사용 하 여 Windows PowerShell에서 IPAM을 사용 하 여 역할 기반 액세스 제어를 관리 하는 방법을 배울 수 있습니다.  
  
>[!NOTE]
>IPAM Windows PowerShell 명령 참조는 [Windows powershell의 IpamServer cmdlet](https://docs.microsoft.com/powershell/module/ipamserver/?view=win10-ps)을 참조 하세요.  
  
새 Windows PowerShell IPAM 명령은 DNS 및 DHCP 개체의 액세스 범위를 검색 하 고 변경할 수 있는 기능을 제공 합니다. 다음 표에서는 각 IPAM 개체에 사용할 올바른 명령을 보여 줍니다.  
  
|IPAM 개체|명령|설명|  
|---------------|-----------|---------------|  
|DNS 서버|IpamDnsServer|이 cmdlet은 IPAM의 DNS 서버 개체를 반환 합니다.|  
|DNS 영역|IpamDnsZone|이 cmdlet은 IPAM의 DNS 영역 개체를 반환 합니다.|  
|DNS 리소스 레코드|IpamResourceRecord|이 cmdlet은 IPAM의 DNS 리소스 레코드 개체를 반환 합니다.|  
|DNS 조건부 전달자|IpamDnsConditionalForwarder|이 cmdlet은 IPAM의 DNS 조건부 전달자 개체를 반환 합니다.|  
|DHCP 서버|IpamDhcpServer|이 cmdlet은 IPAM에서 DHCP 서버 개체를 반환 합니다.|  
|DHCP 대범위|IpamDhcpSuperscope|이 cmdlet은 IPAM의 DHCP 대 범위 개체를 반환 합니다.|  
|DHCP 범위|IpamDhcpScope|이 cmdlet은 IPAM의 DHCP 범위 개체를 반환 합니다.|  
  
다음 명령 출력 예제에서 `Get-IpamDnsZone` cmdlet은 **Dublin.contoso.com** DNS 영역을 검색 합니다.  
  
```  
PS C:\Users\Administrator.CONTOSO> Get-IpamDnsZone -ZoneType Forward -ZoneName dublin.contoso.com  
  
ZoneName             : dublin.contoso.com  
ZoneType             : Forward  
AccessScopePath      : \Global\Dublin  
IsSigned             : False  
DynamicUpdateStatus  : None  
ScavengeStaleRecords : False  
```  
  
## <a name="setting-access-scopes-on-ipam-objects"></a>IPAM 개체에 대 한 액세스 범위 설정  
`Set-IpamAccessScope` 명령을 사용 하 여 IPAM 개체에 대 한 액세스 범위를 설정할 수 있습니다. 이 명령을 사용 하 여 액세스 범위를 개체의 특정 값으로 설정 하거나 개체가 부모 개체에서 액세스 범위를 상속 하도록 할 수 있습니다. 다음은이 명령을 사용 하 여 구성할 수 있는 개체입니다.  
  
-   DHCP 범위  
  
-   DHCP 서버  
  
-   DHCP 대범위  
  
-   DNS 조건부 전달자  
  
-   DNS 리소스 레코드  
  
-   DNS 서버  
  
-   DNS 영역  
  
-   IP 주소 블록  
  
-   IP 주소 범위  
  
-   IP 주소 공간  
  
-   IP 주소 서브넷  
  
다음은 `Set-IpamAccessScope` 명령에 대 한 구문입니다.  
  
```  
NAME  
    Set-IpamAccessScope  
  
SYNTAX  
    Set-IpamAccessScope [-IpamRange] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamDnsServer] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamDhcpServer] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamDhcpSuperscope] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamDhcpScope] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamDnsConditionalForwarder] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamDnsResourceRecord] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamDnsZone] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamAddressSpace] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamSubnet] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamBlock] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  [<CommonParameters>]  
```  
  
다음 예제에서는 DNS 영역 **dublin.contoso.com** 의 액세스 범위가 **더블린** 에서 **유럽**으로 변경 됩니다.  
  
```  
PS C:\Users\Administrator.CONTOSO> Get-IpamDnsZone -ZoneType Forward -ZoneName dublin.contoso.com  
  
ZoneName             : dublin.contoso.com  
ZoneType             : Forward  
AccessScopePath      : \Global\Dublin  
IsSigned             : False  
DynamicUpdateStatus  : None  
ScavengeStaleRecords : False  
  
PS C:\Users\Administrator.CONTOSO> $a = Get-IpamDnsZone -ZoneType Forward -ZoneName dublin.contoso.com  
PS C:\Users\Administrator.CONTOSO> Set-IpamAccessScope -IpamDnsZone -InputObject $a -AccessScopePath \Global\Europe -PassThru  
  
ZoneName             : dublin.contoso.com  
ZoneType             : Forward  
AccessScopePath      : \Global\Europe  
IsSigned             : False  
DynamicUpdateStatus  : None  
ScavengeStaleRecords : False  
```  
  


