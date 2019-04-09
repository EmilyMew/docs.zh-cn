---
title: 默认 XAML 架构上下文和 WPF XAML 架构上下文
ms.date: 03/30/2017
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
ms.openlocfilehash: 1312541321e74668e6527c6c54e712342fbb3a17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124691"
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>默认 XAML 架构上下文和 WPF XAML 架构上下文
XAML 架构上下文是有资格使用特定的 XAML 词汇 XAML 生产与编写的行为，包括如何类型映射解析时，如何将加载程序集、 如何某些读取器和编写器的对象交互的方式的概念实体设置被解释。 本主题介绍.NET Framework XAML 服务和基于 CLR 类型系统的关联的默认 XAML 架构上下文的功能。 本主题还介绍用于 WPF 的 XAML 架构上下文。  
  
## <a name="default-xaml-schema-context"></a>默认 XAML 架构上下文  
 .NET framework XAML 服务同时实施，并使用默认 XAML 架构上下文。 默认 XAML 架构上下文行为并不总是完全可见的 API 中<xref:System.Xaml.XamlSchemaContext>类。 但是，在许多情况下会影响默认 XAML 架构上下文的行为是通过公共 API 的 XAML 类型系统，例如的成员的可观察量<xref:System.Xaml.XamlMember>或<xref:System.Xaml.XamlType>，或通过在 XAML 读取器和 XAML 编写器使用的公开的 Api默认 XAML 架构上下文。  
  
 您可以创建<xref:System.Xaml.XamlSchemaContext>通过调用封装的默认行为<xref:System.Xaml.XamlSchemaContext>构造函数。 这将显式创建的默认 XAML 架构上下文。 如果初始化 XAML 读取器或 XAML 编写器使用 Api 显式不采用隐式地创建相同的默认 XAML 架构上下文<xref:System.Xaml.XamlSchemaContext>输入的参数。  
  
 默认 XAML 架构上下文依赖于 CLR 反射对其类型的映射行为。 这包括检查定义 CLR <xref:System.Type>，及相关<xref:System.Reflection.PropertyInfo>或<xref:System.Reflection.MethodInfo>。 此外，CLR 特性的类型或成员将使用填写的 XAML 类型或使用 CLR 后备类型的 XAML 成员信息的具体信息。 默认 XAML 架构上下文不需要类型系统扩展技术，如`Invoker`模式，因为所需的信息是可从 CLR 类型系统。  
  
 加载逻辑的程序集，主要从事 XAML 命名空间映射中提供的任何程序集值依赖于默认 XAML 架构上下文。 此外，<xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>可以提示为方案，例如加载内部类型加载程序集。  
  
## <a name="wpf-xaml-schema-context"></a>WPF XAML 架构上下文  
 由于 WPF 实现提供有趣举例说明了各种可以通过实现的非默认 XAML 架构上下文中引入的功能，本主题中描述的 WPF XAML 架构上下文。 此外，XAML 架构上下文概念中未讨论很大程度的 WPF 文档，解决了 WPF XAML;启用 XAML 架构上下文的行为可能仅与默认 XAML 架构上下文的工作方式的讨论集成完全可以理解。 WPF XAML 架构上下文实现以下行为。  
  
 **查找重写：** WPF 的 XAML 具有几个内容模型有没有正在起作用的 XAML 内容属性<xref:System.Windows.Markup.ContentPropertyAttribute>特性化。 <xref:System.Xaml.XamlType.LookupContentProperty%2A> WPF 的替代实现此行为。  
  
 **对于 WPF 表达式的延迟：** WPF 功能的运行时上下文可用之前延迟值的多个表达式类。 此外，模板扩展是依赖于延迟技术的运行时行为。  
  
 **类型系统查找优化：** WPF 具有广泛 XAML 词汇和对象模型，包括继承的成百上千个 WPF 定义的类到基类成员定义。 此外，WPF 本身是分布在多个程序集。 WPF 可优化使用查找表和其他技术在其查找类型。 这通过默认 XAML 架构上下文和查找其基于 CLR 类型提供了性能改进。 在其中查找表中不存在类型的情况下，行为使用类似于默认 XAML 架构上下文的 XAML 架构上下文技术。  
  
 **XamlType 和 XamlMember 扩展：** 属性概念与依赖关系属性和事件与路由事件的概念，扩展了 WPF。 为了让用于 XAML 处理操作的这些概念更好的可视性，WPF 扩展<xref:System.Xaml.XamlType>和<xref:System.Xaml.XamlMember>，并将添加报告依赖关系属性和路由事件特征的内部属性。  
  
