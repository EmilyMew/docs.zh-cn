---
title: Module 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: f546498e5282bcf58d07a06968bb4303e4e6d7b9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838139"
---
# <a name="module-statement"></a>Module 语句
声明模块的名称，并引入的变量、 属性、 事件和该模块包含的过程的定义。  
  
## <a name="syntax"></a>语法  
  
```vb 
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a>部件  
 `attributelist`  
 可选。 请参阅[属性列表](../../../visual-basic/language-reference/statements/attribute-list.md)。  
  
 `accessmodifier`  
 可选。 可以是以下各项之一：  
  
-   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 请参阅 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `name`  
 必需。 此模块的名称。 请参阅 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
 `statements`  
 可选。 定义变量、 属性、 事件、 过程和嵌套的类型，此模块的语句。  
  
 `End Module`  
 终止`Module`定义。  
  
## <a name="remarks"></a>备注  
 一个`Module`语句定义在整个命名空间中可用的引用类型。 一个*模块*(有时称为*标准模块*) 类似于类，但有一些重要的差别。 每个模块都有且只有一个实例，并不需要创建或分配给一个变量。 模块不支持继承或实现接口。 请注意，模块并不*类型*类或结构是在意义上，不能声明为具有模块的数据类型的编程元素。  
  
 可以使用`Module`仅在命名空间级别。 这意味着*声明上下文*供模块必须的源文件或命名空间，并且不能为类、 结构、 模块、 接口、 过程或块。 不能嵌套在另一个模块，或在任何类型的模块。 有关详细信息，请参阅[声明上下文和默认访问级别](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 模块具有相同的生存期为您的程序。 因为其成员是所有`Shared`，它们还具有相同的程序的生存期。  
  
 默认为模块[友元](../../../visual-basic/language-reference/modifiers/friend.md)访问。 您可以调整其访问级别和访问修饰符。 有关详细信息，请参阅[访问 Visual Basic 中的级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 模块的所有成员都都隐式`Shared`。  
  
## <a name="classes-and-modules"></a>类和模块  
 这些元素具有许多相似之处，但有一些重要的差异。  
  
-   **术语。** 以前版本的 Visual Basic 识别两种类型的模块：*类模块*（.cls 文件） 和*标准模块*（.bas 文件）。 当前版本调用这些*类*并*模块*分别。  
  
-   **共享的成员。** 您可以控制是否在不共享类的成员或实例成员。  
  
-   **面向对象。** 类是面向对象的但不是模块。 因此，只能将类可以为对象实例化。 有关详细信息，请参阅[对象和类](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
## <a name="rules"></a>规则  
  
-   **修饰符。** 所有模块成员都为隐式[共享](../../../visual-basic/language-reference/modifiers/shared.md)。 不能使用`Shared`关键字时声明一个成员，并且您不能更改任何成员的共享的状态。  
  
-   **继承。** 而不从任何类型继承一个模块，不能<xref:System.Object>，哪些所有模块从继承。 具体而言，不能从另一个继承一个模块。  
  
     不能使用[Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)在模块定义中，甚至指定<xref:System.Object>。  
  
-   **默认属性。** 您不能在模块中定义的任何默认属性。 有关详细信息，请参阅[默认](../../../visual-basic/language-reference/modifiers/default.md)。  
  
## <a name="behavior"></a>行为  
  
-   **访问级别。** 在模块中，可以声明具有其自己的访问级别的每个成员。 模块成员默认为[公共](../../../visual-basic/language-reference/modifiers/public.md)访问，除变量和常量、 到哪些默认[专用](../../../visual-basic/language-reference/modifiers/private.md)访问。 当模块具有比其成员之一的限制性更强的访问时，指定的模块的访问级别将优先。  
  
-   **作用域。** 模块是在整个命名空间范围内。  
  
     每个模块成员的作用域是整个模块。 请注意，所有成员都会都经受*类型提升*，这将导致它们提升到包含该模块的命名空间的范围。 有关详细信息，请参阅[类型提升](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)。  
  
-   **限定。** 您可以在项目中，有多个模块，而您可以声明具有两个或多个模块中具有相同名称的成员。 但是，如果引用是从外部该模块必须限定对此类成员具有适当的模块名称的任何引用。 有关详细信息，请参阅 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
## <a name="example"></a>示例  
 [!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]  
  
## <a name="see-also"></a>请参阅

- [Class 语句](../../../visual-basic/language-reference/statements/class-statement.md)
- [Namespace 语句](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Structure 语句](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Interface 语句](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)
- [类型提升](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
