---
title: 使用世界变换
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
ms.openlocfilehash: f40d7e8cb814344365e8b88c2659751903b79d77
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139953"
---
# <a name="using-the-world-transformation"></a>使用世界变换
世界转换是一个属性的<xref:System.Drawing.Graphics>类。 指定世界转换的数字存储在<xref:System.Drawing.Drawing2D.Matrix>对象，表示 3 × 3 矩阵。 <xref:System.Drawing.Drawing2D.Matrix>和<xref:System.Drawing.Graphics>类有多种方法来设置世界转换矩阵中的数字。  
  
## <a name="different-types-of-transformations"></a>不同类型的转换  
 在以下示例中，代码首先创建 50 × 50 矩形并将其定位在原点 （0，0）。 原点位于工作区的左上角。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 下面的代码应用的缩放转换，可通过沿 x 方向的 1.75 扩展矩形并通过在 y 方向的 0.5 的比例缩小矩形：  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 结果是沿 x 方向的时间更长且 y 方向的长度小于原始矩形。  
  
 若要旋转而不是其缩放矩形，请使用以下代码：  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 若要转换的矩形，请使用以下代码：  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Drawing2D.Matrix>
- [坐标系和坐标转换](coordinate-systems-and-transformations.md)
- [在托管 GDI+ 中使用变换](using-transformations-in-managed-gdi.md)
