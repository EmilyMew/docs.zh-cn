---
title: 如何：拆分和合并语句中的代码 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 680084c39b90d4f664f48559fa21388ce192d999
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837702"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>如何：拆分和合并语句中的代码 (Visual Basic)
编写你的代码时，可能有时创建耗时较长的语句都必须采取措施水平滚动代码编辑器中。 尽管这不会影响的方式运行代码，它使得您或任何其他人无法读取代码在监视器上显示。 在这种情况下，应考虑将单个的长语句分成多个行。  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>若要拆分为多行的一条语句  
  
-   使用行继续符，它是一个下划线 (`_`)，在想要中断的行的点。 该下划线必须紧跟在空格后，并且在它后面紧跟行终止符（回车）。  
  
    > [!NOTE]
    >  在某些情况下，如果您忽略行继续符，Visual Basic 编译器将隐式 continue 语句在下一行代码上。 可以为其省略行继续符的语法元素的列表，请参阅"隐式行继续符"中的[语句](../../../visual-basic/programming-guide/language-features/statements.md)。  
  
     在以下示例中，该语句将划分成四行延续字符终止所有行，但最后一行。  
  
     [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]  
  
     这样可以使代码易于阅读，均通过在线和当打印。  
  
     行继续符必须是一行的最后一个字符。 您不能与任何其他操作跟它在同一行。  
  
     可以在其中使用行继续符; 存在一些限制例如，不能使用它的中间参数名称。 可以中断参数列表与行继续符，但单个自变量名必须保持不变。  
  
     通过使用行继续符将无法继续注释。 编译器不会检查具有特殊含义的注释中的字符。 对于多行注释，重复注释符号 (`'`) 在每一行上。  
  
 尽管推荐的方法是将每个语句放在单独的行，但 Visual Basic 还允许您在同一行上放置多个语句。  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>若要将多个语句置于同一行上  
  
-   用冒号分隔的语句 (`:`)，如下面的示例。  
  
     [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>请参阅

- [程序结构和代码约定](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [语句](../../../visual-basic/programming-guide/language-features/statements.md)
