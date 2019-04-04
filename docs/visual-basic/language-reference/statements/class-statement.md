---
title: Class 语句 (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Class
helpviewer_keywords:
- class modules
- Class statement [Visual Basic]
- classes [Visual Basic], fields
- fields [Visual Basic], of classes
- class types [Visual Basic], class statements
- classes [Visual Basic], creating
- classes [Visual Basic], data members
- data members [Visual Basic], of classes
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
ms.openlocfilehash: 68401571645d77a41b827c13b3cfc3674076e218
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824567"
---
# <a name="class-statement-visual-basic"></a>Class 语句 (Visual Basic)
声明类的名称，并引入的变量、 属性、 事件和类构成的过程的定义。  
  
## <a name="syntax"></a>语法  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`attributelist`|可选。 请参阅[属性列表](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|可选。 可以是以下各项之一：<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [受保护](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [友元](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [专用](../../../visual-basic/language-reference/modifiers/private.md)<br />-   [受保护的友元](../../language-reference/modifiers/protected-friend.md)<br />- [专用受保护](../../language-reference/modifiers/private-protected.md)<br/><br/> 请参阅 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|可选。 请参阅[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`MustInherit`|可选。 请参阅[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)。|  
|`NotInheritable`|可选。 请参阅[NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)。|  
|`Partial`|可选。 指示类的分部定义。 请参阅[分部](../../../visual-basic/language-reference/modifiers/partial.md)。|  
|`name`|必需。 此类的名称。 请参阅 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|可选。 指定这是一个泛型类。|  
|`typelist`|如果在使用需要[的](../../../visual-basic/language-reference/statements/of-clause.md)关键字。 此类的类型参数的列表。 请参阅[类型列表](../../../visual-basic/language-reference/statements/type-list.md)。|  
|`Inherits`|可选。 指示此类继承的另一个类成员。 请参阅[Inherits 语句](../../../visual-basic/language-reference/statements/inherits-statement.md)。|  
|`classname`|如果在使用需要`Inherits`语句。 此类派生的类的名称。|  
|`Implements`|可选。 指示此类实现一个或多个接口的成员。 请参阅[实现语句](../../../visual-basic/language-reference/statements/implements-statement.md)。|  
|`interfacenames`|如果在使用需要`Implements`语句。 此类实现的接口的名称。|  
|`statements`|可选。 定义此类的成员的语句。|  
|`End Class`|必需。 终止`Class`定义。|  
  
## <a name="remarks"></a>备注  
 一个`Class`语句定义新的数据类型。 一个*类*是面向对象的编程 (OOP) 的基本构建块。 有关详细信息，请参阅[对象和类](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
 可以使用`Class`只能在命名空间或模块级别。 这意味着*声明上下文*类必须是源文件、 命名空间、 类、 结构、 模块或接口，并且不能为过程或块。 有关详细信息，请参阅[声明上下文和默认访问级别](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 类的每个实例都独立于所有其他实例的生存期。 此生存期开始时创建该[New 运算符](../../../visual-basic/language-reference/operators/new-operator.md)子句或由函数如<xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>。 指向实例的所有变量已都设置为时结束[Nothing](../../../visual-basic/language-reference/nothing.md)或为其他类的实例。  
  
 类默认为[友元](../../../visual-basic/language-reference/modifiers/friend.md)访问。 您可以调整其访问级别和访问修饰符。 有关详细信息，请参阅[访问 Visual Basic 中的级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="rules"></a>规则  
  
-   **嵌套。** 您可以定义一个类在另一个。 外部的类称为*包含类*，内部的类称为*嵌套类*。  
  
-   **继承。** 如果类使用[Inherits 语句](../../../visual-basic/language-reference/statements/inherits-statement.md)，可以指定只有一个基类或接口。 类不能从多个元素继承。  
  
     类不能从具有限制性更强的访问级别的另一个类继承。 例如，`Public`类不能继承`Friend`类。  
  
     类不能从嵌套在它的类继承。  
  
-   **实现。** 如果类使用[Implements 语句](../../../visual-basic/language-reference/statements/implements-statement.md)，则必须实现定义中指定的每个接口的每个成员`interfacenames`。 一种例外是重新实现的基类成员。 详细信息，请参阅"重新实现"中[实现](../../../visual-basic/language-reference/statements/implements-clause.md)。  
  
-   **默认属性。** 类可以指定最多一个属性作为其*默认属性*。 有关详细信息，请参阅[默认](../../../visual-basic/language-reference/modifiers/default.md)。  
  
## <a name="behavior"></a>行为  
  
-   **访问级别。** 在类中，可以声明具有其自己的访问级别的每个成员。 默认为类成员[公共](../../../visual-basic/language-reference/modifiers/public.md)访问，除变量和常量、 到哪些默认[专用](../../../visual-basic/language-reference/modifiers/private.md)访问。 当一个类具有比其成员之一的限制性更强的访问时，类访问权限级别优先。  
  
-   **作用域。** 类是在整个其包含的命名空间、 类、 结构或模块范围内。  
  
     每个类成员的作用域是整个类。  
  
     **生存期。** Visual Basic 不支持静态类。 在功能上等同的静态类提供的模块。 有关详细信息，请参阅[Module 语句](../../../visual-basic/language-reference/statements/module-statement.md)。  
  
     类成员具有具体取决于如何以及在何处声明它们的生存期。 有关详细信息，请参阅[在 Visual Basic 中的生存期](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)。  
  
-   **限定。** 在类外部的代码必须限定成员的名称与该类的名称。  
  
     如果在嵌套类的代码发出到编程元素中的非限定的引用，Visual Basic 搜索元素首先在嵌套类中，然后在其包含的类，等到最外面的包含元素。  
  
## <a name="classes-and-modules"></a>类和模块  
 这些元素具有许多相似之处，但有一些重要的差异。  
  
-   **术语。** 以前版本的 Visual Basic 识别两种类型的模块：*类模块*（.cls 文件） 和*标准模块*（.bas 文件）。 当前版本调用这些*类*并*模块*分别。  
  
-   **共享的成员。** 您可以控制是否在不共享类的成员或实例成员。  
  
-   **面向对象。** 类是面向对象的但不是模块。 可以创建类的一个或多个实例。 有关详细信息，请参阅[对象和类](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`Class`语句定义的类和几个成员。  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>请参阅

- [对象和类](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [结构和类](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Interface 语句](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Module 语句](../../../visual-basic/language-reference/statements/module-statement.md)
- [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)
- [对象生存期：如何创建和销毁对象](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Visual Basic 中的泛型类型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [如何：使用泛型类](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
