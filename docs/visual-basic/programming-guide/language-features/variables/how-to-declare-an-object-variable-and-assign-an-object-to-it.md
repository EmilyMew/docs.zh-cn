---
title: 如何：声明对象变量并在 Visual Basic 中为其分配对象
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: fb6411efc190dce335422369a8d2bbff564b9523
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819666"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>如何：声明对象变量并在 Visual Basic 中为其分配对象
声明的变量[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)通过指定`As Object`中[Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)。 通过将对象放置在等号后，此类变量分配对象 (`=`) 在赋值语句或初始化子句中。  
  
## <a name="example"></a>示例  
 下面的示例声明`Object`变量，并将分配给它的当前实例。  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 将变量初始化为其声明的一部分，可以组合的声明和分配。 下面的示例相当于前面的示例。  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   对 <xref:System> 命名空间的引用。  
  
-   类、 结构或在其中放入的模块`Dim`语句。  
  
-   所要放在赋值语句中的过程。  
  
## <a name="see-also"></a>请参阅

- [变量声明](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [对象变量](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [对象变量声明](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object 数据类型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [局部类型推理](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict 语句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
