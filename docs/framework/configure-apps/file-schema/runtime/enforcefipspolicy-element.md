---
title: <enforceFIPSPolicy> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1aa958e15449949a1b7ca740198fff71295b2ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59114828"
---
# <a name="enforcefipspolicy-element"></a>\<enforceFIPSPolicy > 元素
指定是否强制执行以下计算机配置要求：加密算法必须符合美国联邦信息处理标准 (FIPS)。  
  
 \<配置 > 元素  
\<运行时 > 元素  
\<enforceFIPSPolicy > 元素  
  
## <a name="syntax"></a>语法  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|enabled|必需的特性。<br /><br /> 指定是否启用强制执行的计算机配置要求，必须符合 FIPS 的加密算法。|  
  
## <a name="enabled-attribute"></a>enabled 特性  
  
|“值”|描述|  
|-----------|-----------------|  
|`true`|如果您的计算机配置为要求要符合 FIPS 的加密算法，则强制实施该要求。 如果一个类实现一种算法，不符合 FIPS，构造函数或`Create`为该类的方法会引发异常，该计算机上运行时。 这是默认设置。|  
|`false`|应用程序使用的加密算法不需要为符合 FIPS，而不考虑计算机配置。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关程序集绑定和垃圾回收的信息。|  
  
## <a name="remarks"></a>备注  
 从.NET Framework 2.0 开始，由计算机的配置控制的实现加密算法的类创建。 如果计算机配置为要求算法来为符合 FIPS，并且一个类实现不符合 FIPS 的算法，任何尝试创建该类的实例将引发异常。 构造函数引发<xref:System.InvalidOperationException>异常，并`Create`方法抛出<xref:System.Reflection.TargetInvocationException>内部异常<xref:System.InvalidOperationException>异常。  
  
 如果你的应用程序在其配置要求符合 FIPS，计算机上运行并且你的应用程序使用不符合 FIPS 的算法，您可以使用此元素在配置文件中以防止公共语言运行时 (CLR) 从强制实施的 FIPS 符合性。 中引入了此元素[!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)]。  
  
## <a name="example"></a>示例  
 下面的示例显示了如何防止 CLR 强制实施 FIPS 符合性。  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- [运行时设置架构](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [配置文件架构](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [加密模型](../../../../../docs/standard/security/cryptography-model.md)
