---
title: XamlWriter.Save 的序列化限制
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 89cb36dba63dccdf7e52b7fcafbe3d9fc2fea1e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113277"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>XamlWriter.Save 的序列化限制
[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] <xref:System.Windows.Markup.XamlWriter.Save%2A>可用于序列化的内容[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]应用程序作为[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]文件。 但是，对于所序列化的内容有一些显著限制。 本主题对这些限制和某些一般注意事项进行了介绍。  

<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>运行时、非设计时表示形式  
 什么通过调用序列化的基本原理<xref:System.Windows.Markup.XamlWriter.Save%2A>是结果将是正在序列化，在运行时对象的表示形式。 许多设计时属性的原始[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文件可能已进行了优化或丢失时，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]加载为内存中对象，并在调用时不会保留<xref:System.Windows.Markup.XamlWriter.Save%2A>要序列化。 序列化的结果是应用程序的结构化逻辑树的有效表示形式，但并不一定是生成该树的原始 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的有效表示形式。 这些问题变得极为困难，若要使用<xref:System.Windows.Markup.XamlWriter.Save%2A>一部分的一个全面的序列化[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]设计图面。  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>序列化是自包含的  
 序列化的输出<xref:System.Windows.Markup.XamlWriter.Save%2A>是自包含; 进行序列化的所有内容，包含在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]单个页上，使用一个根元素，并且不包含外部引用以外的其他[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]。 例如，如果页面从应用程序资源引用了资源，则这些资源看上去如同正在进行序列化的页面的一个组件。  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>取消引用扩展引用  
 由各种标记扩展格式（如 `StaticResource` 或 `Binding`）对对象进行的公共引用将会由序列化进程取消引用。 已时内存中对象所创建的应用程序运行时，将这些取消引用和<xref:System.Windows.Markup.XamlWriter.Save%2A>逻辑不会重新访问原始[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]还原序列化输出到此类引用。 这样可能会将任何数据绑定的或资源获得的值冻结为运行时表示形式最后使用的值，并且只能有限地或间接地区别这样的值与任何其他在本地设置的值。 由于图像存在于项目中，因此图像也会序列化为图像的对象引用（而不是原始的源引用），从而会丢失最初引用的文件名或 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。 即使是在同一页面内声明的资源，也会序列化到引用点内，而不是保留为资源集合的键。  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>不保留事件处理  
 当对通过 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 添加的事件处理程序进行序列化后，不会保留这些事件处理程序。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 无需代码隐藏 （且还不相关的 X:code 机制） 无法序列化运行时过程逻辑。 因为序列化是自包含的且限于逻辑树，所以不存在用于存储事件处理程序的设施。 因此，会从输出 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中删除事件处理程序特性（特性本身和用于命名处理程序的字符串值）。  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>XAMLWriter.Save 实用方案  
 虽然限制列出以下是非常重大，仍有几个相应的使用方案<xref:System.Windows.Markup.XamlWriter.Save%2A>进行序列化。  
  
-   向量或图形输出：呈现区域的输出可用于重现相同的向量或图形时重新加载。  
  
-   丰富的文本和流文档：文本和在其中的所有元素格式和元素包含保留在输出中。 这对类似于剪贴板功能的机制可能非常有用。  
  
-   保留业务对象数据：如果数据中存储自定义元素，如[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]数据，因此只要您的业务对象遵循基本[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]规则，如提供自定义构造函数和转换，则为按引用属性值，这些业务对象可以是通过序列化永久保留。
