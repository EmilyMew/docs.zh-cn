---
title: 如何：匹配字符串与模式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: ca6537d81f080120fcbea0cf083f450dce4e9f62
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826010"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>如何：匹配字符串与模式 (Visual Basic)
如果想要找出的表达式[字符串数据类型](../../../../visual-basic/language-reference/data-types/string-data-type.md)满足一种模式，则可以使用[Like 运算符](../../../../visual-basic/language-reference/operators/like-operator.md)。  
  
 `Like` 采用两个操作数。 左的操作数是字符串表达式和右操作数是一个包含要用于匹配的模式字符串。 `Like` 返回`Boolean`值，该值指示字符串表达式是否满足模式的要求。  
  
 可以与匹配针对特定字符、 通配符字符、 字符列表或字符范围的字符串表达式中的每个字符。 模式字符串中的规范的位置对应于要在字符串表达式中匹配的字符的位置。  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>若要匹配针对特定字符的字符串表达式中的字符  
  
-   直接在模式字符串中放置的特定字符。 某些特殊字符必须括在方括号中 (`[ ]`)。 有关详细信息，请参阅[Like 运算符](../../../../visual-basic/language-reference/operators/like-operator.md)。  
  
     下面的示例测试是否`myString`只包含单个字符`H`。  
  
     [!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>在对通配符字符的字符串表达式中的字符进行匹配  
  
-   将问号 (`?`) 模式字符串中。 此位置中的任何有效字符，可以成功匹配。  
  
     下面的示例测试是否`myString`包含单个字符`W`跟两个字符的任何值。  
  
     [!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>针对列表的字符的字符串表达式中的字符进行匹配  
  
-   将括号放 (`[ ]`) 在模式字符串，并放置的字符列表括号内。 不要用逗号或任何其他分隔符分隔字符。 在列表中的任何单个字符，可以成功匹配。  
  
     下面的示例测试是否`myString`包含跟一个字符的任意有效字符`A`， `C`，或`E`。  
  
     [!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]  
  
     请注意，此匹配区分大小写。  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>针对一系列字符的字符串表达式中的字符进行匹配  
  
-   将括号放 (`[ ]`) 在模式字符串中，并将最低和最高的字符范围中放入括号内，由连字符分隔 (`–`)。 在范围内的任何单个字符，可以成功匹配。  
  
     下面的示例测试是否`myString`包含的字符`num`正好有一个字符后跟`i`， `j`， `k`， `l`， `m`，或`n`。  
  
     [!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]  
  
     请注意，此匹配区分大小写。  
  
## <a name="matching-empty-strings"></a>匹配空字符串  
 `Like` 将序列`[]`为零长度字符串 (`""`)。 可以使用`[]`来测试是否将整个字符串表达式为空，但不能使用它来测试是否为空的字符串表达式中的特定位置。 如果空位置选项之一需要测试对于您可以使用`Like`不止一次。  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>针对列表的字符或任何字符的字符串表达式中的字符进行匹配  
  
1.  调用`Like`两次在同一个运算符的字符串表达式，并使用连接的两个调用[或运算符](../../../../visual-basic/language-reference/operators/or-operator.md)或[OrElse 运算符](../../../../visual-basic/language-reference/operators/orelse-operator.md)。  
  
2.  在模式字符串中第一个`Like`子句，包括字符列表中，用方括号括起来 (`[ ]`)。  
  
3.  在模式字符串中第二个`Like`子句中，不要将放在任何字符的位置有问题。  
  
     下面的示例测试的七位数电话号码`phoneNum`为 3 个数字后, 跟一个空格、 连字符 (`–`)，一段 (`.`)，或没有字符后, 跟 4 个数字。  
  
     [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]  
  
## <a name="see-also"></a>请参阅

- [比较运算符](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [运算符和表达式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Like 运算符](../../../../visual-basic/language-reference/operators/like-operator.md)
- [String 数据类型](../../../../visual-basic/language-reference/data-types/string-data-type.md)
