---
title: <httpListener> 元素 （网络设置）
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: b3a6d527bc1bf8210bb85424fa218fda495a2a2d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099737"
---
# <a name="httplistener-element-network-settings"></a>\<httpListener > 元素 （网络设置）
自定义使用参数<xref:System.Net.HttpListener>类。  
  
 \<configuration>  
\<system.net>  
\<settings>  
\<httpListener>  
  
## <a name="syntax"></a>语法  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a>类型  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|unescapeRequestUrl|一个布尔值，该值指示如果<xref:System.Net.HttpListener>实例使用未经转义的原始 URI，而不是经过转换的 URI。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|[设置](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|配置 <xref:System.Net> 命名空间的基本网络选项。|  
  
## <a name="remarks"></a>备注  
 **UnescapeRequestUrl**属性指示如果<xref:System.Net.HttpListener>使用未经转义的原始 URI，而不是经过转换的 URI 其中任何百分比编码值转换和执行其他任何规范化步骤。  
  
 当<xref:System.Net.HttpListener>实例收到的请求通过`http.sys`服务，它创建的提供的 URI 字符串实例`http.sys`，并将其作为公开<xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>属性。  
  
 `http.sys`服务公开两个请求的 URI 字符串：  
  
-   原始 URI  
  
-   经过转换的 URI  
  
 原始 URI 是<xref:System.Uri?displayProperty=nameWithType>HTTP 请求的请求行中提供：  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 提供的原始 URI`http.sys`前面所述的请求是"/ 路径 /"。 这表示在通过网络发送以下 HTTP 谓词字符串。  
  
 `http.sys`服务从使用 HTTP 请求行中提供的 URI 请求中提供的信息创建经过转换的 URI，并要确定源服务器请求的主机标头应转发到。 这是通过比较已注册的 URI 前缀的一组与请求中的信息。 HTTP 服务器 SDK 文档引用此经过转换的 URI 作为 HTTP_COOKED_URL 结构。  
  
 以便可以请求与已注册的 URI 前缀进行比较，需要完成一些规范化到请求。 对于以上经过转换的 URI 示例将按如下所示：  
  
 `http://www.contoso.com/path/`  
  
 `http.sys`服务结合<xref:System.Uri.Host%2A?displayProperty=nameWithType>属性值和要创建一个已转换的 URI 的请求行中的字符串。 此外，`http.sys`和<xref:System.Uri?displayProperty=nameWithType>类还执行以下操作：  
  
-   取消转义所有百分比编码的值。  
  
-   将百分比编码为 utf-16 字符表示形式的非 ASCII 字符。 请注意，Unicode 字符 （Unicode 编码使用 %uxxxx 格式） 以及支持 utf-8 和 ANSI/DBCS 字符。  
  
-   执行其他规范化步骤，如路径压缩。  
  
 请求不包含有关使用百分比编码值的编码的任何信息，因为它可能无法确定正确的编码只是通过分析百分比编码值。  
  
 因此`http.sys`提供了用于修改该过程的两个注册表项：  
  
|注册表项|默认值|描述|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|如果为零，`http.sys`接受只有 UTF-8 编码的 Url。<br /><br /> 如果非零`http.sys`还接受请求中的 ANSI 编码或 DBCS 编码 Url。|  
|FavorUTF8|1|如果非零`http.sys`始终尝试解码 URL 为 utf-8 第一次; 如果该转换失败，并且 EnableNonUTF8 为非零，Http.sys 然后尝试将其解码为 ANSI 或者与 DBCS。<br /><br /> 如果为零 （和 EnableNonUTF8 为非零），`http.sys`尝试对其进行解码为 ANSI 或者与 DBCS; 如果该操作不成功，它会尝试 utf-8 转换。|  
  
 当<xref:System.Net.HttpListener>收到请求时，它使用从经过转换的 URI`http.sys`作为输入到<xref:System.Net.HttpListenerRequest.Url%2A>属性。  
  
 没有需要在 Uri 中支持除字符和数字的字符。 例如，以下 URI，用于检索客户的客户信息数字"1/3812":  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 请注意 Uri (%2f) 中的百分号编码斜杠。 这是有必要，请因为在这种情况下包含斜杠字符表示数据而不是路径分隔符。  
  
 将字符串传递给 Uri 构造函数将导致以下 URI:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 将路径拆分为其段将导致以下元素：  
  
 `Customer('1`  
  
 `3812')`  
  
 这不是请求的发件人的意图。  
  
 如果**unescapeRequestUrl**属性设置为**false**，然后当<xref:System.Net.HttpListener>收到请求时，它使用的原始 URI 而不是从经过转换的 URI`http.sys`作为的输入<xref:System.Net.HttpListenerRequest.Url%2A>属性。  
  
 默认值为**unescapeRequestUrl**属性是**true**。  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>属性可以用于获取的当前值**unescapeRequestUrl**适用的配置文件中的属性。  
  
## <a name="example"></a>示例  
 下面的示例演示如何配置<xref:System.Net.HttpListener>类在收到请求使用的原始 URI，而不是从经过转换的 URI 后`http.sys`作为输入到<xref:System.Net.HttpListenerRequest.Url%2A>属性。  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a>元素信息  
  
|||
|-|-|  
|命名空间|System.Net|  
|架构名称||  
|验证文件||  
|可以为空||  
  
## <a name="see-also"></a>请参阅

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [网络设置架构](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
