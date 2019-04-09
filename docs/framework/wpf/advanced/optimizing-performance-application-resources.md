---
title: 优化性能：应用程序资源
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
ms.openlocfilehash: 362d0f0fd3282365e5e05dcd43c49a9fd2ddc9a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139420"
---
# <a name="optimizing-performance-application-resources"></a>优化性能：应用程序资源
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以共享应用程序资源，以便可以跨类似类型的元素支持一致的外观或行为。 本主题提供了一些建议在此区域中可帮助你改进应用程序的性能。  
  
 有关资源的详细信息，请参阅 [XAML 资源](xaml-resources.md)。  
  
## <a name="sharing-resources"></a>共享资源  
 如果你的应用程序使用自定义控件和定义中的资源<xref:System.Windows.ResourceDictionary>（或 XAML 资源节点），建议，您可以定义在资源<xref:System.Windows.Application>或<xref:System.Windows.Window>对象级别，或定义中的默认主题自定义控件。 定义一个自定义控件中的资源<xref:System.Windows.ResourceDictionary>施加了该控件的每个实例的性能造成影响。 例如，如果有需要进行大量性能的画笔操作定义为资源定义的自定义控件的部件和自定义控件的多个实例，则应用程序的工作集将显著增加。  
  
 若要演示这一点，请考虑以下。 假设你正在开发卡游戏 using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 对于大多数纸牌游戏，需要 52 张牌，52 不同的人脸。 还可以实施一种卡片自定义控件和卡自定义控件的资源中定义 52 画笔 （每个元素表示一种纸牌外观）。 在主应用程序，最初创建此卡自定义控件 52 个的实例。 卡自定义控件的每个实例生成的 52 个实例<xref:System.Windows.Media.Brush>对象，这将使您总共 52 * 52<xref:System.Windows.Media.Brush>你的应用程序中的对象。 通过将移动到的卡自定义控件资源超出画笔<xref:System.Windows.Application>或<xref:System.Windows.Window>对象级别，或在自定义控件的默认主题中定义它们你降低该应用程序的工作集，因为现在正在共享 52 画笔52 个实例的卡片控件。  
  
## <a name="sharing-a-brush-without-copying"></a>不进行复制而共享画笔  
 如果您有多个元素使用的相同<xref:System.Windows.Media.Brush>对象，定义为资源的画笔并引用它，而不是定义中的画笔内联[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]。 此方法将创建一个实例，并重复使用它，而定义画笔中的以内联方式[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]创建的每个元素的新实例。  
  
 以下标记示例阐释了这一点：  
  
 [!code-xaml[Performance#PerformanceSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>使用静态资源在可能的情况  
 静态资源通过查找对已定义资源的引用，为任何 XAML 属性提供值。 类似于编译时查找该资源的查找行为。  
  
 动态资源，但是，将创建初始编译期间的临时表达式，并因此延迟的资源查找，直到实际需要来构造对象请求的资源值为止。 该资源的查找行为是类似于运行时查找，它会影响性能。 使用静态资源应尽可能使用动态资源仅在必要时你应用程序中。  
  
 以下标记示例演示如何使用这两种类型的资源：  
  
 [!code-xaml[Performance#PerformanceSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>请参阅

- [优化 WPF 应用程序性能](optimizing-wpf-application-performance.md)
- [规划应用程序性能](planning-for-application-performance.md)
- [利用硬件](optimizing-performance-taking-advantage-of-hardware.md)
- [布局和示例](optimizing-performance-layout-and-design.md)
- [二维图形和图像处理](optimizing-performance-2d-graphics-and-imaging.md)
- [对象行为](optimizing-performance-object-behavior.md)
- [Text](optimizing-performance-text.md)
- [数据绑定](optimizing-performance-data-binding.md)
- [其他性能建议](optimizing-performance-other-recommendations.md)
