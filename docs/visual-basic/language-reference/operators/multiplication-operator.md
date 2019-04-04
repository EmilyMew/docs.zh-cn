---
title: '* 运算符 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: 09b95585325b05c0b7925c4c1c9e123f45791e10
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828948"
---
# <a name="-operator-visual-basic"></a>* 运算符 (Visual Basic)
将两个数字相乘。  
  
## <a name="syntax"></a>语法  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`number1`|必需。 任何数值表达式。|  
|`number2`|必需。 任何数值表达式。|  
  
## <a name="result"></a>结果  
 结果是乘积`number1`和`number2`。  
  
## <a name="supported-types"></a>支持的类型  
 所有数值类型，包括未签名和浮点类型和`Decimal`。  
  
## <a name="remarks"></a>备注  
 结果的数据类型取决于操作数的类型。 下表显示了如何确定结果的数据类型。  
  
|操作数数据类型|结果数据类型|  
|---|---|  
|这两个表达式是整数数据类型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)，[字节](../../../visual-basic/language-reference/data-types/byte-data-type.md)，[短](../../../visual-basic/language-reference/data-types/short-data-type.md)， [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)，[整数](../../../visual-basic/language-reference/data-types/integer-data-type.md)，[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)，[长](../../../visual-basic/language-reference/data-types/long-data-type.md)， [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|适用于数据类型的数值数据类型`number1`和`number2`。 请参阅中的"整数运算"表[数据类型的运算符结果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。|  
|两个表达式均[十进制](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|两个表达式均[单一](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|其中任何一个表达式是浮点数据类型 (`Single`或[双](../../../visual-basic/language-reference/data-types/double-data-type.md))，但不是能同时`Single`(请注意`Decimal`不是浮点数据类型)|`Double`|  
  
 如果表达式计算结果为[Nothing](../../../visual-basic/language-reference/nothing.md)，它将被视为零。  
  
## <a name="overloading"></a>重载  
 `*`运算符可以被*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 如果你的代码对此类的类或结构使用此运算符，请确保了解其被重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 此示例使用`*`运算符将两个数相乘。 结果是两个操作数的乘积。  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>请参阅

- [*= 运算符](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [算术运算符](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的算术运算符](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
