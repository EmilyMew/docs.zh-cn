---
title: Property 语句 (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 7b2d388cbcd1995178adf4102520ecaa1c9b1889
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814173"
---
# <a name="property-statement"></a>Property Statement
声明的属性，以及用来存储和检索属性的值的属性过程的名称。  
  
## <a name="syntax"></a>语法  
  
```vb  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]  
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
    [ <attributelist> ] [ accessmodifier ] Get  
        [ statements ]  
    End Get  
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )  
        [ statements ]  
    End Set  
End Property  
- or -  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]   
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
```  
  
## <a name="parts"></a>部件  
  
-   `attributelist`  
  
     可选。 将应用于此属性的属性的列表或`Get`或`Set`过程。 请参阅[属性列表](../../../visual-basic/language-reference/statements/attribute-list.md)。  
  
-   `Default`  
  
     可选。 指定此属性是类或结构在其定义的默认属性。 默认属性必须接受参数并可以设置和检索而无需指定属性名称。 如果声明属性作为`Default`，不能使用`Private`属性中或在属性过程。  
  
-   `accessmodifier`  
  
     在上可选`Property`语句和上最多`Get`和`Set`语句。 可以是以下各项之一：  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Protected Friend](../../language-reference/modifiers/protected-friend.md) 

    - [Private Protected](../../language-reference/modifiers/private-protected.md)
  
     请参阅 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
-   `propertymodifiers`  
  
     可选。 可以是以下各项之一：  
  
    -   [重载](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     可选。 请参阅[共享](../../../visual-basic/language-reference/modifiers/shared.md)。  
  
-   `Shadows`  
  
     可选。 请参阅[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。  
  
-   `ReadOnly`  
  
     可选。 请参阅[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
-   `WriteOnly`  
  
     可选。 请参阅[WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)。  
  
-   `Iterator`  
  
     可选。 请参阅[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)。  
  
-   `name`  
  
     必需。 属性的名称。 请参阅 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
-   `parameterlist`  
  
     可选。 表示此属性的参数和可能具有的其他参数的本地变量名称的列表`Set`过程。 请参阅[参数列表](../../../visual-basic/language-reference/statements/parameter-list.md)。  
  
-   `returntype`  
  
     需要`Option Strict`是`On`。 返回此属性的值的数据类型。  
  
-   `Implements`  
  
     可选。 指示此属性实现一个或多个属性，此属性的包含类或结构实现接口中定义每个。 请参阅[实现语句](../../../visual-basic/language-reference/statements/implements-statement.md)。  
  
-   `implementslist`  
  
     如果提供 `Implements`，则是必需的。 正在实现的属性的列表。  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     每个 `implementedproperty` 都具有以下语法和部件：  
  
     `interface.definedname`  
  
    |部件|描述|  
    |---|---|  
    |`interface`|必需。 实现此属性的接口的名称的包含类或结构。|  
    |`definedname`|必需。 所依据的属性定义中的名称`interface`。|  
  
-   `Get`  
  
     可选。 需要该属性标记为`WriteOnly`。 启动`Get`用于返回属性的值的属性过程。  
  
-   `statements`  
  
     可选。 要在中运行的语句块`Get`或`Set`过程。  
  
-   `End Get`  
  
     终止`Get`属性过程。  
  
-   `Set`  
  
     可选。 需要该属性标记为`ReadOnly`。 启动`Set`用于存储属性的值的属性过程。  
  
-   `End Set`  
  
     终止`Set`属性过程。  
  
-   `End Property`  
  
     终止此属性的定义。  
  
## <a name="remarks"></a>备注  
 `Property`语句引入属性声明。 属性可以具有`Get`过程 （只读），`Set`过程 （只写） 或这两个 （读-写）。 可以省略`Get`和`Set`过程时使用自动实现的属性。 有关详细信息，请参阅[自动实现的属性](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)。  
  
 可以使用`Property`仅在类级别。 这意味着*声明上下文*属性必须是类、 结构、 模块或接口，并且不能为源文件、 命名空间、 过程或块。 有关详细信息，请参阅[声明上下文和默认访问级别](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 默认情况下，属性使用公共访问权限。 可以调整使用访问修饰符的属性的访问级别`Property`语句，并且您可以选择性地调整其限制性更强的访问级别的属性过程之一。  
  
 Visual Basic 将传递到参数`Set`属性分配期间的过程。 如果未提供的参数`Set`，在集成的开发环境 (IDE) 使用名为的隐式参数`value`。 此参数包含要分配给属性的值。 通常将此值存储在专用本地变量并将其返回每当`Get`调用过程。  
  
## <a name="rules"></a>规则  
  
-   **混合的访问级别。** 如果你正在定义的读-写属性，您可以选择指定不同的访问级别为`Get`或`Set`过程，但不可同时使用两者。 如果执行此操作时，过程访问级别必须比属性的访问级别限制性更强。 例如，如果属性声明`Friend`，可以声明`Set`过程`Private`，但不是`Public`。  
  
     如果您要定义`ReadOnly`或`WriteOnly`属性中，单个属性过程 (`Get`或`Set`分别) 表示所有属性。 因为这会设置该属性的两个访问级别，您無法宣告此类过程中，不同的访问级别。  
  
-   **返回类型。** `Property`语句可以声明其返回的值的数据类型。 您可以指定任何数据类型或枚举、 结构、 类或接口的名称。  
  
     如果未指定`returntype`，该属性返回`Object`。  
  
-   **实现。** 如果此属性使用`Implements`关键字、 包含类或结构必须具有`Implements`紧随其`Class`或`Structure`语句。 `Implements`语句必须包含每个接口中指定`implementslist`。 但是，通过该接口定义的名称`Property`(在`definedname`) 不一定要与此属性的名称相同 (在`name`)。  
  
## <a name="behavior"></a>行为  
  
-   **从属性过程中返回。** 当`Get`或`Set`过程返回到调用代码时，继续执行的语句之后调用它的语句。  
  
     `Exit Property`和`Return`语句从属性过程会导致立即退出。 任意数量的`Exit Property`并`Return`语句可以在过程中，任何位置出现，并且可以混合`Exit Property`和`Return`语句。  
  
-   **返回值。** 若要返回的值`Get`过程中，可以将值分配给属性名称或将其包含在`Return`语句。 下面的示例将返回值分配给属性名称`quoteForTheDay`，然后使用`Exit Property`语句返回。  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     如果您使用`Exit Property`而不将分配到的值`name`，则`Get`过程将返回属性的数据类型的默认值。  
  
     `Return`语句在同一时间将分配`Get`过程返回值，并退出该过程。 以下示例演示了此。  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>示例  
 下面的示例声明一个类中的属性。  
  
 [!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]  
  
## <a name="see-also"></a>请参阅

- [自动实现的属性](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [对象和类](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Get 语句](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set 语句](../../../visual-basic/language-reference/statements/set-statement.md)
- [参数列表](../../../visual-basic/language-reference/statements/parameter-list.md)
- [默认](../../../visual-basic/language-reference/modifiers/default.md)
