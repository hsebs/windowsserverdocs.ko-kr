---
title: HCN (호스트 계산 네트워크) JSON 문서 스키마
ms.author: jmesser
author: jmesser81
ms.prod: windows-server
ms.date: 11/05/2018
ms.openlocfilehash: 0cb29dd1b8b602080f0e0036904b91b0768b8996
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859856"
---
# <a name="hcn-json-document-schemas"></a>HCN JSON 문서 스키마

>적용 대상: Windows Server (반기 채널), Windows Server 2019

## <a name="hcn-schema"></a>HCN 스키마

```json
// Network
{
    "Id" : <string>,
    "Owner" : <string>,
    "SchemaVersion" : {
        "Major" : <uint32>,
        "Minor" : <uint32>
    },
    "Flags" : <enum bit mask>, 
         // AsString; Values: 
         // "None" (0),
         // "EnableDnsProxy" (1),
         // "EnableDhcpServer" (2),
         // "IsolateVSwitch" (8)
    "Type"  : <enum>, 
         // AsString; Values: 
         // "NAT" (0), 
         // "ICS" (1), 
         // "Transparent" (2)
    "Ipams" : [ {
         "Type" : <enum>, 
             // AsString; Values: 
             // "Static" (0), 
             // "Dhcp" (1)
         "Subnets" : [ {
                "IpAddressPrefix" : <ip prefix in CIDR>,
                "Policies" : [ {
                        "Type" : <enum>, 
                            // AsString; Values: 
                            // "VLAN" (0)
                        "Data" : <any>
                 } ],
                "Routes" : [ {
                       "NextHop" : <ip address of the next hop gateway>,
                       "DestinationPrefix" : <ip prefix in cidr>,
                       "Metric" : <route metric in uint8>,
                 } ],
          } ],
     } ],
    "Policies" : [{
         "Type" : <enum>, 
              // AsString; Values: 
              // "NetAdapterName" (1), 
              // "InterfaceConstraint" (2)
         "Data" : <any>
    }],
    "Dns" : {
        "Suffix" : <local connection specific suffix>,
        "Search" : [<list of additional suffixes>],
        "ServerList" : [<string>],
        "Options" : [<string>],
    },
    "MacPool" : {
        "Ranges" : [ {
              "StartMacAddress" : <string>,
              "EndMacAddress" : <string>
         } ],
    },
}
```

## <a name="hcn-endpoint-schema"></a>HCN 끝점 스키마

```json
// Endpoint 
{
    "Id" : <string>,
    "Owner" : <string>,
    "SchemaVersion" : {
        "Major" : <uint32>,
        "Minor" : <uint32>
    },
    "Flags" : <enum bit mask>, 
         // AsString; Values: 
         // "None" (0),
         // "DisableInterComputeCommunication" (2)
    "HostComputeNetwork" : <string>,
    "MacAddress" : <string>,
    "Policies" : [ {
         "Type" : <enum>, 
              // AsString; Values: 
              // "PortMapping" (0), 
              // "ACL" (1)
         "Data" : <any>
    } ],
    "Dns" : {
        "Suffix" : <local connection specific suffix>,
        "Search" : [<list of additional suffixes>],
        "ServerList" : [<string>],
        "Options" : [<string>],
    },
    "IPConfigurations" : [ {
        "IPAddress" : <ip address>,
        "PrefixLength" : <prefix length uint16>,
    } ],
    "Routes" : [ {
        "NextHop" : <ip address of the next hop gateway>,
        "DestinationPrefix" : <ip prefix in cidr>,
        "Metric" : <route metric in uint8>,

    } ],
}
```

## <a name="hcn-policy-schema"></a>HCN 정책 스키마

```json
// VlanPolicy
{
    "Type" : "VLAN",
    "IsolationId" : <uint32>,
}

// PortMappingPolicy
{
    "Type" : "PortMapping",
    "Protocol" : <enum>,
         // AsString; Values: 
         // "Unknown" (0),
         // "ICMPv4" (1),
         // "IGMP" (2),
         // "TCP" (6),
         // "UDP" (17),
         // "ICMPv6" (58)
    "InternalPort" : <uint16>,
    "ExternalPort" : <uint16>,
}
```

## <a name="hcn-load-balancer-schema"></a>HCN 부하 분산 장치 스키마

```json
// Host Compute LoadBalancer
{
    "Id" : <string>,
    "Owner" : <string>,
    "SchemaVersion" : {
        "Major" : <uint32>,
        "Minor" : <uint32>
    },
    "Flags" : <enum bit mask>, 
         // AsString; Values: 
         // "None" (0),
         // "EnableDirectServerReturn" (1)
         // "EnableInternalLoadBalancer" (2)
    "HostComputeEndpoints" : [<Host compute Endpoint id>],
    "VirtualIPs" : [<Virtual IpAddress>],
    "PortMappings" : [ {
        "Type" : "PortMapping",
        "Protocol" : <enum>,
             // AsString; Values: 
             // "Unknown" (0),
             // "ICMPv4" (1),
             // "IGMP" (2),
             // "TCP" (6),
             // "UDP" (17),
             // "ICMPv6" (58)
        "InternalPort" : <uint16>,
        "ExternalPort" : <uint16>,
    } ],
    "Policies" : [ {
         "Type" : <enum>, 
              // AsString; Values: 
              // "SourceVirtualIp" (0), 
         "Data" : <any>
    } ],
}
```

## <a name="hcn-namespace-schema"></a>HCN 네임 스페이스 스키마

```json
// Namespace
{
    "Id" : <string>,
    "Owner" : <string>,
    "SchemaVersion" : {
        "Major" : <uint32>,
        "Minor" : <uint32>
    },
    "NamespaceId" : <uint32>,
    "NamespaceGuid" : <guid>,
    "Type"  : <enum>,
              // AsString; Values: 
              // "Host" (0), 
              // "HostDefault" (1), 
              // "Guest" (2), 
              // "GuestDefault" (3)
    "Resources" : [ {
          "Type"  : <enum>,
              // AsString; Values: 
              // "Container" (0), 
              // "Endpoint" (1)
          "Data"  : <any>
    } ],
}
```

## <a name="hcn-notification-schema"></a>HCN 알림 스키마

```json
// Notification
{
    "ID" : Guid,
    "Flags" : <uint32>,
};
```

## <a name="result-error-schema"></a>결과 오류 스키마

```json
// ErrorSchema
{
    "ErrorCode" : <uint32>,
    "Error" : <string>,
    "Success" : <bool>,
}
```

