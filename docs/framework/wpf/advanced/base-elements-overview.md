---
title: 基元素概述
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: 0cd69a4d2d6087c1ebf93bb5931511f32a4c9c5f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110053"
---
# <a name="base-elements-overview"></a>基元素概述
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中较高比重的类都派生自四类，它们通常在 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 文档中称为基元素。 这些类是<xref:System.Windows.UIElement>， <xref:System.Windows.FrameworkElement>， <xref:System.Windows.ContentElement>，和<xref:System.Windows.FrameworkContentElement>。 <xref:System.Windows.DependencyObject>类也相关，因为它是这两者的一个公共基类<xref:System.Windows.UIElement>和 <xref:System.Windows.ContentElement>  

<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>WPF 类中的基元素 API  
 这两<xref:System.Windows.UIElement>并<xref:System.Windows.ContentElement>派生自<xref:System.Windows.DependencyObject>，通过某种程度上不同的途径。 如何处理此级别拆分<xref:System.Windows.UIElement>或<xref:System.Windows.ContentElement>中的用户界面和什么作用其处理的应用程序中使用。 <xref:System.Windows.UIElement> 还有<xref:System.Windows.Media.Visual>在其类层次结构，它是一个类公开低级别图形支持基础[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。 <xref:System.Windows.Media.Visual> 通过定义独立矩形屏幕区域提供呈现框架。 在实践中，<xref:System.Windows.UIElement>是将支持较大的对象模型的元素为目标来呈现和分成若干个区域，可以描述为矩形屏幕区域和内容模型是有意更加开放，以允许不同的布局元素的组合。 <xref:System.Windows.ContentElement> 不是派生自<xref:System.Windows.Media.Visual>; 其模型是<xref:System.Windows.ContentElement>将由其他用途，如读取器或查看器，然后解释元素，并生成完整<xref:System.Windows.Media.Visual>为[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]来使用。 某些<xref:System.Windows.UIElement>类旨在成为内容宿主： 它们提供了一个或多个承载和呈现<xref:System.Windows.ContentElement>类 (<xref:System.Windows.Controls.DocumentViewer>举例说明这样的类)。 <xref:System.Windows.ContentElement> 用于内承载带有某种程度上较小的对象模型的元素的基类和文档内容的或更多地址的文本的信息，如<xref:System.Windows.UIElement>。  
  
### <a name="framework-level-and-core-level"></a>框架级别和核心级别  
 <xref:System.Windows.UIElement> 用作类的基类<xref:System.Windows.FrameworkElement>，并<xref:System.Windows.ContentElement>用作类的基类<xref:System.Windows.FrameworkContentElement>。 此下一级别类的目的是支持独立于 WPF 框架级别的 WPF 核心级别，同时这种划分也存在于 PresentationCore 和 PresentationFramework 程序集间如何划分 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。 WPF 框架级别表示一种更完整的解决方案，以满足基本应用程序需求，其中包括实现演示文稿的布局管理器。 WPF 核心级别可提供一种方法，使你能够充分利用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，而无需使用其他程序集的开销。 这些级别间的区别对大多数典型的应用程序开发方案几乎没影响，但一般情况下，你应整体考虑 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，而不是关注 WPF 框架级别和 WPF 核心级别间的差异。 如果应用程序设计选择替换大量 WPF 框架级别功能，建议了解级别差异，例如，整体解决方案是否已有其自己的 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 组合和布局的实现。  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>选择要从其中派生的元素  
 若要创建扩展 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的自定义类，最实用的方法是派生自 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 类之一，你可在其中通过现有类层次结构获得尽可能多的所需功能。 本节列出了以下三个最重要的元素类附带的功能，以帮助决定要从其中继承的类。  
  
 如果要实现一个控件，这的确是从派生更常见的原因之一[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]类中，你可能想要派生自的类的实际控件、 控件系列基类，也在至少从<xref:System.Windows.Controls.Control>基类。 有关指导和实际示例，请参阅[控件创作概述](../controls/control-authoring-overview.md)。  
  
 如果没有创建控件且需要派生自位于层次结构中较高层次的类，以下各节可用于指导在每个基元素类中定义哪些特征。  
  
 如果创建派生的类<xref:System.Windows.DependencyObject>，还将继承以下功能：  
  
-   <xref:System.Windows.DependencyObject.GetValue%2A> 和<xref:System.Windows.DependencyObject.SetValue%2A>支持以及常规属性系统支持。  
  
-   能够使用依赖属性和实现为依赖属性的附加属性。  
  
 如果创建派生自类<xref:System.Windows.UIElement>，还将继承以下功能之外，提供的<xref:System.Windows.DependencyObject>:  
  
-   对已动画处理的属性值的基本支持。 有关详细信息，请参阅 [动画概述](../graphics-multimedia/animation-overview.md)。  
  
-   基本输入事件支持以及命令支持。 有关详细信息，请参阅[输入概述](input-overview.md)和[命令概述](commanding-overview.md)。  
  
-   可进行替代以便介绍布局系统的虚拟方法。  
  
 如果创建派生自类<xref:System.Windows.FrameworkElement>，还将继承以下功能之外，提供的<xref:System.Windows.UIElement>:  
  
-   样式和情节提要支持。 有关详细信息，请参阅<xref:System.Windows.Style>并[演示图板概述](../graphics-multimedia/storyboards-overview.md)。  
  
-   数据绑定支持。 有关详细信息，请参阅 [数据绑定概述](../data/data-binding-overview.md)。  
  
-   动态资源引用支持。 有关详细信息，请参阅 [XAML 资源](xaml-resources.md)。  
  
-   属性值继承支持，以及元数据中的其他标记，这些标记有助于报告关于框架服务属性的情况，例如数据绑定、样式或布局的框架实现。 有关详细信息，请参阅[框架属性元数据](framework-property-metadata.md)。  
  
-   逻辑树概念。 有关详细信息，请参见 [WPF 中的树](trees-in-wpf.md)。  
  
-   布局系统的实用 WPF 框架级别实现的支持包括<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>可以检测到的重写更改为属性影响布局。  
  
 如果创建派生自类<xref:System.Windows.ContentElement>，还将继承以下功能之外，提供的<xref:System.Windows.DependencyObject>:  
  
-   支持动画。 有关详细信息，请参阅 [动画概述](../graphics-multimedia/animation-overview.md)。  
  
-   基本输入事件支持以及命令支持。 有关详细信息，请参阅[输入概述](input-overview.md)和[命令概述](commanding-overview.md)。  
  
 如果创建派生自类<xref:System.Windows.FrameworkContentElement>，你将获得以下功能之外，提供的<xref:System.Windows.ContentElement>:  
  
-   样式和情节提要支持。 有关详细信息，请参阅<xref:System.Windows.Style>并[动画概述](../graphics-multimedia/animation-overview.md)。  
  
-   数据绑定支持。 有关详细信息，请参阅 [数据绑定概述](../data/data-binding-overview.md)。  
  
-   动态资源引用支持。 有关详细信息，请参阅 [XAML 资源](xaml-resources.md)。  
  
-   属性值继承支持，以及元数据中的其他标记，这些标记有助于报告关于框架服务属性的情况，例如数据绑定、样式或布局的框架实现。 有关详细信息，请参阅[框架属性元数据](framework-property-metadata.md)。  
  
-   你不会继承布局系统修改访问 (如<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>)。 布局系统实现才可在上找到<xref:System.Windows.FrameworkElement>。 但是，继承<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>可以检测对影响布局，并报告给任何内容宿主的属性的更改的替代。  
  
 针对各种类记录内容模型。 如果想要查找相应的类进行派生，类的内容模型是应该考虑的一个可能因素。 有关详细信息，请参阅 [WPF 内容模型](../controls/wpf-content-model.md)。  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>其他基类  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject> 提供对支持[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]线程处理模型还可为创建的所有对象[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]与关联的应用程序<xref:System.Windows.Threading.Dispatcher>。 即使您并非派生<xref:System.Windows.UIElement>， <xref:System.Windows.DependencyObject>，或<xref:System.Windows.Media.Visual>，则应考虑派生自<xref:System.Windows.Threading.DispatcherObject>以便获得此线程模型支持。 有关详细信息，请参阅[线程模型](threading-model.md)。  
  
### <a name="visual"></a>视觉对象  
 <xref:System.Windows.Media.Visual> 实现通常要求在大致矩形的区域中的可视化展示了 2D 对象的概念。 实际呈现<xref:System.Windows.Media.Visual>发生在其他类 （它不是自包含），但<xref:System.Windows.Media.Visual>类提供了呈现进程在不同级别使用的已知的类型。 <xref:System.Windows.Media.Visual> 实现命中测试，但它不公开报告点击测试阳性的事件 (这些对象位于<xref:System.Windows.UIElement>)。 有关详细信息，请参阅[可视化层编程](../graphics-multimedia/visual-layer-programming.md)。  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable> 通过提供所需或出于性能原因不可变对象时生成的对象的副本的方法来模拟可变对象的不可变性。 <xref:System.Windows.Freezable>类型提供了公共基础对于某些图形元素，如几何和画笔以及动画。 值得注意的是，<xref:System.Windows.Freezable>不是<xref:System.Windows.Media.Visual>; 它可保留成为子属性的属性时<xref:System.Windows.Freezable>应用以填充属性值的另一个对象，并且这些子属性可能会影响呈现。 有关详细信息，请参阅 [Freezable 对象概述](freezable-objects-overview.md)。  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> 是<xref:System.Windows.Freezable>派生的类，它特别添加了动画控件层和一些实用程序成员，以便可以区分当前动画的属性的属性区分开。  
  
### <a name="control"></a>控件  
 <xref:System.Windows.Controls.Control> 是所需的基类的类型的对象，该控件或组件，具体取决于该技术称为对象。 一般情况下，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控件类可直接表示 UI 控件或积极参与控件组合。 主要功能的<xref:System.Windows.Controls.Control>启用是控制模板化。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.Control>
- [依赖项属性概述](dependency-properties-overview.md)
- [控件创作概述](../controls/control-authoring-overview.md)
- [WPF 体系结构](wpf-architecture.md)
