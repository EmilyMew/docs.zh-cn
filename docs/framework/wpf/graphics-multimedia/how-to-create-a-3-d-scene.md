---
title: 如何：创建三维场景
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: 8e176cb437055787da86d56770dd71323134fa33
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126225"
---
# <a name="how-to-create-a-3-d-scene"></a>如何：创建三维场景
此示例演示如何创建三维对象，如下所示已旋转的纸张的平面表。 一个<xref:System.Windows.Controls.Viewport3D>以及以下组件用于创建此简单的三维场景：  
  
-   使用创建照相机<xref:System.Windows.Media.Media3D.PerspectiveCamera>。 照相机指定可查看三维场景的哪个部分。  
  
-   创建一个网格，以指定的三维对象 （张纸的） 使用形状<xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>属性的<xref:System.Windows.Media.Media3D.GeometryModel3D>。  
  
-   材料指定要在对象 （线性渐变在此示例中） 使用的图面上显示<xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A>属性的<xref:System.Windows.Media.Media3D.GeometryModel3D>。  
  
-   创建光照射对象使用<xref:System.Windows.Media.Media3D.DirectionalLight>。  
  
## <a name="example"></a>示例  
 下面的代码演示如何在 XAML 中创建三维场景。  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>示例  
 下面的代码演示如何在程序代码中创建相同的三维场景。  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>请参阅

- [三维图形概述](3-d-graphics-overview.md)
