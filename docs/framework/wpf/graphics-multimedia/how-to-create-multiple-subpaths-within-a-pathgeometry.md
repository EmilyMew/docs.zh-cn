---
title: 如何：在 PathGeometry 内创建多个子路径
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 286075448cd6a343f8a7b15b2b5005f840f68e1d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111743"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a>如何：在 PathGeometry 内创建多个子路径
此示例演示如何创建在多个子路径<xref:System.Windows.Media.PathGeometry>。 若要创建多个子路径，您创建<xref:System.Windows.Media.PathFigure>每一子路径。  
  
## <a name="example"></a>示例  
 以下示例创建两个子路径，每个三角形。  
  
 [!code-xaml[GeometrySample#38](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 下面的示例演示如何使用创建多个子路径<xref:System.Windows.Shapes.Path>和[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]特性语法。 每个`M`，以便此示例将创建一个三角形的两个子路径创建一个新的子路径。  
  
 [!code-xaml[GeometrySample#58](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 (请注意，此属性语法实际上创建了<xref:System.Windows.Media.StreamGeometry>的轻量版本<xref:System.Windows.Media.PathGeometry>。 有关详细信息，请参阅[路径标记语法](path-markup-syntax.md)页。）  
  
## <a name="see-also"></a>请参阅

- [Geometry 概述](geometry-overview.md)
