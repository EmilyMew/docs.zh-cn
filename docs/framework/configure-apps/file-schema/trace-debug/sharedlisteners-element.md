---
title: <sharedListeners> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: 281cc0bd2e577dedaffb7f7eaf04fe46e6ee0b59
ms.sourcegitcommit: 344d82456f27d09a210671214a14cfd7daf1f97c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2019
ms.locfileid: "58348812"
---
# <a name="sharedlisteners-element"></a>\<sharedListeners > 元素
包含任何源或跟踪元素可以引用的侦听器。  这些侦听器不会收到默认情况下，任何跟踪并不能在运行时检索这些侦听器。 标识为共享的侦听器可以按名称添加到源或跟踪侦听器。  
  
 \<configuration>  
\<system.diagnostics>  
\<sharedListeners>  
  
## <a name="syntax"></a>语法  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|将侦听器添加到 `sharedListeners` 集合中。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`Configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`system.diagnostics`|为 ASP.NET 配置节指定根元素。|  
  
## <a name="remarks"></a>备注  
 将侦听器添加到共享的侦听器集合不会使其活动的侦听器。 它必须仍将添加到跟踪源或跟踪添加到`Listeners`该跟踪元素的集合。 .NET Framework 中的侦听器类派生<xref:System.Diagnostics.TraceListener>类。  
  
 计算机配置文件 (Machine.config) 和应用程序配置文件中，可以使用此元素。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`<sharedListeners>`元素添加侦听器`console`到`Listeners`两个集合<xref:System.Diagnostics.TraceSource>和<xref:System.Diagnostics.Trace>类。 控制台跟踪侦听器将跟踪信息写入到通过调用控制台<xref:System.Diagnostics.TraceSource>或<xref:System.Diagnostics.Trace>。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a>请参阅
- <xref:System.Diagnostics.TraceListener>
- [跟踪和调试设置架构](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [跟踪侦听器](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
