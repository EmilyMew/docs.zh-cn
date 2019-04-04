---
title: Sub 表达式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 5b26a091dc8eb7415702c3c2853a569324def7d5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824606"
---
# <a name="sub-expression-visual-basic"></a>Sub 表达式 (Visual Basic)
声明的参数和子例程 lambda 表达式定义的代码。  
  
## <a name="syntax"></a>语法  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`parameterlist`|可选。 表示过程的参数的本地变量名称的列表。 括号必须存在，即使该列表为空。 有关更多信息，请参见 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`statement`|必需。 一条语句。|  
|`statements`|必需。 语句的列表。|  
  
## <a name="remarks"></a>备注  
 一个*lambda 表达式*是不具有名称的子例程并执行一个或多个语句。 可以任意位置使用 lambda 表达式，您可以使用委托类型，除作为自变量到`RemoveHandler`。 有关委托和 lambda 表达式与委托一起使用的详细信息，请参阅[委托语句](../../../visual-basic/language-reference/statements/delegate-statement.md)并[宽松委托转换](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## <a name="lambda-expression-syntax"></a>Lambda 表达式语法  
 Lambda 表达式的语法类似于标准的子例程。 差异如下所示：  
  
-   Lambda 表达式没有名称。  
  
-   Lambda 表达式不能有修饰符，如`Overloads`或`Overrides`。  
  
-   单行 lambda 表达式的主体必须是一条语句，不是表达式。 主体可以包含调用的 sub 过程，但不是为 function 过程的调用。  
  
-   在 lambda 表达式中，必须必须推断数据类型或所有参数已指定所有参数。  
  
-   可选和`ParamArray`lambda 表达式中不允许使用参数。  
  
-   在 lambda 表达式中不允许使用泛型参数。  
  
## <a name="example"></a>示例  
 下面是向控制台写入值的 lambda 表达式的示例。 该示例显示了一个子例程的这两个单行和多行 lambda 表达式语法。 有关更多示例，请参阅[Lambda 表达式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>请参阅

- [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Lambda 表达式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [运算符和表达式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [语句](../../../visual-basic/programming-guide/language-features/statements.md)
- [宽松委托转换](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
