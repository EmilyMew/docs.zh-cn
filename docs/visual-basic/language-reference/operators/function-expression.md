---
title: 函数表达式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 0aa47fd277cfe47b3d8f08b41ffca9c547dcbfe9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839662"
---
# <a name="function-expression-visual-basic"></a>函数表达式 (Visual Basic)
声明的参数和函数的 lambda 表达式定义的代码。  
  
## <a name="syntax"></a>语法  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`parameterlist`|可选。 表示此过程的参数的本地变量名称的列表。 括号必须存在，即使该列表为空。 请参阅[参数列表](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`expression`|必需。 一个表达式。 表达式的类型是该函数的返回类型。|  
|`statements`|必需。 返回一个值，通过使用一系列语句`Return`语句。 (请参阅[Return 语句](../../../visual-basic/language-reference/statements/return-statement.md)。)返回的值的类型为该函数的返回类型。|  
  
## <a name="remarks"></a>备注  
 一个*lambda 表达式*是没有名称，用于计算并返回一个值的函数。 可以使用 lambda 表达式任意位置可用作委托类型，除参数`RemoveHandler`。 有关委托和 lambda 表达式与委托一起使用的详细信息，请参阅[委托语句](../../../visual-basic/language-reference/statements/delegate-statement.md)并[宽松委托转换](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## <a name="lambda-expression-syntax"></a>Lambda 表达式语法  
 Lambda 表达式的语法类似于标准函数。 差异如下所示：  
  
-   Lambda 表达式没有名称。  
  
-   Lambda 表达式不能有修饰符，如`Overloads`或`Overrides`。  
  
-   不使用 lambda 表达式`As`子句来指定该函数的返回类型。 相反，从单行 lambda 表达式的主体的计算结果为，值或多行 lambda 表达式的返回值推断类型。 例如，单行 lambda 表达式的主体是否`Where cust.City = "London"`，其返回类型是`Boolean`。  
  
-   单行 lambda 表达式的主体必须是表达式，而不是语句。 主体可以包含调用的函数过程中，但未一个 sub 过程调用。  
  
-   必须必须推断数据类型或全部指定或者所有参数。  
  
-   不允许使用可选和 Paramarray 参数。  
  
-   不允许使用泛型参数。  
  
## <a name="example"></a>示例  
 下面的示例演示两种方法来创建简单的 lambda 表达式。 第一个示例使用`Dim`提供函数的名称。 若要调用函数时，发送时的参数值中。  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a>示例  
 或者，可以声明并在同一时间运行该函数。  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a>示例  
 下面是递增其参数和返回值的 lambda 表达式的示例。 该示例显示了函数的这两个单行和多行 lambda 表达式语法。 有关更多示例，请参阅[Lambda 表达式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a>示例  
 Lambda 表达式基础中的查询运算符的许多[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]，并可以在基于方法的查询中显式使用。 下面的示例演示一个典型[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查询中，为方法格式后跟查询的转换。  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 有关查询方法的详细信息，请参阅[查询](../../../visual-basic/language-reference/queries/index.md)。 有关标准查询运算符的详细信息，请参阅[标准查询运算符概述](../../programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
## <a name="see-also"></a>请参阅

- [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)
- [Lambda 表达式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [运算符和表达式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [语句](../../../visual-basic/programming-guide/language-features/statements.md)
- [值的比较](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [布尔表达式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [If 运算符](../../../visual-basic/language-reference/operators/if-operator.md)
- [宽松委托转换](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
