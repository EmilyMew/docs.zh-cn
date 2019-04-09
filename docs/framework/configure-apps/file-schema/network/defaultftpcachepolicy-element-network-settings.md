---
title: <defaultFtpCachePolicy> 元素 （网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 36d174beea58ff96674bd873bfbcb8be89591669
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132530"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a>\<defaultFtpCachePolicy > 元素 （网络设置）
介绍 FTP 缓存功能是否处于活动状态并介绍了默认的缓存策略。  
  
 \<configuration>  
\<system.net>  
\<requestCaching>  
\<defaultFtpCachePolicy>  
  
## <a name="syntax"></a>语法  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`policyLevel`|指定 FTP 缓存策略。 默认值为 `Default`。|  
  
## <a name="policylevel-attribute"></a>policyLevel 属性  
  
|“值”|描述|  
|-----------|-----------------|  
|`Default`|如果资源是最新、 内容长度是准确的并且存在过期、 修改和内容长度属性将，返回缓存的资源。|  
|`BypassCache`|从服务器返回的资源。|  
|`CacheOnly`|如果内容长度存在并且匹配的项大小，则返回缓存的资源。|  
|`CacheIfAvailable`|如果提供了内容的长度，并且与匹配项的大小;，返回缓存的资源否则为该资源从服务器下载，并返回到调用方。|  
|`Revalidate`|如果缓存资源的时间戳是与服务器; 上的资源的时间戳相同，则返回缓存的资源否则为资源是从服务器下载，存储在缓存中，并返回给调用方。|  
|`Reload`|从服务器下载资源、 将其存储在缓存中，并返回给调用方的资源。|  
|`NoCacheNoStore`|如果缓存的资源存在，将删除它。 资源从服务器下载，并返回到调用方。|  
|`Revalidate`|如果时间戳与服务器上的资源的时间戳相同，则使用资源的缓存副本满足请求；否则从服务器下载资源，将资源展示给调用方，然后再存储在缓存中。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|控制网络请求的缓存机制。|  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 下面的示例演示如何指定缓存策略的 FTP `NoCacheNoStore`。  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [网络设置架构](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
