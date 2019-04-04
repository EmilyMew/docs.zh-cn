---
title: 类型提升 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: f7ac6bfb944da8bd50e035ba97b2b513176dc661
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838867"
---
# <a name="type-promotion-visual-basic"></a>类型提升 (Visual Basic)
声明模块中的编程元素时，Visual Basic 会将其范围到包含该模块的命名空间的提升。 这称为*类型提升*。  
  
 下面的示例演示一个模块的主干定义和该模块的两个成员。  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 内`projModule`编程中，在模块级别声明的元素将被提升到`projNamespace`。 在前面的示例中，`basicEnum`并`innerClass`进行升级，但`numberSub`无效，因为不能在模块级别声明。  
  
## <a name="effect-of-type-promotion"></a>类型提升的结果  
 类型提升的效果是限定字符串不需要包含模块名称。 下面的示例调用两个过程在前面的示例。  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 在前面的示例中，第一次调用使用完全限定字符串。 但是，这是不必要因为类型提升。 第二个调用也访问该模块的成员而不包括`projModule`限定字符串中。  
  
## <a name="defeat-of-type-promotion"></a>类型提升失效  
 如果命名空间已有一个同名成员模块成员，类型提升则会为该模块成员失效。 下面的示例显示了枚举和相同的命名空间内的模块的主干定义。  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 在前面的示例中，Visual Basic 不能将类提升`abc`到`thisNameSpace`因为已存在具有相同的名称在命名空间级别的枚举。 访问`abcSub`，必须使用完全限定字符串`thisNamespace.thisModule.abc.abcSub`。 但是，类`xyz`仍会提升，并且可以访问`xyzSub`使用较短的限定字符串`thisNamespace.xyz.xyzSub`。  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>分部类型的类型提升的失效  
 如果类或结构在模块内的使用[分部](../../../../visual-basic/language-reference/modifiers/partial.md)关键字，类型提升会自动失效该类或结构，指示是否在命名空间不包含具有相同名称的成员。 该模块中的其他元素都仍可进行类型提升。  
  
 **后果。** 意外的结果，甚至编译器错误，则可能会导致失败的部分定义的类型提升。 下面的示例演示主干分部定义的类，其中之一是在模块内。  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 在前面的示例中，开发人员可能希望编译器要合并的两个分部定义`sampleClass`。 但是，编译器不考虑分部定义中的促销`sampleModule`。 因此，它会尝试编译两个单独且完全不同的类、 命名`sampleClass`但具有不同限定路径。  
  
 仅当其完全限定的路径相同时，编译器才将合并分部定义。  
  
## <a name="recommendations"></a>建议  
 下面的建议提供良好编程习惯。  
  
-   **唯一的名称。** 在必须对编程元素的命名的完全控制，请始终是最好的场合使用唯一的名称。 相同的名称需要额外的限定，并且可以使代码难以阅读。 它们还可能会导致细微错误和意外的结果。  
  
-   **完全限定。** 当你使用模块和相同的命名空间中的其他元素时，最安全的方法是始终使用完全限定的所有编程元素。 如果类型提升大大降低模块成员，并且不完全限定的成员，可能会无意中访问不同的编程元素。  
  
## <a name="see-also"></a>请参阅

- [Module 语句](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Namespace 语句](../../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [在 Visual Basic 中的作用域](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [如何：控制变量的作用域](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [对已声明元素的引用](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
