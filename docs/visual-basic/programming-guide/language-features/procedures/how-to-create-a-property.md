---
title: 如何：创建一个属性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: 3e3f1168a983b2fa608cbadffba0531afef7c92b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816838"
---
# <a name="how-to-create-a-property-visual-basic"></a>如何：创建一个属性 (Visual Basic)
将属性定义之间`Property`语句和一个`End Property`语句。 在此定义中，定义`Get`过程中，`Set`过程中，或两者。 该属性的所有代码均位于这些过程中。  
  
 `Get`过程中检索该属性的值和`Set`过程存储一个值。 如果你想要具有读/写访问权限的属性，则必须定义这两个过程。 对于只读属性，只需定义`Get`，并只写属性，只需定义`Set`。  
  
### <a name="to-create-a-property"></a>若要创建属性  
  
1.  外部任何属性或过程，使用[Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)后, 跟`End Property`语句。  
  
2.  如果该属性会采用参数，请按照`Property`关键字的过程，然后在括号中的参数列表的名称。  
  
3.  括号后跟`As`子句来指定属性的值的数据类型。 必须指定即使对于只写属性的数据类型。  
  
4.  添加`Get`和`Set`过程，根据需要。 请参阅下面的说明。  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>若要创建用于检索属性值的获取过程  
  
1.  之间`Property`并`End Property`语句，编写[Get 语句](../../../../visual-basic/language-reference/statements/get-statement.md)后, 跟`End Get`语句。 不需要定义任何参数`Get`过程。  
  
2.  若要检索的属性值之间的代码语句放`Get`和`End Get`语句。 此代码还可以包括其他计算和数据操作，除了生成和返回属性的值。  
  
3.  使用`Return`语句可以返回到调用代码的属性的值。  
  
 您必须编写`Get`过程为读写属性以及只读属性。 无需定义`Get`只写属性的过程。  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>若要创建组过程，它将写入属性的值  
  
1.  之间`Property`并`End Property`语句，编写[Set 语句](../../../../visual-basic/language-reference/statements/set-statement.md)后, 跟`End Set`语句。  
  
2.  在`Set`语句，请按照`Set`关键字与在括号中的参数列表。 此参数列表必须包含通过调用代码传递的值至少为值参数。 此值参数的默认名称是`Value`，但是如果需要，可以使用不同的名称。 值参数必须具有相同的数据类型与属性本身。  
  
3.  将代码语句之间的属性中存储值`Set`和`End Set`语句。 此代码还可以包括其他计算和数据操作除了验证和存储属性的值。  
  
4.  使用值参数以接受由调用代码提供的值。 可以直接在赋值语句中，存储此值，也可以使用它在表达式中计算要存储的内部值。  
  
 您必须编写`Set`过程对于读写属性和只写属性。 无需定义`Set`只读属性的过程。  
  
## <a name="example"></a>示例  
 以下示例创建一个将完整的名称存储为两个构成的名称、 名字和姓氏的读/写属性。 当调用代码中读取`fullName`，则`Get`过程组合姓名的两个组成部分，并返回的完整名称。 当调用代码将分配新的完整名称，`Set`过程尝试将其分为两个构成的名称。 如果找不到空间，它将其存储所有为第一个名称。  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 下面的示例演示的属性过程的典型调用`fullName`。 第一次调用设置的属性值和第二个调用会检索它。  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [属性过程](./property-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [在 Visual Basic 中属性和变量之间的差异](./differences-between-properties-and-variables.md)
- [如何：声明具有混合的访问级别的属性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：调用 Property 过程](./how-to-call-a-property-procedure.md)
- [如何：声明并在 Visual Basic 中调用默认属性](./how-to-declare-and-call-a-default-property.md)
- [如何：在属性中放置值](./how-to-put-a-value-in-a-property.md)
- [如何：从属性获取一个值](./how-to-get-a-value-from-a-property.md)
