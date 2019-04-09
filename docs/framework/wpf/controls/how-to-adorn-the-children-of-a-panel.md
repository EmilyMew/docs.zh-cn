---
title: 如何：装饰面板的子元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: e96e1772794a1594d97e1a0109d944d23515468d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100881"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a>如何：装饰面板的子元素
此示例演示如何以编程方式将装饰器绑定到指定的子级<xref:System.Windows.Controls.Panel>。  
  
## <a name="example"></a>示例  
 若要将装饰器绑定到的子级<xref:System.Windows.Controls.Panel>，请执行以下步骤：  
  
1.  声明一个新<xref:System.Windows.Documents.AdornerLayer>对象，并调用`static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>方法的子级为要装饰的元素查找装饰器层。  
  
2.  枚举的子级的父元素并调用<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法将装饰器绑定到每个子元素。  
  
 下面的示例将 SimpleCircleAdorner （如上所示） 的子级绑定<xref:System.Windows.Controls.StackPanel>名为*myStackPanel*。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  目前不支持使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 将装饰器绑定到另一个元素。  
  
## <a name="see-also"></a>请参阅

- [装饰器概述](adorners-overview.md)
