---
title: StaticResource 标记扩展
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 8319e451268152e95326c02027157db72df631b8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125141"
---
# <a name="staticresource-markup-extension"></a>StaticResource 标记扩展
提供值的任何[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]通过查找对已定义资源的引用的属性特性。 对该资源的查找行为是类似于加载时查找，将在当前的标记从先前加载的资源查找[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]以及其他应用程序源页上，将生成与该资源值在运行时对象的属性值。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性用法  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML 对象元素用法  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`key`|所请求资源的密钥。 最初由该键[X:key 指令](../../xaml-services/x-key-directive.md)如果资源已在标记中，或作为提供`key`参数调用时<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>如果资源在代码中创建的。|  
  
## <a name="remarks"></a>备注  
  
> [!IMPORTANT]
>  一个`StaticResource`不能尝试使对资源定义前向引用在词法上进一步[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文件。 不支持尝试这样做，并且即使此类引用不会失败，尝试前向引用将会产生对加载时间性能产生负面影响时表示的内部哈希表<xref:System.Windows.ResourceDictionary>搜索。 为获得最佳结果，调整资源字典的组合，这样可以避免前向引用。 如果无法避免前向引用，使用[DynamicResource 标记扩展](dynamicresource-markup-extension.md)相反。  
  
 指定<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>应该对应于现有资源，以标识[X:key 指令](../../xaml-services/x-key-directive.md)页面、 应用程序，可用的控件的主题和外部资源或系统资源中的某个级别。 资源查找发生的顺序。 有关静态和动态资源的资源查找行为的详细信息，请参阅[XAML 资源](xaml-resources.md)。  
  
 资源键可以是任何字符串中定义[XamlName 语法](../../xaml-services/xamlname-grammar.md)。 资源键也可以是其他对象类型，如<xref:System.Type>。 一个<xref:System.Type>密钥是如何控件可以设置的样式的主题，通过隐式样式项的基础。 有关详细信息，请参阅[控件创作概述](../controls/control-authoring-overview.md)。  
  
 引用资源的可选声明性方式是作为[DynamicResource 标记扩展](dynamicresource-markup-extension.md)。  
  
 特性语法是最常用于该标记扩展的语法。 在 `StaticResource` 标识符字符串之后提供的字符串标记被指定为基础 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 扩展类的 <xref:System.Windows.StaticResourceExtension> 值。  
  
 `StaticResource` 可以在对象元素语法中使用。 在这种情况下，指定的值<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>属性是必需的。  
  
 `StaticResource` 此外可以在详细特性用法中，指定使用<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>属性作为属性 = 值对：  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 如果扩展具有一个以上的可设置属性，或者某些属性是可选的，则详细用法通常会很有用。 由于 `StaticResource` 仅有一个可设置的属性，并且此属性是必需的，因此该详细用法不具有典型性。  
  
 在中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]处理器实现中，对此标记扩展的处理由定义<xref:System.Windows.StaticResourceExtension>类。  
  
 `StaticResource` 是标记扩展。 当要求转义特性值应为非文本值或非处理程序名称时，通常会实现标记扩展，相对于只在某些类型或属性上放置类型转换器而言，此需求更具有全局性。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有标记扩展在其特性语法中都使用 { 和 } 字符，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 处理器通过这一约定确认标记扩展必须处理该特性。 有关详细信息，请参阅[标记扩展和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>请参阅

- [样式设置和模板化](../controls/styling-and-templating.md)
- [XAML 概述 (WPF)](xaml-overview-wpf.md)
- [标记扩展和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [XAML 资源](xaml-resources.md)
- [资源和代码](resources-and-code.md)
