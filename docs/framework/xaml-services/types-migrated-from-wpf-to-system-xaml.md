---
title: 从 WPF 迁移到 System.Xaml 的类型
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: dcfad1c2b2f95783e2b348a3a1111501f958143f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116475"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>从 WPF 迁移到 System.Xaml 的类型
在中[!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]并[!INCLUDE[net_v30_long](../../../includes/net-v30-long-md.md)]，这两个[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]和 Windows Workflow Foundation 包含一个 XAML 语言实现。 为 WPF XAML 实现提供扩展性的很多公共类型都存在于 WindowsBase、PresentationCore 和 PresentationFramework 程序集中。 同样，为 Windows Workflow Foundation XAML 提供扩展性的公共类型存在于 System.Workflow.ComponentModel 程序集中。 在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]中，一些与 XAML 相关的类型已迁移到 System.Xaml 程序集。 XAML 语言服务的一个常见 .NET Framework 实现支持最初由特定框架的 XAML 实现定义的很多 XAML 扩展性方案，但是现在这些方案都属于整体 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] XAML 语言支持的一部分。 本主题列出了迁移的类型并讨论了与迁移有关的问题。  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>程序集和命名空间  
 在 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]中，WPF 为支持 XAML 而实现的类型通常位于 <xref:System.Windows.Markup> 命名空间中。 大多数这些类型都位于 WindowsBase 程序集中。  
  
 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中，新增了一个 <xref:System.Xaml> 命名空间和 System.Xaml 程序集。 最初为 WPF XAML 实现的很多类型现在作为任何 XAML 实现的扩展性点或服务提供。 为了使其可用于更普通的方案，将类型从其最初所在的 WPF 程序集类型转发到 System.Xaml 程序集。 这可启用 XAML 扩展性方案而无需包含其他框架 （如 WPF 和 Windows Workflow Foundation） 的程序集。  
  
 对于已迁移的类型，大多数类型仍位于 <xref:System.Windows.Markup> 命名空间中。 这是做部分是为了避免中断每个文件上现有实现中的 CLR 命名空间映射。 因此， <xref:System.Windows.Markup> 中的 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 命名空间包含混合的常规 XAML 语言支持类型（来自 System.Xaml 程序集）和特定于 WPF XAML 实现的类型（来自 WindowsBase 和其他 WPF 程序集）。 在版本 4 的 WPF 程序集中，已迁移到 System.Xaml，但以前存在于 WPF 程序集中的任何类型都具有类型转发支持。  
  
### <a name="workflow-xaml-support-types"></a>工作流 XAML 支持类型  
 Windows Workflow Foundation 还提供 XAML 支持类型，并在许多情况下它们具有相同 wpf 等效的短名称。 下面是 Windows Workflow Foundation XAML 支持类型的列表：  
  
-   <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
-   <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
-   <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 这些支持类型仍存在于的 Windows Workflow Foundation 程序集[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]并仍可用于特定的 Windows Workflow Foundation 应用程序; 但是，它们不应引用的应用程序或不使用的框架Windows Workflow Foundation。  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 在 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]中，WPF 的 <xref:System.Windows.Markup.MarkupExtension> 类位于 WindowsBase 程序集中。 Windows Workflow Foundation 的 parallel 类<xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>、 现有 System.Workflow.ComponentModel 程序集中。 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中， <xref:System.Windows.Markup.MarkupExtension> 类被迁移到 System.Xaml 程序集中。 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中， <xref:System.Windows.Markup.MarkupExtension> 适用于使用 .NET Framework XAML 服务的任何 XAML 扩展性方案，而不仅仅用于在特定框架上生成的方案。 在可能的情况下，特定的框架或架构中的用户代码也应在 XAML 扩展的 <xref:System.Windows.Markup.MarkupExtension> 类上生成。  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>MarkupExtension 支持服务类  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 并[!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]WPF 提供了可以使用的多个服务对<xref:System.Windows.Markup.MarkupExtension>实施者和<xref:System.ComponentModel.TypeConverter>实现以支持 XAML 中的类型/属性用法。 这些服务如下所示：  
  
-   <xref:System.Windows.Markup.IProvideValueTarget>  
  
-   <xref:System.Windows.Markup.IUriContext>  
  
