---
title: <gcAllowVeryLargeObjects> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19103b2ac6e6dbba930050074fcea3cfd5a97661
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098011"
---
# <a name="gcallowverylargeobjects-element"></a>\<gcAllowVeryLargeObjects > 元素
在 64 位平台上，启用总大小大于 2 千兆字节 (GB) 的数组。  
  
 \<配置 > 元素  
\<运行时 > 元素  
\<gcAllowVeryLargeObjects > 元素  
  
## <a name="syntax"></a>语法  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`enabled`|必需的特性。<br /><br /> 指定是否在 64 位平台上启用的总大小大于 2 GB 的数组。|  
  
## <a name="enabled-attribute"></a>enabled 特性  
  
|“值”|描述|  
|-----------|-----------------|  
|`false`|数组大于 2 GB 的总大小不会启用。 这是默认设置。|  
|`true`|64 位平台上启用了数组大于 2 GB 的总大小。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关运行时初始化选项的信息。|  
  
## <a name="remarks"></a>备注  
 在应用程序配置文件中使用此元素启用数组大于 2 GB 的大小，但不会更改对对象大小或数组大小的其他限制：  
  
-   最大数组中元素数是<xref:System.UInt32.MaxValue?displayProperty=nameWithType>。  
  
-   在任何单个维度中的最大索引是 2,147,483,591 (0x7FFFFFC7) 的字节数组和单字节结构的数组和 2,146,435,071 (0X7FEFFFFF) 对于其他类型。  
  
-   字符串和其他非数组对象的最大大小保持不变。  
  
> [!CAUTION]
>  启用此功能前，请确保你的应用程序不包括假设所有数组大于 2 GB 的大小较小的不安全代码。 例如，如果写入假定数组不会超过 2 GB，数组用作缓冲区的不安全代码可能是容易受到缓冲区溢出。  
  
## <a name="example"></a>示例  
 下面的示例演示如何启用此功能的应用程序。  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- [运行时设置架构](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [配置文件架构](../../../../../docs/framework/configure-apps/file-schema/index.md)
