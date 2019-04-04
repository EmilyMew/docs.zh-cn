---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 692c4cf6688bfc2f9b99f065f4b16711f7f08063
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412040"
---
# <a name="nettcp"></a>\<net.tcp>
指定允许多个进程共享同一 TCP 端口的 NET.TCP 端口共享服务的配置设置。  
  
 \<system.serviceModel.activation>  
\<net.tcp>  
  
## <a name="syntax"></a>语法  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="Integer"
             maxPendingAccepts="Integer"
             maxPendingConnections="Integer"
             receiveTimeout="TimeSpan"
             teredoEnabled="Boolean">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only)-->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a>类型  
 `Type`  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`listenBacklog`|一个整数，指定从共享连接接受但仍未调度给 Windows Communication Foundation (WCF) 服务的最大未完成连接。 默认值为 10。|  
|`maxPendingAccepts`|一个整数，指定共享服务侦听终结点上的最大未完成并发接受线程数。 默认值为 2。|  
|`MaxPendingConnections`|侦听器可以拥有的正在等待应用程序接受的最大连接数。 超出此配额值时，新的传入连接会被丢弃而不是等待接受。 连接功能（如消息安全）可能会使客户端打开多个连接。 在设置此配额值时，服务管理员应该考虑这些额外的连接。 默认值为 10。|  
|`receiveTimeout`|
  <xref:System.TimeSpan>，它将为读取组帧数据并执行来自基础连接的连接调度指定超时值。 默认值为“00:00:10”。|  
|`teredoEnabled`|一个布尔值，该值指示端口共享服务是否使用 Microsoft Teredo 服务代表 WCF 服务的 TCP 端口上进行侦听。 默认值为 `false`。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<allowAccounts>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|包含的配置元素的集合`securityIdentifier`属性指定的进程的承载 WCF 服务并被授予对共享服务的连接访问权限的用户帐户。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|包含侦听器进程 SMSvcHost.exe 的配置设置。|  
  
## <a name="remarks"></a>备注  
 端口共享的详细信息，请参阅[Net.TCP 端口共享](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)。 若要了解如何配置端口共享服务，请参阅[配置 Net.TCP 端口共享服务](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)。  
  
## <a name="see-also"></a>请参阅
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [Net.TCP 端口共享](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [配置 Net.TCP 端口共享服务](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
