---
title: <filter> 元素<add>为 <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: 2bef729f179b41509d3c0381b26e38e364dbf86b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120739"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a>\<筛选器 > 元素\<添加 > 为\<sharedListeners >
将筛选器添加到 `sharedListeners` 集合中的侦听器。  
  
 \<configuration>  
\<system.diagnostics>  
\<sharedListeners > 元素  
\<add>  
\<filter>  
  
## <a name="syntax"></a>语法  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|**类型**|必需的特性。<br /><br /> 指定筛选器的类型。 可以使用仅该类型的完整名称 (格式为<xref:System.Type.FullName%2A?displayProperty=nameWithType>属性)，也可以使用完全限定的类型名称包括程序集信息 (格式为<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>属性)。 有关创建完全限定的类型名称的信息，请参阅[指定完全限定的类型名称](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。|  
|**initializeData**|可选特性。<br /><br /> 传递给构造函数为指定类的字符串。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`system.diagnostics`|指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。|  
|`sharedListeners`|任何源或跟踪元素可以引用的侦听器集合。|  
|`add`|将侦听器添加到**sharedListeners**集合。|  
  
## <a name="remarks"></a>备注  
 如果在中定义一个侦听器`<add>`的元素`<sharedListeners>`元素中，应在定义该侦听器的筛选器`<filter>`的子元素`<add>`元素。  
  
 计算机配置文件 (Machine.config) 和应用程序配置文件中，可以使用此元素。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`<filter>`元素添加到跟踪侦听器的筛选器`console`中`sharedListeners`集合。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [跟踪和调试设置架构](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
