---
title: 不在对象树中的对象元素的初始化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- logical tree [WPF]
- visual tree [WPF]
- elements [WPF], initializing
- initializing elements [WPF]
ms.assetid: 7b8dfc9b-46ac-4ce8-b7bb-035734d688b7
ms.openlocfilehash: 6f3c8611b83977431038573eb1c5c880acbefdc4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108961"
---
# <a name="initialization-for-object-elements-not-in-an-object-tree"></a>不在对象树中的对象元素的初始化
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 初始化时某些方面会被推迟，在通常依赖连接到逻辑树或可视化树的元素的进程中执行。 本主题介绍了针对未连接到两种树之一的元素，将其初始化可能需要的步骤。  

## <a name="elements-and-the-logical-tree"></a>元素和逻辑树  
 在代码中创建 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 类的实例时，应该注意在调用类构造函数时所执行的代码中，需要有意地不包含 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 类的对象初始化的几个方面。 特别是对于控件类，该控件的大部分可视化表示形式都不是由构造函数定义的。 而是由控件的模板定义。 模板可能来自各种源，但最常见的情况是来自于主题样式。 模板实际上是晚期绑定的；在控件已准备好布局之后，才会将所需模板附加到相关控件。 并且控件只有在已附加到连接到根级别的呈现图面的逻辑树时，才能准备好应用布局。 正是该根级别元素启动逻辑树中定义的所有子元素的呈现。  
  
 可视化树也参与此过程。 通过模板成为可视化树一部分的元素也是在连接后才完全实例化的。  
  
 此行为的结果是依赖某个元素已完成的可视化特征的某些操作需要额外的步骤。 例如，如果你试图获取一个已构造但尚未附加到树中的类的可视化特征，就需要额外的步骤。 例如，如果你想要调用<xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A>上<xref:System.Windows.Media.Imaging.RenderTargetBitmap>均通过视觉对象是未连接到树中，元素和额外的初始化步骤在完成之前，该元素不是直观地完成。  
  
### <a name="using-begininit-and-endinit-to-initialize-the-element"></a>使用 BeginInit 和 EndInit 初始化元素  
 各个类中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]实现<xref:System.ComponentModel.ISupportInitialize>接口。 您使用<xref:System.ComponentModel.ISupportInitialize.BeginInit%2A>和<xref:System.ComponentModel.ISupportInitialize.EndInit%2A>接口来表示包含初始化步骤 （例如，设置属性的值影响呈现的） 在代码中的区域的方法。 之后<xref:System.ComponentModel.ISupportInitialize.EndInit%2A>调用布局系统在序列中，可以处理元素并开始查找隐式样式。  
  
 如果该元素设置属性上是<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>派生的类，则可以调用的类版本<xref:System.Windows.FrameworkElement.BeginInit%2A>并<xref:System.Windows.FrameworkElement.EndInit%2A>而不是强制转换为<xref:System.ComponentModel.ISupportInitialize>。  
  
### <a name="sample-code"></a>代码示例  
 下面的示例是使用呈现的控制台应用程序的示例代码[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]并<xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=nameWithType>松散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文件来说明的正确位置<xref:System.Windows.FrameworkElement.BeginInit%2A>并<xref:System.Windows.FrameworkElement.EndInit%2A>相对于其他[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]调用调整影响呈现的属性。  
  
 该示例仅演示主要函数。 函数 `Rasterize` 和 `Save`（未显示）是负责图像处理和 IO 的实用工具函数。  
  
 [!code-csharp[InitializeElements#Main](~/samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## <a name="see-also"></a>请参阅

- [WPF 中的树](trees-in-wpf.md)
- [WPF 图形呈现疑难解答](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [XAML 概述 (WPF)](xaml-overview-wpf.md)
