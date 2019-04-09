---
title: <bypassTrustedAppStrongNames> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c39d9a1e3da9cccb2f027e9597a6f2272d187ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179135"
---
# <a name="bypasstrustedappstrongnames-element"></a>\<bypassTrustedAppStrongNames > 元素
指定是否以跳过上加载到完全信任的完全信任程序集的强名称验证<xref:System.AppDomain>。  
  
 \<configuration>  
\<运行时 >  
\<bypassTrustedAppStrongNames>  
  
## <a name="syntax"></a>语法  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`enabled`|必需的特性。<br /><br /> 指定是否启用可避免验证完全信任程序集的强名称跳过功能。 启用此功能后，强名称的程序集加载时不验证正确。 默认值为 `true`。|  
  
## <a name="enabled-attribute"></a>enabled 特性  
  
|“值”|描述|  
|-----------|-----------------|  
|`true`|加载到完全信任程序集时，不会验证在完全信任程序集的强名称签名<xref:System.AppDomain>。 这是默认设置。|  
|`false`|在完全信任程序集的强名称签名进行验证时将其加载到完全信任程序集<xref:System.AppDomain>。 仅检查签名正确性; 强名称签名与另一个强名称的匹配项，它不进行比较。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关程序集绑定和垃圾回收的信息。|  
  
## <a name="remarks"></a>备注  
 强名称跳过功能可避免完全信任程序集的强名称签名验证的开销。  
  
 跳过功能适用于使用强名称进行签名及具有以下特征的任何程序集：  
  
-   完全受信任而无需<xref:System.Security.Policy.StrongName>证据 (例如，具有`MyComputer`区域证据)。  
  
-   加载到完全受信任的 <xref:System.AppDomain>。  
  
-   加载自该 <xref:System.AppDomain> 的 <xref:System.AppDomainSetup.ApplicationBase%2A> 属性下的某个位置。  
  
-   签名没有延迟。  
  
> [!NOTE]
>  如果跳过功能已禁用的计算机上的所有应用程序使用注册表项，则此配置文件设置无效。 有关详细信息，请参阅[如何：禁用强名称跳过功能](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何指定验证上完全信任程序集的强名称签名的行为。  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- [运行时设置架构](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [配置文件架构](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [如何：禁用强名称跳过功能](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
