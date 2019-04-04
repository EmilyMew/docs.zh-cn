---
title: + 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 4fc8ce96caea436b63fe346139e27ec8dd048f10
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814102"
---
# <a name="-operator-visual-basic"></a>+ 运算符 (Visual Basic)
两个数字相加或返回数值表达式的正值。 此外可以用于连接两个字符串表达式。  
  
## <a name="syntax"></a>语法  
  
```vb
expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`expression1`|必需。 任何数值或字符串表达式。|  
|`expression2`|必填，除非`+`运算符正在计算值为负。 任何数值或字符串表达式。|  
  
## <a name="result"></a>结果  
 如果`expression1`和`expression2`均为数值，结果是其算术的总和。  
  
 如果`expression2`不存在，`+`操作员*一元*恒等运算符的表达式的未更改值。 在这种情况下，该操作包含的保留的符号`expression1`，因此，结果为负如果`expression1`为负。  
  
 如果`expression1`和`expression2`都是字符串，结果是其值的串联。  
  
 如果`expression1`并`expression2`是混合类型的所执行的操作取决于它们的类型、 其内容和设置[Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)。 有关详细信息，请参阅"备注。"中的表  
  
## <a name="supported-types"></a>支持的类型  
 所有数值类型，包括未签名和浮点类型和`Decimal`，和`String`。  
  
## <a name="remarks"></a>备注  
 一般情况下，`+`执行算术加法运算，如果可能，并将连接仅当这两个表达式都是字符串。  
  
 如果一个表达式都不是`Object`，Visual Basic 将采取以下措施。  
  
|数据类型的表达式|由编译器的操作|  
|---|---|  
|这两个表达式是数值数据类型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`， `ULong`， `Decimal`， `Single`，或`Double`)|添加。 结果数据类型为数值类型的数据类型的相应`expression1`和`expression2`。 请参阅中的"整数运算"表[数据类型的运算符结果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。|  
|这两个表达式都是类型 `String`|串联在一起。|  
|一个表达式是数值数据类型和另一个是一个字符串，|如果`Option Strict`是`On`，然后生成编译器错误。<br /><br /> 如果`Option Strict`是`Off`，然后隐式转换`String`到`Double`和添加。<br /><br /> 如果`String`不能转换为`Double`，然后引发<xref:System.InvalidCastException>异常。|  
|一个表达式是数值数据类型，和另一个是[执行任何操作](../../../visual-basic/language-reference/nothing.md)|添加，请使用`Nothing`作为零值。|  
|一个表达式是一个字符串，另一个是 `Nothing`|连接，使用`Nothing`值为""。|  
  
 如果一个表达式是`Object`表达式，Visual Basic 将采取以下措施。  
  
|数据类型的表达式|由编译器的操作|  
|---|---|  
|`Object` 表达式包含的数值和另一个是数值数据类型|如果`Option Strict`是`On`，然后生成编译器错误。<br /><br /> 如果`Option Strict`是`Off`，然后添加。|  
|`Object` 表达式包含的数值和另一个是类型 `String`|如果`Option Strict`是`On`，然后生成编译器错误。<br /><br /> 如果`Option Strict`是`Off`，然后隐式转换`String`到`Double`和添加。<br /><br /> 如果`String`不能转换为`Double`，然后引发<xref:System.InvalidCastException>异常。|  
|`Object` 表达式包含一个字符串，另一个是数值数据类型|如果`Option Strict`是`On`，然后生成编译器错误。<br /><br /> 如果`Option Strict`是`Off`，然后将字符串隐式转换`Object`到`Double`和添加。<br /><br /> 如果字符串`Object`不能转换为`Double`，然后引发<xref:System.InvalidCastException>异常。|  
|`Object` 表达式包含一个字符串和另一个是类型 `String`|如果`Option Strict`是`On`，然后生成编译器错误。<br /><br /> 如果`Option Strict`是`Off`，然后隐式转换`Object`到`String`和连接。|  
  
 如果两个表达式均`Object`表达式，Visual Basic 将采取以下措施 (`Option Strict Off`仅)。  
  
|数据类型的表达式|由编译器的操作|  
|---|---|  
|同时`Object`表达式包含数字值|添加。|  
|同时`Object`表达式均为类型 `String`|串联在一起。|  
|一个`Object`表达式包含的数字值和其他包含字符串|将字符串隐式转换`Object`到`Double`和添加。<br /><br /> 如果字符串`Object`不能转换为数值，则引发<xref:System.InvalidCastException>异常。|  
  
 如果任一`Object`表达式的计算结果[Nothing](../../../visual-basic/language-reference/nothing.md)或<xref:System.DBNull>，则`+`运算符将其视为`String`值为""。  
  
> [!NOTE]
>  当你使用`+`运算符，您可能不能确定是否将进行加法或字符串串联。 使用`&`串联以消除二义性，并提供自我说明代码的运算符。  
  
## <a name="overloading"></a>重载  
 `+`运算符可以被*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 如果你的代码对此类的类或结构使用此运算符，请确保了解其被重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`+`运算符将数相加。 如果操作数均为数值的同时，Visual Basic 计算运算的结果。 算术结果表示两个操作数之和。  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 此外可以使用`+`运算符来串联字符串。 如果操作数均为这两个字符串，Visual Basic 将它们连接。 串联结果表示在它们包含两个操作数的内容的单个字符串。  
  
 如果操作数均为混合类型的结果取决于的设置[Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)。 下面的示例说明了结果时`Option Strict`是`On`。  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 下面的示例说明了结果时`Option Strict`是`Off`。  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 若要消除二义性，应使用`&`运算符而不是`+`的串联。  
  
## <a name="see-also"></a>请参阅

- [& 运算符](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [串联运算符](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [算术运算符](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [在 Visual Basic 中的算术运算符](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)
