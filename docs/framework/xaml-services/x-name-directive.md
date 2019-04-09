---
title: x:Name 指令
ms.date: 03/30/2017
f1_keywords:
- x:Name
- xName
- Name
helpviewer_keywords:
- x:Name attribute [XAML Services]
- XAML [XAML Services], x:Name attribute
- Name attribute in XAML [XAML Services]
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
ms.openlocfilehash: d25c8500250411083e9fb6b33b3f743e5cd103c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076740"
---
# <a name="xname-directive"></a>x:Name 指令
唯一地标识 XAML 定义 XAML 名称范围中的元素。 XAML 名称范围和其唯一性模型可以应用于实例化的对象，框架提供的 Api 或实现在运行时访问 XAML 创建对象图的行为时。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性用法  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`XAMLNameValue`|一个字符串，符合的限制[XamlName 语法](xamlname-grammar.md)。|  
  
## <a name="remarks"></a>备注  
 之后`x:Name`应用于一个框架的支持的编程模型，名称是等效于包含的对象引用或实例由一个构造函数返回的变量。  
  
 值`x:Name`必须是唯一在 XAML 名称范围内的指令的使用情况。 默认情况下时使用的.NET Framework XAML 服务 API，主 XAML 名称范围中定义在 XAML 根元素的单个 XAML 生产，并使包含在该 XAML 生产环境中包含的元素。 可通过以满足特定情况的框架定义其他离散 XAML 名称范围中单个 XAML 生产可能发生的。 例如，在 WPF 中，新的 XAML 名称范围定义并在该 XAML 生产也定义任何模板创建的。 有关 XAML 名称范围 （但适用于许多 XAML 名称范围概念编写为 WPF） 的详细信息，请参阅[WPF XAML 名称范围](../wpf/advanced/wpf-xaml-namescopes.md)。  
  
 一般情况下，`x:Name`不应在还使用的情况下应用`x:Key`。 由现有的特定框架的 XAML 实现引入了替换概念之间`x:Key`和`x:Name`，但并不是建议的做法。 .NET framework XAML 服务不支持此类替换概念，如处理名称/密钥信息时<xref:System.Windows.Markup.INameScope>或<xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>。  
  
 规则的许可`x:Name`由特定实现的框架可能定义以及名称强制唯一性。 但是，为了与.NET Framework XAML 服务可用，XAML 名称范围唯一性的框架定义应与一致的定义<xref:System.Windows.Markup.INameScope>本文档中的信息和有关位置应使用相同的规则应用的信息。 例如，[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]实现将各种标记元素划分为单独<xref:System.Windows.NameScope>范围逻辑树中创建的页级 XAML、 模板和其他延迟的内容，例如资源字典，以及然后强制执行 XAML在每个这些 XAML 名称范围名称的唯一性。  
  
 对于使用.NET Framework XAML 服务 XAML 对象编写器的自定义类型，一个属性，它映射到`x:Name`上可建立一种类型，或将其更改。 通过引用的属性要映射的名称定义此行为<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>类型定义代码中。  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 是类型级别属性。  
  
 可通过实现以非特定于框架的方式定义 Using.NET Framework XAML 服务 XAML 命名空间支持的后备逻辑<xref:System.Windows.Markup.INameScope>接口。  
  
