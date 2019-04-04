---
title: 无法推断“<variablename>”的类型，因为循环边界和步骤变量未扩大到同一类型
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: e90e881546c12df2c8b19ff03a4d4c7304c4596c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815868"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>类型\<变量名 > 无法推断，因为循环边界和步骤变量未扩大到同一类型
您编写`For...Next`循环中的编译器无法推断 for 循环控制变量的数据类型因为以下条件成立：  
  
-   未在 `As` 子句中指定循环控制变量的数据类型。  
  
-   循环边界和步骤变量包含至少两种数据类型。  
  
-   数据类型之间存在的标准转换。  
  
 因此，编译器无法推断的循环控制变量的数据类型。  
  
 在以下示例中，步骤变量是字符，且循环边界都是整数。 由于没有任何标准字符和整数之间转换，会报告此错误。  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 **错误 ID:** BC30982  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   更改类型的循环边界和步骤变量根据需要，以便在至少一个其他扩大到的类型。 在前面的示例中，更改的类型`stepVar`到`Integer`。  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     - 或 -  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   使用显式转换函数将转换为相应类型的循环边界和步骤变量。 在上述示例中，将应用`Val`函数来`stepVar`。  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [For...Next 语句](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [隐式转换和显式转换](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [局部类型推理](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer 语句](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [扩大转换和收缩转换](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
