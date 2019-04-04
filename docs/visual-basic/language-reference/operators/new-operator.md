---
title: New 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: 630b0c48def77449f426b287a26f95af7cfb930e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837686"
---
# <a name="new-operator-visual-basic"></a>New 运算符 (Visual Basic)
引入了`New`子句，以创建新的对象实例，指定类型参数的构造函数约束或标识`Sub`作为类构造函数的过程。  
  
## <a name="remarks"></a>备注  
 声明或赋值语句中`New`子句必须指定将从其创建实例定义的类。 这意味着类必须公开一个或多个构造函数的调用代码可以访问。  
  
 可以使用`New`声明语句或赋值语句中的子句。 该语句在运行时将调用相应的构造函数的指定的类，并传入具有提供的所有参数。 下面的示例演示这通过创建的实例`Customer`类具有两个构造函数，一个不带参数，一个采用字符串参数。  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 由于数组是类，`New`可以创建一个新数组实例，如以下示例所示。  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 公共语言运行时 (CLR) 会引发<xref:System.OutOfMemoryException>错误是否存在内存不足，无法创建新实例。  
  
> [!NOTE]
>  `New`关键字还用于在类型形参列表中指定所提供的类型必须公开一个可访问的无参数构造函数。 有关类型参数和约束的详细信息，请参阅[类型列表](../../../visual-basic/language-reference/statements/type-list.md)。  
  
 若要创建一个类的构造函数过程，请设置的名称`Sub`过程`New`关键字。 有关详细信息，请参阅[对象生存期：如何创建和销毁对象](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。  
  
 `New` 关键字可用于以下上下文中：  
  
 [Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>请参阅

- <xref:System.OutOfMemoryException>
- [关键字](../../../visual-basic/language-reference/keywords/index.md)
- [类型列表](../../../visual-basic/language-reference/statements/type-list.md)
- [Visual Basic 中的泛型类型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [对象生存期：如何创建和销毁对象](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
