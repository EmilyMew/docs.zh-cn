---
title: 如何：调用过程返回值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: ee80ae48a9b9bfae0afe8f0a2c6e7ebf047d9d36
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820381"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>如何：调用过程返回值 (Visual Basic)
一个`Function`过程返回到调用代码的值。 它通过调用包括其名称和参数放在右边的赋值语句或表达式中。  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>若要调用的表达式内 Function 过程  
  
1.  使用`Function`过程名称将使用变量的方法相同。 可以使用`Function`过程调用任何位置可以在表达式中使用的变量或常数。  
  
2.  过程名后面加上括号将参数列表括起来。 如果没有任何自变量，可以选择性地省略括号。 但是，使用括号使您的代码易于阅读。  
  
3.  将参数放在括号中，由逗号分隔参数列表中。 请确保提供的相同顺序中的自变量的`Function`过程定义的相应参数。  
  
     或者，您可以按名称传递一个或多个参数。 有关详细信息，请参阅[按位置和按名称传递自变量](./passing-arguments-by-position-and-by-name.md)。  
  
4.  从过程返回的值出现在中，只需作为值的表达式的变量或常数那样。  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>若要在赋值语句中调用的函数过程  
  
1.  使用`Function`过程名称之后等号 (`=`) 在赋值语句登录。  
  
2.  过程名后面加上括号将参数列表括起来。 如果没有任何自变量，可以选择性地省略括号。 但是，使用括号使您的代码易于阅读。  
  
3.  将参数放在括号中，由逗号分隔参数列表中。 请确保提供的相同顺序中的自变量的`Function`过程定义相应的参数，除非您按名称传递它们。  
  
4.  从过程返回的值存储在变量或赋值语句左侧的属性。  
  
## <a name="example"></a>示例  
 下面的示例调用 Visual Basic<xref:Microsoft.VisualBasic.Interaction.Environ%2A>检索操作系统环境变量的值。 第一个行调用`Environ`在表达式中，第二个行调用它在赋值语句中。 `Environ` 将变量名称作为其唯一的参数。 它返回到调用代码的变量的值。  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>请参阅

- [Function 过程](./function-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [Function 语句](../../../../visual-basic/language-reference/statements/function-statement.md)
- [如何：创建一个过程，返回一个值](./how-to-create-a-procedure-that-returns-a-value.md)
- [如何：从过程返回值](./how-to-return-a-value-from-a-procedure.md)
- [如何：调用不返回值的过程](./how-to-call-a-procedure-that-does-not-return-a-value.md)