## <a name="wpf-usage-notes"></a>WPF 用法说明  
 下的标准生成配置[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]使用 XAML、 分部类和代码隐藏中，指定应用程序`x:Name`将成为在基础中创建的字段名称的代码时[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]处理的标记编译生成任务，并且该字段保留对对象的引用。 默认情况下，为内部创建的字段。 可以通过指定更改字段访问[X:fieldmodifier 特性](x-fieldmodifier-directive.md)。 在 WPF 和 Silverlight 中，该序列是标记编译定义和名称在一个分部类，但值字段是最初为空。 然后，生成的方法名为`InitializeComponent`从类构造函数中调用。 `InitializeComponent` 组成`FindName`使用的每个调用`x:Name`作为分部类的 XAML 定义部分中存在的值输入字符串。 返回值然后分配给名称类似的字段引用以填充的字段值从 XAML 创建的对象与分析。 在执行`InitializeComponent`使其可引用运行的时对象关系图使用`x:Name`而不是无需调用的直接，字段名称 /`FindName`显式任何时间你需要向 XAML 定义的对象的引用。  
  
 Wpf 使用 Microsoft Visual Basic 应用程序的目标，并包括与 XAML 文件`Page`添加的编译期间创建生成操作，单独的引用属性`WithEvents`关键字的所有元素具有`x:Name`，以支持`Handles`事件处理程序委托的语法。 此属性始终为公共。 有关详细信息，请参阅 [Visual Basic 和 WPF 事件处理](../wpf/advanced/visual-basic-and-wpf-event-handling.md)。  
  
 `x:Name` 用于 WPF XAML 处理器在加载时，即使对于其中的页面不是由生成操作 (例如，资源字典的松散 XAML) 进行标记编译的情况下注册到 XAML 名称范围的名称。 此行为的一个原因是因为`x:Name`可能所需的<xref:System.Windows.Data.Binding.ElementName%2A>绑定。 有关详细信息，请参阅[数据绑定概述](../wpf/data/data-binding-overview.md)。  
  
 如前文所述， `x:Name` (或`Name`) 不应在还使用的情况下应用`x:Key`。 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary>具有特殊行为的定义本身为 XAML 名称范围，但未实现或包含空值，返回<xref:System.Windows.Markup.INameScope>Api 作为一种方式强制执行此行为。 如果 WPF XAML 分析器遇到`Name`或`x:Name`中的 XAML 定义<xref:System.Windows.ResourceDictionary>，名称不会添加到任何 XAML 名称范围。 尝试查找该名称从任何 XAML 名称范围和`FindName`方法不会返回有效结果。  
  
### <a name="xname-and-name"></a>x： 名称和名称  
 许多 WPF 应用程序方案可以完全避免使用`x:Name`属性，因为`Name`作为依赖项属性中指定默认 XAML 命名空间的几个重要的基本类如<xref:System.Windows.FrameworkElement>和<xref:System.Windows.FrameworkContentElement>满足此同一目的。 仍有一些常见的 XAML 和 WPF 方案的代码中直接访问的元素没有`Name`框架级别属性是非常重要。 例如，不支持某些动画和情节提要支持类`Name`属性，但它们通常需要在代码中引用以控制动画。 应指定`x:Name`为时间线和转换创建 XAML，如果你想要更高版本在代码中引用它们的属性。  
  
 如果<xref:System.Windows.FrameworkElement.Name%2A>可在类上的属性用作<xref:System.Windows.FrameworkElement.Name%2A>和`x:Name`可以互换使用作为属性，但如果同时指定了相同的元素上，将会导致分析异常。 如果 XAML 标记编译，该异常将可能出现在标记编译，否则会出现在负载。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> 可以使用 XAML 特性语法中，设置并在代码中使用<xref:System.Windows.DependencyObject.SetValue%2A>; 但是请注意该设置<xref:System.Windows.FrameworkElement.Name%2A>在代码中的属性不会在大多数情况下，XAML 已创建的 XAML 名称范围内的有代表性的字段引用加载。 而不是尝试设置<xref:System.Windows.FrameworkElement.Name%2A>在代码中，使用<xref:System.Windows.NameScope>方法从代码中根据相应的名称范围。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> 也可以通过内部文本中使用属性元素语法设置，但这不常见。 与此相反，`x:Name`不能在 XAML 属性元素语法中，或在代码中使用设置<xref:System.Windows.DependencyObject.SetValue%2A>; 它只能设置对象上使用特性语法，因为它是一个指令。  
  
## <a name="silverlight-usage-notes"></a>Silverlight Usage 备注。  
 `x:Name` 适用于 Silverlight 单独说明了。 有关详细信息，请参阅[XAML Namespace （x:）语言功能 (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [WPF 中的树](../wpf/advanced/trees-in-wpf.md)
