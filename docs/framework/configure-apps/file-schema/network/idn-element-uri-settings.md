---
title: <idn> 元素 （Uri 设置）
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 3940f30f2ef90a77560a82edc909071f0ee8e130
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129397"
---
# <a name="idn-element-uri-settings"></a>\<idn > 元素 （Uri 设置）
指定是否对域名应用国际化域名 (IDN) 分析。  
  
## <a name="schema-hierarchy"></a>架构层次结构  
 [\<配置 > 元素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Uri > 元素 （Uri 设置）](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<idn>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a>语法  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|`enabled`|指定对域名应用国际化域名 (IDN) 分析的默认值为 none。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父元素  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|[uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|包含指定.NET Framework 如何处理使用统一资源标识符 (Uri) 表示的 web 地址的设置。|  
  
## <a name="remarks"></a>备注  
 现有<xref:System.Uri>类具有.NET Framework 3.5 中进行了扩展。 3.0 SP1 和 2.0 SP1 中的对国际资源标识符 (IRI) 和国际化域名 (IDN) 的支持。 当前用户不会看到从.NET Framework 2.0 行为的任何更改，除非专门启用 IRI 和 IDN 支持。 这确保了 NET Framework 以前版本的应用程序兼容性。  
  
 若要启用 IRI 支持，以下两项更改是必需的：  
  
1.  将以下行添加到.NET Framework 2.0 目录下的 machine.config 文件  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  指定是否对域名应用国际化域名 (IDN) 分析以及是否应该应用 IRI 分析规则。 这可以在 machine.config 或应用配置文件中完成。  
  
 有三个可能的 IDN 值具体取决于使用的 DNS 服务器：  
  
-   启用 idn = All  
  
     此值会将任何 Unicode 域名转换为 Punycode 等效项 （IDN 名称）。  
  
-   启用 idn = AllExceptIntranet  
  
     此值会将不在使用 Punycode 等效项 （IDN 名称） 在本地 Intranet 上的所有 Unicode 域名都转换。 在这种情况下若要处理本地 Intranet 上的国际化名称，用于 Intranet 的 DNS 服务器应该支持 Unicode 名称解析。  
  
-   启用 idn = 无  
  
     此值不会将转换为使用 Punycode 任何 Unicode 域名。 这是默认值是与.NET Framework 2.0 行为一致。  
  
 启用 IDN 可以将域名中所有 Unicode 标签转换成标签的 Punycode 等同项。 Punycode 名称只包含 ASCII 字符，并且始终以 xn-- 前缀开头。 这样是为了支持 Internet 上的 DNS 服务器，因为大部分 DNS 服务器仅支持 ASCII 字符（参见 RFC 3940）。  
  
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

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [网络设置架构](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
