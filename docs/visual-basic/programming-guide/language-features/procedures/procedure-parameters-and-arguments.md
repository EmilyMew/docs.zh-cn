---
title: 过程参数和自变量 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 80065cabcacdcf44b04fef7bacb978ca9c8077ae
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825451"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>过程参数和自变量 (Visual Basic)
在大多数情况下，一个过程需要一些信息已在其中调用它的情况。 执行重复或共享任务的过程为每个调用使用不同的信息。 此信息包括变量、 常量和表达式在调用时传递给该过程。  
  
 一个*参数*表示一个值，此过程需要您提供时调用它。 该过程的声明定义其参数。  
  
 你可以定义不使用参数、 一个参数，或者多个过程。 指定的参数在过程定义的一部分被称作*参数列表*。  
  
 *自变量*调用过程时对过程参数表示所提供的值。 当调用该过程时，调用代码将提供参数。 指定的参数在过程调用的一部分被称作*自变量列表*。  
  
 下图显示了代码调用该过程`safeSquareRoot`从两个不同的位置。 第一次调用将变量的值传递`x`(4.0) 给参数`number`，和中的返回值`root`(2.0) 赋给变量`y`。 第二次调用将传递到的文本值 9.0 `number`，并将返回值 (3.0) 赋给变量`z`。  
  
 ![显示了将自变量传递给参数的关系图](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 有关详细信息，请参阅[差异之间形参和实参](./differences-between-parameters-and-arguments.md)。  
  
## <a name="parameter-data-type"></a>参数数据类型  
 使用定义为参数的数据类型`As`其声明中的子句。 例如，以下函数接受一个字符串和整数。  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 如果类型检查开关 ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`Off,``As`子句是可选的只不过如果任一参数使用它，则所有参数必须都使用它。 如果类型检查`On`，则`As`子句是必需的所有过程的参数。  
  
 如果调用代码需要具有数据类型不同于其相应的参数，如提供参数`Byte`到`String`参数，它必须执行下列操作之一：  
  
-   提供唯一的参数和扩大到参数的数据类型; 的数据类型  
  
-   设置`Option Strict Off`以允许隐式收缩转换; 或  
  
-   使用转换关键字可以显式转换的数据类型。  
  
### <a name="type-parameters"></a>类型参数  
 一个*泛型过程*还定义了一个或多个*类型参数*除了其正常参数。 泛型过程，调用代码，以便它可以调整每个调用的要求的数据类型，它调用过程时，每次传递不同的数据类型。 请参阅 [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)。  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [Sub 过程](./sub-procedures.md)
- [Function 过程](./function-procedures.md)
- [属性过程](./property-procedures.md)
- [运算符过程](./operator-procedures.md)
- [如何：为过程定义参数](./how-to-define-a-parameter-for-a-procedure.md)
- [如何：将参数传递给过程](./how-to-pass-arguments-to-a-procedure.md)
- [按值和按引用传递自变量](./passing-arguments-by-value-and-by-reference.md)
- [过程重载](./procedure-overloading.md)
- [在 Visual Basic 中的类型转换](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
