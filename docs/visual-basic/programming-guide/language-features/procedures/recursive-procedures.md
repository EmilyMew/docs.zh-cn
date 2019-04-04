---
title: 递归过程 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: de9a2af9fc3cd78879b6525245727a6f52d51c63
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832380"
---
# <a name="recursive-procedures-visual-basic"></a>递归过程 (Visual Basic)
一个*递归*过程是指调用其自身。 一般情况下，这不是编写 Visual Basic 代码的最有效方法。  
  
 以下过程使用递归来计算其原始自变量的阶乘。  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a>递归过程的注意事项  
 **限制条件**。 必须设计的递归过程测试可以终止递归的至少一个条件和您还必须处理任何此类条件均在合理的递归调用数内的情况。 没有可以满足而不会出现的至少一个条件，您的过程在运行高风险的无限循环中执行。  
  
 **内存使用率**。 你的应用程序具有有限的数量的本地变量的空间。 每次过程调用其自身，将使用这些空间的详细信息为其本地变量的其他副本。 如果此过程将无限期地继续，则最终会导致<xref:System.StackOverflowException>错误。  
  
 **效率**。 您几乎总是可以替换为递归循环。 循环没有初始化其他存储和返回值传递自变量的开销。 应用的性能可以更好的而无需递归调用。  
  
 **相互递归**。 你可能会发现性能非常差或甚至无限循环，如果两个过程相互调用。 这样的设计带来了在一个递归过程中，相同的问题，但很难检测和调试。  
  
 **使用括号调用**。 当`Function`过程调用其自身以递归方式，必须执行的过程名称使用括号，即使没有参数列表。 否则，执行的函数名称作为表示该函数的返回值。  
  
 **测试**。 如果您编写一个递归过程时，应对其进行测试应非常小心以确保其始终满足某些限制条件。 你还应确保您不能运行由于递归调用过多的内存不足。  
  
## <a name="see-also"></a>请参阅

- <xref:System.StackOverflowException>
- [过程](./index.md)
- [Sub 过程](./sub-procedures.md)
- [Function 过程](./function-procedures.md)
- [属性过程](./property-procedures.md)
- [运算符过程](./operator-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [过程重载](./procedure-overloading.md)
- [过程疑难解答](./troubleshooting-procedures.md)
- [循环结构](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
