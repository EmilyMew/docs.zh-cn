---
title: <iriParsing> 元素 （Uri 设置）
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: 710d82b70eb16e88404d4d8bbf38d2d030693103
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092495"
---
# <a name="iriparsing-element-uri-settings"></a>\<iriParsing > 元素 （Uri 设置）
指定是否对 <xref:System.Uri> 应用国际资源标识符 (IRI) 分析以及是否应该应用 IRI 分析规则。  
  
## <a name="schema-hierarchy"></a>架构层次结构  
 [\<配置 > 元素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Uri > 元素 （Uri 设置）](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<iriParsing>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a>语法  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|`enabled`|指定是否启用 IRI 分析。 默认值为 `false`。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父元素  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|[uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|包含指定.NET Framework 如何处理使用统一资源标识符 (Uri) 表示的 web 地址的设置。|  
  
## <a name="remarks"></a>备注  
 现有<xref:System.Uri>类具有.NET Framework 3.5 中进行了扩展。 3.0 SP1 和 2.0 SP1 提供对国际资源标识符 (IRI) 和国际化域名 (IDN) 的支持。 当前用户不会看到从.NET Framework 2.0 行为的任何更改，除非专门启用 IRI 和 IDN 支持。 这确保了 NET Framework 以前版本的应用程序兼容性。  
  
 若要启用 IRI 支持，以下两项更改是必需的：  
  
1.  将以下行添加到.NET Framework 2.0 目录下的 machine.config 文件  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  指定是否应该应用 IRI 分析规则。 这可以在 machine.config 或应用配置文件中完成。  
  
 启用 IRI 分析 (iriParsing 启用 = `true`) 将执行规范化和字符检查根据最新 IRI 规则在 RFC 3987。 默认值是`false`，将执行规范化和字符检查根据 RFC 2396 和 RFC 3986 （适用于 IPv6 文本）。  
  
### <a name="configuration-files"></a>配置文件  
 此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例演示使用的配置<xref:System.Uri>类，以支持分析 IRI 和 IDN 名称。  
  
### <a name="code"></a>代码  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [网络设置架构](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
