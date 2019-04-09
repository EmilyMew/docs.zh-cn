---
title: ThemeDictionary 标记扩展
ms.date: 03/30/2017
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
ms.openlocfilehash: ad2248c791fadc5363d90ff496d5e040f6036ab3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132088"
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary 标记扩展
为集成第三方控件的自定义控件创作者或应用程序提供一种方法，用于加载要在设置控件样式时使用的特定于主题的资源字典。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性用法  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML 对象元素用法  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`assemblyUri`|程序集的 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]，其中包含主题信息。 通常，这是一个引用较大包中程序集的 Pack URI。 程序集资源和 Pack URI 可以简化部署问题。 有关详细信息，请参阅 [WPF 中的 Pack URI](../app-development/pack-uris-in-wpf.md)。|  
  
## <a name="remarks"></a>备注  
 此扩展旨在填补只有一个特定属性值： 的值<xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>。  
  
 通过使用此扩展，可以指定一个纯资源程序集，该程序集包含一些仅在向用户系统应用 [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] 主题时使用的样式、当 Luna 主题处于活动状态时的其他样式等。 通过使用此扩展，可以自动让特定于控件的资源字典的内容失效，并在需要时重新将其加载为特定于其他主题的内容。  
  
 `assemblyUri`字符串 (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>属性值) 标识的字典适用于特定主题的命名约定的基础。 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>逻辑`ThemeDictionary`通过生成来完成约定[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]，它指向特定主题字典变体，包含在预编译的资源程序集中。 本文并未将该约定（即主题与一般控件样式设置和页/应用程序级样式设置之间的交互）作为一个概念进行详细介绍。 使用的基本情形`ThemeDictionary`是指定<xref:System.Windows.ResourceDictionary.Source%2A>属性的`ResourceDictionary`应用程序级别的声明。 将 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 通过 `ThemeDictionary` 扩展而不是作为一个直接的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 提供给程序集时，扩展逻辑将提供系统主题更改时适用的失效逻辑。  
  
 特性语法是最常用于该标记扩展的语法。 在 `ThemeDictionary` 标识符字符串之后提供的字符串标记被指定为基础 <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> 扩展类的 <xref:System.Windows.ThemeDictionaryExtension> 值。  
  
 `ThemeDictionary` 此外可能在对象元素语法中使用。 在这种情况下，指定的值<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>属性是必需的。  
  
 `ThemeDictionary` 此外可以在详细特性用法中，指定使用<xref:System.Windows.Markup.StaticExtension.Member%2A>属性作为属性 = 值对：  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 如果扩展具有一个以上的可设置属性，或者某些属性是可选的，则详细用法通常会很有用。 由于 `ThemeDictionary` 仅有一个可设置的属性，并且此属性是必需的，因此该详细用法不具有典型性。  
  
 在中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]处理器实现中，对此标记扩展的处理由定义<xref:System.Windows.ThemeDictionaryExtension>类。  
  
 `ThemeDictionary` 是标记扩展。 当要求转义特性值应为非文本值或非处理程序名称时，通常会实现标记扩展，相对于只在某些类型或属性上放置类型转换器而言，此需求更具有全局性。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有标记扩展在其特性语法中都使用 { 和 } 字符，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 处理器通过这一约定确认标记扩展必须处理该特性。 有关详细信息，请参阅[标记扩展和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>请参阅

- [样式设置和模板化](../controls/styling-and-templating.md)
- [XAML 概述 (WPF)](xaml-overview-wpf.md)
- [标记扩展和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [WPF 应用程序资源、内容和数据文件](../app-development/wpf-application-resource-content-and-data-files.md)
