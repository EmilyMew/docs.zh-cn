---
title: 如何：创建新的变量 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 86236f7e6f4821cc45dfab80273d82b6f167fba8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823280"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>如何：创建新的变量 (Visual Basic)
创建的变量[Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
### <a name="to-create-a-new-variable"></a>创建新变量  
  
1.  声明中的变量`Dim`语句。  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  包括变量的特征的规范如下所述[私有](../../../../visual-basic/language-reference/modifiers/private.md)，[静态](../../../../visual-basic/language-reference/modifiers/static.md)，[阴影](../../../../visual-basic/language-reference/modifiers/shadows.md)，或者[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)。 有关详细信息，请参阅[声明元素的特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)。  
  
    ```  
    Public Static newCustomer  
    ```  
  
     不需要`Dim`关键字声明中使用其他关键字。  
  
3.  请按照与变量的名称，必须遵循 Visual Basic 规则和约定规范。 有关详细信息，请参阅[声明的元素名称](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  名称后接[作为](../../../../visual-basic/language-reference/statements/as-clause.md)子句来指定变量的数据类型。  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     如果未指定的数据类型，它使用默认值： `Object`。  
  
5.  请按照`As`子句以等号 (`=`) 和等号后使用该变量的初始值。  
  
     Visual Basic 将指定的值分配给变量每次运行时`Dim`语句。 如果不指定一个初始值，Visual Basic 时赋给变量的数据类型的默认初始值首次进入包含的代码`Dim`语句。  
  
     如果变量为引用类型，则可以通过包括创建其类的实例[New 运算符](../../../../visual-basic/language-reference/operators/new-operator.md)中的关键字`As`子句。 如果不使用`New`，该变量的初始值是[Nothing](../../../../visual-basic/language-reference/nothing.md)。  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>请参阅

- [变量](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [变量声明](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [已声明的元素名称](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [已声明元素的特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [值类型和引用类型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [语句](../../../../visual-basic/language-reference/statements/index.md)
- [局部类型推理](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer 语句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
