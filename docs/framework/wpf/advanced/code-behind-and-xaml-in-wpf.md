---
title: WPF 中的代码隐藏和 XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 4a77060661cb0d71b0209cbcdeba23ffc2c6e5c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088555"
---
# <a name="code-behind-and-xaml-in-wpf"></a>WPF 中的代码隐藏和 XAML
<a name="introduction"></a> 代码隐藏是一个术语，用于描述标记定义的对象，与联接的代码时[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]页进行标记编译。 本主题介绍了代码隐藏的要求以及代码中的可选内联代码机制[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 本主题包含以下各节：  
  
-   [系统必备](#Prerequisites)  
  
-   [代码隐藏和 XAML 语言](#codebehind_and_the_xaml_language)  
  
-   [代码隐藏、 事件处理程序和 WPF 中的分部类要求](#Code_behind__Event_Handler__and_Partial_Class)  
  
-   [x:Code](#x_Code)  
  
-   [内联代码的限制](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>系统必备  
 本主题假定你已阅读[XAML 概述 (WPF)](xaml-overview-wpf.md)具备的一些基础知识和[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]和面向对象的编程。  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>代码隐藏和 XAML 语言  
 XAML 语言包含语言级别功能，使得可以将代码文件与标记文件，然后在标记文件端相关联。 具体而言，XAML 语言定义的语言功能[X:class 指令](../../xaml-services/x-class-directive.md)， [X:subclass 指令](../../xaml-services/x-subclass-directive.md)，并[X:classmodifier 指令](../../xaml-services/x-classmodifier-directive.md)。 完全应该如何生成代码，以及如何将集成标记和代码，不是 XAML 语言指定的一部分。 它应由 WPF 来确定如何将代码集成之类的框架、 如何为使用 XAML 在应用程序和编程模型和生成操作或其他支持的所有这些要求。  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>代码隐藏、 事件处理程序和 WPF 中的分部类要求  
  
-   分部类必须派生自支持的根元素的类型。  
  
-   请注意，标记编译生成操作的默认行为下, 您可以将派生留空的分部类定义中的代码隐藏侧。 即使未指定，编译的结果将假定页面根后备类型的分部类的基础。 但是，依赖于此行为不是一种最佳做法。  
  
-   在代码隐藏中编写的事件处理程序的实例方法，并且不能为静态方法。 这些方法必须由标识的 CLR 命名空间中的分部类定义`x:Class`。 您不能有资格的一个事件处理程序，以指示名称[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]处理器，查找事件布线，另一个类作用域中的事件处理程序。  
  
-   该处理程序必须在后备类型系统中匹配相应的事件的委托。  
  
-   对于 Microsoft Visual Basic 语言具体而言，您使用的是特定于语言的`Handles`关键字将处理程序相关联的实例和事件处理程序声明，而不是附加处理程序中的属性中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 但是，此方法也存在一些限制，因为`Handles`关键字不能支持所有的特定功能[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]事件系统，如某些路由事件方案或附加事件。 有关详细信息，请参阅[Visual Basic 和 WPF 事件处理](visual-basic-and-wpf-event-handling.md)。  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x:Code  
 [X:code](../../xaml-services/x-code-intrinsic-xaml-type.md)中定义的指令元素[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 `x:Code`指令元素可以包含嵌入式编程代码。 是以内联方式定义的代码可以与交互[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]同一页面上。 下面的示例说明了内联 C# 代码。 请注意，该代码位于`x:Code`元素和代码必须用引起`<CDATA[`...`]]>`用于对内容进行转义[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]，以便[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]处理器 (解释任一[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]架构或[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]架构) 不会尝试解释内容按字面意思为[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]。  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>内联代码的限制  
 应考虑避免或限制的内联代码使用。 根据体系结构和编码基本原理，维护分离标记和代码隐藏保留设计器和开发人员角色得更为明显。 在更多技术级别中，为内联代码编写的代码可能难以编写，因为始终写入[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]生成的分部类，并且只能使用默认 XML 命名空间映射。 因为不能添加`using`语句，您必须完全限定的许多[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]所做的调用。 默认值[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]映射包括最而不是全部[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]命名空间中存在的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程序集; 必须完全限定的类型和成员中的其他 CLR 命名空间包含对的调用。 您还不能定义分部类以外的项目中的内联代码，并且您引用的所有用户代码实体必须都存在作为成员或生成的分部类中的变量。 其他语言特定编程功能，例如宏或`#ifdef`对全局变量或生成变量，也不是可用。 有关详细信息，请参阅[X:code 内部 XAML 类型](../../xaml-services/x-code-intrinsic-xaml-type.md)。  
  
## <a name="see-also"></a>请参阅

- [XAML 概述 (WPF)](xaml-overview-wpf.md)
- [x:Code 内部 XAML 类型](../../xaml-services/x-code-intrinsic-xaml-type.md)
- [生成 WPF 应用程序](../app-development/building-a-wpf-application-wpf.md)
- [XAML 语法详述](xaml-syntax-in-detail.md)
