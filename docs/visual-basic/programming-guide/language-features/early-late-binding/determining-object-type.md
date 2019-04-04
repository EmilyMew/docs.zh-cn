---
title: 确定对象类型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 625ddb8fc153708a80e8cf475f48d595efbe4df2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842624"
---
# <a name="determining-object-type-visual-basic"></a>确定对象类型 (Visual Basic)
一般的对象变量 (也就是说，变量声明为`Object`) 可以包含来自任何类的对象。 使用类型的变量时`Object`，可能需要采取不同操作基于对象的类; 例如，某些对象可能的特定属性或方法不支持。 Visual Basic 提供两种方法来确定哪种类型的对象存储在一个对象变量：`TypeName`函数和`TypeOf...Is`运算符。  
  
## <a name="typename-and-typeofis"></a>类型名称和 TypeOf...是  
 `TypeName`函数返回一个字符串，并且是最佳选择，在需要时存储或显示类对象的名称，如下面的代码段中所示：  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 `TypeOf...Is`运算符是用于测试的对象类型的最佳选择，因为它是比等效的字符串比较使用更快`TypeName`。 使用下面的代码段`TypeOf...Is`内`If...Then...Else`语句：  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 此处需要注意的一点是因为。 `TypeOf...Is`运算符返回`True`如果属于特定类型或派生自特定类型的对象。 使用 Visual Basic 实现几乎所有内容涉及到对象，其中包括一些通常不被视为对象，如字符串和整数的元素。 这些对象派生自和继承方法从<xref:System.Object>。 当传递`Integer`和使用计算`Object`，则`TypeOf...Is`运算符将返回`True`。 下面的示例报告参数`InParam`既`Object`和`Integer`:  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 下面的示例使用这两个`TypeOf...Is`并`TypeName`来确定对象中传递给它的类型`Ctrl`参数。 `TestObject`过程调用`ShowType`与三种不同的控件。  
  
#### <a name="to-run-the-example"></a>运行示例  
  
1.  创建一个新的 Windows 应用程序项目并添加<xref:System.Windows.Forms.Button>控件，<xref:System.Windows.Forms.CheckBox>控件，和一个<xref:System.Windows.Forms.RadioButton>到窗体控件。  
  
2.  从你的窗体上的按钮，调用`TestObject`过程。  
  
3.  将以下代码添加到你的窗体：  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [使用字符串名调用属性或方法](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [Object 数据类型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [If...Then...Else 语句](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [String 数据类型](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Integer 数据类型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
