---
title: <publisherPolicy> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29932eb27bcd13876ea6982982e67341edb8e0de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076284"
---
# <a name="publisherpolicy-element"></a>\<publisherPolicy > 元素
指定运行时是否使用发布者策略。  
  
 \<configuration>  
\<运行时 >  
\<assemblyBinding>  
\<dependentAssembly>  
\<publisherPolicy>  
  
## <a name="syntax"></a>语法  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`apply`|指定是否将应用发布者策略。|  
  
## <a name="apply-attribute"></a>应用特性  
  
|“值”|描述|  
|-----------|-----------------|  
|`yes`|将发布服务器策略应用。 此为默认设置。|  
|`no`|不适用于发布服务器策略。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关程序集绑定和垃圾回收的信息。|  
  
## <a name="remarks"></a>备注  
 时组件供应商发布新版本的程序集，供应商可以包括发布服务器策略，以便现在使用旧版本的应用程序使用新版本。 若要指定是否为特定的程序集应用出版商策略，请将 **\<publisherPolicy >** 中的元素 **\<dependentAssembly >** 元素。  
  
 默认设置为**应用**属性是**是**。 设置**应用**归于**没有**替代以前所有**是**程序集的设置。  
  
 权限是以显式忽略发行者策略使用的应用需要[ \<apply ="no"/ >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)应用程序配置文件中的元素。 通过设置授予权限<xref:System.Security.Permissions.SecurityPermissionFlag>标志<xref:System.Security.Permissions.SecurityPermission>。 有关详细信息，请参阅[程序集绑定重定向安全权限](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)。  
  
## <a name="example"></a>示例  
 下面的示例会关闭发行者策略程序集， `myAssembly`。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- [运行时设置架构](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [配置文件架构](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [运行时如何定位程序集](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [重定向程序集版本](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
