---
title: Implements 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 1f0c6b052ead303e0b43465dac2067422abc4ef8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818861"
---
# <a name="implements-statement"></a>Implements 语句
指定一个或多个接口，或必须在类中实现的接口成员或结构定义中的出现。  
  
## <a name="syntax"></a>语法  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>部件  
 `interfacename`  
 必需。 一个其属性、 过程和事件是由类或结构中的相应成员来实现的接口。  
  
 `interfacemember`  
 必需。 正在实现的接口的成员。  
  
## <a name="remarks"></a>备注  
 接口是集合接口封装的原型表示的成员 （属性、 过程和事件）。 接口包含仅成员; 的声明类和结构实现这些成员。 有关详细信息，请参阅[接口](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。  
  
 `Implements`语句必须紧跟`Class`或`Structure`语句。  
  
 当实现接口时，必须实现该接口中声明的所有成员。 省略任何成员被视为是语法错误。 若要实现单个成员，则指定[实现](../../../visual-basic/language-reference/statements/implements-clause.md)关键字 (即独立于`Implements`语句) 中的类或结构的成员的声明时。 有关详细信息，请参阅[接口](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。  
  
 类可以使用[专用](../../../visual-basic/language-reference/modifiers/private.md)了仅通过强制转换到一个变量中的实现类实例声明为接口的类型的可访问的属性和过程，但这些成员实现。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`Implements`语句来实现的接口成员。 它定义一个接口，名为`ICustomerInfo`与事件、 属性和过程。 类`customerInfo`实现在接口中定义的所有成员。  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 请注意，该类`customerInfo`使用`Implements`单独的源文件的代码行以指示该类实现的所有成员上的语句`ICustomerInfo`接口。 然后，在类中的每个成员使用`Implements`关键字作为其成员声明，以指示它实现该接口成员的一部分。  
  
## <a name="example"></a>示例  
 以下两个过程演示如何使用在前面的示例实现的接口。 若要测试实现，请将这些过程添加到项目中并调用`testImplements`过程。  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>请参阅

- [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)
- [Interface 语句](../../../visual-basic/language-reference/statements/interface-statement.md)
- [接口](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
