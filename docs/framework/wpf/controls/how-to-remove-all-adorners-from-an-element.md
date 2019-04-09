---
title: 如何：从元素中删除所有装饰器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
ms.openlocfilehash: 8504bb1ec70de188033b2b092bbb66cf9da3dc11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116789"
---
# <a name="how-to-remove-all-adorners-from-an-element"></a>如何：从元素中删除所有装饰器
此示例演示如何以编程方式移除所有装饰器从指定<xref:System.Windows.UIElement>。  
  
## <a name="example"></a>示例  
 此详细的代码示例中移除所有装饰器的装饰器返回的数组中<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>。  此示例检索在装饰器恰好<xref:System.Windows.UIElement>名为*myTextBox*。  如果在调用中指定元素<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>有任何装饰器，`null`返回。  此代码显式检查 null 的数组，并最适合应用程序的空数组的地方是比较常见。  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a>示例  
 此简化的代码示例是功能上等效于上面所示的详细示例。 此代码不显式检查 null 数组，因此很可能，<xref:System.NullReferenceException>可能引发异常。  Null 数组的地方很少出现，此代码是最适合应用程序。  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a>请参阅

- [装饰器概述](adorners-overview.md)
