---
title: 如何：向三维模型应用绘图
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: a20b89a7359fc85d9790ac02dd2b173452df8c22
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125029"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>如何：向三维模型应用绘图
此示例演示如何使用<xref:System.Windows.Media.DrawingBrush>作为<xref:System.Windows.Media.Media3D.Material>应用于[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]模型。  
  
 下面的代码定义<xref:System.Windows.Media.DrawingGroup>的内容作为<xref:System.Windows.Media.DrawingBrush>。  <xref:System.Windows.Media.DrawingBrush>设置为<xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A>的属性<xref:System.Windows.Media.Media3D.DiffuseMaterial>应用于[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]平面。  
  
 **注意：** 通常是需要复杂的对象和值，如下面的绘图定义为资源可以重复使用并简化你的代码。 请参阅[XAML 资源](../advanced/xaml-resources.md)有关详细信息。  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>示例  
 下面的代码演示了整个示例。  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>请参阅

- [XAML 资源](../advanced/xaml-resources.md)
- [创建三维场景](how-to-create-a-3-d-scene.md)
- [Drawing 对象概述](drawing-objects-overview.md)
- [三维图形概述](3-d-graphics-overview.md)
