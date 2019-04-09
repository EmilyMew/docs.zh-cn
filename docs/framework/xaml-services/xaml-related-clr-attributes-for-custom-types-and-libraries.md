---
title: 自定义类型和库的 XAML 相关 CLR 特性
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: ace1b40b25bd12ff7092459e468a90f382434bf4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086203"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>自定义类型和库的 XAML 相关 CLR 特性
本主题介绍由.NET Framework XAML 服务定义的公共语言运行时 (CLR) 属性。 它还介绍了在.NET Framework 中定义具有对程序集或类型的应用程序的 XAML 相关方案的其他 CLR 属性。 使用这些 CLR 特性属性的程序集、 类型或成员提供了与您的类型相关的 XAML 类型系统信息。 到直接处理 XAML 节点流或专用的 XAML 读取器和 XAML 编写器通过使用.NET Framework XAML 服务的任何 XAML 使用者提供信息。  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>自定义类型和自定义成员的 XAML 相关 CLR 特性  
 使用 CLR 特性要求整体 CLR 您用来定义您的类型，否则此类属性不可用。 如果您使用 CLR 定义的类型支持，.NET Framework XAML 服务 XAML 编写器使用的默认 XAML 架构上下文可以读取通过反射对支持程序集的 CLR 特性。  
  
 以下部分介绍可应用于自定义类型或自定义成员的 XAML 相关的属性。 每个 CLR 特性通信相关的 XAML 类型系统的信息。 在加载路径中，特性化的信息可帮助形成有效的 XAML 节点流中，XAML 读取器或帮助生成有效的对象图形的 XAML 编写器。 在保存路径，或者可以帮助形成重构 XAML 类型系统信息; 有效的 XAML 节点流的 XAML 读取器的特性化的信息或它声明了序列化提示或 XAML 编写器或其他 XAML 使用者的要求。  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **参考文档：**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **适用于：** 类、 属性或`get`支持可附加属性的访问器成员。  
  
 **参数：** None  
  
 <xref:System.Windows.Markup.AmbientAttribute> 指示该属性或采用特性化的类型的所有属性应解释 XAML 中的环境属性概念。 环境概念涉及 XAML 处理器如何确定成员的类型所有者。 环境属性是属性的值应为分析器上下文中可用时创建对象图，但其典型类型成员查找挂起直接 XAML 节点集创建的。  
  
 环境概念可以应用于可附加成员，它们不表示为属性定义 CLR 特性的方式方面<xref:System.AttributeTargets>。 方法特性用法应仅在的情况下应用`get`XAML 支持可附加的使用情况的访问器。  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **参考文档：**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **适用于：** 类  
  
 **参数：** 一个字符串，指定与单个构造函数自变量匹配的属性的名称。  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute> 指定可以使用非默认构造函数语法来初始化的对象和指定名称的属性提供构造信息。 此信息主要用于 XAML 序列化。 有关详细信息，请参阅 <xref:System.Windows.Markup.ConstructorArgumentAttribute>。  
  
