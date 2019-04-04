---
title: Comparison Operators in Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
ms.openlocfilehash: d08974a929a723d4037300f9d72ae03c072d47fa
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826153"
---
# <a name="comparison-operators-in-visual-basic"></a>Comparison Operators in Visual Basic
比较运算符比较两个表达式并返回`Boolean`值，该值表示其值的关系。 有运算符用于比较数字值、 字符串、 比较运算符和运算符用于比较的对象。 所有三种类型的运算符是此处所述。  
  
## <a name="comparing-numeric-values"></a>比较数值  
 Visual Basic 将使用六个数字的比较运算符的数字值进行比较。 每个运算符采用两个表达式的计算结果为数字值作为操作数。 下表列出的运算符，并显示了每个示例。  
  
|运算符|测试条件|示例|  
|--------------|----------------------|--------------|  
|`=` （相等）|第一个表达式相等的值是否为第二个值？|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` （不等于）|第一个表达式的值是否为第二个值不相等？|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` （小于）|第一个表达式的值小于第二个值是否是？|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` （大于）|第一个表达式的值是否大于第二个值？|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` （小于或等于）|第一个表达式的值是否小于或等于第二个值？|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` （大于或等于）|第一个表达式的值是否大于或等于第二个值？|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>比较字符串  
 Visual Basic 对使用的字符串进行比较[Like 运算符](../../../../visual-basic/language-reference/operators/like-operator.md)以及数值的比较运算符。 `Like`运算符允许您指定的模式。 与指定模式进行比较的字符串，如果匹配，则结果是`True`。 否则，结果为 `False`。 数字运算符，你可以比较`String`值基于它们的排序顺序，如以下示例所示。  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 在前面的示例结果是`True`因为第一个字符串中的第一个字符的排序之前第二个字符串中的第一个字符。 如果第一个字符相等，比较将继续到两个字符串中的下一个字符，依此类推。 此外可以测试使用相等运算符，如以下示例所示的字符串相等。  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 如果一个字符串为前缀，如"aa"和"aaa"，被认为更长的字符串可以大于较短的字符串。 下面的示例阐释了这一点。  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 排序顺序基于二进制比较或文本比较，具体取决于设置`Option Compare`。 有关详细信息请参阅[Option 比较语句](../../../../visual-basic/language-reference/statements/option-compare-statement.md)。  
  
## <a name="comparing-objects"></a>比较对象  
 Visual Basic 使用的两个对象引用变量进行比较[Is 运算符](../../../../visual-basic/language-reference/operators/is-operator.md)并[IsNot 运算符](../../../../visual-basic/language-reference/operators/isnot-operator.md)。 可以使用其中任一运算符确定两个引用变量引用同一对象实例。 下面的示例阐释了这一点。  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 在前面的示例中，`x Is y`计算结果为`True`，因为这两个变量引用同一个实例。 此结果与下面的示例进行对比。  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 在前面的示例中，`x Is y`计算结果为`False`，因为虽然变量引用相同类型的对象，但它们是指该类型的不同实例。  
  
 当你想要测试两个对象不指向同一个实例，`IsNot`运算符可避免通过编程方式笨拙的组合`Not`和`Is`。 下面的示例阐释了这一点。  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 在前面的示例中，`If a IsNot b`等效于`If Not a Is b`。  
  
### <a name="comparing-object-type"></a>比较对象类型  
 你可以测试是否与特定类型的对象是`TypeOf`...`Is`表达式。 语法如下所示：  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 当`typename`指定接口类型，则`TypeOf`...`Is`表达式返回`True`如果对象实现的接口类型。 当`typename`是类类型，则表达式将返回`True`如果对象是指定类或派生自指定类的类的实例。 下面的示例阐释了这一点。  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 在前面的示例中，`TypeOf x Is Control`表达式的计算结果`True`因为的类型`x`是`Button`，后者又继承`Control`。  
  
 有关详细信息，请参阅[TypeOf 运算符](../../../../visual-basic/language-reference/operators/typeof-operator.md)。  
  
## <a name="see-also"></a>请参阅

- [值的比较](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [比较运算符](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [运算符](../../../../visual-basic/language-reference/operators/index.md)
- [在 Visual Basic 中的算术运算符](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [在 Visual Basic 中的串联运算符](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [在 Visual Basic 中的逻辑和位运算符](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
