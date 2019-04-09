---
title: <add> 元素<listeners>为 <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: ba0ffc4f95b9af7fcd319068501ce0bb9714c2ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089557"
---
# <a name="add-element-for-listeners-for-trace"></a>\<添加 > 元素\<侦听器 > 为\<跟踪 >
将侦听器添加到**侦听器**集合。  
  
 \<configuration>  
\<system.diagnostics>  
\<trace>  
\<listeners>  
\<add>  
  
## <a name="syntax"></a>语法  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|**类型**|必需的特性。<br /><br /> 指定的侦听器的类型。 必须使用满足要求中指定的字符串[指定完全限定的类型名称](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。|  
|**initializeData**|可选特性。<br /><br /> 传递给构造函数为指定类的字符串。|  
|**name**|可选特性。<br /><br /> 指定侦听器的名称。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|将筛选器添加到中的侦听器`Listeners`跟踪的集合。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`listeners`|指定的侦听器，可收集、 存储，并将消息路由。 侦听器将跟踪输出定向到适当的目标。|  
|`system.diagnostics`|为 ASP.NET 配置节指定根元素。|  
|`trace`|包含用于收集、存储和路由跟踪消息的侦听器。|  
  
## <a name="remarks"></a>备注  
 <xref:System.Diagnostics.Debug>并<xref:System.Diagnostics.Trace>类将共享相同**侦听器**集合。 如果将侦听器对象添加到在其中一个类的集合，其他类将使用相同的侦听器。 侦听器类派生自<xref:System.Diagnostics.TraceListener>。  
  
 如果未指定`name`特性，跟踪侦听器<xref:System.Diagnostics.TraceListener.Name%2A>的跟踪侦听器默认值为空字符串 ("")。 如果应用程序具有只有一个侦听器，可以将其添加而无需指定一个名称，并指定空字符串的名称将其删除。 但是，如果你的应用程序具有多个侦听器，则应指定每个跟踪侦听器，这样就可以识别和管理各个跟踪侦听器中的唯一名称<xref:System.Diagnostics.Debug.Listeners%2A>和<xref:System.Diagnostics.Trace.Listeners%2A>集合。  
  
> [!NOTE]
>  添加多个相同类型并且具有相同的跟踪侦听器命名为只有一个跟踪侦听器中的该类型的结果并命名要添加到`Listeners`集合。 但是，您可以以编程方式添加到多个完全相同的侦听器`Listeners`集合。  
  
 值**initializeData**属性取决于您创建的侦听器类型。 并非所有的跟踪侦听器需要你指定**initializeData**。  
  
> [!NOTE]
>  当你使用`initializeData`属性中，你可能会收到编译器警告"未声明 initializeData 属性。" 由于配置设置时根据的抽象基类进行验证，会出现此警告<xref:System.Diagnostics.TraceListener>，这不能识别`initializeData`属性。 通常情况下，可以忽略具有构造函数采用参数的跟踪侦听器实现此警告。  
  
 下表显示了随.NET Framework 中的跟踪侦听器，并说明的值及其**initializeData**属性。  
  
|跟踪侦听器类|initializeData 属性值|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream`值<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>构造函数。  设置`initializeData`属性为"`true`"来写入跟踪和调试输出到<xref:System.Console.Error%2A?displayProperty=nameWithType>;"`false`"要写入到<xref:System.Console.Out%2A?displayProperty=nameWithType>。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|文件的名称<xref:System.Diagnostics.DelimitedListTraceListener>写入。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|现有事件日志源的名称的名称。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|文件的名称，<xref:System.Diagnostics.EventSchemaTraceListener>写入。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|文件的名称，<xref:System.Diagnostics.TextWriterTraceListener>写入。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|文件的名称，<xref:System.Diagnostics.XmlWriterTraceListener>写入。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**\<添加 >** 元素添加侦听器`MyListener`并`MyEventListener`到**侦听器**集合。 `MyListener` 创建一个名为文件`MyListener.log`并将输出写入到该文件。 `MyEventListener` 事件日志中创建一个条目。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [跟踪和调试设置架构](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [跟踪侦听器](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
