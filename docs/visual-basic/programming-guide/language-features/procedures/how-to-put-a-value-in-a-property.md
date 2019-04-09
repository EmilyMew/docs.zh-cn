---
title: 如何：将值放在属性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: ee2449ff905bfdacaeeee4cc244db1ce50e00104
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824297"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>如何：将值放在属性 (Visual Basic)
通过将属性名称放在赋值语句左侧，可以在属性中存储值。  
  
 该属性的`Set`过程存储一个值，但并不按名称显式调用它。 您使用该属性，就像您将使用变量。 Visual Basic 可以对该属性的过程的调用。  
  
### <a name="to-store-a-value-in-a-property"></a>若要在属性中存储的值  
  
1.  在赋值语句左侧使用属性名称。  
  
     下面的示例设置的值的 Visual Basic`TimeOfDay`属性设置为中午，隐式调用其`Set`过程。  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2.  如果该属性接受参数，请按照使用括号将参数列表括起来的属性名称。 如果没有任何自变量，可以选择性地省略括号。  
  
3.  将参数放在括号中，由逗号分隔参数列表中。 请确保提供的属性定义的相应参数的相同顺序中的自变量。  
  
4.  在属性中存储生成的赋值语句右侧的值。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [属性过程](./property-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [Property 语句](../../../../visual-basic/language-reference/statements/property-statement.md)
- [在 Visual Basic 中属性和变量之间的差异](./differences-between-properties-and-variables.md)
- [如何：创建属性](./how-to-create-a-property.md)
- [如何：声明具有混合的访问级别的属性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：调用 Property 过程](./how-to-call-a-property-procedure.md)
- [如何：声明并在 Visual Basic 中调用默认属性](./how-to-declare-and-call-a-default-property.md)
- [如何：从属性获取一个值](./how-to-get-a-value-from-a-property.md)
