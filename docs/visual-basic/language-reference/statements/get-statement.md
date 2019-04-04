---
title: Get 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: 245d2cc36abde76a8f8bd73bae5d7ede183d4d03
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840505"
---
# <a name="get-statement"></a>Get 语句
声明`Get`用于检索属性值的属性过程。  
  
## <a name="syntax"></a>语法  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`attributelist`|可选。 请参阅[属性列表](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|在最多一个的可选`Get`和`Set`中此属性的语句。 可以是以下各项之一：<br /><br /> -   [受保护](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [友元](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [专用](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 请参阅 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`statements`|可选。 运行时的一个或多个语句`Get`调用属性过程。|  
|`End Get`|必需。 终止的定义`Get`属性过程。|  
  
## <a name="remarks"></a>备注  
 每个属性必须具有`Get`属性过程除非该属性标记为`WriteOnly`。 `Get`过程用于返回属性的当前值。  
  
 Visual Basic 会自动调用属性的`Get`表达式请求属性的值时的过程。  
  
 属性声明的主体可以包含仅属性的`Get`并`Set`过程之间[Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)和`End Property`语句。 它不能存储这些过程之外的任何内容。 具体而言，它不能存储属性的当前值。 必须存储属性，超出此值，因为如果将其存储在属性过程之一，另一个属性过程不能访问它。 常用方法是存储中的值[专用](../../../visual-basic/language-reference/modifiers/private.md)变量声明为属性的级别相同。 必须定义`Get`它所应用于的属性内的过程。  
  
 `Get`过程默认为其包含的属性的访问级别，除非使用`accessmodifier`中`Get`语句。  
  
## <a name="rules"></a>规则  
  
-   **混合的访问级别。** 如果你正在定义的读-写属性，您可以选择指定不同的访问级别为`Get`或`Set`过程，但不可同时使用两者。 如果执行此操作时，过程访问级别必须比属性的访问级别限制性更强。 例如，如果属性声明`Friend`，可以声明`Get`过程`Private`，但不是`Public`。  
  
     如果您要定义`ReadOnly`属性，`Get`过程都表示整个属性。 不能声明不同的访问级别`Get`，因为这会设置属性的两个访问级别。  
  
-   **返回类型。** [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)可以声明其返回的值的数据类型。 `Get`过程会自动返回数据类型。 您可以指定任何数据类型或枚举、 结构、 类或接口的名称。  
  
     如果`Property`语句不指定`returntype`，该过程返回`Object`。  
  
## <a name="behavior"></a>行为  
  
-   **从过程中返回。** 当`Get`过程返回到调用代码，请求的属性值的语句中将继续执行。  
  
     `Get` 属性过程可以返回值使用[Return 语句](../../../visual-basic/language-reference/statements/return-statement.md)或者将返回值分配给属性名称。 详细信息，请参阅"返回值"中[Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)。  
  
     `Exit Property`和`Return`语句从属性过程会导致立即退出。 任意数量的`Exit Property`并`Return`语句可以在过程中，任何位置出现，并且可以混合`Exit Property`和`Return`语句。  
  
-   **返回值。** 若要返回的值`Get`过程中，可以将值分配给属性名称或将其包含在[Return 语句](../../../visual-basic/language-reference/statements/return-statement.md)。 `Return`语句将同时分配`Get`过程返回值，并退出该过程。  
  
     如果您使用`Exit Property`而不将值分配到的属性名`Get`过程将返回属性的数据类型的默认值。 详细信息，请参阅"返回值"中[Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)。  
  
     下面的示例演示两种方法的只读属性`quoteForTheDay`可保存在私有变量的值返回`quoteValue`。  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>示例  
 下面的示例使用`Get`语句返回的属性值。  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>请参阅

- [Set 语句](../../../visual-basic/language-reference/statements/set-statement.md)
- [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit 语句](../../../visual-basic/language-reference/statements/exit-statement.md)
- [对象和类](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [演练：定义类](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
