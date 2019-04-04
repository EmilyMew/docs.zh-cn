---
title: 过程疑难解答 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: 492a7474a38a7e41b7e3b3f59dfa118c30256ea4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830131"
---
# <a name="troubleshooting-procedures-visual-basic"></a>过程疑难解答 (Visual Basic)
此页列出了在使用过程时可能发生的一些常见问题。  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>从函数过程中返回数组类型  
 如果`Function`过程返回数组数据类型，不能使用`Function`要将值存储在数组的元素名称。 如果您尝试执行此操作，编译器将其解释为调用`Function`。 下面的示例生成编译器错误。  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 该语句`allOnes(i) = 1`生成编译器错误，因为它看起来在调用`allOnes`与错误的数据类型的自变量 (单一实例`Integer`而不是`Integer`数组)。 该语句`Return allOnes()`生成编译器错误，因为它看起来在调用`allOnes`不带参数。  
  
 **正确的方法：** 若要在无法修改将返回一个数组的元素，请为本地变量定义内部数组。 下面的示例将编译没有错误。  
  
 [!code-vb[VbVbcnProcedures#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#66)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>未修改的参数的过程调用  
 如果你想要允许更改基础调用代码中的自变量的编程元素的过程，必须通过引用传递。 但是，一个过程可以访问的元素的引用类型自变量，即使按值传递。  
  
-   **基础变量**。 若要允许的值替换为基础的变量元素本身的过程，该过程必须声明参数[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。 此外，调用代码必须不在括号中，将自变量，因为这样会重写`ByRef`传递机制。  
  
-   **引用类型元素**。 如果将参数声明[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)，该过程不能修改基础变量元素本身。 但是，如果参数为引用类型，该过程可以修改它指向的该对象的成员，即使它不能替换变量的值一样。 例如，如果参数为数组变量，该过程不能将一个新数组分配给它，但它可以更改一个或多个元素。 更改的元素将反映在调用代码中的基础数组变量。  
  
 下面的示例定义两个过程采用一个数组变量的值并运行它的元素上。 过程`increase`只需添加一个到每个元素。 过程`replace`将一个新数组分配给该参数`a()`，然后添加一个到每个元素。 但是，重新分配不影响调用代码中的基础数组变量因为`a()`被声明为`ByVal`。  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 以下示例将调用`increase`和`replace`。  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 第一个`MsgBox`调用显示"increase(n) 后：11, 21, 31, 41". 因为`n`是引用类型，`increase`可以更改其中一个成员，即使它传递`ByVal`。  
  
 第二个`MsgBox`调用显示"replace(n) 后：11, 21, 31, 41". 因为`n`传递`ByVal`，`replace`不能修改变量`n`通过向它分配一个新数组。 当`replace`创建新的数组实例`k`并将其分配给本地变量`a`，它将失去对引用`n`由调用代码传入。 当它递增的成员`a`，只有本地数组`k`受到影响。  
  
 **正确的方法：** 若要能够修改基础变量元素本身，请按引用传递。 下面的示例中的声明演示更改`replace`允许以替换与另一个调用代码中的一个数组。  
  
 [!code-vb[VbVbcnProcedures#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#64)]  
  
## <a name="unable-to-define-an-overload"></a>无法定义重载方法  
 如果你想要定义一个过程的重载的版本，则必须使用相同名称但不同的签名。 如果编译器无法区分从重载方法具有相同的签名声明，则将生成错误。  
  
 *签名*的过程由过程名称和参数列表。 每个重载必须具有与所有其他重载相同的名称，但必须至少一个签名的其他组件中所有不同。 有关更多信息，请参见 [Procedure Overloading](./procedure-overloading.md)。  
  
 以下各项，即使它们与参数列表中，不是签名的过程的组件：  
  
-   过程修饰符关键字，如`Public`， `Shared`，和 `Static`  
  
-   参数名称  
  
-   参数修饰符关键字，如`ByRef`和 `Optional`  
  
-   （除转换运算符） 的返回值数据类型  
  
 不能通过只改变一个或多个前面的项目重载的过程。  
  
 **正确的方法：** 若要能够定义过程重载，您必须改变签名。 因为必须使用相同的名称，您必须改变数目、 顺序或参数的数据类型。 在泛型过程中，可以使用不同类型参数的数目。 在转换运算符 ([CType 函数](../../../../visual-basic/language-reference/functions/ctype-function.md))，可以采用不同的返回类型。  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>重载具有可选的解析和 ParamArray 参数  
 如果重载具有一个或多个过程[可选](../../../../visual-basic/language-reference/modifiers/optional.md)参数或[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)参数，必须避免重复任何*隐式重载*。 有关信息，请参阅[中重载过程注意事项](./considerations-in-overloading-procedures.md)。  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>调用重载过程的错误版本  
 如果过程具有多个重载的版本，应熟悉所有其参数列表，并了解 Visual Basic 如何解析重载之间的调用。 否则，您可以调用除预期之外的重载。  
  
 在确定你想要调用的重载，请务必遵守以下规则：  
  
-   提供正确数量的自变量，并按正确的顺序。  
  
-   理想情况下，参数应具有与对应的参数完全相同的数据类型。 在任何情况下，每个自变量的数据类型必须扩大到的其对应的参数。 这是如此[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)设置为`Off`。 如果某个重载需要从参数列表中，该重载任何收缩转换不能调用。  
  
-   如果你提供需要扩大转换的参数，请尽可能地为相应的参数数据类型及其数据类型。 如果两个或多个重载接受您的自变量数据类型，则编译器将解析对调用进行最少量的扩大转换的重载的调用。  
  
 可以通过减少数据类型不匹配的可能性[CType 函数](../../../../visual-basic/language-reference/functions/ctype-function.md)转换关键字时准备自己的参数。  
  
### <a name="overload-resolution-failure"></a>重载决策失败  
 当您调用重载的过程时，编译器将尝试消除所有但的重载之一。 如果成功，它解析为该重载的调用。 如果它消除了所有重载，或者如果它不能减少为单个候选符合条件的重载，则将生成错误。  
  
 下面的示例阐释了重载决策过程。  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 在第一次调用，编译器无第一个重载，因为第一个参数的类型 (`Short`) 收缩到的相应参数的类型 (`Byte`)。 它然后能消除第三个重载，因为每个自变量类型中的第二个重载 (`Short`并`Single`) 将扩展到第三个重载中的相应类型 (`Integer`和`Single`)。 第二个重载需要较少扩大转换，因此编译器将其用于调用。  
  
 在第二个调用中，编译器不能消除任何根据收缩的重载。 因为它可以调用与自变量类型的最少扩大的第二个重载，它可以消除第三个重载了如下所示的第一个调用中，由于同一原因。 但是，编译器无法解析的第一个和第二个重载之间。 每个都有一个定义的参数类型扩展到其他相应的类型 (`Byte`到`Short`，但`Single`到`Double`)。 因此，编译器将生成重载解析错误。  
  
 **正确的方法：** 若要能够调用无歧义地重载的过程，请使用[CType 函数](../../../../visual-basic/language-reference/functions/ctype-function.md)以匹配的参数类型的参数数据类型。 下面的示例演示如何调用`z`强制解析到第二个重载。  
  
 [!code-vb[VbVbcnProcedures#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#65)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>重载具有可选的解析和 ParamArray 参数  
 如果过程的两个重载具有相同的签名，只不过声明的最后一个参数[可选](../../../../visual-basic/language-reference/modifiers/optional.md)合一和[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)中另一个，则编译器将解析对该过程的调用根据最接近的匹配。 有关更多信息，请参见 [Overload Resolution](./overload-resolution.md)。  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [Sub 过程](./sub-procedures.md)
- [Function 过程](./function-procedures.md)
- [属性过程](./property-procedures.md)
- [运算符过程](./operator-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [过程重载](./procedure-overloading.md)
- [重载过程注意事项](./considerations-in-overloading-procedures.md)
- [重载决策](./overload-resolution.md)
