---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: ca1f680e2de67984dfcec49b3d262799000a2625
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102578"
---
# <a name="channelpoolsettings"></a>\<channelPoolSettings>
指定自定义绑定的通道池设置。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<oneWay>  
\<channelPoolSettings>  
  
## <a name="syntax"></a>语法  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`idleTimeout`|一个值为正的 <xref:System.TimeSpan>，指定池中的通道在断开前可以空闲的最长时间。 默认值为 00:02:00。|  
|`leaseTimeout`|<xref:System.TimeSpan>，用于指定从通道返回池到通道关闭之间的时间间隔。 默认值为 00:10:00。|  
|`maxOutboundChannelsPerEndpoint`|一个正整数，指定对于每个远程端点可以存储在池中的通道的最大数目。 默认值为 10。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<oneWay>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|针对自定义绑定启用数据包路由。|  
  
## <a name="remarks"></a>备注  
 配额用作一种策略机制，防止消耗过多资源。 它们可防止恶意或无意的拒绝服务 (DOS) 攻击。 在设置自定义通道的通道配额时使用此元素。  
  
 `ChannelPoolSettings` 指定三项配额：  
  
-   `idleTimeout` 配额用于减少通过长时间占用资源来对服务器实施的拒绝服务 (DOS) 攻击。 在客户端，设置正确的值可增加与服务连接的可靠性。 默认值基于资源的保守适度分配。 该值适用于开发环境和小型安装方案。 如果某个安装耗尽了资源或是连接受到限制，则无论是否还有其他资源可用，服务管理员都应检查该值。  
  
-   `leaseTimeout` 配额用于与负载均衡器的集成以及提高可靠性。 默认值基于资源的保守分配。 该值适用于开发环境和小型安装方案。 如果某个安装耗尽了资源或是连接受到限制，则无论是否还有其他资源可用，服务管理员都应检查该值。  
  
-   `maxOutboundChannelsPerEndpoint` 配额设置服务器与客户端上的缓存限制，用于提高可靠性。 其默认值基于资源的保守适度分配，适用于开发环境和小型安装方案。 如果某个安装耗尽了资源或是连接受到限制，则无论是否还有其他资源可用，服务管理员都应检查该值。  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [绑定](../../../../../docs/framework/wcf/bindings.md)
- [扩展绑定](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [自定义绑定](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