### <a name="contentpropertyattribute"></a>ContentPropertyAttribute  
 **参考文档：**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **适用于：** 类  
  
 **参数：** 一个字符串，指定的特性化类型的成员名称。  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute> 指示参数命名的属性应充当该类型的 XAML 内容属性。 XAML 内容属性定义继承到可分配给定义的类型的所有派生类型。 您可以通过应用覆盖特定派生类型上的定义<xref:System.Windows.Markup.ContentPropertyAttribute>特定派生类型。  
  
 可作为 XAML 内容属性的属性，可以在 XAML 用法中省略属性元素标记的属性。 通常情况下，您将指定将提升您的内容和包含模型简化了的 XAML 标记的 XAML 内容属性。 可以将只有一个成员指定为 XAML 内容属性，因为有时可以设计选择选项以使多个容器的哪些类型的属性应被指定为 XAML 内容属性。 必须使用显式属性元素使用的其他容器属性。  
  
 在 XAML 节点流中，XAML 内容属性仍然产生`StartMember`并`EndMember`使用的属性的名称的节点<xref:System.Xaml.XamlMember>。 若要确定成员是否为 XAML 内容属性，检查<xref:System.Xaml.XamlType>值从`StartObject`定位和获取的值<xref:System.Xaml.XamlType.ContentProperty%2A>。  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **参考文档：**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **适用于：** 类，特别是集合类型。  
  
 **参数：** 一个<xref:System.Type>，它指定要用作外部内容的内容包装类型的类型。  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute> 指定将用于包装外部内容的关联的集合类型的一个或多个类型。 外部内容是指其中的内容属性的类型的类型系统约束不捕获所有可能的内容事例所属类型的 XAML 用法将支持的情况下。 例如，XAML 支持特定类型的内容可能支持在强类型化的泛型字符串<xref:System.Collections.ObjectModel.Collection%601>。 内容包装可用于将预先存在的标记约定迁移到 XAML 的概念可分配的值的集合，如迁移与文本相关的内容模型。  
  
 若要指定多个内容包装类型，请多次应用该属性。  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **参考文档：**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **适用于：** 属性  
  
 **参数：** 一个字符串，指定的特性化类型的另一个成员的名称。  
  
 <xref:System.Windows.Markup.DependsOnAttribute> 指示特性化的属性依赖于另一个属性的值。 将此特性应用于属性定义可确保在 XAML 对象编写第一次处理依赖属性。 用法<xref:System.Windows.Markup.DependsOnAttribute>其中的分析特定的顺序必须遵循有效的对象创建的类型上指定属性的这种例外情况。  
  
 您可以应用多个<xref:System.Windows.Markup.DependsOnAttribute>到属性定义的情况。  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **参考文档：**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **适用于：** 类，它应为<xref:System.Windows.Markup.MarkupExtension>派生类型。  
  
 **参数：** 一个<xref:System.Type>，它指定要为预期的最精确类型`ProvideValue`结果的特性化<xref:System.Windows.Markup.MarkupExtension>。  
  
 有关详细信息，请参阅[Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md)。  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **参考文档：**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **适用于：** 类  
  
 **参数：** 支持两种形式的属性：  
  
-   一个字符串，在特性化类型上指定的属性名称。  
  
