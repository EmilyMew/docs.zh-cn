---
title: 如何：从已绑定的目标属性获取绑定对象
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: 7c7392bc11af57b2e9f27e2302f36efb59d40e9d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083099"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>如何：从已绑定的目标属性获取绑定对象
本示例演示如何从数据绑定的目标属性获取绑定对象。  
  
## <a name="example"></a>示例  
 可以执行以下操作来获取 <xref:System.Windows.Data.Binding> 对象：  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  要获取所需的绑定，必须指定依赖属性，因为目标对象中正在使用数据绑定的属性可能不止一个。  
  
 或者，可以获取 <xref:System.Windows.Data.BindingExpression>，然后获取 <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> 属性的值。  
  
 有关完整示例，请参阅[绑定验证示例](https://go.microsoft.com/fwlink/?LinkID=159972)。  
  
> [!NOTE]
>  如果绑定是 <xref:System.Windows.Data.MultiBinding>，则使用 <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>。 如果是 <xref:System.Windows.Data.PriorityBinding>，则使用 <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>。 如果你不确定目标属性是否使用 <xref:System.Windows.Data.Binding>、<xref:System.Windows.Data.MultiBinding> 或 <xref:System.Windows.Data.PriorityBinding> 进行了绑定，可以使用 <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>。  
  
## <a name="see-also"></a>请参阅

- [在代码中创建绑定](how-to-create-a-binding-in-code.md)
- [帮助主题](data-binding-how-to-topics.md)
