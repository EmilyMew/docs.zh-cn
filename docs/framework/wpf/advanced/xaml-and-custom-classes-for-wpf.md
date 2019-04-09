---
title: XAML 及 WPF 的自定义类
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: e71946ec06eb1b4c75f30084dfdb863d8e3b093e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122351"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>XAML 及 WPF 的自定义类
[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 框架中实现的 XAML 支持定义任何 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 语言的自定义类或结构，然后使用 XAML 标记访问类。 通常通过将自定义类型映射到 XAML 命名空间前缀，可在同一标记文件中混合使用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 定义类型和自定义类型。 本主题讨论将自定义类用作 XAML 元素必须满足的要求。  

<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>应用程序或程序集中的自定义类  
 XAML 中使用的自定义类可通过两种不同的方式进行定义：在代码隐藏或其他生成主 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 应用程序的代码内，或者在单独程序集中作为类（例如用作类库的可执行文件或 DLL）。 这些方法各有特定的优点和缺点。  
  
-   创建类库的优点在于可在多个不同的应用程序间共享任意此类自定义类。 通过使用单独的库，更易于控制应用程序的版本控制问题，并可简化类创建过程，在此过程中，所需的类用法是作为 XAML 页面上的根元素。  
  
-   在应用程序中定义自定义类的优点在于此方法相对轻量，可减少在主应用程序可执行文件外引入单独程序集时遇到的部署和测试问题。  
  
-   无论定义在相同还是不同的程序集中，自定义类若要在 XAML 中用作元素，都需要在 CLR 命名空间和 XML 命名空间之间进行映射。 请参阅 [WPF XAML 的 XAML 命名空间和命名空间映射](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>将自定义类用作 XAML 元素的要求  
 为能够实例化为对象元素，类必须满足以下要求：  
  
-   自定义类必须是公共的且支持默认（无参数）公共构造函数。 （有关结构注释，请参阅下节内容。）  
  
-   自定义类不得为嵌套类。 嵌套类及其常规 CLR 使用语法中的“点”会干扰其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和/或 XAML 功能（例如附加属性）。  
  
 除启用对象元素语法外，对象定义还会对任何其他将该对象作为值类型的公共属性启用属性元素语法。 这是因为对象现在可被实例化为对象元素，且可填充此类属性的属性元素值。  
  
### <a name="structures"></a>结构  
 可始终在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的 XAML 中构造定义为自定义类型的结构。这是因为 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 编译器会对将所有属性值初始化为默认值的结构隐式创建默认构造函数。 某些情况下，结构并不需要默认构造行为和/或对象元素用法。 这可能是因为结构需要通过概念方式将值和函数作为联合来填充，其中包含的值可能具有互斥的解释，因而其不存在任何可设置属性。 一个[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]这种结构的示例是<xref:System.Windows.GridLength>。 通常情况下，此类结构应实现类型转换器，以便可通过属性形式表达值，方法是使用创建结构值的不同解释或模式的字符串约定。 结构还应通过非默认构造函数对代码构造公开类似的行为。  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>将自定义类属性用作 XAML 特性的要求  
 属性必须引用按值类型（例如基元），或者使用特定类型的一个类（此特定类型需具有默认构造函数或 XAML 处理器可访问的专用类型转换器）。 在 CLR XAML 实现中，XAML 处理器，查找通过语言基元的本机支持或应用程序的此类转换器<xref:System.ComponentModel.TypeConverterAttribute>类型或后备类型定义中的成员  
  
 或者，属性可引用抽象类类型或接口。 对于抽象类或接口，XAML 分析的所需条件是必须用实现接口的实际类实例或派生自抽象类的类型实例填充属性值。  
  
 属性可在抽象类上声明，但仅可在派生自抽象类的实际类上设置。 这是因为创建类的对象元素需要类上的公共默认构造函数。  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>启用 TypeConverter 的特性语法  
 如果提供类级别的专用特性化类型转换器，则应用的类型转换会对需实例化该类型的任何属性启用特性语法。 类型转换器不会启用类型的对象元素用法；仅在该类型存在默认构造函数时启用对象元素用法。 因此，启用类型转换器的属性通常不适用于属性语法，除非类型本身也支持对象元素语法。 此规则存在一个例外，即可指定属性元素语法，但使属性元素包含一个字符串。 实质上相当于特性语法用法，该使用情况，这类使用情况不常见，除非需要进行更可靠的空白处理的属性值。 例如，以下是一个采用字符串的属性元素用法以及一个特性用法等效项：  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 属性允许特性语法，但包含的对象元素的属性元素语法不允许使用通过 XAML 的示例包括的各种属性<xref:System.Windows.Input.Cursor>类型。 <xref:System.Windows.Input.Cursor>类具有专用的类型转换器<xref:System.Windows.Input.CursorConverter>，但不公开默认构造函数，因此<xref:System.Windows.FrameworkElement.Cursor%2A>属性只能设置通过特性语法即使实际<xref:System.Windows.Input.Cursor>类型是引用类型。  
  
### <a name="per-property-type-converters"></a>按属性类型转换器  
 或者，属性本身可能声明属性级别的类型转换器。 这样，"最小语言"作为输入处理传入的字符串值的属性通过实例化内联属性类型的对象<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>操作根据适当的类型。 此操作的目的通常是提供方便的访问器，且这不是在 XAML 中启用属性设置的唯一方式。 但是，如果要使用不提供默认构造函数或特性化类型转换器的现有 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 类型，也可使用特性的类型转换器。 从示例[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]API 将某些属性<xref:System.Globalization.CultureInfo>类型。 在这种情况下，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用现有的 Microsoft.NET Framework<xref:System.Globalization.CultureInfo>类型，以更好地解决兼容性和迁移方案使用在早期版本的框架，但<xref:System.Globalization.CultureInfo>类型不支持所需的构造函数或类型级别的类型转换为直接用作 XAML 属性值。  
  
 每当公开具有 XAML 用法的属性时，特别是对于控件作者，应特别考虑使用依赖属性支持此属性。 这是如果您使用现有[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]实现的 XAML 处理器，因为可以通过使用提高性能<xref:System.Windows.DependencyProperty>备份。 依赖属性将对用户针对 XAML 可访问属性所需的属性公开属性系统功能。 这包括动画、数据绑定和样式支持等功能。 有关详细信息，请参阅[自定义依赖属性](custom-dependency-properties.md)和 [XAML 加载和依赖属性](xaml-loading-and-dependency-properties.md)。  
  
### <a name="writing-and-attributing-a-type-converter"></a>编写和特性化类型转换器  
 您偶尔需要编写自定义<xref:System.ComponentModel.TypeConverter>派生的类提供对属性类型的类型转换。 有关如何派生和创建可以支持 XAML 用法的类型转换器以及如何将应用的说明<xref:System.ComponentModel.TypeConverterAttribute>，请参阅[TypeConverters 和 XAML](typeconverters-and-xaml.md)。  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>自定义类事件上 XAML 事件处理程序特性语法的要求  
 若要用作 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件，事件必须在支持默认构造函数的类上或在派生类可访问事件的抽象类上公开为公共事件。 以可方便地用作路由事件，你[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]事件应实现显式`add`并`remove`方法，这些添加和删除处理程序方法[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]事件签名并转发到这些处理程序<xref:System.Windows.UIElement.AddHandler%2A>和<xref:System.Windows.UIElement.RemoveHandler%2A>方法。 这些方法添加或删除事件所附加到的实例上的路由事件处理程序存储的处理程序。  
  
> [!NOTE]
>  可以直接为使用的路由事件注册处理程序<xref:System.Windows.UIElement.AddHandler%2A>，并在特意不定义[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]公开路由的事件的事件。 通常不建议采用此操作，因为事件不会启用 XAML 特性语法用于附加处理程序，并且生成类提供的类型功能的 XAML 视图透明度较低。  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>编写集合属性  
 采用集合类型的属性所具有的 XAML 语法使你可指定添加到集合的对象。 此语法具有两个重要功能。  
  
-   无需在对象元素语法中指定作为集合对象的对象。 无论何时在采用集合类型的 XAML 中指定属性，该集合类型的状态总是隐式。  
  
-   标记中集合属性的子元素经处理后变成集合的成员。 对集合成员的代码访问通常通过列表/字典方法（例如 `Add`）或通过索引器执行。 但 XAML 语法不支持方法和索引器 (异常：XAML 2009 可以支持这些方法，但使用 XAML 2009 会限制可能的 WPF 用法;请参阅[XAML 2009 语言功能](../../xaml-services/xaml-2009-language-features.md))。 对生成元素树而言，集合显然是非常常见的要求，并且你需要某种方法来填充声明 XAML 中的这些集合。 因此，通过将集合属性的子元素添加到作为集合属性类型值的集合中来对其进行处理。  
  
 .NET Framework XAML 服务实现和 WPF XAML 处理器将以下定义用于组成集合属性的项。 属性的属性类型必须实现以下项之一：  
  
-   实现<xref:System.Collections.IList>。  
  
-   实现<xref:System.Collections.IDictionary>或泛型等效项 (<xref:System.Collections.Generic.IDictionary%602>)。  
  
-   派生自<xref:System.Array>(有关在 XAML 中数组的详细信息，请参阅[X:array 标记扩展](../../xaml-services/x-array-markup-extension.md)。)  
  
-   实现<xref:System.Windows.Markup.IAddChild>(通过定义的接口[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)])。  
  
 CLR 中这些类型每个都具有 `Add` 方法，创建对象图时，XAML 处理器使用该方法将项添加到基础集合。  
  
> [!NOTE]
>  泛型`List`并`Dictionary`接口 (<xref:System.Collections.Generic.IList%601>并<xref:System.Collections.Generic.IDictionary%602>) 不支持对于集合检测通过[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 处理器。 但是，可以使用<xref:System.Collections.Generic.List%601>类作为基类，因为它实现<xref:System.Collections.IList>直接，或<xref:System.Collections.Generic.Dictionary%602>作为基类，因为它实现了<xref:System.Collections.IDictionary>直接。  
  
 声明采用集合的属性时，请注意类型的新实例中如何实例化此属性值。 如果不将此属性实现为依赖属性，则使属性使用调用此集合类型构造函数的支持字段已可满足使用需求。 如果属性为依赖属性，则可能需要将集合属性初始化为默认类型构造函数的一部分。 这是因为依赖属性从元数据获取其默认值，而通常不希望集合属性的初始值为静态共享集合。 每个包含类型实例应具有一个集合实例。 有关详细信息，请参阅[自定义依赖属性](custom-dependency-properties.md)。  
  
 可为集合属性实现自定义集合类型。 由于隐式集合属性处理的原因，自定义集合类型无需提供默认构造函数即可隐式用于 XAML 中。 但是，可选择为集合类型提供默认构造函数。 此做法是有用的。 除非提供默认构造函数，否则无法显式将集合声明为对象元素。 一些标记作者可能希望看到作为标记样式的显式集合。 此外，创建将集合类型用作属性值的新对象时，默认构造函数可简化初始化要求。  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>声明 XAML 内容属性  
 XAML 语言定义 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 内容属性的概念。 对象语法中可用的每个类仅可具有一个 XAML 内容属性。 若要将属性声明为 XAML 内容属性为您的类，应用<xref:System.Windows.Markup.ContentPropertyAttribute>为类定义的一部分。 指定作为目标的 XAML 内容属性的名称<xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A>属性中。 指定的属性是作为字符串名称，不与反射构造如<xref:System.Reflection.PropertyInfo>。  
  
 可将集合属性指定为 XAML 内容属性。 这产生一种属性的用法，通过此用法，对象元素可具有一个或多个子元素，不干扰集合对象元素或属性元素标记。 这些元素被视为 XAML 内容属性的值，并添加到支持集合实例中。  
  
 一些现有 XAML 内容属性使用 `Object` 的属性类型。 这使 XAML 内容属性可接受基元值如<xref:System.String>和单一引用对象值。 如果按照此模型，类型负责类型确定以及处理可能的类型。 典型的原因<xref:System.Object>内容类型是为了支持这两个简单的方法，将对象内容添加为字符串 （接收默认演示文稿处理），或添加的高级的方法对象指定非默认演示文稿的内容或其他数据。  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>序列化 XAML  
 某些情况下（例如对于控件作者），可能还需要确保任何可在 XAML 中实例化的对象演示文稿也可被序列化到等效的 XAML 标记。 本主题中未介绍序列化要求。 请参阅[控件创作概述](../controls/control-authoring-overview.md)和[元素树和序列化](element-tree-and-serialization.md)。  
  
## <a name="see-also"></a>请参阅

- [XAML 概述 (WPF)](xaml-overview-wpf.md)
- [自定义依赖项属性](custom-dependency-properties.md)
- [控件创作概述](../controls/control-authoring-overview.md)
- [基元素概述](base-elements-overview.md)
- [XAML 加载和依赖项属性](xaml-loading-and-dependency-properties.md)
