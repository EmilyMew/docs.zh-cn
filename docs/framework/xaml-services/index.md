---
title: XAML 服务
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: 37fdd96c0666bc6ecda0f46daa5ca6271a8666ab
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2019
ms.locfileid: "58048153"
---
# <a name="xaml-services"></a>XAML 服务
本主题介绍的技术一名为.NET Framework XAML 服务的功能。 服务和 Api 所述的大多数都位于 System.Xaml，它是一个程序集随程序集[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]的.NET 核心程序集。 服务包括阅读器和编写器，架构类和架构支持，工厂类、 XAML 语言内部函数支持和其他 XAML 语言功能的特性化。  
  
## <a name="about-this-documentation"></a>有关此文档  
 .NET Framework XAML 服务的概念文档假定你具有上述体验 XAML 语言以及如何它可能会应用到特定的框架，例如[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]或 Windows Workflow Foundation 或特定技术功能区域中，例如生成自定义项中的功能<xref:Microsoft.Build.Framework.XamlTypes>。 本文档不会尝试解释为标记语言，XAML 语法术语或其他介绍性材料的 XAML 基础知识。 相反，本文档重点介绍专门在 System.Xaml 程序集库中使用启用.NET Framework XAML 服务。 这些 Api 的大部分都是为 XAML 语言集成和扩展性方案。 这可能包括以下任一项：  
  
-   扩展基本 XAML 读取器或 XAML 编写器 （直接处理 XAML 节点流; 派生您自己的 XAML 读取器或 XAML 编写器） 的功能。  
  
-   定义不存在特定的框架依赖关系，XAML 可使用自定义类型和特性化的类型来传达其 XAML 类型到.NET Framework XAML 服务的系统特征。  
  
-   应用程序，例如可视化设计器或 XAML 标记源的交互式编辑器的一个组件的形式承载 XAML 读取器或 XAML 编写器。  
  
-   编写 XAML 值转换器 （标记扩展; 自定义类型的类型转换器）。  
  
