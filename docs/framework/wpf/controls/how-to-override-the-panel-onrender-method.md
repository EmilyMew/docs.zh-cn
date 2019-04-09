---
title: 如何：重写面板的 OnRender 方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
ms.openlocfilehash: c4539847368c1a5789e99ec92106d17077ed5943
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102526"
---
# <a name="how-to-override-the-panel-onrender-method"></a>如何：重写面板的 OnRender 方法
此示例演示如何重写<xref:System.Windows.Controls.Panel.OnRender%2A>方法的<xref:System.Windows.Controls.Panel>以便将自定义图形效果添加到布局元素。  
  
## <a name="example"></a>示例  
 使用<xref:System.Windows.Controls.Panel.OnRender%2A>方法，以将图形效果添加到呈现的面板元素。 例如，可以使用此方法添加自定义边框或背景效果。 一个<xref:System.Windows.Media.DrawingContext>对象作为参数，它提供用于绘制形状、 文本、 图像或视频的方法传递。 因此，此方法很有用的面板对象自定义项。  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.Panel>
- [面板概述](panels-overview.md)
- [自定义径向面板示例](https://go.microsoft.com/fwlink/?LinkID=159982)
- [帮助主题](panel-how-to-topics.md)
