---
title: 如何：获取一个值，从属性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 7dbc9d926ae937dd032c0c054bde440037ab9f0d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842910"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>如何：获取一个值，从属性 (Visual Basic)
通过将属性名称包含在表达式中检索属性的值。  
  
 该属性的`Get`过程中检索值，但并不按名称显式调用它。 您使用该属性，就像您将使用变量。 Visual Basic 可以对该属性的过程的调用。  
  
### <a name="to-retrieve-a-value-from-a-property"></a>若要检索属性的值  
  
1.  将使用变量名的相同方式在表达式中使用的属性名称。 可以使用属性可以在任意位置使用一个变量或常量。  
  
     或  
  
     使用属性名称之后等号 (`=`) 在赋值语句登录。  
  
     下面的示例读取的值的 Visual Basic`Now`属性外，隐式调用其`Get`过程。  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2.  如果该属性接受参数，请按照使用括号将参数列表括起来的属性名称。 如果没有任何自变量，可以选择性地省略括号。  
  
3.  将参数放在括号中，由逗号分隔参数列表中。 请确保提供的属性定义的相应参数的相同顺序中的自变量。  
  
 属性的值出现在中，只需为变量表达式或常数那样，或存储在变量或赋值语句左侧的属性。  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [属性过程](./property-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [Property 语句](../../../../visual-basic/language-reference/statements/property-statement.md)
- [在 Visual Basic 中属性和变量之间的差异](./differences-between-properties-and-variables.md)
- [如何：创建属性](./how-to-create-a-property.md)
- [如何：声明具有混合的访问级别的属性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：调用 Property 过程](./how-to-call-a-property-procedure.md)
- [如何：声明并在 Visual Basic 中调用默认属性](./how-to-declare-and-call-a-default-property.md)
- [如何：在属性中放置值](./how-to-put-a-value-in-a-property.md)
