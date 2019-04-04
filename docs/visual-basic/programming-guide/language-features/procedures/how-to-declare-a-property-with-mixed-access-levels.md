---
title: 如何：声明具有混合的访问级别 (Visual Basic 中) 的属性
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: aa0c71621b72d01067db0749a0678b706d13fbfa
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832120"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>如何：声明具有混合的访问级别 (Visual Basic 中) 的属性
如果你想`Get`并`Set`要具有不同的访问级别的属性的过程，您可以使用中的限制性更弱级别`Property`语句，并在限制性更强的级别`Get`或`Set`语句。 当你想要能够获取属性的值的代码的某些部分和某些其他部分的代码要能够更改的值时，可以在属性上使用混合的访问级别。  
  
 有关访问级别的详细信息，请参阅[访问 Visual Basic 中的级别](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>若要声明具有混合的访问级别的属性  
  
1.  以正常方式声明的属性和指定限制性较弱的访问级别 (如`Public`) 中`Property`语句。  
  
2.  声明`Get`或`Set`过程指定限制性更强的访问级别 (如`Friend`)。  
  
3.  不要对其他属性过程指定访问级别。 它假定中声明的访问级别`Property`语句。 你可以限制属性过程之一上的访问。  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     在前面的示例中，`Get`过程具有相同`Protected`与该属性本身的访问权限时`Set`过程包含`Private`访问。 一个类派生自`employee`可以读取`salary`值，但只有`employee`类可以将其设置。  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [属性过程](./property-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [Property 语句](../../../../visual-basic/language-reference/statements/property-statement.md)
- [在 Visual Basic 中属性和变量之间的差异](./differences-between-properties-and-variables.md)
- [如何：创建属性](./how-to-create-a-property.md)
- [如何：调用 Property 过程](./how-to-call-a-property-procedure.md)
- [如何：声明并在 Visual Basic 中调用默认属性](./how-to-declare-and-call-a-default-property.md)
- [如何：在属性中放置值](./how-to-put-a-value-in-a-property.md)
- [如何：从属性获取一个值](./how-to-get-a-value-from-a-property.md)
