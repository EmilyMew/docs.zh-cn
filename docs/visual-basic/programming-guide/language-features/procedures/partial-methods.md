---
title: 分部方法 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: 765a667f18340c53909c3ff1e9fcc5f2ffc0f9bc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837463"
---
# <a name="partial-methods-visual-basic"></a>分部方法 (Visual Basic)
分部方法使开发人员能够将自定义逻辑插入到代码。 通常情况下，代码是类的一个设计器生成的一部分。 分部方法中创建的代码生成器的分部类定义和它们通常用于提供的内容已更改的通知。 它们使开发人员指定自定义行为响应更改。  
  
 代码生成器的设计器定义仅在方法签名和对方法的一个或多个调用。 如果用户想要自定义生成的代码的行为，开发人员然后可以提供方法的实现。 时未不提供任何实现，对方法的调用将删除由编译器，从而导致任何额外的性能开销。  
  
## <a name="declaration"></a>声明  
 生成的代码的分部方法定义标记上来将关键字`Partial`签名行的开头。  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 定义必须满足以下条件：  
  
-   该方法必须是`Sub`，而不`Function`。  
  
-   方法的主体必须保留为空。  
  
-   访问修饰符必须`Private`。  
  
## <a name="implementation"></a>实现  
 实现主要包含分部方法的正文中填充。 实现通常是在单独的分部类定义中，并由一名开发人员想要扩展生成的代码编写。  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 前面的示例重复在声明中的签名完全正确，但可能变体。 具体而言，其他可以添加修饰符，如`Overloads`或`Overrides`。 只有一个`Overrides`允许使用修饰符。 有关方法的修饰符的详细信息，请参阅[Sub 语句](../../../../visual-basic/language-reference/statements/sub-statement.md)。  
  
## <a name="use"></a>使用  
 调用任何其他方式调用的分部方法`Sub`过程。 如果已实现方法，计算自变量和执行方法的主体。 但请记住，实现分部方法是可选的。 如果未实现方法，则调用不起任何作用，并且无法计算的表达式作为参数传递给该方法。  
  
## <a name="example"></a>示例  
 在文件中名，定义`Product`类具有`Quantity`属性。  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 在文件中名，提供的实现`QuantityChanged`。  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 最后，在项目的 Main 方法中，声明`Product`实例，并提供一个初始值及其`Quantity`属性。  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 应出现一个消息框将显示此消息：  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>请参阅

- [Sub 语句](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Sub 过程](./sub-procedures.md)
- [可选参数](./optional-parameters.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [LINQ to SQL 中的代码生成](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [通过使用分部方法添加业务逻辑](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
