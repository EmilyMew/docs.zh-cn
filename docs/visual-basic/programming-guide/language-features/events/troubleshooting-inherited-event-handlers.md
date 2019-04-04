---
title: 有关 Visual Basic 中继承的事件处理程序的疑难解答
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: 704ca667a6d14ade7be0192e872f5e40791cb864
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830183"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>有关 Visual Basic 中继承的事件处理程序的疑难解答
本主题列出了使用继承的组件中的事件处理程序时出现的常见问题。  
  
## <a name="procedures"></a>过程  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>为每个调用两次执行事件处理程序中的代码  
  
-   继承的事件处理程序中不能包含[处理](../../../../visual-basic/language-reference/statements/handles-clause.md)子句。 中的基类的方法已与事件相关联，并且将相应地触发。 删除`Handles`子句从继承的方法。  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
-   如果继承的方法没有`Handles`关键字，验证你的代码不包含一个额外[AddHandler 语句](../../../../visual-basic/language-reference/statements/addhandler-statement.md)或处理相同事件的任何其他方法。  
  
## <a name="see-also"></a>请参阅

- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
