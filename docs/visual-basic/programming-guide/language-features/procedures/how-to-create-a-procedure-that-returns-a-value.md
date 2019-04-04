---
title: 如何：创建一个过程，返回值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 88e30caed97938501302c05830df6546a6822a48
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831249"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>如何：创建一个过程，返回值 (Visual Basic)
您使用`Function`值返回给调用代码的过程。  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>若要创建的过程将返回一个值  
  
1.  任何其他过程之外，使用`Function`语句后, 跟`End Function`语句。  
  
2.  在中`Function`语句，请按照`Function`关键字的过程，然后在括号中的参数列表的名称。  
  
3.  括号后跟`As`子句指定返回的值的数据类型。  
  
4.  将过程的代码语句之间`Function`和`End Function`语句。  
  
5.  使用`Return`语句以返回到调用代码的值。  
  
     以下`Function`过程计算的最长边或斜边的直角三角形而言，其他两个方面为给定的值。  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     下面的示例演示对典型调用`hypotenuse`。  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [Sub 过程](./sub-procedures.md)
- [属性过程](./property-procedures.md)
- [运算符过程](./operator-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [Function 语句](../../../../visual-basic/language-reference/statements/function-statement.md)
- [如何：从过程返回值](./how-to-return-a-value-from-a-procedure.md)
- [如何：调用返回的值的过程](./how-to-call-a-procedure-that-returns-a-value.md)