-   一个字符串，指定属性的名称和一个<xref:System.Type>定义命名的属性的类型。 此窗体是用于为 XAML 名称范围属性指定可附加成员。  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute> 指定为特性化类提供的 XAML 名称范围值的属性。 应引用实现的对象的 XAML 名称范围属性<xref:System.Windows.Markup.INameScope>并保存的实际的 XAML 名称范围，其存储区，其行为。  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **参考文档：**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **适用于：** 类  
  
 **参数：** 一个字符串，在特性化类型上指定的运行时名称属性的名称。  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 报告将映射到 XAML 特性化类型的属性[X:name 指令](x-name-directive.md)。 属性的类型必须为<xref:System.String>并且必须是读/写。  
  
 定义继承到可分配给定义的类型的所有派生类型。 您可以通过应用覆盖特定派生类型上的定义<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>特定派生类型。  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **参考文档：**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **适用于：** 类型  
  
 **参数：** 无。  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 应用于可能显示为空白有意义的内容内的子元素的特定类型 (内容由集合具有<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>)。 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 主要与保存路径，但现已推出的加载路径中的 XAML 类型系统通过检查<xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>。 有关详细信息，请参阅[空格处理在 XAML 中](whitespace-processing-in-xaml.md)。  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **参考文档：**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **适用于：** 类、 属性、 方法 (仅 XAML 有效的方法用例是`get`支持可附加成员的访问器)。  
  
 **参数：**<xref:System.Type> 的 <xref:System.ComponentModel.TypeConverter>。  
  
 <xref:System.ComponentModel.TypeConverterAttribute> 上下文在 XAML 中引用自定义<xref:System.ComponentModel.TypeConverter>。 这<xref:System.ComponentModel.TypeConverter>的自定义类型或该类型的成员提供类型转换行为。  
  
 您将应用<xref:System.ComponentModel.TypeConverterAttribute>属性为所引用您的类型转换器实现的类型。 在类、 结构或接口，可以为 XAML 定义的类型转换器。 不需要提供类型转换为枚举，以本机方式启用转换。  
  
 类型转换器应该能够从到预期的目标类型使用的属性或在标记中，初始化文本字符串转换。 有关详细信息，请参阅[TypeConverters 和 XAML](../wpf/advanced/typeconverters-and-xaml.md)。  
  
 而不是将应用于所有类型的值，也可建立 XAML 的类型转换器行为上的特定属性。 在这种情况下，应用<xref:System.ComponentModel.TypeConverterAttribute>到属性定义 (外部定义，而不是特定`get`和`set`定义)。  
  
 可以通过将应用分配的自定义的可附加成员的 XAML 用法的类型转换器行为<xref:System.ComponentModel.TypeConverterAttribute>到`get`支持 XAML 用法的方法访问器。  
  
 类似于<xref:System.ComponentModel.TypeConverter>，<xref:System.ComponentModel.TypeConverterAttribute>存在于 XAML，是否存在之前的.NET Framework 和类型转换器模型提供其他目的。 若要引用和使用<xref:System.ComponentModel.TypeConverterAttribute>，你必须完全限定它，或者提供`using`语句<xref:System.ComponentModel>。 此外必须在项目中包括系统程序集。  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **参考文档：**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **适用于：** 类  
  
 **参数：** 按名称引用的相关属性的字符串。  
  
 指示该别名的一个类的 CLR 属性[X:uid 指令](x-uid-directive.md)。  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **参考文档：**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **适用于：** 类  
  
 **参数：** 一个布尔值。 如果使用为该特性的预期用途，这应始终指定为`true`。  
  
 指示在 XAML 对象图创建期间是否自上而下生成此类型。 这是一种高级的概念，这与编程模型的定义可能密切相关。 有关详细信息，请参阅 <xref:System.Windows.Markup.UsableDuringInitializationAttribute>。  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **参考文档：**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **适用于：** 类、 属性、 方法 (仅 XAML 有效的方法用例是`get`支持可附加成员的访问器)。  
  
 **参数：** 一个<xref:System.Type>，它指定要使用序列化的特性化类型的所有属性时的值序列化程序支持类或特定于特性化属性。  
  
 <xref:System.Windows.Markup.ValueSerializer> 指定一个值序列化类，需要更多状态和上下文比<xref:System.ComponentModel.TypeConverter>does。 <xref:System.Windows.Markup.ValueSerializer> 可以通过将应用与可附加成员相关联<xref:System.Windows.Markup.ValueSerializerAttribute>静态属性`get`可附加成员的访问器方法。 值序列化也适用于枚举、 接口和结构，但不适用于委托。  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **参考文档：**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **适用于：** 类，特别是应承载混合的内容，其中对象元素周围的空白区域可能会很明显的用户界面表示形式的集合类型。  
  
 **参数：** 无。  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 指示集合类型应为重要的空白区域处理由 XAML 处理器，这会影响构造的 XAML 节点流的值在集合中的节点。 有关详细信息，请参阅[空格处理在 XAML 中](whitespace-processing-in-xaml.md)。  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **参考文档：**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **适用于：** 类，属性。  
  
 **参数：** 支持两个属性窗体以字符串形式的类型或类型定义为<xref:System.Type>。 请参阅 <xref:System.Windows.Markup.XamlDeferLoadAttribute>。  
  
 指示类或属性具有 XAML 的延迟的加载用途 （如模板行为），并报告启用延迟行为和其目标/内容类型的类。  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **参考文档：**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **适用于：** 类  
  
 **参数：** 命名该回调。  
  
 指示类可以使用标记扩展提供的值为一个或多个属性，并引用 XAML 编写器应在执行上类的任何属性标记扩展设置操作之前调用的处理程序。  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **参考文档：**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **适用于：** 类  
  
 **参数：** 命名该回调。  
  
 指示类可以使用类型转换器提供的值为一个或多个属性，并引用 XAML 编写器应在执行上类的任何属性类型转换器设置操作之前调用的处理程序。  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **参考文档：**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **适用于：** 类  
  
 **参数：** 一个字符串，指定别名的属性名称`xml:lang`特性化类型上。  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute> 报告的属性映射到 XML 的特性化类型`lang`指令。 该属性不一定类型的<xref:System.String>，但必须可从字符串 （这可以通过将关联的类型转换器与该属性的类型或特定属性来实现）。 属性必须为读/写。  
  
 为映射方案`xml:lang`，以便运行时对象模型而不会与 XMLDOM 专门处理有权访问 XML 指定语言信息。  
  
 定义继承到可分配给定义的类型的所有派生类型。 您可以通过应用覆盖特定派生类型上的定义<xref:System.Windows.Markup.XmlLangPropertyAttribute>特定派生类型，但这一情况不常见。  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>在程序集级别的 XAML 相关 CLR 特性  
 以下部分介绍与 XAML 相关的属性不应用于类型或成员定义，但而是应用于程序集。 这些属性是与定义包含要在 XAML 中使用的自定义类型的库的总体目标相关。 某些属性不一定影响 XAML 节点流直接，但在节点流中使用的其他使用者上传递。 使用者的信息包括设计环境或序列化过程的需要 XAML 命名空间信息和关联的前缀的信息。 XAML 架构上下文 （包括.NET Framework XAML 服务默认值） 也使用此信息。  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **参考文档：**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **参数：**  
  
