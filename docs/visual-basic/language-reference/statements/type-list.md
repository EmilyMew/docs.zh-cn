---
title: 类型列表 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: d071e59d94e51ca55167983d0ee3098bd5c7dd8f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843625"
---
# <a name="type-list-visual-basic"></a>类型列表 (Visual Basic)
指定*类型参数*有关*泛型*编程元素。 由逗号分隔多个参数。 下面是一个类型参数的语法。  
  
## <a name="syntax"></a>语法  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`genericmodifier`|可选。 可以仅在泛型接口和委托中使用。 您可以将类型声明协变通过使用[出](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)关键字或通过使用逆变[中](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)关键字。 请参阅 [协变和逆变](../../programming-guide/concepts/covariance-contravariance/index.md)。|  
|`typename`|必需。 类型参数的名称。 这是一个占位符，将替换为已定义的类型提供的相应类型参数。|  
|`constraintlist`|可选。 约束可以为提供的数据类型的要求列表`typename`。 如果有多个约束，则将它们括在大括号中 (`{ }`)，并用逗号分隔。 您必须引入的约束列表[作为](../../../visual-basic/language-reference/statements/as-clause.md)关键字。 您使用`As`仅一次，在列表的开头。|  
  
## <a name="remarks"></a>备注  
 每个泛型编程元素必须采用至少一个类型参数。 类型参数是特定类型的占位符 (*构造的元素*) 客户端代码在创建泛型类型的实例时指定。 可以定义一个泛型类、 结构、 接口、 过程或委托。  
  
 有关何时定义泛型类型的详细信息，请参阅[在 Visual Basic 中的泛型类型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。 类型参数名称的详细信息，请参阅[声明的元素名称](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## <a name="rules"></a>规则  
  
-   **括号。** 如果您提供类型参数列表，则必须将其括在括号中，并且必须引入与列表[的](../../../visual-basic/language-reference/statements/of-clause.md)关键字。 您使用`Of`仅一次，在列表的开头。  
  
-   **约束。** 一系列*约束*对类型参数可以包括以下各项的任意组合：  
  
    -   任意数量的接口。 此列表中，所提供的类型必须实现的每个接口。  
  
    -   最多一个类。 所提供的类型必须继承自该类的类。  
  
    -   `New` 关键字。 所提供的类型必须公开泛型类型可以访问的无参数构造函数。 这是限制由一个或多个接口的类型参数的情况下很有用。 实现接口的类型不一定是公开一个构造函数，并根据构造函数的访问级别，可能无法再对其进行访问的泛型类型中的代码。  
  
    -   任一`Class`关键字或`Structure`关键字。 `Class`关键字约束泛型类型形参以要求传递给它的任何类型参数是引用类型，例如字符串、 数组或委托，或从类创建对象。 `Structure`关键字约束泛型类型形参，以要求传递给它的任何类型参数是值类型，例如结构、 枚举或基本数据类型。 不能同时包括`Class`并`Structure`在同一个`constraintlist`。  
  
     所提供的类型必须满足每个要求中包括`constraintlist`。  
  
     在每个类型参数约束均独立于其他类型参数的约束。  
  
## <a name="behavior"></a>行为  
  
-   **编译时替换。** 从通用的编程元素创建构造的类型时，你提供每个类型参数定义的的类型。 Visual Basic 编译器就会替换该类型提供的每个匹配项`typename`泛型元素内。  
  
-   **不是存在的约束。** 如果不指定任何约束类型参数上的，你的代码仅限于运算和成员受[Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)为该类型形参。  
  
## <a name="example"></a>示例  
 下面的示例演示泛型字典类，包括将新项添加到字典中的主干函数的主干定义。  
  
 [!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]  
  
## <a name="example"></a>示例  
 因为`dictionary`是泛型类型，使用它的代码，可以创建多个对象，每个具有相同的功能，但却作用于不同的数据类型。 下面的示例演示创建的代码行`dictionary`对象使用`String`条目和`Integer`密钥。  
  
 [!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]  
  
## <a name="example"></a>示例  
 下面的示例演示由前面的示例生成等效的主干定义。  
  
 [!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>请参阅

- [Of](../../../visual-basic/language-reference/statements/of-clause.md)
- [New 运算符](../../../visual-basic/language-reference/operators/new-operator.md)
- [在 Visual Basic 中的访问级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Object 数据类型](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)
- [Structure 语句](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)
- [如何：使用泛型类](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [协变和逆变](../../programming-guide/concepts/covariance-contravariance/index.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