### <a name="accessing-the-wpf-xaml-schema-context"></a>访问 WPF XAML 架构上下文  
 如果使用基于 WPF 的 XAML 技术<xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType>或<xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>，WPF XAML 架构上下文已在使用这些 XAML 读取器和 XAML 编写器实现。  
  
 如果使用其他 XAML 读取器或未初始化的 XAML 编写器实现与 WPF XAML 架构上下文，您可能能够获得一个有效的 WPF XAML 架构上下文从<xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>。 然后可以使用此值作为使用其他 API 的初始化<xref:System.Xaml.XamlSchemaContext>。 例如，您可以调用<xref:System.Xaml.XamlXmlReader.%23ctor%2A>的初始化，然后传递 WPF XAML 架构上下文。 或者，可以使用 WPF XAML 架构上下文的 XAML 类型系统操作。 这可能包括构造初始化<xref:System.Xaml.XamlType>或<xref:System.Xaml.XamlMember>，或调用<xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>。  
  
 请注意，是否从纯 XAML 节点流角度访问 WPF XAML 的某些方面，一些 WPF 框架功能可能不具有处理尚未。 例如，将不应用 WPF 控件的模板。 因此如果访问一个属性，它在运行时可能会填充整个可视化树，您可能只能看到所引用的模板的属性值。 用于 WPF 的标记扩展提供的服务上下文可能不会准确如果从非运行时的情况下，提供和尝试写入对象图时可能会导致异常。  
  
## <a name="xaml-and-assembly-loading"></a>XAML 和程序集加载  
 程序集加载的 XAML 和.NET Framework XAML 服务集成的 CLR 定义概念<xref:System.AppDomain>。 XAML 架构上下文将解释如何加载程序集或查找类型在运行的时或设计时，基于使用的<xref:System.AppDomain>和其他因素。 逻辑略有不同，具体取决于 XAML 是松散 XAML 的 XAML 读取器，编译到 DLL 的 XAML `XamlBuildTask`，或由 WPF 的生成 BAML `PresentationBuildTask`。  
  
 WPF 的 XAML 架构上下文与 WPF 应用程序模型，后者又使用<xref:System.AppDomain>以及其他因素的 WPF 实现的详细信息。  
  
#### <a name="xaml-reader-input-loose-xaml"></a>XAML 读取器输入 (松散 XAML)  
  
1.  循环访问 XAML 架构上下文<xref:System.AppDomain>最近从最开始加载应用程序，查找匹配名称的所有方面的已加载的程序集。 如果找到匹配项，则该程序集用于解析。  
  
2.  否则，以下方法之一将基于 CLR <xref:System.Reflection.Assembly> API 用于加载程序集：  
  
    -   如果名称限定的映射中，调用<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>限定名称。  
  
    -   如果在上一步失败，请使用短名称 （和公钥标记如果存在） 来调用<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。  
  
    -   如果名称非限定的映射中，调用<xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>。  
  
#### <a name="xamlbuildtask"></a>XamlBuildTask  
 `XamlBuildTask` 用于 Windows Communication Foundation (WCF) 和 Windows Workflow Foundation。  
  
 请注意，程序集引用通过`XamlBuildTask`始终是完全限定。  
  
1.  调用<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>限定名称。  
  
2.  如果在上一步失败，请使用短名称 （和公钥标记如果存在） 来调用<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。  
  
#### <a name="baml-presentationbuildtask"></a>BAML （presentationbuildtask 生成）  
 有两个方面与程序集加载为 BAML： 加载包含作为组件，BAML 的初始程序集和加载引用 BAML 生产的任何类型的类型的后备程序集。  
  
##### <a name="assembly-load-for-initial-markup"></a>初始标记的程序集加载：  
 对要加载中的标记的程序集的引用始终是非限定。  
  
1.  WPF XAML 架构上下文循环<xref:System.AppDomain>WPF 应用程序，查找匹配名称的所有方面的已加载的最近从最开始加载程序集。 如果找到匹配项，则该程序集用于解析。  
  
2.  如果在上一步失败，请使用短名称 （和公钥标记如果存在） 来调用<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。  
  
##### <a name="assembly-references-by-baml-types"></a>BAML 类型的程序集引用：  
 程序集引用在 BAML 生产环境中使用的类型始终是完全限定，作为生成任务的输出。  
  
1.  WPF XAML 架构上下文循环<xref:System.AppDomain>WPF 应用程序，查找匹配名称的所有方面的已加载的最近从最开始加载程序集。 如果找到匹配项，则该程序集用于解析。  
  
2.  否则，以下方法之一用于加载程序集：  
  
    -   调用<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>限定名称。  
  
    -   如果短名称和公钥标记的组合匹配 BAML 从中加载的程序集，使用该程序集。  
  
    -   使用短名称和公钥标记调用<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。  
  
## <a name="see-also"></a>请参阅

- [了解 XAML 节点流结构和概念](understanding-xaml-node-stream-structures-and-concepts.md)
