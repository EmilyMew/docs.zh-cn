---
title: 参数数组 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: 8ea4c77056701b8f61c1ed5a53cf20d98ae913bc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834150"
---
# <a name="parameter-arrays-visual-basic"></a>参数数组 (Visual Basic)
通常情况下，不能调用有更多参数不是过程声明指定的过程。 当您需要的参数数量不确定时，可以声明*参数数组*，它允许过程接受一个参数的值的数组。 无需知道何时定义过程的参数数组中的元素数。 数组大小由该过程每次调用单独确定。  
  
## <a name="declaring-a-paramarray"></a>声明一个参数数组  
 您使用[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)关键字来表示的参数列表中的参数数组。 适用以下规则：  
  
-   一个过程可以定义只有一个参数数组，并且它必须在过程定义中的最后一个参数。  
  
-   必须通过值传递参数数组。 它是一个良好的编程做法中显式包括[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)过程定义中的关键字。  
  
-   参数数组是自动可选的。 其默认值为空的参数数组的元素类型的一维数组。  
  
-   前面的参数数组的所有参数都是必需的。 参数数组必须是唯一的可选参数。  
  
## <a name="calling-a-paramarray"></a>调用参数数组  
 时调用定义的参数数组的过程，可以通过以下方式之一提供参数：  
  
-   执行任何操作-即，则可以省略[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)参数。 在这种情况下，将一个空数组传递给过程。 你还可以传递[Nothing](../../../../visual-basic/language-reference/nothing.md)关键字，使用相同的效果。  
  
-   任意数量的参数，由逗号分隔列表。 每个自变量的数据类型必须是隐式转换为`ParamArray`元素类型。  
  
-   包含与参数数组的元素类型相同的元素类型的数组。  
  
 在所有情况下，该过程中的代码将参数的数组视为与相同的数据类型的元素的一维数组`ParamArray`数据类型。  
  
> [!IMPORTANT]
>  每当处理数组可以是无限期较大，则存在无限大的某种内部容量的应用程序的风险。 如果接受一个参数数组时，你应测试调用代码传递给它的数组的大小。 如果你的应用程序太大，请采取适当的措施。 有关详细信息，请参阅[数组](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="example"></a>示例  
 下面的示例定义并调用该函数`calcSum`。 `ParamArray`的参数修饰符`args`使函数能够接受数目可变的参数。  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 下面的示例定义了一个使用参数数组，并输出传递给参数数组的所有数组元素的值。  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [过程](./index.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [按值和按引用传递自变量](./passing-arguments-by-value-and-by-reference.md)
- [按位置和按名称传递自变量](./passing-arguments-by-position-and-by-name.md)
- [可选参数](./optional-parameters.md)
- [过程重载](./procedure-overloading.md)
- [数组](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
