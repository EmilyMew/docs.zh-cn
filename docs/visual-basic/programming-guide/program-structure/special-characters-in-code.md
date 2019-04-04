---
title: 代码中的特殊字符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: 65fcd10521742e287c7934080b3352a06668df7a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835552"
---
# <a name="special-characters-in-code-visual-basic"></a>代码中的特殊字符 (Visual Basic)
有时您必须在代码中，即，不是字母或数字的字符使用特殊字符。 标点和 Visual Basic 字符集中的特殊字符各有其用途，从组织程序文本到定义编译器或已编译的程序执行的任务。 它们不指定要执行的操作。  
  
## <a name="parentheses"></a>括号  
 使用括号时定义一个过程，如`Sub`或`Function`。 必须将所有过程自变量列表都括在括号中。 你还使用括号将变量或参数放到逻辑组，尤其是重写中的复杂表达式的运算符优先级的默认顺序。 下面的示例阐释了这一点。  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 按照上面的代码的值执行`d`8.225 和的值是`e`为 3。 计算`d`使用的默认优先级`/`转移`+`，等效于`d = b + (c / a)`。 中的计算的括号`e`重写默认的优先级。  
  
## <a name="separators"></a>分隔符  
 分隔符执行其名称所示： 分隔各部分的代码。 在 Visual Basic 中，分隔符为冒号 (`:`)。 当你想要包括在单个行而不是单独的行上的多个语句时，请使用分隔符。 这可节省空间并提高你的代码的可读性。 下面的示例演示三个由冒号分隔的语句。  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 有关详细信息，请参阅[如何：拆分和合并代码中的语句](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。  
  
 冒号 (`:`) 字符也用于标识语句标签。 有关详细信息，请参阅[如何：标记语句](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)。  
  
## <a name="concatenation"></a>串联  
 使用`&`运算符*串联*，或将字符串链接在一起。 请将其与混淆`+`运算符，将数值相加。 如果使用`+`运算符来串联时对数字值，您可以获得不正确的结果。 下面的示例演示这一操作。  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 按照上面的代码的值执行`resultA`21.01 和的值是`resultB`为"10.0111"。  
  
## <a name="member-access-operators"></a>成员访问运算符  
 若要访问类型的成员，请使用句点 (`.`) 或感叹号 (`!`) 之间的类型名称和成员名称的运算符。  
  
### <a name="dot--operator"></a>点 （.）运算符  
 使用`.`运算符是成员访问运算符作为类、 结构、 接口或枚举。 成员可以是字段、 属性、 事件或方法。 下面的示例阐释了这一点。  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>惊叹号 （！）运算符  
 使用`!`运算符仅在类或接口上的作为字典访问运算符。 类或接口必须具有默认属性接受单个`String`参数。 紧随`!`运算符将成为传递给字符串形式的默认属性的参数值。 下面的示例演示这一操作。  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 三个输出行`MsgBox`的值显示所有`32856`。 第一行使用传统的访问权限属性`index`，第二个利用了这一事实，`index`是类的默认属性`hasDefault`，和第三个使用字典访问权限类。  
  
 请注意，第二个操作数`!`运算符必须是有效的 Visual Basic 标识符不括在双引号内 (`" "`)。 换而言之，不能使用字符串文字或字符串变量。 以下的最后一个更改的行`MsgBox`调用将生成一个错误，因为`"X"`是文字括住的字符串。  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  对默认集合的引用必须为显式。 具体而言，不能使用`!`运算符的后期绑定变量。  
  
 `!`字符也用作`Single`键入字符。  
  
## <a name="see-also"></a>请参阅

- [程序结构和代码约定](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [类型字符](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
