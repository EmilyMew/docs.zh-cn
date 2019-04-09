---
title: <add> Bypasslist （网络设置） 的元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 904c8e23f7a09a975a6f3b9322ed6bc4148d9ba4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098281"
---
# <a name="add-element-for-bypasslist-network-settings"></a>\<添加 > bypasslist （网络设置） 的元素
将 IP 地址或 DNS 名称添加到代理跳过列表。  
  
 \<configuration>  
\<system.net>  
\<defaultProxy >  
\<bypasslist >  
\<add>  
  
## <a name="syntax"></a>语法  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|**特性**|**描述**|  
|-------------------|---------------------|  
|**地址**|正则表达式描述 IP 地址或 DNS 名称。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|提供一组描述不使用代理的地址的正则表达式。|  
  
## <a name="remarks"></a>备注  
 `add`元素插入正则表达式描述 IP 地址或 DNS 服务器名称的绕过代理服务器的地址的列表。  
  
 值`address`属性应为描述一组 IP 地址或主机名的正则表达式。  
  
 指定此元素的正则表达式时应十分小心。 正则表达式"[a-z] +\\.contoso\\.com"匹配任意主机在 contoso.com 域，但它还将匹配 contoso.com.cpandl.com 域中的任何主机。 若要匹配仅在 contoso.com 域中的主机，使用的定位点 （"$"）:"[a-z] +\\.contoso\\.com$"。  
  
 有关正则表达式的详细信息，请参阅。[.NET framework 正则表达式](../../../../../docs/standard/base-types/regular-expressions.md)。  
  
## <a name="configuration-files"></a>配置文件  
 此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。  
  
## <a name="example"></a>示例  
 下面的示例将两个地址添加到忽略列表。 第一个跳过 contoso.com 域; 中的所有服务器的代理第二个跳过与 192.168 其 IP 地址开始的所有服务器的代理。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [网络设置架构](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