-   一个字符串，指定要包含的 XAML 命名空间标识符。  
  
-   一个字符串，指定可以包含从上一个参数的 XAML 命名空间的 XAML 命名空间的标识符。  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> 指定可由另一个 XAML 命名空间被包含到 XAML 命名空间。 通常，先前定义的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 中指示了包含 XAML 命令空间。 此方法可用于版本控制库中，使其符合针对以前版本的词汇以前定义的标记的 XAML 词汇。  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **参考文档：**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **参数：**  
  
-   一个字符串，指定要定义的 XAML 命名空间标识符。  
  
-   命名的 CLR 命名空间的字符串。 CLR 命名空间应在您的程序集，定义公共类型和 CLR 命名空间类型至少应适用于 XAML 使用情况。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 指定每个程序集基于 XAML 命名空间和 CLR 命名空间，然后是用于进行类型解析的 XAML 对象编写器或 XAML 架构上下文之间的映射。  
  
 多个<xref:System.Windows.Markup.XmlnsDefinitionAttribute>可以应用于程序集。 这可能会出于以下原因的任意组合：  
  
-   库设计包含用于运行时 API 访问权限; 的逻辑组织的多个 CLR 命名空间但是，你希望这些命名空间中的所有类型才能通过引用相同的 XAML 命名空间使用 XAML。 在这种情况下，应用多个<xref:System.Windows.Markup.XmlnsDefinitionAttribute>属性使用的相同<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值但具有不同<xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A>值。 这是特别有用，如果你正在定义的框架或应用程序想要将默认 XAML 命名空间中常见的用法的 XAML 命名空间映射。  
  
-   库设计包含多个 CLR 命名空间，并且你希望之间的这些 CLR 命名空间中的类型使用实例的有意 XAML 命名空间分隔。  
  
-   在程序集中定义的 CLR 命名空间，并且希望它能够通过多个 XAML 命名空间。 要支持多个具有相同的基本代码的词汇表，将发生这种情况。  
  
-   在一个或多个 CLR 命名空间中定义 XAML 语言支持。 对于这些数据，<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值应为`http://schemas.microsoft.com/winfx/2006/xaml`。  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **参考文档：**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **参数：**  
  
-   一个字符串，指定的 XAML 命名空间标识符。  
  
-   一个字符串，指定建议的前缀。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 指定要用于 XAML 命名空间的推荐的前缀。 前缀时，可以在由.NET Framework XAML 服务序列化的 XAML 文件中编写元素和属性<xref:System.Xaml.XamlXmlWriter>，或 XAML 实现的库与具有 XAML 的设计环境进行的交互时编辑功能。  
  
 多个<xref:System.Windows.Markup.XmlnsPrefixAttribute>可以应用于程序集。 这可能会出于以下原因的任意组合：  
  
-   您的程序集定义多个 XAML 命名空间的类型。 在这种情况下您应定义每个 XAML 命名空间不同的前缀的值。  
  
-   支持多个词汇，并为每个词汇和 XAML 命名空间中使用不同的前缀。  
  
-   在程序集中定义 XAML 语言支持和具有<xref:System.Windows.Markup.XmlnsDefinitionAttribute>为`http://schemas.microsoft.com/winfx/2006/xaml`。 在这种情况下，通常应提升前缀`x`。  
  
> [!NOTE]
>  .NET framework XAML 服务还可定义与 XAML 相关的属性<xref:System.Windows.Markup.RootNamespaceAttribute>。 此属性是项目系统支持的程序集级别属性并不是适用于 XAML 的自定义类型。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Attribute>
- [定义与 .NET Framework XAML 服务一起使用的自定义类型](defining-custom-types-for-use-with-net-framework-xaml-services.md)
