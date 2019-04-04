---
title: 变量 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: 9a39c53ea2d57bca379297897d6d4d1b9f7a1a9f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840375"
---
# <a name="variables-in-visual-basic"></a>变量 (Visual Basic)
通常需要执行使用 Visual Basic 的计算时存储的值。 例如，可能需要计算、比较多个值，并根据比较结果对这些值执行不同的运算。 若要进行比较，必须保留这些值。  
  
## <a name="usage"></a>用法  
 Visual Basic 中，就像大多数编程语言一样使用变量来存储值。 变量有名称（用于引用变量中值的词语）。 变量还具有数据类型（用于确定变量可存储的数据种类）。 如果变量需要存储一组密切相关的索引数据项，可以表示数组。  
  
 使用本地类型推断，可以声明变量，而无需显式声明数据类型。 相反，编译器将通过初始化表达式的类型推断出变量的类型。 有关详细信息，请参阅[本地类型推断](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)和 [Option Infer 语句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。  
  
## <a name="assigning-values"></a>赋值  
 使用赋值语句执行计算，并将结果赋给变量，如以下示例所示。  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
>  在此示例中，等于号 (`=`) 为赋值运算符，而不是相等运算符。 值会赋给变量 `applesSold`。  
  
 有关详细信息，请参阅[如何：将数据移入和移出变量](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)。  
  
## <a name="variables-and-properties"></a>变量和属性  
 与变量一样，属性表示可访问的值。 不过，它比变量更复杂。 属性使用代码块来控制如何设置并检索值。 有关详细信息，请参阅 [Visual Basic 中属性和变量的差异](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)。  
  
## <a name="see-also"></a>请参阅

- [变量声明](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [对象变量](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [变量疑难解答](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
- [如何：将数据移入和移出变量](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [在 Visual Basic 中属性和变量之间的差异](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)
- [局部类型推理](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