-   <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  来自 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 且与标记扩展有关的另一个服务是 <xref:System.Windows.Markup.IReceiveMarkupExtension> 接口。 <xref:System.Windows.Markup.IReceiveMarkupExtension> 未迁移并且被标记为`[Obsolete]`为[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]。 以前使用 <xref:System.Windows.Markup.IReceiveMarkupExtension> 的方案应改用 <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> 特性化回调。 <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> 也标记为`[Obsolete]`。  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>XAML 语言功能  
 WPF 的多个 XAML 语言功能和组件以前存在于 PresentationFramework 程序集中。 这些功能和组件作为 <xref:System.Windows.Markup.MarkupExtension> 子类实现以在 XAML 标记中公开标记扩展用法。 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中，它们存在于 System.Xaml 程序集中，以便不包含 WPF 程序集的项目可以使用这些 XAML 语言级别的功能。 WPF 对 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 应用程序使用这些相同的实现。 与本主题中列出的其他情况一样，这些支持类型继续存在于 <xref:System.Windows.Markup> 命名空间中，以避免中断以前的引用。  
  
 下表包含在 System.Xaml 中定义的 XAML 功能支持类的列表。  
  
|XAML 语言功能|用法|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 虽然 System.Xaml 可能没有特定支持类，但用于处理 XAML 语言的语言功能的常规逻辑现在位于 System.Xaml 及其实现的 XAML 读取器和 XAML 编写器中。 例如， `x:TypeArguments` 是一个由 System.Xaml 实现中的 XAML 读取器和 XAML 编写器处理的特性；该特性可在 XAML 节点流中说明，可在默认的（基于 CLR 的）XAML 架构上下文中进行处理，具有 XAML 类型系统表示形式，等等。 因此，所有 XAML 语言级别功能的参考文档都是 [XAML Services](index.md) 的子主题和 .NET Framework 文档集的常规区域，而不属于 WPF 文档集以 [高级 (Windows Presentation Foundation)](../wpf/advanced/index.md) 的子主题的形式存在（在 3.5 文档集中仍是如此）。  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer 和支持类  
 <xref:System.Windows.Markup.ValueSerializer> 类支持到字符串的类型转换，尤其对于序列化可能需要输出中有多个模式或节点的 XAML 序列化情况。 在 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]中，WPF 的 <xref:System.Windows.Markup.ValueSerializer> 位于 WindowsBase 程序集中。 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中， <xref:System.Windows.Markup.ValueSerializer> 类位于 System.Xaml 中，并且适用于任何 XAML 扩展性方案，而不仅仅用于在 WPF 上生成的方案。 <xref:System.Windows.Markup.IValueSerializerContext> （支持服务） 和<xref:System.Windows.Markup.DateTimeValueSerializer>（特定子类） 也会迁移到 System.Xaml。  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>与 XAML 相关的属性  
 WPF XAML 包含多个特性，这些特性可应用于 CLR 类型以指示有关它们的 XAML 行为的某些内容。 下面是在 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]的 WPF 程序集中存在的特性列表。 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中，这些特性迁移到 System.Xaml 中。  
  
-   <xref:System.Windows.Markup.AmbientAttribute>  
  
-   <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
-   <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
-   <xref:System.Windows.Markup.DependsOnAttribute>  
  
-   <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
-   <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
-   <xref:System.Windows.Markup.RootNamespaceAttribute>  
  
-   <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
-   <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
-   <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
-   <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
-   <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>其他类  
 在 <xref:System.Windows.Markup.IComponentConnector> 和 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 中， [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]接口存在于 WindowsBase 中，但在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中，该接口存在于 System.Xaml 中。 <xref:System.Windows.Markup.IComponentConnector> 主要适用于工具支持和 XAML 标记编译器。  
  
 在 <xref:System.Windows.Markup.INameScope> 和 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 中， [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]接口存在于 WindowsBase 中，但在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中，该接口存在于 System.Xaml 中。 <xref:System.Windows.Markup.INameScope> 定义 XAML 名称范围的基本的操作。  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>存在于 WPF 和 System.Xaml 中具有共享名称的与 XAML 相关的类  
 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中，以下类既存在于 WPF 程序集中，也存在于 System.Xaml 程序集中：  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 WPF 实现位于 <xref:System.Windows.Markup> 命名空间和 PresentationFramework 程序集中。 System.Xaml 实现位于 <xref:System.Xaml> 命名空间中。 如果你使用的是 WPF 类型或是从 WPF 类型派生的，则通常应使用 <xref:System.Windows.Markup.XamlReader> 和 <xref:System.Windows.Markup.XamlWriter> 的 WPF 实现，而不是 System.Xaml 实现。 有关详细信息，请参阅 <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> 和 <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>中的“备注”。  
  
 如果要包括对 WPF 程序集和 System.Xaml 的应用，并且还要对 `include` 和 <xref:System.Windows.Markup> 命名空间使用 <xref:System.Xaml> 语句，则可能需要完全限定对这些 API 的调用，以便清楚无误地解析类型。  
  
## <a name="see-also"></a>请参阅

- [XAML 服务](index.md)
