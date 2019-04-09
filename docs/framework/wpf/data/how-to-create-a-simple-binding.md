---
title: 如何：创建简单绑定
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: d617c8b97aa679398ed2d061a652f5164f1e499b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094380"
---
# <a name="how-to-create-a-simple-binding"></a>如何：创建简单绑定
此示例演示如何创建一个简单<xref:System.Windows.Data.Binding>。  
  
## <a name="example"></a>示例  
 此示例中有一个 `Person` 对象，该对象具有名为 `PersonName` 的字符串属性。 该 `Person` 对象在名为 `SDKSample` 的命名空间中定义。  
  
 在下面的示例中，突出显示的包含 `<src>` 元素的行将实例化 `Person` 对象，该对象的 `PersonName` 属性值为 `Joe`。 该操作在 `Resources` 部分完成，并指定了 `x:Key`。  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 然后，突出显示的包含 `<TextBlock>` 元素的行会将 <xref:System.Windows.Controls.TextBlock> 控件绑定到 `PersonName` 属性。 这样，<xref:System.Windows.Controls.TextBlock> 显示的值将为 “Joe”。  
  
## <a name="see-also"></a>请参阅

- [数据绑定概述](data-binding-overview.md)
- [帮助主题](data-binding-how-to-topics.md)
