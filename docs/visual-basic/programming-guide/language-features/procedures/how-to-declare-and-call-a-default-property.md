---
title: 如何：声明并在 Visual Basic 中调用默认属性
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: f11b5a184b72df68e302094dee762ec6876a397c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829325"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>如何：声明并在 Visual Basic 中调用默认属性
一个*默认属性*是一个类或结构的属性，而无需指定它可以访问你的代码。 当调用代码名称的类或结构，但未一个属性和上下文允许访问某一属性时，Visual Basic 对该类或结构的默认属性解析的访问权限，如果存在。  
  
 类或结构最多可以有一个默认属性。 但是，可以重载默认属性，并且具有多个版本。  
  
 有关详细信息，请参阅[默认](../../../../visual-basic/language-reference/modifiers/default.md)。  
  
### <a name="to-declare-a-default-property"></a>若要声明默认属性  
  
1.  以正常方式声明的属性。 未指定`Shared`或`Private`关键字。  
  
2.  包括`Default`属性声明中的关键字。  
  
3.  指定至少一个参数的属性。 不能定义不采用任何参数的默认属性。  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a>若要调用默认属性  
  
1.  声明包含的类或结构类型的变量。  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2.  使用的表达式中单独的变量名称通常要包括的属性名称。  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3.  变量名后面加上括号中的参数列表。 默认属性需要至少一个参数。  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4.  若要检索默认属性值，请使用变量名称，其自变量列表，或等号后面的表达式中 (`=`) 在赋值语句登录。  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5.  若要设置默认属性值，使用其自变量列表，在赋值语句左侧的变量的名称。  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6.  就像访问任何其他属性一样，始终可以指定默认属性名以及变量名。  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a>示例  
 下面的示例声明了默认属性的类上。  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a>示例  
 下面的示例演示如何调用默认属性`myProperty`类上`class1`。 三个赋值语句存储中的值`myProperty`，和<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>调用读取这些值。  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 默认属性的最常见用途是<xref:Microsoft.VisualBasic.Collection.Item%2A>对各种集合类型的属性。  
  
## <a name="robust-programming"></a>可靠编程  
 默认属性可能会导致小减少源代码的字符，但它们会使代码更难以阅读。 如果发出对类或结构名称的引用时，调用代码不熟悉你的类或结构，它无法确定该引用访问的类或结构本身或默认属性。 这可能会导致编译器错误或细微的运行时逻辑错误。  
  
 您可以始终使用某种程度上减少默认属性错误的可能性[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)设置编译器类型检查到`On`。  
  
 如果想要使用预定义的类或结构在代码中，您必须确定是否具有默认属性，以及如果成功，其名称是什么。  
  
 由于这些缺点，应考虑未定义默认属性。 代码的可读性，应该还考虑始终显式引用的所有属性，包括默认属性。  
  
## <a name="see-also"></a>请参阅

- [属性过程](./property-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [Property 语句](../../../../visual-basic/language-reference/statements/property-statement.md)
- [默认](../../../../visual-basic/language-reference/modifiers/default.md)
- [在 Visual Basic 中属性和变量之间的差异](./differences-between-properties-and-variables.md)
- [如何：创建属性](./how-to-create-a-property.md)
- [如何：声明具有混合的访问级别的属性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：调用 Property 过程](./how-to-call-a-property-procedure.md)
- [如何：在属性中放置值](./how-to-put-a-value-in-a-property.md)
- [如何：从属性获取一个值](./how-to-get-a-value-from-a-property.md)
