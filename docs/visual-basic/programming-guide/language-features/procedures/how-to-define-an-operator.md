---
title: 如何：定义运算符 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: 3a09657ee7a79b7f590adba0e4fb0c04a8e89043
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843638"
---
# <a name="how-to-define-an-operator-visual-basic"></a>如何：定义运算符 (Visual Basic)
如果已定义的类或结构，可以定义标准运算符的行为 (如`*`， `<>`，或`And`) 当一个或两个操作数是类或结构的类型。  
  
 标准运算符定义为类或结构中的运算符过程。 所有运算符过程都必须都是`Public` `Shared`。  
  
 在类或结构上定义一个运算符也称为*重载*运算符。  
  
## <a name="example"></a>示例  
 下面的示例定义`+`调用的运算符为结构`height`。 该结构的高度以英尺、 英寸为单位。 一个*英寸*2.54 厘米和一个*foot*为 12 英寸。 若要确保规范化的值 (英寸 < 12.0)，该构造函数执行*取模*12 的运算。 `+`运算符使用构造函数生成规范化的值。  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 可以测试结构`height`用下面的代码。  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  
  
  
## <a name="see-also"></a>请参阅

- [运算符过程](./operator-procedures.md)
- [如何：定义转换运算符](./how-to-define-a-conversion-operator.md)
- [如何：调用运算符过程](./how-to-call-an-operator-procedure.md)
- [如何：使用定义运算符的类](./how-to-use-a-class-that-defines-operators.md)
- [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure 语句](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [如何：声明结构](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Mod 运算符](../../../../visual-basic/language-reference/operators/mod-operator.md)
