---
title: <trace> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 5faf352dce2a459a999b3cf54209f6bd9793bde0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073788"
---
# <a name="trace-element"></a>\<跟踪 > 元素
包含用于收集、存储和路由跟踪消息的侦听器。  
  
 \<configuration>  
\<system.diagnostics>  
\<trace>  
  
## <a name="syntax"></a>语法  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`autoflush`|可选特性。<br /><br /> 指定的跟踪侦听器是否在每个写入操作后会自动刷新输出缓冲区。|  
|`indentsize`|可选特性。<br /><br /> 指定要缩进空格的数。|  
|`useGlobalLock`|可选特性。<br /><br /> 指示是否应使用全局锁。|  
  
## <a name="autoflush-attribute"></a>自动刷新属性  
  
|“值”|描述|  
|-----------|-----------------|  
|`false`|不自动刷新输出缓冲区。 这是默认设置。|  
|`true`|自动刷新输出缓冲区。|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock Attribute  
  
|“值”|描述|  
|-----------|-----------------|  
|`false`|侦听器是线程安全; 如果不使用全局锁否则，将使用全局锁。|  
|`true`|使用全局锁，而不管侦听器是线程安全。 这是默认设置。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|指定的侦听器，可收集、 存储，并将消息路由。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`system.diagnostics`|指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`<trace>`元素添加侦听器`MyListener`到`Listeners`集合。 `MyListener` 创建一个名为的文件`MyListener.log`并将输出写入到该文件。 `useGlobalLock`属性设置为`false`，这将导致非用于如果跟踪侦听器是线程安全的全局锁。 `autoflush`属性设置为`true`，这将导致跟踪侦听器写入到文件而不考虑是否<xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>调用方法。 `indentsize`属性设置为 0 （零），这会导致要缩进没有任何空间的侦听器时<xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>调用方法。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [跟踪和调试设置架构](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
