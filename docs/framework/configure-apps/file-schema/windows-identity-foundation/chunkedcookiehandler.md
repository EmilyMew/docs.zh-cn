---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: d9c81d5de7bea343f0d67fa00037763fbae7b8c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120778"
---
# <a name="chunkedcookiehandler"></a>\<chunkedCookieHandler>
配置<xref:System.IdentityModel.Services.ChunkedCookieHandler>。 此元素仅可能存在如果`mode`属性的`<cookieHandler>`元素是"Default"块"。  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<cookieHandler>  
\<chunkedCookieHandler>  
  
## <a name="syntax"></a>语法  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|chunkSize|最大大小，以字符为单位的任何一个 HTTP cookie 的 HTTP cookie 数据。 您必须是块区大小调整时请小心。 Web 浏览器 cookie 和每个域允许数量的大小具有不同的限制。 例如，原始 Netscape 规范规定这些限制：将总 300 cookie，cookie 标头 （包括元数据，而不仅仅是 cookie 值），每 4096 字节数和每个域的 20 cookie。 默认值为 2000年。 必需。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<cookieHandler>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|配置<xref:System.IdentityModel.Services.CookieHandler>的<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) 用于读取和写入 cookie。|  
  
## <a name="remarks"></a>备注  
 当指定<xref:System.IdentityModel.Services.ChunkedCookieHandler>通过设置`mode`的属性`<cookieHandler>`为"Default"或"Chunked"元素，可以指定块的大小的 cookie 处理程序用来读取和写入 cookie 包括`<chunkedCookieHandler>`子元素和设置其`chunkSize`属性。 如果`<chunkedCookieHandler>`元素不存在，则使用默认区块大小的 2000 个字节。 不能为此元素时指定`mode`属性设置为"自定义"。  
  
 `<chunkedCookieHandler>`元素表示由<xref:System.IdentityModel.Services.ChunkedCookieHandlerElement>类。  
  
## <a name="example"></a>示例  
 下面的示例配置中的 3000 个字节块写入 cookie chunked 的 cookie 处理程序。  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
