---
title: 如何：在值 (Visual Basic 中) 创建一个变量，不会更改
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 57792db826caa996e163bc0a51b01a6bbd6a4858
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823319"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>如何：在值 (Visual Basic 中) 创建一个变量，不会更改
不会更改其值的变量的概念可能似乎是矛盾。 但有些情况下常量不可行时，并可用于具有固定值的变量。 在这种情况下，你可以定义具有的成员变量[ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)关键字。  
  
 不能使用[Const 语句](../../../../visual-basic/language-reference/statements/const-statement.md)来声明和分配在以下情况下的常量值：  
  
-   `Const`语句不接受你想要使用的数据类型  
  
-   在编译时不知道值  
  
-   无法在编译时计算的常量值  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a>若要在值中创建一个变量，不会更改  
  
1.  在模块级别声明的成员变量[Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)，并包括[ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)关键字。  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     您可以指定`ReadOnly`仅在成员变量上。 这意味着您必须定义在模块级别，任何过程之外的变量。  
  
2.  如果可以计算在编译时的单个语句中的值，使用中的初始化子句`Dim`语句。 请按照[作为](../../../../visual-basic/language-reference/statements/as-clause.md)子句以等号 (`=`) 后, 跟表达式。 请确保编译器可以计算此表达式为常量值。  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     可以将值赋给`ReadOnly`变量仅一次。 一旦您这样做，没有代码可以不断更改其值。  
  
     如果在编译时，不知道的值或不能在单个语句中的编译时计算，可以仍将其分配在构造函数中的运行时。 若要执行此操作，必须声明`ReadOnly`变量在类或结构的级别。 在该类或结构的构造函数，计算该变量的固定的值，并返回从构造函数之前将其分配给该变量。  
  
## <a name="see-also"></a>请参阅

- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Const 语句](../../../../visual-basic/language-reference/statements/const-statement.md)
