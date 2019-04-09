---
title: <qualifyAssembly> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a4741c6a4745bdba00fdb525b39b70d0b15e005
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109443"
---
# <a name="qualifyassembly-element"></a>\<qualifyAssembly > 元素
指定使用部分名称时应动态加载的程序集全名。  
  
 \<configuration>  
\<运行时 >  
\<assemblyBinding>  
\<qualifyAssembly>  
  
## <a name="syntax"></a>语法  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`partialName`|必需的特性。<br /><br /> 显示在代码中指定的程序集的部分名称。|  
|`fullName`|必需的特性。<br /><br /> 显示在全局程序集缓存中指定的程序集的全名。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`assemblyBinding`|包含有关程序集版本重定向和程序集位置的信息。|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关程序集绑定和垃圾回收的信息。|  
  
## <a name="remarks"></a>备注  
 调用<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>使用部分程序集名称的方法会导致公共语言运行时查找仅在应用程序基目录中的程序集。 使用 **\<qualifyAssembly >** 可提供完整的程序集信息 （名称、 版本、 公钥标记和区域性） 并且使公共语言运行时搜索应用程序配置文件中的元素有关全局程序集缓存中的程序集。  
  
 **FullName**属性必须包含程序集标识的四个字段： 名称、 版本、 公钥标记和区域性。 **PartialName**属性部分必须引用的程序集。 您必须至少指定程序集的文本名称 （最常见的情况），但您还可以包含版本、 公钥标记或区域性 （或四个，但并非所有四个的任意组合）。 **PartialName**的调用中指定的名称必须匹配。 例如，不能指定`"math"`作为**partialName**属性中，配置文件并调用`Assembly.Load("math, Version=3.3.3.3")`在代码中。  
  
## <a name="example"></a>示例  
 下面的示例以逻辑方式调用变成`Assembly.Load("math")`到`Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- [运行时设置架构](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [运行时如何定位程序集](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [部分程序集引用](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))
