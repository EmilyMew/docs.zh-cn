---
title: 使用转换来调整颜色
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
ms.openlocfilehash: 9255dd4adba19bfef1332e5e3dfa463ee96f43f0
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653985"
---
# <a name="using-transformations-to-scale-colors"></a>使用转换来调整颜色
缩放转换将乘以一个或多个数字的四个颜色组件。 下表给出表示缩放颜色矩阵项。  
  
|若要缩放的组件|矩阵条目|  
|----------------------------|------------------|  
|红色|[0][0]|  
|绿色|[1][1]|  
|蓝色|[2][2]|  
|Alpha|[3][3]|  
  
## <a name="scaling-one-color"></a>缩放的一种颜色  
 下面的示例构造<xref:System.Drawing.Image>ColorBars2.bmp 文件中的对象。 然后代码会 2 的因素在图中每个像素的蓝色组件。 转换后的图像一起绘制原始图像。  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 下图显示在右侧左侧上的原始图像和缩放的图像：  
  
 ![比较原始和缩放颜色的屏幕截图。](./media/using-transformations-to-scale-colors/four-bar-scale-one-color.png)  
  
 下表列出了四个条形的颜色矢量之前和之后的蓝色缩放。 请注意，第四个颜色栏中的蓝色组件发送给 0.6 了从 0.8。 这是因为[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]保留仅结果的小数部分。 例如，(2)(0.8) = 1.6，1.6 的小数部分为 0.6。 保留仅的小数部分，可确保结果始终是中间隔 [0，1]。  
  
|原始|缩放|  
|--------------|------------|  
|(0.4, 0.4, 0.4, 1)|(0.4, 0.4, 0.8, 1)|  
|(0.4, 0.2, 0.2, 1)|(0.4, 0.2, 0.4, 1)|  
|(0.2, 0.4, 0.2, 1)|(0.2, 0.4, 0.4, 1)|  
|(0.4, 0.4, 0.8, 1)|(0.4, 0.4, 0.6, 1)|  
  
## <a name="scaling-multiple-colors"></a>缩放多个颜色  
 下面的示例构造<xref:System.Drawing.Image>ColorBars2.bmp 文件中的对象。 然后，代码会在图像中每个像素的红色、 绿色和蓝色组件。 红色分量缩小了 25%、 绿色分量缩小了 35%和蓝色分量缩小了 50%。  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 下图显示在右侧左侧上的原始图像和缩放的图像：  
  
 ![比较原始和缩放颜色的屏幕截图。](./media/using-transformations-to-scale-colors/four-bar-scale-multiple-colors.png)  
  
 下表列出了四个条形的颜色矢量之前和之后的红色、 绿色和蓝色的缩放。  
  
|原始|缩放|  
|--------------|------------|  
|(0.6, 0.6, 0.6, 1)|(0.45, 0.39, 0.3, 1)|  
|(0, 1, 1, 1)|(0, 0.65, 0.5, 1)|  
|(1, 1, 0, 1)|(0.75, 0.65, 0, 1)|  
|(1, 0, 1, 1)|(0.75, 0, 0.5, 1)|  
  
## <a name="see-also"></a>请参阅
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows 窗体中的图形和绘制](graphics-and-drawing-in-windows-forms.md)
- [对图像重新着色](recoloring-images.md)
