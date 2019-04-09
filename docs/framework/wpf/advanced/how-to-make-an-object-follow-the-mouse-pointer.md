---
title: 如何：使对象跟随鼠标指针移动
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: b9b13b4eec3e42744ba2be6031ec841fb5f215e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107310"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>如何：使对象跟随鼠标指针移动
此示例演示如何在屏幕上移动鼠标指针时更改对象的维度。  
  
 该示例包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]创建的文件[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]和创建事件处理程序的代码隐藏文件。  
  
## <a name="example"></a>示例  
 以下[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]创建[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，其中包括<xref:System.Windows.Shapes.Ellipse>内<xref:System.Windows.Controls.StackPanel>，并将附加的事件处理程序<xref:System.Windows.UIElement.MouseMove>事件。  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 下面的代码隐藏创建<xref:System.Windows.UIElement.MouseMove>事件处理程序。  当鼠标指针移动，高度和宽度<xref:System.Windows.Shapes.Ellipse>增加和减少。  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>请参阅

- [输入概述](input-overview.md)
