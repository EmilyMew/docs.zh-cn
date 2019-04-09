---
title: x:Shared 特性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: da35f209b632bdf9e4ab2298239a505df69d6048
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125731"
---
# <a name="xshared-attribute"></a>x:Shared 特性
如果设置为`false`，修改 WPF 资源检索行为，以便特性化的资源的请求创建每个请求而不是共享同一个实例的所有请求的新实例。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性用法  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>备注  
 `x:Shared` 映射到 XAML 语言 XAML 命名空间并被识别为有效的 XAML 语言元素的.NET Framework XAML 服务和其 XAML 读取器。 但是，所述的功能`x:Shared`时才有意义的 WPF 应用程序和 WPF XAML 分析器。 在 WPF 中，`x:Shared`应用于在 WPF 中存在的对象时才有用作为特性<xref:System.Windows.ResourceDictionary>。 分析异常或其他错误，不会引发其他用法，但它们不起任何作用。  
  
 含义`x:Shared`XAML 语言规范中未指定。 其他 XAML 实现中的，如那些构建在.NET Framework XAML 服务，不一定提供资源共享支持。 此类的 XAML 实现可以提供类似的行为也使用的支持框架中`x:Shared`值。  
  
 在 WPF 中，默认值`x:Shared`资源的条件是`true`。 这种情况意味着，任何给定的资源请求将始终返回同一个实例。  
  
 修改一个对象，返回通过资源 API，如<xref:System.Windows.FrameworkElement.FindResource%2A>，或修改对象直接内的<xref:System.Windows.ResourceDictionary>，更改原始资源。 如果对该资源的引用是动态资源引用，该资源的使用者将获取已更改的资源。  
  
 如果对资源的引用是静态资源引用，将更改后的资源为[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]处理时间是不相关。 有关静态与动态资源引用的详细信息，请参阅[XAML 资源](../wpf/advanced/xaml-resources.md)。  
  
 显式指定`x:Shared="true"`很少这么做，因为这已是默认值。 没有直接代码等效于`x:Shared`WPF 中对象模型; 它仅可以指定在 XAML 用法中，必须处理由默认 WPF 行为或在加载路径上的中间 XAML 节点流中使用.NET Framework XAML Se 处理服务和其 XAML 读取器。  
  
 方案`x:Shared="false"`是如果您定义<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>派生的类作为资源，然后将元素资源到内容模型。 `x:Shared="false"` 启用元素资源，将会推出在同一集合中的多个时间 (如<xref:System.Windows.Controls.UIElementCollection>)。 无需`x:Shared="false"`这是无效的因为集合强制其内容的唯一性。 但是，`x:Shared="false"`行为创建的资源而不是返回同一实例的另一个相同实例。  
  
 另一方案`x:Shared="false"`是如果您使用<xref:System.Windows.Freezable>动画值，但想要修改的每个动画基础上的资源的资源。  
  
 字符串处理`false`不区分大小写。  
  
 在 WPF 中，`x:Shared`是仅在以下情况下有效：  
  
-   <xref:System.Windows.ResourceDictionary> ，其中包含与项`x:Shared`必须进行编译。 <xref:System.Windows.ResourceDictionary>不能为松散 XAML 中或用于主题。  
  
-   <xref:System.Windows.ResourceDictionary>包含的项不能嵌套在另一个<xref:System.Windows.ResourceDictionary>。 例如，不能使用`x:Shared`中的项<xref:System.Windows.ResourceDictionary>，位于<xref:System.Windows.Style>已<xref:System.Windows.ResourceDictionary>项。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.ResourceDictionary>
- [XAML 资源](../wpf/advanced/xaml-resources.md)
- [基元素](../wpf/advanced/base-elements.md)
