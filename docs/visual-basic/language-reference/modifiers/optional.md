---
title: Optional (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: 67ceedffecdfba8ec0c2829a3af31d194f18bd88
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820784"
---
# <a name="optional-visual-basic"></a>Optional (Visual Basic)
指定调用此过程时，可以省略过程自变量。  
  
## <a name="remarks"></a>备注  
 对于每个可选参数，必须为该参数的默认值指定的常量表达式。 如果表达式的计算结果[Nothing](../../../visual-basic/language-reference/nothing.md)，值数据类型的默认值用作参数的默认值。  
  
 如果参数列表包含一个可选参数，则可以跟踪该域控制器的每个参数还必须是可选的。  
  
 `Optional` 修饰符可用于下面的上下文中：  
  
-   [Declare 语句](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  在调用时使用或不带可选参数的过程，您可以按位置或名称传递参数。 有关详细信息，请参阅[按位置和按名称传递自变量](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)。  
  
> [!NOTE]
>  此外可以通过使用重载定义带可选参数的过程。 如果您有一个可选参数，可以定义两个重载的版本的过程，一个接受参数，一个不会。 有关更多信息，请参见 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。  
  
## <a name="example"></a>示例  
 下面的示例定义具有一个可选参数的过程。  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用按位置传递的参数和使用按名称传递的参数调用的过程。 该过程有两个可选参数。  
  
 [!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]  
  
## <a name="see-also"></a>请参阅

- [参数列表](../../../visual-basic/language-reference/statements/parameter-list.md)
- [可选参数](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [关键字](../../../visual-basic/language-reference/keywords/index.md)
