---
title: 在 GDI+ 中限制绘制图面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
ms.openlocfilehash: d0508166f905b45789ce638b03d0747dd6fa904e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074951"
---
# <a name="restricting-the-drawing-surface-in-gdi"></a>在 GDI+ 中限制绘制图面
剪辑涉及到将绘制限制为特定矩形或区域。 下图显示字符串"Hello"剪辑到心形区域。  
  
 ![受限绘制图面](./media/aboutgdip02-art30.gif "AboutGdip02_Art30")  
  
## <a name="clipping-with-regions"></a>使用区域进行剪辑  
 区域可以构造从路径，并且路径可包含的字符串，概述了，因此你可用于剪辑的空心的文字。 下图显示了一系列同心省略号剪辑到的文本字符串的内部。  
  
 ![受限绘制图面](./media/aboutgdip02-art31.gif "AboutGdip02_Art31")  
  
 若要绘制的剪辑，创建<xref:System.Drawing.Graphics>对象，设置其<xref:System.Drawing.Graphics.Clip%2A>属性，然后调用绘制方法的相同<xref:System.Drawing.Graphics>对象：  
  
 [!code-csharp[LinesCurvesAndShapes#91](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [直线、曲线和图形](lines-curves-and-shapes.md)
- [使用区域](using-regions.md)
