---
title: 如何：调用不返回值 (Visual Basic 中) 的过程
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 05b4b1cb29abff97c44c33d462375fc4d5ab159d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818574"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>如何：调用不返回值 (Visual Basic 中) 的过程
一个`Sub`过程不会返回到调用代码的值。 显式调用该过程与独立的调用语句。 不能只需使用其名称的表达式内调用它。  
  
### <a name="to-call-a-sub-procedure"></a>若要调用的 Sub 过程  
  
1.  指定的名称`Sub`过程。  
  
2.  过程名后面加上括号将参数列表括起来。 如果没有任何自变量，可以选择性地省略括号。 但是，使用括号使您的代码易于阅读。  
  
3.  将参数放在括号中，由逗号分隔参数列表中。 请确保提供的相同顺序中的自变量的`Sub`过程定义的相应参数。  
  
     下面的示例调用 Visual Basic<xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>函数以激活应用程序窗口。 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> 将窗口标题作为其唯一的参数。 不会返回到调用代码的值。 如果未运行 Notepad 进程，则本示例引发<xref:System.ArgumentException>。 `Shell`过程假设应用程序中指定的路径。  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [过程](./index.md)
- [Sub 过程](./sub-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [Sub 语句](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [如何：创建过程](./how-to-create-a-procedure.md)
- [如何：调用返回的值的过程](./how-to-call-a-procedure-that-returns-a-value.md)
- [如何：在 Visual Basic 中调用事件处理程序](./how-to-call-an-event-handler.md)
