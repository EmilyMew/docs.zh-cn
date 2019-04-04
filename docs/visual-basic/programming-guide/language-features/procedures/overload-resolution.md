---
title: 重载决策 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
ms.openlocfilehash: e7a05a5fb0b2053e92d9f947f197bdb2dcfa7ce0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832276"
---
# <a name="overload-resolution-visual-basic"></a>重载决策 (Visual Basic)
当 Visual Basic 编译器遇到多个重载版本中定义的过程调用时，编译器必须确定哪个重载来调用。 做到这一点，请执行以下步骤：  
  
1.  **辅助功能。** 它消除了一种访问级别，以防止调用代码中调用它的任何重载。  
  
2.  **参数数目。** 它消除了定义不同数量的参数提供的调用中的任何重载。  
  
3.  **参数数据类型。** 编译器则报告实例方法优先于扩展方法。 如果需要仅进行扩大转换来匹配的过程调用找到的任何实例方法，则所有扩展方法将被都删除，并且编译器将通过仅候选实例方法继续。 如果找到此类的实例方法，则将继续使用实例和扩展方法。  
  
     在此步骤中，它消除了所有重载的调用参数的数据类型无法转换的重载中定义的参数类型。  
  
4.  **收缩转换。** 它消除了所有需要收缩转换从调用的参数类型为定义的参数类型的重载。 这是 true 还是类型检查开关 ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`On`或`Off`。  
  
5.  **最小扩大。** 编译器会考虑对其余的重载。 对于每个对，它将进行比较已定义的参数的数据的类型。 如果所有的重载之一中的类型扩大到中的其他的相应类型，编译器消除了后者。 也就是说，它将保留要求最少量的扩大转换的重载。  
  
6.  **单个候选项。** 它会持续假设重载直到只有一个成对重载会保留，并解析对重载的调用。 如果编译器不能减少到单个的候选版本的重载，则将生成错误。  
  
 下图显示了确定哪一组重载版本来调用的进程。  
  
 ![重载解析过程的流程图](./media/overload-resolution/determine-overloaded-version.gif "在重载版本中")    
  
 下面的示例阐释了此重载决策过程。  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 在第一次调用，编译器无第一个重载，因为第一个参数的类型 (`Short`) 收缩到的相应参数的类型 (`Byte`)。 它然后能消除第三个重载，因为每个自变量类型中的第二个重载 (`Short`并`Single`) 将扩展到第三个重载中的相应类型 (`Integer`和`Single`)。 第二个重载需要较少扩大转换，因此编译器将其用于调用。  
  
 在第二个调用中，编译器不能消除任何根据收缩的重载。 因为它可以调用与自变量类型的最少扩大的第二个重载，它可以消除第三个重载了如下所示的第一个调用中，由于同一原因。 但是，编译器无法解析的第一个和第二个重载之间。 每个都有一个定义的参数类型扩展到其他相应的类型 (`Byte`到`Short`，但`Single`到`Double`)。 因此，编译器将生成重载解析错误。  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>重载可选和 ParamArray 参数  
 如果过程的两个重载具有相同的签名，只不过声明的最后一个参数[可选](../../../../visual-basic/language-reference/modifiers/optional.md)合一和[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)中另一个，则编译器将解析对作为该过程的调用如下所示：  
  
|如果调用提供了最后一个参数为|编译器解析对声明为的最后一个参数的重载的调用|  
|---|---|  
|没有值 （省略该参数）|`Optional`|  
|单个值|`Optional`|  
|以逗号分隔的列表中的两个或多个值|`ParamArray`|  
|（包括一个空数组） 任何长度的数组|`ParamArray`|  
  
## <a name="see-also"></a>请参阅

- [可选参数](./optional-parameters.md)
- [参数数组](./parameter-arrays.md)
- [过程重载](./procedure-overloading.md)
- [过程疑难解答](./troubleshooting-procedures.md)
- [如何：定义一个过程的多个版本](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：调用重载的过程](./how-to-call-an-overloaded-procedure.md)
- [如何：重载带有可选参数的过程](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：重载的参数数量不确定的过程](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [重载过程注意事项](./considerations-in-overloading-procedures.md)
- [重载](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [扩展方法](./extension-methods.md)
