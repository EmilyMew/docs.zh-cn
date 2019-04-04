---
title: 如何：调用 Property 过程 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 7b85239f80b4bfa87d1dbb1e3207e63d0cef7eeb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827206"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>如何：调用 Property 过程 (Visual Basic)
在属性中存储一个值，或检索其值由调用 property 过程。 访问属性访问的变量的相同方法。  
  
 该属性的`Set`过程存储一个值，并将其`Get`过程检索的值。 但是，不显式调用这些过程的名称。 就像将存储或检索变量的值使用赋值语句或表达式中的属性。 Visual Basic 可以对该属性的过程的调用。  
  
### <a name="to-call-a-propertys-get-procedure"></a>若要调用 property Get 过程  
  
1.  将使用变量名的相同方式在表达式中使用的属性名称。 可以使用属性可以在任意位置使用一个变量或常量。  
  
     或  
  
     使用属性名称之后等号 (`=`) 在赋值语句登录。  
  
     下面的示例读取的值<xref:Microsoft.VisualBasic.DateAndTime.Now%2A>属性外，隐式调用其`Get`过程。  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2.  如果该属性接受参数，请按照使用括号将参数列表括起来的属性名称。 如果没有任何自变量，可以选择性地省略括号。  
  
3.  将参数放在括号中，由逗号分隔参数列表中。 请确保提供的属性定义的相应参数的相同顺序中的自变量。  
  
 属性的值出现在中，只需为变量表达式或常数那样，或存储在变量或赋值语句左侧的属性。  
  
### <a name="to-call-a-propertys-set-procedure"></a>若要调用属性的设置过程  
  
1.  在赋值语句左侧使用属性名称。  
  
     下面的示例设置的值<xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>属性外，隐式调用`Set`过程。  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2.  如果该属性接受参数，请按照使用括号将参数列表括起来的属性名称。 如果没有任何自变量，可以选择性地省略括号。  
  
3.  将参数放在括号中，由逗号分隔参数列表中。 请确保提供的属性定义的相应参数的相同顺序中的自变量。  
  
 在属性中存储生成的赋值语句右侧的值。  
  
## <a name="see-also"></a>请参阅

- [属性过程](./property-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [Property 语句](../../../../visual-basic/language-reference/statements/property-statement.md)
- [在 Visual Basic 中属性和变量之间的差异](./differences-between-properties-and-variables.md)
- [如何：创建属性](./how-to-create-a-property.md)
- [如何：声明具有混合的访问级别的属性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：声明并在 Visual Basic 中调用默认属性](./how-to-declare-and-call-a-default-property.md)
- [如何：在属性中放置值](./how-to-put-a-value-in-a-property.md)
- [如何：从属性获取一个值](./how-to-get-a-value-from-a-property.md)
- [Get 语句](../../../../visual-basic/language-reference/statements/get-statement.md)
- [Set 语句](../../../../visual-basic/language-reference/statements/set-statement.md)
