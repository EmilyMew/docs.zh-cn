---
title: Implements 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: 05de1d9f8966c17d84deba34f27819cce4aff3fe
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832614"
---
# <a name="implements-clause-visual-basic"></a>Implements 子句 (Visual Basic)
指示类或结构成员提供在接口中定义的成员的实现。  
  
## <a name="remarks"></a>备注  
`Implements`关键字不是与相同[Implements 语句](../../../visual-basic/language-reference/statements/implements-statement.md)。 您使用`Implements`语句指定的类或结构实现一个或多个接口，然后为每个成员使用`Implements`关键字来指定哪个接口和哪个成员实现。

如果类或结构实现一个接口，它必须包括`Implements`语句之后立即[Class 语句](../../../visual-basic/language-reference/statements/class-statement.md)或[Structure 语句](../../../visual-basic/language-reference/statements/structure-statement.md)，并且它必须实现的所有成员定义由接口。

## <a name="reimplementation"></a>重新实现  
在派生类中，可以重新实现接口成员的已实现的基类。 这是不同于重写基类成员在以下方面：

- 基类成员不需要进行[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)来重新实现。
- 您可以重新实现具有不同名称的成员。

`Implements`关键字可以在以下上下文中使用：
- [Event 语句](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>请参阅

- [Implements 语句](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interface 语句](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Class 语句](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure 语句](../../../visual-basic/language-reference/statements/structure-statement.md)
