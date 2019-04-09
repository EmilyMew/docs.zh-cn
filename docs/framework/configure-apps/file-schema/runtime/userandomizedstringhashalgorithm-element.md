---
title: <UseRandomizedStringHashAlgorithm> 元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a51b9fb485da605effbad0e81b8baf5e05e382a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087789"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<Userandomizedstringhashalgorithm，那么 > 元素
确定公共语言运行时是否在计算字符串的哈希代码每个应用程序域。  
  
 \<configuration>  
\<运行时 >  
\<UseRandomizedStringHashAlgorithm>  
  
## <a name="syntax"></a>语法  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`enabled`|必需的特性。<br /><br /> 指定字符串的哈希代码计算每个应用程序域。|  
  
## <a name="enabled-attribute"></a>enabled 特性  
  
|“值”|描述|  
|-----------|-----------------|  
|`0`|公共语言运行时不会计算字符串的哈希代码对每个应用程序域;使用单个算法来计算字符串哈希代码。 这是默认设置。|  
|`1`|公共语言运行时计算字符串的哈希代码对每个应用程序域。 在不同应用程序域和不同进程中的相同字符串将具有不同的哈希代码。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关运行时初始化选项的信息。|  
  
## <a name="remarks"></a>备注  
 默认情况下<xref:System.StringComparer>类和<xref:System.String.GetHashCode%2A?displayProperty=nameWithType>方法使用跨应用程序域生成一致的哈希代码的单个哈希算法。 这相当于设置`enabled`的属性`<UseRandomizedStringHashAlgorithm>`元素`0`。 这是在中使用的哈希算法[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]。  
  
 <xref:System.StringComparer>类和<xref:System.String.GetHashCode%2A?displayProperty=nameWithType>方法还可以使用不同的哈希算法计算哈希代码对每个应用程序域。 因此，等效的字符串的哈希代码将不同跨应用程序域。 这是一项选择加入的功能;若要充分利用它，必须设置`enabled`的属性`<UseRandomizedStringHashAlgorithm>`元素`1`。  
  
 哈希表中的字符串查找通常是 o （1） 的操作。 但是，大量冲突发生时，查找会变为 O (n<sup>2</sup>) 操作。 可以使用`<UseRandomizedStringHashAlgorithm>`要生成随机的哈希算法，每个应用程序域，从而限制潜在冲突数量，尤其是在从其计算哈希代码的密钥根据数据输入时配置元素由用户。  
  
## <a name="example"></a>示例  
 下面的示例定义`DisplayString`类，其中包含私有字符串常量， `s`，其值是"这是一个字符串"。 它还包括`ShowStringHashCode`显示的字符串值和其哈希代码，以及在其中执行方法的应用程序域的名称的方法。  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 不提供配置文件的情况下运行该示例时，它会显示类似于以下的输出。 请注意，该字符串的哈希代码完全相同的两个应用程序域中。  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 但是，如果将下面的配置文件添加到该示例的目录，然后运行该示例相同的字符串的哈希代码将通过应用程序域不同。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 当存在配置文件时，该示例将显示以下输出：  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
