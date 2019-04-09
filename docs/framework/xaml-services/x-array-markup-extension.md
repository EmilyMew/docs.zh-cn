---
title: x:Array 标记扩展
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: 4f4e26eb3e5ccaf66b2173c7fc9952375c5f2a58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139134"
---
# <a name="xarray-markup-extension"></a>x:Array 标记扩展
有关在 XAML 中通过标记扩展的对象的数组，提供了常规支持。 这对应于`x:ArrayExtension`[MS-XAML] 中的 XAML 类型。  
  
## <a name="xaml-object-element-usage"></a>XAML 对象元素用法  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`typeName`|类型的名称，你`x:Array`将包含。 `typeName` 可能会 （并且通常为） 作为前缀的 XAML 命名空间包含 XAML 的类型定义。|  
|`arrayContents`|分配给该内部函数的项内容`ArrayExtension.Items`属性。 通常情况下，这些项被指定为中包含的一个或多个对象元素`x:Array`开始和结束标记。 此处应为可分配给中指定的 XAML 类型的指定对象`typeName`。|  
  
## <a name="remarks"></a>备注  
 `Type` 为所有的必需的属性`x:Array`对象元素。 一个`Type`参数值不需要使用`x:Type`标记扩展; 短类型的名称是 XAML 类型，这可以指定为字符串。  
  
 在.NET Framework XAML 服务实现中，输入的 XAML 类型和 CLR 的输出之间的关系<xref:System.Type>创建数组的会影响服务上下文的标记扩展。 输出<xref:System.Type>是<xref:System.Xaml.XamlType.UnderlyingType%2A>后查找所需的输入的 XAML 类型<xref:System.Xaml.XamlType>基于 XAML 架构上下文和<xref:System.Windows.Markup.IXamlTypeResolver>上下文提供的服务。  
  
 处理时，将数组内容分配给`ArrayExtension.Items`内部属性。 在中<xref:System.Windows.Markup.ArrayExtension>实现中，这由<xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>。  
  
 在.NET Framework XAML 服务实现中，对此标记扩展的处理由定义<xref:System.Windows.Markup.ArrayExtension>类。 <xref:System.Windows.Markup.ArrayExtension> 未密封，并且无法用作自定义的数组类型的标记扩展插件实现的基础。  
  
 `x:Array` 是的详细信息适用于常规 XAML 语言可扩展性。 但`x:Array`还可用于指定 XAML 的 XAML 支持的集合作为其结构化的属性内容某些属性的值。 例如，可以指定的内容<xref:System.Collections.IEnumerable>具有属性`x:Array`使用情况。  
  
 `x:Array` 是标记扩展。 当要求转义特性值应为非文本值或非处理程序名称时，通常会实现标记扩展，相对于只在某些类型或属性上放置类型转换器而言，此需求更具有全局性。 `x:Array` 部分是该规则的例外，因为而不是提供替代属性值处理`x:Array`另类处理其内部文本内容。 此行为使现有的内容模型以进行分组到一个数组和更高版本在代码隐藏中引用的访问已命名的数组; 可能不支持的类型您可以调用<xref:System.Array>方法来获取个人数组项。  
  
 在 XAML 中的所有标记扩展都使用大括号 ({,} `)`在其特性语法，该命令是依据 XAML 处理器认定标记扩展必须处理的属性值的约定。 有关通常的标记扩展的详细信息，请参阅[Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions-for-xaml.md)。  
  
 在 XAML 2009 年，`x:Array`定义为一种语言基元而不是标记扩展。 有关详细信息，请参阅[常见 XAML 语言基元的内置类型](built-in-types-for-common-xaml-language-primitives.md)。  
  
## <a name="wpf-usage-notes"></a>WPF 用法说明  
 通常情况下，填充的对象元素`x:Array`不是元素中存在的[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]XAML 命名空间，并且需要对非默认 XAML 命名空间的前缀映射。  
  
 例如，以下是两个字符串的简单数组与`sys`前缀 (以及`x`) 数组的级别定义。  
  
 [xaml]  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 对于用作数组元素的自定义类型，类还必须支持在 XAML 中作为对象元素实例化的要求。 有关详细信息，请参阅[XAML 及 WPF 的自定义类](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)。  
  
## <a name="see-also"></a>请参阅

- [标记扩展和 WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [从 WPF 迁移到 System.Xaml 的类型](types-migrated-from-wpf-to-system-xaml.md)
