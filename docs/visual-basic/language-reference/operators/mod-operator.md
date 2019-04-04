---
title: Mod 运算符 (Visual Basic)
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: b127c50f3319d4fe7c4890fc3bffb295baa37466
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840167"
---
# <a name="mod-operator-visual-basic"></a>Mod 运算符 (Visual Basic)
使两个数字相除，仅返回余数。  
  
## <a name="syntax"></a>语法  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a>部件  
 `number1`  
 必需。 任何数值表达式。  
  
 `number2`  
 必需。 任何数值表达式。  
  
## <a name="supported-types"></a>支持的类型  
 所有数值类型。 这包括未签名和浮点类型和`Decimal`。  
  
## <a name="result"></a>结果

结果是后的余数`number1`除以`number2`。 例如，表达式`14 Mod 4`计算结果为 2。  

> [!NOTE]
> 没有之间的差异*余数*并*取模*在数学中，使用不同的结果为负数。 `Mod`运算符在 Visual Basic 中，.NET Framework`op_Modulus`运算符，并且基础[rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL 指令执行其余操作。

结果`Mod`操作将保留被除数，符号`number1`，因此它可以是正数或负数。 结果始终处于范围内 (-`number2`， `number2`)、 排他。 例如：

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a>备注  
 如果任一`number1`或`number2`是浮点值，返回浮点除法运算的余数。 结果的数据类型是可以容纳所有可能的值而导致的部门使用的数据类型的最小数据类型`number1`和`number2`。  
  
 如果`number1`或`number2`的计算结果为[Nothing](../../../visual-basic/language-reference/nothing.md)，它将被视为零。  
  
 相关的运算符包括：  
  
-   [\ 运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)返回整数除法运算的商。 例如，表达式`14 \ 4`的计算结果为 3。  
  
-   [/ 运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)返回完整商，包括其余部分中的，作为浮点数。 例如，表达式`14 / 4`的计算结果为 3.5。  
  
## <a name="attempted-division-by-zero"></a>尝试的除数为零  
 如果`number2`的计算结果为零的行为`Mod`运算符取决于操作数的数据类型。 整数除法引发<xref:System.DivideByZeroException>异常。 浮点除法运算返回<xref:System.Double.NaN>。  
  
## <a name="equivalent-formula"></a>等效公式  
 表达式`a Mod b`等效于以下公式之一：  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a>浮点不精确性  
 当使用浮点数时，请记住在内存中不一定有精确的十进制表示形式。 这可能会导致意外的结果从某些操作，如值比较和`Mod`运算符。 有关详细信息，请参阅[故障排除数据类型](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
## <a name="overloading"></a>重载  
 `Mod`运算符可以被*重载*，这意味着类或结构可以重新定义其行为。 如果你的代码适用`Mod`到类或结构，其中包含此类重载的实例，请确保了解其被重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`Mod`运算符将两个数相除，并只返回余数。 如果一个数是浮点数，结果是表示余数的浮点数。  
  
 [!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]  
  
## <a name="example"></a>示例  
 下面的示例演示可能不精确的浮点操作数。 在第一个语句中，操作数均为`Double`，0.2，存储的值是为 0.20000000000000001 的无限重复二进制小数。 在第二个语句中，文本类型字符`D`强制的两个操作数`Decimal`，，0.2 具有精确的表示形式。  
  
 [!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [算术运算符](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [数据类型疑难解答](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [在 Visual Basic 中的算术运算符](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\ 运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
