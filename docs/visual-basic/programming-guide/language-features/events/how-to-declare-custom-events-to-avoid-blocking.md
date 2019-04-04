---
title: 如何：声明自定义事件以避免阻止 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 6eea47ea2c8aee697eb34ca904dad22ca88e6ce4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821252"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>如何：声明自定义事件以避免阻止 (Visual Basic)
非常重要的一个事件处理程序不会阻止后续事件处理程序时，有几种情况。 自定义事件，以异步方式调用其事件处理程序的事件。  
  
 默认情况下，事件声明的后备存储字段是多路广播的委托，它按顺序将合并所有事件处理程序。 这意味着，如果一个处理程序需要很长时间才能完成，则会阻止其他处理程序完成之前。 （功能良好的事件处理程序应永远不会执行耗时较长或可能阻止的操作。）  
  
 而不是使用 Visual Basic 提供的事件的默认实现，可以使用自定义事件以异步方式执行的事件处理程序。  
  
## <a name="example"></a>示例  
 在此示例中，`AddHandler`访问器添加的每个处理程序委托`Click`事件<xref:System.Collections.ArrayList>存储在`EventHandlerList`字段。  
  
 在代码引发`Click`事件，`RaiseEvent`访问器调用以异步方式使用的所有事件处理程序委托<xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>方法。 该方法调用的工作线程上的每个处理程序，并立即返回，因此处理程序无法阻止另一个。  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [如何：声明自定义事件以节省内存](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
