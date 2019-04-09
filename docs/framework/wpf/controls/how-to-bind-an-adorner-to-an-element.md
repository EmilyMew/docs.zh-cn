---
title: 如何：将装饰器绑定到元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: 54c9e6dfff2bbf7bfabde523b5d6ae5a623fe733
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194716"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>如何：将装饰器绑定到元素
此示例演示如何以编程方式将装饰器绑定到指定<xref:System.Windows.UIElement>。  
  
## <a name="example"></a>示例  
 若要将装饰器绑定到特定<xref:System.Windows.UIElement>，请执行以下步骤：  
  
1.  调用`static`方法<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>若要获取<xref:System.Windows.Documents.AdornerLayer>对象<xref:System.Windows.UIElement>为要装饰。 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> 从指定的可视化树向上**UIElement**，并返回它找到的第一个装饰器层。 （如果未发现装饰器层，该方法将返回 null。）  
  
2.  调用<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法以将装饰器绑定到目标**UIElement**。  
  
 下面的示例将 SimpleCircleAdorner （如上所示） 到绑定<xref:System.Windows.Controls.TextBox>名为*myTextBox*。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  目前不支持使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 将装饰器绑定到另一个元素。  
  
## <a name="see-also"></a>请参阅

- [装饰器概述](adorners-overview.md)
