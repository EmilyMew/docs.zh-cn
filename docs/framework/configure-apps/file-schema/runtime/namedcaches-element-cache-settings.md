---
title: <namedCaches> 元素 （缓存设置）
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 36920a5e585c0c7581fbc4f84043d68550fbdac1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104931"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedCaches > 元素 （缓存设置）
指定的配置设置的命名集合<xref:System.Runtime.Caching.MemoryCache>实例。 <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>属性引用的配置设置集合中一个或多个`namedCaches`配置文件中的元素。  
  
 \<configuration>  
\< system.runtime.caching>  
\<memoryCache>  
\<namedCaches>  
  
## <a name="syntax"></a>语法  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a>类型  
 `None`  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|指定的最大大小，以兆字节为单位，一个整数值的实例<xref:System.Runtime.Caching.MemoryCache>可以增长到。 默认值为 0，这意味着的自动调整大小试探法<xref:System.Runtime.Caching.MemoryCache>类默认情况下使用。|  
|`name`|缓存的名称。|  
|`physicalMemoryLimitPercentage`|一个整数值介于 0 和 100 之间，指定可以使用由缓存以物理方式安装的计算机内存的最大百分比。 默认值为 0，这意味着的自动调整大小试探法<xref:System.Runtime.Caching.MemoryCache>类默认情况下使用。|  
|`pollingInterval`|一个时间间隔的值，在该时间间隔之后，缓存实现会将当前内存负载与为缓存实例设置的基于绝对值和百分比的内存限制进行比较。 "Hh: mm:"格式输入此值。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|向内存缓存的 `namedCaches` 集合添加一个命名的缓存。|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|清除内存缓存的 `namedCaches` 集合。|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|从内存缓存的 `namedCaches` 集合中删除一个命名的缓存条目。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|定义一个用于配置基于 <xref:System.Runtime.Caching.MemoryCache> 类的缓存的元素。|  
  
## <a name="remarks"></a>备注  
 可以包含 Web.config 文件的内存缓存配置部分`add`， `remove`，并`clear`属性`namedCaches`集合。 每个`namedCaches`由唯一标识条目`name`属性。  
  
 可以通过引用应用程序配置文件中的信息来检索实例的内存缓存项。 默认情况下，默认的缓存实例配置文件中具有条目。 默认缓存实例是从返回的实例<xref:System.Runtime.Caching.MemoryCache.Default%2A>属性。  
  
 如果设置为"default"的 name 属性，该元素使用的默认内存缓存实例。  
  
## <a name="example"></a>示例  
 下面的示例演示如何通过设置缓存的名称设置为默认缓存项名称`name`属性设置为"default"。  
  
 将 `cacheMemoryLimitMegabytes` 属性和 `physicalMemoryPercentage` 属性设置为零。 将这些属性设置为零意味着的自动调整大小试探法<xref:System.Runtime.Caching.MemoryCache>类使用。 缓存实现将当前内存负载与每隔两分钟的绝对内存和基于百分比的内存限制进行比较。  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- [\<memoryCache > 元素 （缓存设置）](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
