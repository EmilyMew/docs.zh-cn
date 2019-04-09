---
title: <clear> SchemeSettings （Uri 设置） 的
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 132506dc15335b738fcdb026f4d31429bc45a228
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082680"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a>\<清除 > schemeSettings （Uri 设置） 的
清除所有现有方案设置。  
  
 \<configuration>  
\<uri>  
\<schemeSettings>  
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
|[\<schemeSettings > 元素 （Uri 设置）](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|指定如何分析特定方案的 <xref:System.Uri>。|  
  
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
 下面的示例演示使用的配置<xref:System.Uri>清除所有方案设置，然后添加对未转义的 http 方案的百分比编码路径分隔符的支持的类。  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [网络设置架构](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
