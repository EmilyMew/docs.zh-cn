---
title: 如何：实现装饰器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
ms.openlocfilehash: da318fee42b4628351217774de2a2225cfb21ee1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120804"
---
# <a name="how-to-implement-an-adorner"></a>如何：实现装饰器
此示例显示了最小的装饰器实现。  
  
## <a name="notes-for-implementers"></a>实施者的说明  
 请务必注意，装饰器不包括任何继承呈现行为，确保装饰器呈现是装饰器实施者的责任。   实现呈现行为的常用方法是重写<xref:System.Windows.UIElement.OnRender%2A>方法，并使用一个或多个<xref:System.Windows.Media.DrawingContext>对象以便呈现装饰器的视觉对象根据需要 （如在此示例中所示）。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 通过实现继承自抽象的类创建自定义装饰器<xref:System.Windows.Documents.Adorner>类。  示例装饰器简单装饰的边角<xref:System.Windows.UIElement>使用通过重写的圆圈<xref:System.Windows.UIElement.OnRender%2A>方法。  
  
### <a name="code"></a>代码  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a>请参阅

- [装饰器概述](adorners-overview.md)
