---
title: << 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 75c16c27dc919ba365cbe3c28c61a1e46496b0ae
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824281"
---
# <a name="-operator-visual-basic"></a>\<\< 运算符 (Visual Basic)
对位模式执行算术左的移位运算。  
  
## <a name="syntax"></a>语法  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>部件  
 `result`  
 必需。 整型数值。 移位的位模式的结果。 数据类型是相同的`pattern`。  
  
 `pattern`  
 必需。 整型数值表达式。 要移动的位模式。 数据类型必须为整型类型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`)。  
  
 `amount`  
 必需。 数值表达式。 要移位的位模式的比特数。 数据类型必须是`Integer`或扩大到`Integer`。  
  
## <a name="remarks"></a>备注  
 算术移位不是循环，这意味着移出结果的一端的数位另一端不重新移入。 在算术左移位运算移出的结果数据类型范围的位将被丢弃，并在右侧而空出的位设置为零。  
  
 若要防止移位的结果可以容纳超出的位数，Visual Basic 使用的值`amount`具有对应的数据类型大小掩码`pattern`。 这些值的二进制 AND 用于位移量。 大小掩码如下所示：  
  
|数据类型 `pattern`|大小掩码 （十进制）|大小掩码 （十六进制）|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`， `Byte`|7|&H00000007|  
|`Short`， `UShort`|15|&H0000000F|  
|`Integer`， `UInteger`|31|&H0000001F|  
|`Long`， `ULong`|63|&H0000003F|  
  
 如果`amount`为零的值`result`的值是否相同`pattern`。 如果`amount`是负数，它是作为无符号值，使用适当的大小掩码进行屏蔽。  
  
 算术移位永远不会产生溢出异常。  
  
> [!NOTE]
>  `<<`运算符可以被*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 如果你的代码对此类的类或结构使用此运算符，请确保您了解其被重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`<<`运算符执行算术左移位对整数值。 结果始终具有相同的数据类型的被移位的表达式。  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 前一示例的结果如下所示：  
  
-   `result1` 为 192 (0000 0000 0000 1100年)。  
  
-   `result2` 为 3072 (0000 0000 0000 1100年)。  
  
-   `result3` 是-32768 (1000年 0000 0000 0000)。  
  
-   `result4` 是 384 (0000 0001 1000年 0000)。  
  
-   `result5` 为 0 （向左移动 15 位）。  
  
 移位量`result4`计算为 17 和 15，等于 1。  
  
## <a name="see-also"></a>请参阅

- [移位运算符](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [赋值运算符](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<<= 运算符](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的算术运算符](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
