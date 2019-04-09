---
title: <CompatSortNLSVersion> 元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfd241056947fbf1daf48b84ff41e3f74ff7b8de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195769"
---
# <a name="compatsortnlsversion-element"></a>\<CompatSortNLSVersion > 元素
指定在执行字符串比较时，运行时应使用旧排序顺序。  
  
 \<configuration>  
\<运行时 >  
\<CompatSortNLSVersion > 元素  
  
## <a name="syntax"></a>语法  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`enabled`|必需的特性。<br /><br /> 指定要使用其排序顺序的区域设置 ID。|  
  
## <a name="enabled-attribute"></a>enabled 特性  
  
|“值”|描述|  
|-----------|-----------------|  
|4096|表示备选排序顺序的区域设置 ID。 在此示例中，4096 表示 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 和更早版本的排序顺序。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关运行时初始化选项的信息。|  
  
## <a name="remarks"></a>备注  
 因为由执行字符串比较、 排序和大小写的操作<xref:System.Globalization.CompareInfo?displayProperty=nameWithType>类中[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]如符合 Unicode 5.1 标准，字符串比较方法的结果<xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType>和<xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType>可能不同于.NET framework 的早期版本。 如果你的应用程序依赖于旧行为，则可以通过在你的应用程序配置文件中包括 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 元素来还原 `<CompatSortNLSVersion>` 及早期版本中使用的字串比较和排序规则。  
  
> [!IMPORTANT]
>  还原旧的字符串比较和排序规则还要求 sort00001000.dll 动态链接库在本地系统上可用。  
  
 此外，通过在创建应用程序域时将字符串“NetFx40_Legacy20SortingBehavior”传递到 <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> 方法，可以在特定的应用程序域中使用旧的字符串排序和比较规则。  
  
## <a name="example"></a>示例  
 下面的示例实例化两个 <xref:System.String> 对象，并调用 <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法以通过使用当前区域性的约定对它们进行比较。  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 上运行此示例时，将显示以下输出。  
  
```  
sta follows a in the sort order.  
```  
  
 这完全不同于你在 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 上运行此示例时显示的输出。  
  
```  
sta equals a in the sort order.  
```  
  
 但是，如果将下面的配置文件添加到示例的目录中，然后在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 上运行此示例，则输出将与示例在 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 上运行时产生的输出相同。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- [运行时设置架构](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [配置文件架构](../../../../../docs/framework/configure-apps/file-schema/index.md)