-   定义自定义的 XAML 架构上下文 (用于后备类型源使用备用的程序集加载方法; 而不始终使用已知类型查找技术专用于反映将程序集; 使用加载的程序集不使用 CLR 的概念`AppDomain`和其关联的安全模型）。  
  
-   基本的 XAML 类型系统的扩展。  
  
-   使用`Lookup`或`Invoker`技术来影响 XAML 类型系统和如何评估类型后备。  
  
 如果您正在寻找有关 XAML 用作语言的介绍性材料，则可以尝试[XAML 概述 (WPF)](../wpf/advanced/xaml-overview-wpf.md)。 该主题将讨论 XAML 的新的读者到[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]并指向通过使用 XAML 标记和 XAML 语言功能。 另一个有用的文档是中的介绍性材料[XAML 语言规范](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>.NET framework XAML 服务和 System.Xaml 中.NET 体系结构  
 在以前版本的 Microsoft.NET Framework，支持有关 XAML 语言功能所实现的 Microsoft.NET Framework 构建的框架 ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]，Windows Workflow Foundation 和 Windows Communication Foundation (WCF))，并因此不同的行为和使用 API，具体取决于哪个特定的框架已使用。 这包括 XAML 分析器及其对象图创建机制、 XAML 语言内部函数、 序列化支持等。  
  
 在[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，.NET Framework XAML 服务和 System.Xaml 程序集中定义了大部分所需的支持 XAML 语言功能。 这包括基类，这些类的 XAML 读取器和 XAML 编写器。 添加到未出现在任何特定于框架的 XAML 实现的.NET Framework XAML 服务的最重要功能是 XAML 类型系统表示形式。 类型系统表示形式提供一种面向对象的方法，而不依赖于框架的特定功能为中心的 XAML 功能显示 XAML。  
  
 XAML 类型系统不受限制的标记窗体或运行时细节的 XAML 的原点;也不受任何特定后备类型的系统限制。 XAML 类型系统包括类型、 成员、 XAML 架构上下文、 XML 级别概念和其他 XAML 语言概念或 XAML 内部函数的对象表示形式。 使用或扩展的 XAML 类型系统使用可以派生自的类，如 XAML 读取器和 XAML 编写器，并扩展到启用的一种框架、 一种技术或使用的应用程序的特定功能的 XAML 表示形式中的功能或发出 XAML。 XAML 架构上下文概念使从 XAML 对象编写器实现，一种技术的后备类型系统的通信通过上下文和 XAML 节点中的程序集信息的组合的实际对象关系图写入操作源。 有关 XAML 架构概念的详细信息。 请参阅[默认 XAML 架构上下文和 WPF XAML 架构上下文](default-xaml-schema-context-and-wpf-xaml-schema-context.md)。  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>XAML 节点流中，XAML 读取器和 XAML 编写器  
 若要了解.NET Framework XAML 服务 XAML 语言和特定的技术，使用 XAML 作为一种语言之间的关系中所扮演的角色，将有助于您了解 XAML 节点流和这一概念如何形状 API 的概念和术语。 XAML 节点流是 XAML 语言表示形式与 XAML 表示或定义的对象图之间概念中间。  
  
-   XAML 读取器是以某种格式，处理 XAML 并生成 XAML 节点流的实体。 在 API 中，XAML 读取器表示由基类<xref:System.Xaml.XamlReader>。  
  
-   XAML 编写器是处理 XAML 节点流并生成其他内容的实体。 在 API 中，XAML 编写器表示由基类<xref:System.Xaml.XamlWriter>。  
  
 两个最常见的方案涉及 XAML 是加载 XAML 来实例化对象关系图，并从应用程序或工具保存对象关系图和生成的 XAML 表示形式 （通常在另存为文本文件的标记窗体）。 加载 XAML 和创建对象图通常称为加载路径作为此文档中。 正在保存或序列化到 XAML 的现有对象图通常称为在本文档中作为保存路径。  
  
 加载路径的最常见类型如下所述：  
  
-   启动与 XAML 表示形式，采用 UTF 编码的 XML 格式并另存为文本文件。  
  
-   加载到该 XAML <xref:System.Xaml.XamlXmlReader>。 <xref:System.Xaml.XamlXmlReader> 是<xref:System.Xaml.XamlReader>子类。  
  
-   结果是一个 XAML 节点流。 您可以访问 XAML 节点流使用的各个节点<xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader> API。 最典型的操作是无法进一步处理 XAML 节点流中，处理每个节点使用"当前记录"隐喻。  
  
-   将生成的节点传递到 XAML 节点流从<xref:System.Xaml.XamlObjectWriter>API。 <xref:System.Xaml.XamlObjectWriter> 是<xref:System.Xaml.XamlWriter>子类。  
  
-   <xref:System.Xaml.XamlObjectWriter>写入对象图，一个对象时，根据通过源 XAML 节点流的进度。 这是通过 XAML 架构上下文和可以访问程序集和类型的后备类型系统和框架实现的帮助。  
  
-   调用<xref:System.Xaml.XamlObjectWriter.Result%2A>获取对象图的根对象的 XAML 节点流的末尾。  
  
 保存路径最常见的类型可以描述如下：  
  
-   开始的整个应用程序运行时间时，UI 内容和状态的运行时间或在运行时的整体应用程序的对象表示形式的较小段的对象图。  
  
-   从逻辑开始对象，如应用程序根目录或文档根元素，将对象加载到<xref:System.Xaml.XamlObjectReader>。 <xref:System.Xaml.XamlObjectReader> 是<xref:System.Xaml.XamlReader>子类。  
  
-   结果是一个 XAML 节点流。 您可以访问 XAML 节点流使用的各个节点<xref:System.Xaml.XamlObjectReader>和<xref:System.Xaml.XamlReader>API。 最典型的操作是无法进一步处理 XAML 节点流中，处理每个节点使用"当前记录"隐喻。  
  
-   将生成的节点传递到 XAML 节点流从<xref:System.Xaml.XamlXmlWriter>API。 <xref:System.Xaml.XamlXmlWriter> 是<xref:System.Xaml.XamlWriter>子类。  
  
-   <xref:System.Xaml.XamlXmlWriter>写入 XAML 中 XML UTF 编码。 您可以将它保存为文本文件，为流，或在其他窗体中。  
  
-   调用<xref:System.Xaml.XamlXmlWriter.Flush%2A>获取最终的输出。  
  
 有关 XAML 节点流概念的详细信息，请参阅[理解 XAML 节点 Stream 结构和概念](understanding-xaml-node-stream-structures-and-concepts.md)。  
  
### <a name="the-xamlservices-class"></a>XamlServices 类  
 它并不总是需要处理 XAML 节点流。 如果所需的基本加载路径或保存路径 basic，则可以使用中的 Api<xref:System.Xaml.XamlServices>类。  
  
-   各种签名<xref:System.Xaml.XamlServices.Load%2A>实现加载路径。 您可以加载文件或流，或可以加载<xref:System.Xml.XmlReader>，<xref:System.IO.TextReader>或<xref:System.Xaml.XamlReader>通过使用该读取器的 Api 加载包装您的 XAML 输入。  
  
-   各种签名<xref:System.Xaml.XamlServices.Save%2A>保存对象图并生成流、 输出文件，或<xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter>实例。  
  
-   <xref:System.Xaml.XamlServices.Transform%2A> 将 XAML 转换通过链接一个加载路径或保存路径作为单个操作。 可以为使用不同的架构上下文或不同的后备类型系统<xref:System.Xaml.XamlReader>和<xref:System.Xaml.XamlWriter>，这会影响如何转换生成的 XAML。  
  
 有关如何使用详细信息<xref:System.Xaml.XamlServices>，请参阅[XAMLServices 类和基本的 XAML 读取或写入](xamlservices-class-and-basic-xaml-reading-or-writing.md)。  
  
## <a name="xaml-type-system"></a>XAML 类型系统  
 XAML 类型系统提供了使用 XAML 节点流的给定的单个节点所需的 Api。  
  
 <xref:System.Xaml.XamlType> 是你要处理的起始对象节点和结束对象节点之间的对象的表示形式。  
  
 <xref:System.Xaml.XamlMember> 是你要处理的起始成员节点和结束成员节点之间的成员的表示形式。  
  
 等 Api 就<xref:System.Xaml.XamlType.GetAllMembers%2A>并<xref:System.Xaml.XamlType.GetMember%2A>并<xref:System.Xaml.XamlMember.DeclaringType%2A>报表之间的关系<xref:System.Xaml.XamlType>和<xref:System.Xaml.XamlMember>。  
  
 由.NET Framework XAML 服务实现的 XAML 类型系统的默认行为基于公共语言运行时 (CLR) 和静态分析的程序集中的 CLR 类型使用反射。 因此，对于特定的 CLR 类型，XAML 类型系统的默认实现可以公开该类型及其成员的 XAML 架构并将其报告的 XAML 类型系统方面。 在默认 XAML 类型系统中，类型可分配性的概念映射到 CLR 继承和实例、 值类型和等等的概念也将映射到支持的行为和 CLR 的功能。  
  
## <a name="reference-for-xaml-language-features"></a>XAML 语言功能的参考  
 若要支持 XAML，.NET Framework XAML 服务提供特定实现 XAML 语言概念为 XAML 语言 XAML 命名空间定义的一样。 这些被记录为特定的参考页。 从这些语言功能时，会由 XAML 读取器或 XAML 编写器，它由.NET Framework XAML 服务定义的行为的角度来看记录语言功能。 有关详细信息，请参阅[XAML Namespace （x:）语言功能](xaml-namespace-x-language-features.md)。
