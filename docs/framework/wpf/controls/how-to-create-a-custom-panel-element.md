---
title: 如何：创建自定义 Panel 元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: d4fc9d76ada9f27bd52619280b323691af9382c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139563"
---
# <a name="how-to-create-a-custom-panel-element"></a>如何：创建自定义 Panel 元素
## <a name="example"></a>示例  
 此示例演示如何重写的默认布局行为<xref:System.Windows.Controls.Panel>元素，并创建自定义布局元素派生自<xref:System.Windows.Controls.Panel>。  
  
 该示例定义了一个简单的自定义<xref:System.Windows.Controls.Panel>元素称为`PlotPanel`，其中定位子元素根据两个硬编码 x 坐标和 y 坐标。 在此示例中，`x`并`y`都设置为`50`; 因此，所有子元素都放置在该位置上的 x 和 y 轴。  
  
 若要实现自定义<xref:System.Windows.Controls.Panel>行为，该示例使用<xref:System.Windows.FrameworkElement.MeasureOverride%2A>和<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法。 每个方法返回<xref:System.Windows.Size>需要定位和呈现子元素的数据。  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.Panel>
- [面板概述](panels-overview.md)
- [创建自定义内容换行面板示例](https://go.microsoft.com/fwlink/?LinkID=159979)
