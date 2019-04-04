---
title: 如何：从过程 (Visual Basic 中) 中返回值
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 293234346053034b544866b6a2eff84974d8a02b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824554"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>如何：从过程 (Visual Basic 中) 中返回值
一个`Function`过程返回一个值到调用代码可以通过执行`Return`语句或在遇到`Exit Function`或`End Function`语句。  
  
### <a name="to-return-a-value-using-the-return-statement"></a>返回值使用 Return 语句  
  
1.  放置`Return`语句在完成该过程的任务时的点。  
  
2.  请按照`Return`想要返回到调用代码会生成值的表达式的关键字。  
  
3.  在同一过程中可拥有多个 `Return` 语句。  
  
     以下`Function`过程计算的最长边或斜边的直角三角形而言，并将其返回给调用代码。  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     下面的示例演示对典型调用`hypotenuse`，用于存储返回的值。  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>返回值使用 Exit 函数或最终函数  
  
1.  中至少一个就地`Function`过程中，分配到过程的名称的值。  
  
2.  当您执行`Exit Function`或`End Function`语句，Visual Basic 将返回最近分配给该过程的名称的值。  
  
3.  在同一过程中可拥有多个 `Exit Function` 语句，也可混合 `Return` 和 `Exit Function` 语句。  
  
4.  只能有一个`End Function`中的语句`Function`过程。  
  
     详细信息和示例，请参阅"返回值"中的[Function 语句](../../../../visual-basic/language-reference/statements/function-statement.md)。  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [Sub 过程](./sub-procedures.md)
- [属性过程](./property-procedures.md)
- [运算符过程](./operator-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [Function 语句](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Return 语句](../../../../visual-basic/language-reference/statements/return-statement.md)
- [如何：创建一个过程，返回一个值](./how-to-create-a-procedure-that-returns-a-value.md)
- [如何：调用返回的值的过程](./how-to-call-a-procedure-that-returns-a-value.md)
