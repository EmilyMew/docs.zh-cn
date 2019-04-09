---
title: x:Null 标记扩展
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: e46d8561b62d9137d4fed4df447338a97fc0577b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100803"
---
# <a name="xnull-markup-extension"></a>x:Null 标记扩展
指定`null`作为 XAML 成员的值。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性用法  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>备注  
 中的空引用的关键字C#并[!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)]为 null。 Null 引用的 Microsoft Visual Basic 关键字`Nothing`，但始终使用`{x:Null}`作为 XAML 使用而不考虑 XAML 与关联的隐藏代码语言。  
  
 `x:Null`标记扩展没有任何可设置属性。  
  
 为 null 的使用情况通常是与 XAML 成员公开的 CLR<xref:System.Nullable%601>值。  
  
 `x:Null`标记扩展，所有 XAML 标记扩展，如使用大括号 (`{,}`) 用于转义属性值为非文本或事件处理程序引用的处理。 特性语法是最常使用此标记扩展使用的语法。 对象元素语法`<x:Null />`是从技术上讲是可行的但很少使用，因为`x:Null`标记扩展不包含位置参数或构造参数。  
  
 有关标记扩展的信息，请参阅[标记扩展和 WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
 在.NET Framework XAML 服务中，对此标记扩展的处理由定义<xref:System.Windows.Markup.NullExtension>类。  
  
## <a name="wpf-usage-notes"></a>WPF 用法说明  
 请注意，`null`不一定是引用类型依赖属性的初始取消设置的值。 初始默认值为每个依赖属性而异，并可以基于特定于属性的元数据。 许多依赖项属性不接受`null`值，不管是通过标记或代码由于它们的验证回调实现。 有关依赖项属性的详细信息，请参阅[依赖属性概述](../wpf/advanced/dependency-properties-overview.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [XAML 概述 (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [标记扩展和 WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
