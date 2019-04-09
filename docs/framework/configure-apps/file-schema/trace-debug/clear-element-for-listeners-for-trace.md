---
title: <clear> 元素<listeners>为 <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 97b18f9d6baa618b0f535955b232e2119c758b11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124886"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<清除 > 元素\<侦听器 > 为\<跟踪 >
清除跟踪的 `Listeners` 集合。  
  
 \<configuration>  
\<system.diagnostics>  
\<trace>  
\<listeners>  
\<clear>  
  
## <a name="syntax"></a>语法  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`system.diagnostics`|指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。|  
|`trace`|包含用于收集、存储和路由跟踪消息的侦听器。|  
|`listeners`|包含用于收集、 存储和路由消息的侦听器。 侦听器将跟踪输出定向到适当的目标。|  
  
## <a name="remarks"></a>备注  
 `<clear>`元素中移除所有侦听器从`Listeners`跟踪的集合。 可以使用`<clear>`元素之前使用`<add>`元素为特定集合中没有任何其他活动的侦听器。  
  
 您可以清除`Listeners`以编程方式调用集合<xref:System.Diagnostics.TraceListenerCollection.Clear%2A>方法<xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>属性 (`System.Diagnostics.Trace.Listeners.Clear()`)。  
  
 计算机配置文件 (Machine.config) 和应用程序配置文件中，可以使用此元素。  
  
> [!NOTE]
>  `<clear>`元素中移除<xref:System.Diagnostics.DefaultTraceListener>从`Listeners`集合中，更改的行为<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>， <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>， <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>，和<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>方法。 调用`Assert`或`Fail`方法通常会显示一个消息框中。 但是，消息框如果不显示<xref:System.Diagnostics.DefaultTraceListener>不在`Listeners`集合。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`<clear>`之前使用的元素`<add>`元素添加侦听器`console`到`Listeners`跟踪的集合。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [跟踪和调试设置架构](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)
- [跟踪侦听器](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
