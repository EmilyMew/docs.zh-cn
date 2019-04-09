---
title: 如何：使元素就地旋转
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: aca9bd577f2882e31e8d49abe5eeb5ade86f95f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110659"
---
# <a name="how-to-make-an-element-spin-in-place"></a>如何：使元素就地旋转
此示例演示如何使某个元素通过使用旋转<xref:System.Windows.Media.RotateTransform>和一个<xref:System.Windows.Media.Animation.DoubleAnimation>。  
  
 下面的示例应用<xref:System.Windows.Media.RotateTransform>到<xref:System.Windows.UIElement.RenderTransform%2A>元素的属性。 该示例使用<xref:System.Windows.Media.Animation.DoubleAnimation>进行动画处理<xref:System.Windows.Media.RotateTransform.Angle%2A>的<xref:System.Windows.Media.RotateTransform>。 若要使元素就地旋转，该示例设置<xref:System.Windows.UIElement.RenderTransformOrigin%2A>到点 （0.5，0.5） 元素的属性。  
  
## <a name="example"></a>示例  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 有关完整示例，其中包括转换的更多示例，请参阅[2d 转换示例](https://go.microsoft.com/fwlink/?LinkID=158252)。  
  
## <a name="see-also"></a>请参阅

- [动画概述](animation-overview.md)
- [变换概述](transforms-overview.md)
