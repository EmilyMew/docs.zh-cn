---
title: DynamicResource 标记扩展
ms.date: 03/30/2017
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
ms.openlocfilehash: d07816718ebee2507f1888cffb70e6f8037bb996
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091403"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource 标记扩展
提供值的任何[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]通过推迟将对定义资源的引用值的属性特性。 类似于运行时查找该资源的查找行为。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性用法  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>XAML 属性元素用法  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`key`|所请求资源的密钥。 最初由该键[X:key 指令](../../xaml-services/x-key-directive.md)如果资源已在标记中，或作为提供`key`参数调用时<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>如果资源在代码中创建的。|  
  
## <a name="remarks"></a>备注  
 一个`DynamicResource`将创建初始编译期间的临时表达式并因此延迟的资源查找，直到实际需要来构造对象请求的资源值为止。 这可能后[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]加载页面。 资源值将基于与当前的页范围，从开始的所有活动的资源字典的密钥搜索找到并替换为从编译的占位符表达式。  
  
> [!IMPORTANT]
>  依赖关系属性在优先级方面，`DynamicResource`表达式等效于应用的动态资源引用的位置的位置。 如果将以前的属性的本地值`DynamicResource`作为本地值，表达式`DynamicResource`完全删除。 有关详细信息，请参阅[依赖属性值优先级](dependency-property-value-precedence.md)。  
  
 某些资源的访问方案是特别适合`DynamicResource`而不是[StaticResource 标记扩展](staticresource-markup-extension.md)。 请参阅[XAML 资源](xaml-resources.md)有关的相对优点和性能产生的影响的讨论`DynamicResource`和`StaticResource`。  
  
 指定<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>应该对应于现有的资源由[X:key 指令](../../xaml-services/x-key-directive.md)在您的页面、 应用程序、 可用的控件的主题和外部资源或系统资源，在某种程度上和查找资源也将按该顺序。 有关静态和动态资源的资源查找的详细信息，请参阅[XAML 资源](xaml-resources.md)。  
  
 资源键可以是任何字符串中定义[XamlName 语法](../../xaml-services/xamlname-grammar.md)。 资源键也可以是其他对象类型，如<xref:System.Type>。 一个<xref:System.Type>密钥是如何可以由主题样式控件的基础。 有关详细信息，请参阅[控件创作概述](../controls/control-authoring-overview.md)。  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 用于查找资源值，如<xref:System.Windows.FrameworkElement.FindResource%2A>，遵循所使用的相同的资源查找逻辑`DynamicResource`。  
  
 引用资源的可选声明性方式是作为[StaticResource 标记扩展](staticresource-markup-extension.md)。  
  
 特性语法是最常用于该标记扩展的语法。 在 `DynamicResource` 标识符字符串之后提供的字符串标记被指定为基础 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 扩展类的 <xref:System.Windows.DynamicResourceExtension> 值。  
  
 `DynamicResource` 可以在对象元素语法中使用。 在这种情况下，指定的值<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>属性是必需的。  
  
 `DynamicResource` 此外可以在详细特性用法中，指定使用<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>属性作为属性 = 值对：  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 如果扩展具有一个以上的可设置属性，或者某些属性是可选的，则详细用法通常会很有用。 由于 `DynamicResource` 仅有一个可设置的属性，并且此属性是必需的，因此该详细用法不具有典型性。  
  
 在中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]处理器实现中，对此标记扩展的处理由定义<xref:System.Windows.DynamicResourceExtension>类。  
  
 `DynamicResource` 是标记扩展。 当要求转义特性值应为非文本值或非处理程序名称时，通常会实现标记扩展，相对于只在某些类型或属性上放置类型转换器而言，此需求更具有全局性。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有标记扩展在其特性语法中都使用 { 和 } 字符，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 处理器通过这一约定确认标记扩展必须处理该特性。 有关详细信息，请参阅[标记扩展和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>请参阅

- [XAML 资源](xaml-resources.md)
- [资源和代码](resources-and-code.md)
- [x:Key 指令](../../xaml-services/x-key-directive.md)
- [XAML 概述 (WPF)](xaml-overview-wpf.md)
- [标记扩展和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource 标记扩展](staticresource-markup-extension.md)
- [标记扩展和 WPF XAML](markup-extensions-and-wpf-xaml.md)
