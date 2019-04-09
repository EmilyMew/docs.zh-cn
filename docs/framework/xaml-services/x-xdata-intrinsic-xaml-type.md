---
title: x:XData 内部 XAML 类型
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: c8044bc341ded6ef7b03bbdf701e724654460d54
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125154"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData 内部 XAML 类型
启用 XAML 生产中的 XML 数据岛的布局。 中的 XML 元素`x:XData`如同它们是使其执行操作默认 XAML 命名空间的一部分或任何其他 XAML 命名空间不应由 XAML 处理器处理。 `x:XData` 可以包含任意格式正确的 XML。  
  
## <a name="xaml-object-element-usage"></a>XAML 对象元素用法  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`elementDataRoot`|包含的数据岛的单个根元素。 对于大多数最终用户来说，不具有单个根的 XML 被视为无效。 具体而言，单个根是必需的如果`x:XData`用作 XML 数据源适用于 WPF 或 XML 源用于数据绑定的许多其他技术。|  
|`[elementData]`|可选。 表示 XML 数据的 XML。 可以包含任意数量的元素作为元素数据和其他元素，则中可包含嵌套的元素但是，XML 的常规规则适用。|  
  
## <a name="remarks"></a>备注  
 中的 XML 元素`x:XData`所有可能的命名空间和前缀的数据中包含的 XMLDOM 对象可以重新声明。  
  
 以编程方式访问 XML 数据并`x:XData`是通过.NET Framework XAML 服务中可能存在内部 XAML 类型<xref:System.Windows.Markup.XData>类。  
  
## <a name="wpf-usage-notes"></a>WPF 用法说明  
 `x:XData`主要的子对象的形式使用对象<xref:System.Windows.Data.XmlDataProvider>，或子对象的形式或者<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>属性 （在 XAML，这通常都表示在属性元素语法中）。  
  
 数据通常应重定义为新的默认 XML 命名空间 （设置为空字符串） 的数据岛中的基本 XML 命名空间。 这是最简单的简单数据岛因为<xref:System.Windows.Data.Binding.XPath%2A>用于引用和绑定到数据的表达式可以避免包含前缀。 更复杂的数据岛可能会使用特定前缀的根处的 XML 命名空间和定义的数据的多个前缀。 在这种情况下，所有<xref:System.Windows.Data.Binding.XPath%2A>表达式引用应包括相应的命名空间映射前缀。 有关详细信息，请参阅[数据绑定概述](../wpf/data/data-binding-overview.md)。  
  
 从技术上讲，`x:XData`可以用作类型的任何属性的内容<xref:System.Xml.Serialization.IXmlSerializable>。 但是，<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>是唯一突出的实现。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Data.XmlDataProvider>
- [数据绑定概述](../wpf/data/data-binding-overview.md)
- [绑定标记扩展](../wpf/advanced/binding-markup-extension.md)
