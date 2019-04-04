---
title: Structure 语句 (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
ms.openlocfilehash: ab446319a9e0ef295387d0d6768e813a158939c9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828341"
---
# <a name="structure-statement"></a>Structure 语句
声明结构的名称，并引入的变量、 属性、 事件和结构包含的过程的定义。  
  
## <a name="syntax"></a>语法  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _  
Structure name [ ( Of typelist ) ]  
    [ Implements interfacenames ]  
    [ datamemberdeclarations ]  
    [ methodmemberdeclarations ]  
End Structure  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`attributelist`|可选。 请参阅[属性列表](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|可选。 可以是以下各项之一：<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [受保护](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [友元](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [专用](../../../visual-basic/language-reference/modifiers/private.md)<br />- [受保护的友元](../../language-reference/modifiers/protected-friend.md)<br/>- [专用受保护](../../language-reference/modifiers/private-protected.md) <br /><br /> 请参阅 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|可选。 请参阅[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`Partial`|可选。 指示结构的分部定义。 请参阅[分部](../../../visual-basic/language-reference/modifiers/partial.md)。|  
|`name`|必需。 此结构的名称。 请参阅 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|可选。 指定这是一个泛型结构。|  
|`typelist`|如果在使用需要[的](../../../visual-basic/language-reference/statements/of-clause.md)关键字。 此结构的类型参数的列表。 请参阅[类型列表](../../../visual-basic/language-reference/statements/type-list.md)。|  
|`Implements`|可选。 指示此结构实现一个或多个接口的成员。 请参阅[实现语句](../../../visual-basic/language-reference/statements/implements-statement.md)。|  
|`interfacenames`|如果在使用需要`Implements`语句。 此结构实现接口的名称。|  
|`datamemberdeclarations`|必需。 零个或多`Const`， `Dim`， `Enum`，或`Event`语句声明*数据成员*的结构。|  
|`methodmemberdeclarations`|可选。 零个或多个声明`Function`， `Operator`， `Property`，或`Sub`过程，它充当*方法成员*的结构。|  
|`End Structure`|必需。 终止`Structure`定义。|  
  
## <a name="remarks"></a>备注  
 `Structure`语句定义可以自定义的复合值类型。 一个*结构*是用户定义类型 (UDT) 的以前版本的 Visual Basic 的泛化。 有关详细信息，请参阅[结构](../../../visual-basic/programming-guide/language-features/data-types/structures.md)。  
  
 结构支持很多与类相同的功能。 例如，结构可以具有属性和过程，它们可以实现接口，并也可以具有参数化构造函数。 但是，有结构与类之间继承、 声明和使用情况等方面的明显差异。 此外，类是引用类型和结构是值类型。 有关详细信息，请参阅[结构和类](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)。  
  
 可以使用`Structure`只能在命名空间或模块级别。 这意味着*声明上下文*结构必须是源文件、 命名空间、 类、 结构、 模块或接口，并且不能为过程或块。 有关详细信息，请参阅[声明上下文和默认访问级别](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 结构默认为[友元](../../../visual-basic/language-reference/modifiers/friend.md)访问。 您可以调整其访问级别和访问修饰符。 有关详细信息，请参阅[访问 Visual Basic 中的级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="rules"></a>规则  
  
-   **嵌套。** 您可以定义一个在另一个结构。 外部结构称为*包含结构*，并调用的内部结构*嵌套结构*。 但是，您不能通过包含结构访问嵌套的结构的成员。 相反，必须声明嵌套的结构的数据类型的变量。  
  
-   **成员声明。** 必须声明一个结构的每个成员。 结构成员不能[受保护](../../../visual-basic/language-reference/modifiers/protected.md)或`Protected Friend`由于执行任何操作可以继承自一个结构。 结构本身，但是，可以是`Protected`或`Protected Friend`。  
  
     您可以在结构中声明零个以上的非共享变量或非共享、非自定义的事件。 您不能具有常量、 属性和过程，即使其中一些非共享。  
  
-   **初始化。** 无法初始化结构作为其声明的一部分的任何非共享的数据成员的值。 必须通过在结构上的参数化构造函数初始化此类数据成员或创建该结构的实例后为成员分配一个值。  
  
-   **继承。** 而不从任何类型继承结构，不能<xref:System.ValueType>，从其继承的所有结构。 具体而言，不能从另一个继承一个结构。  
  
     不能使用[Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)在结构定义中，甚至指定<xref:System.ValueType>。  
  
-   **实现。** 如果使用结构[Implements 语句](../../../visual-basic/language-reference/statements/implements-statement.md)，则必须实现定义中指定的每个接口的每个成员`interfacenames`。  
  
-   **默认属性。** 一种结构可以指定最多一个属性作为其*默认属性*，并使用[默认](../../../visual-basic/language-reference/modifiers/default.md)修饰符。 有关详细信息，请参阅[默认](../../../visual-basic/language-reference/modifiers/default.md)。  
  
## <a name="behavior"></a>行为  
  
-   **访问级别。** 结构中，可以声明具有其自己的访问级别的每个成员。 所有结构成员都默认为[公共](../../../visual-basic/language-reference/modifiers/public.md)访问。 请注意，是否结构本身的更受限制的访问级别，这会自动限制访问其成员，即使您调整和访问修饰符及其访问级别。  
  
-   **作用域。** 结构是在整个其包含的命名空间、 类、 结构或模块范围内。  
  
     每个结构成员的作用域是整个结构。  
  
-   **生存期。** 一种结构本身没有生存期。 相反，该结构的每个实例都独立于所有其他实例的生存期。  
  
     实例的生存期开始时创建该[New 运算符](../../../visual-basic/language-reference/operators/new-operator.md)子句。 包含的变量的生存期结束时结束。  
  
     不能扩展结构实例的生存期。 模块被提供了近似的静态结构功能。 有关详细信息，请参阅[Module 语句](../../../visual-basic/language-reference/statements/module-statement.md)。  
  
     结构成员将具体取决于如何以及在何处声明它们的生存期。 详细信息，请参阅"生存期"中[Class 语句](../../../visual-basic/language-reference/statements/class-statement.md)。  
  
-   **限定。** 结构外的代码必须限定成员的名称与该结构的名称。  
  
     如果嵌套结构内的代码发出到编程元素中的非限定的引用，Visual Basic 搜索元素首先在嵌套结构中，然后在其包含结构等到最外面的包含元素。 有关详细信息，请参阅 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
-   **内存占用情况。** 与所有复合数据类型，不能安全地通过同时添加其成员的名义存储分配计算结构的内存总消耗。 此外，不能安全地假定已在内存中存储的顺序声明的顺序相同。 如果需要控制结构的存储布局，你可以申请<xref:System.Runtime.InteropServices.StructLayoutAttribute>属性为`Structure`语句。  
  
## <a name="example"></a>示例  
 下面的示例使用`Structure`语句来为某位员工定义一组相关数据。 它演示如何使用`Public`， `Friend`，和`Private`成员以反映数据项目的敏感度。 它还将显示过程、 属性和事件成员。  
  
 [!code-vb[VbVbalrStatements#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>请参阅

- [Class 语句](../../../visual-basic/language-reference/statements/class-statement.md)
- [Interface 语句](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Module 语句](../../../visual-basic/language-reference/statements/module-statement.md)
- [Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Const 语句](../../../visual-basic/language-reference/statements/const-statement.md)
- [Enum 语句](../../../visual-basic/language-reference/statements/enum-statement.md)
- [Event 语句](../../../visual-basic/language-reference/statements/event-statement.md)
- [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)
- [结构和类](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
