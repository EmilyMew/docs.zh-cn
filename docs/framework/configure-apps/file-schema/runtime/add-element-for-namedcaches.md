---
title: <add> 元素 <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 9a7e370f9cce0e9ddf6dbe49984b7597e041eb84
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094523"
---
# <a name="add-element-for-namedcaches"></a>\<添加 > 元素\<namedCaches >
将添加`namedCache`进入`namedCaches`内存缓存的集合。  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches>  
\<add>  
  
## <a name="syntax"></a>语法  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>类型  
 `None`  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|-|-|  
|`CacheMemoryLimitMegabytes`|一个整数值，指定的最大允许大小 （以兆字节为单位） 的实例<xref:System.Runtime.Caching.MemoryCache>可以增长到。 默认值为 0，这意味着<xref:System.Runtime.Caching.MemoryCache>默认情况下使用类的自动调整大小试探法。|  
|`Name`|缓存的名称。|  
|`PhysicalMemoryLimitPercentage`|一个整数值介于 0 和 100 之间，指定可以使用由缓存以物理方式安装的计算机内存的最大百分比。 默认值为 0，这意味着<xref:System.Runtime.Caching.MemoryCache>默认情况下使用类的自动调整大小试探法。|  
|`PollingInterval`|一个时间间隔的值，在该时间间隔之后，缓存实现会将当前内存负载与为缓存实例设置的基于绝对值和百分比的内存限制进行比较。 "Hh: mm:"格式输入此值。|  
  
### <a name="child-elements"></a>子元素  
 `None`  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|包含的配置设置的命名集合<xref:System.Runtime.Caching.MemoryCache>实例。|  
  
## <a name="remarks"></a>备注  
 `add`元素添加一个条目`namedCaches`内存缓存的集合。 可以使用[清除](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)元素在使用之前`add`元素以确认是否不存在任何其他命名缓存在集合中的。 在 machine.config 文件中并在 Web.config 文件中，可以使用此元素。  
  
## <a name="example"></a>示例  
 下面的示例演示如何定义的默认设置`namedCache`进入`namedCaches`内存缓存的集合。  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- [\<namedCaches > 元素 （缓存设置）](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
