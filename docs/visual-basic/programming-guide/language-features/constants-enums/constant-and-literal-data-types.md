---
title: 常量和 Literal 数据类型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 50e36aa13439bafcca27a7153a8c5d6043f03975
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833498"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>常量和 Literal 数据类型 (Visual Basic)
文本是一个值，表示为本身而不是变量的值或表达式，如数字 3 或字符串"Hello"的结果。 常量是有意义的名称，它接受文本的位置，并将保留在整个程序，而不是变量，其值可能会更改此相同的值。  
  
 当[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)是`Off`并[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)是`On`，您必须显式声明的所有常量具有数据类型。 在下面的示例中的数据类型`MyByte`显式声明数据类型为`Byte`:  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 当`Option Infer`是`On`或`Option Strict`是`Off`，你可以声明变量，而无需指定数据类型为`As`子句。 编译器确定的常量表达式的类型的类型。 默认情况下强制转换数字的整数文本`Integer`数据类型。 默认数据类型为浮点数`Double`，和关键字`True`并`False`指定`Boolean`常量。  
  
## <a name="literals-and-type-coercion"></a>文本和类型强制转换  
 在某些情况下，你可能想要将文本强制为特定的数据类型;例如，如果将特别大的整数文字值分配到类型的变量的`Decimal`。 下面的示例将生成错误：  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 从文本表示形式会导致错误。 `Decimal`数据类型可以保存值过大，但文本隐式表示为`Long`，哪些不能。  
  
 您可以强制转换为两种方法中的特定数据类型的文字： 通过将类型字符追加到它，或将其放在封闭字符。 类型字符或封闭字符必须立即之前和/或按照文本，不带任何干预空格或任何类型的字符。  
  
 若要使上一个示例工作，您可以将附加`D`类型为文本，这会导致它无法表示为字符`Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 下面的示例演示如何正确使用类型字符和封闭字符：  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 如下表所示的封闭字符和 Visual Basic 中可用的类型字符。  
  
|数据类型|封闭字符|追加的类型字符|  
|---|---|---|  
|`Boolean`|(无)|(无)|  
|`Byte`|(无)|(无)|  
|`Char`|"|C|  
|`Date`|#|(无)|  
|`Decimal`|(无)|D 或使用 @|  
|`Double`|(无)|R 或 #|  
|`Integer`|(无)|I 或 %|  
|`Long`|(无)|L 或 （& a)|  
|`Short`|(无)|S|  
|`Single`|(无)|F 或 ！|  
|`String`|"|(无)|  
  
## <a name="see-also"></a>请参阅

- [用户定义的常量](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)
- [如何：声明常量](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)
- [常量概述](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Option Strict 语句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Option Explicit 语句](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [枚举概述](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [如何：声明枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [枚举和名称限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [数据类型](../../../../visual-basic/language-reference/data-types/index.md)
- [常量和枚举](../../../../visual-basic/language-reference/constants-and-enumerations.md)
