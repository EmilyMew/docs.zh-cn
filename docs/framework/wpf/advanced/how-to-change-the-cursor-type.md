---
title: 如何：更改光标类型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: 5c9e6931f6addb62a51e44b06a159d4e7b1e5f8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141201"
---
# <a name="how-to-change-the-cursor-type"></a>如何：更改光标类型
此示例演示如何更改<xref:System.Windows.Input.Cursor>的鼠标指针的特定元素和应用程序。  
  
 此示例中包含的[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]文件和代码隐藏文件。  
  
## <a name="example"></a>示例  
 创建的用户界面，其中包含<xref:System.Windows.Controls.ComboBox>以选择所需<xref:System.Windows.Input.Cursor>，一对<xref:System.Windows.Controls.RadioButton>对象来确定游标更改是否适用于单个元素或适用于整个应用程序，和一个<xref:System.Windows.Controls.Border>这是新光标应用于的元素。  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 下面的代码隐藏创建<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>中更改的游标类型时调用的事件处理程序<xref:System.Windows.Controls.ComboBox>。  Switch 语句的游标名称和集上进行筛选<xref:System.Windows.FrameworkElement.Cursor%2A>上的属性<xref:System.Windows.Controls.Border>其名为*DisplayArea*。  
  
 如果光标更改设置为"整个应用程序"，<xref:System.Windows.Input.Mouse.OverrideCursor%2A>属性设置为<xref:System.Windows.FrameworkElement.Cursor%2A>属性的<xref:System.Windows.Controls.Border>控件。  这会强制更改对整个应用程序的光标。  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>请参阅

- [输入概述](input-overview.md)
