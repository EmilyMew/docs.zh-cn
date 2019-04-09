---
title: <schemeSettings> 元素 （Uri 设置）
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 8dc505d8a9de4e8939372af61b23652551c36530
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094225"
---
# <a name="schemesettings-element-uri-settings"></a>\<schemeSettings > 元素 （Uri 设置）
指定如何分析特定方案的 <xref:System.Uri>。  
  
 \<configuration>  
\<uri>  
\<schemeSettings>  
  
## <a name="syntax"></a>语法  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 None  
  
### <a name="child-elements"></a>子元素  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|[添加](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|添加方案设置的方案名称。|  
|[清除](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|清除所有现有方案设置。|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|删除方案名称的方案设置。|  
  
### <a name="parent-elements"></a>父元素  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|[uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|包含指定.NET Framework 如何处理使用统一资源标识符 (Uri) 表示的 web 地址的设置。|  
  
## <a name="remarks"></a>备注  
 默认情况下，<xref:System.Uri?displayProperty=nameWithType>类取消转义百分号编码执行路径压缩前的路径分隔符。 此操作实施为针对攻击，如以下一种安全机制：  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 如果此 URI 获取传递给模块不处理百分号编码字符正确，可能会导致服务器正在执行的以下命令：  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 出于此原因，<xref:System.Uri?displayProperty=nameWithType>类第一个取消转义的路径分隔符，然后应用路径压缩。 将传递到的恶意 URL 上面的结果<xref:System.Uri?displayProperty=nameWithType>类构造函数结果中的以下 URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 SchemeSettings 配置选项用于特定方案的未取消转义百分比编码的路径分隔符，可以修改此默认行为。  
  
## <a name="configuration-files"></a>配置文件  
 此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。  
  
## <a name="example"></a>示例  
 下面的示例演示使用的配置<xref:System.Uri>类，以支持非转义的 http 方案的百分比编码路径分隔符。  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a>元素信息  
  
|||
|-|-|  
|命名空间|系统|  
|架构名称||  
|验证文件||  
|可以为空||  
  
## <a name="see-also"></a>请参阅

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [网络设置架构](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
