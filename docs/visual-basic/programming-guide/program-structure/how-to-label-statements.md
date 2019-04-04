---
title: 如何：标签语句 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 69ec8c7625410f140c59ba8dd492dca76857eb96
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828636"
---
# <a name="how-to-label-statements-visual-basic"></a>如何：标签语句 (Visual Basic)
语句块组成的代码由冒号分隔行。 标识字符串或整数的代码注释行被称为*标记为*。 语句标签用于标记的一行代码以将其标识用于与语句如`On Error Goto`。  
  
 标签可能是任一有效的 Visual Basic 标识符，如标识编程元素，或整数文本。 标签必须位于源代码的行的开头和必须跟一个冒号，而不考虑它后面的语句置于同一行。  
  
 编译器通过检查行的开头是否与任何已定义的标识符相匹配来标识标签。 如果不是，编译器将假定它是一个标签。  
  
 标签具有其自己的声明空间并不会干扰其他标识符。 标签的作用域是该方法的正文。 标签声明在任何不明确的情况下将优先。  
  
> [!NOTE]
>  标签仅用于在方法内的可执行语句。  
  
### <a name="to-label-a-line-of-code"></a>若要标记的代码行  
  
-   将跟一个冒号，源代码的行的开头的标识符。  
  
     例如，以下代码行标记为`Jump`和`120`分别：  
  
     [!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]  
  
## <a name="see-also"></a>请参阅

- [语句](../../../visual-basic/programming-guide/language-features/statements.md)
- [已声明的元素名称](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [程序结构和代码约定](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
