---
title: 未设置对象变量或 With 块变量
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 1b24bec6dd7c4b5af10349cf523d9a7e93b385fe
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831652"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>未设置对象变量或 With 块变量
正在引用无效的对象变量。   出现此错误的原因可能有多种：  
  
-   如果不指定类型声明了变量。 如果无需指定类型声明的变量，则默认为类型`Object`。  
  
     例如，与声明的变量`Dim x`都属于类型`Object;`与声明的变量`Dim x As String`都属于类型`String`。  
  
    > [!TIP]
    >  `Option Strict`语句不允许隐式键入会导致`Object`类型。 如果省略该类型，将发生编译时错误。 请参阅[Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
-   您尝试引用已被设置为的对象 `Nothing`  
  
     .  
  
-   您尝试访问未正确声明数组变量中的元素。  
  
     例如，数组声明为`products() As String`如果您尝试引用数组的元素，则会触发错误`products(3) = "Widget"`。 数组不包含任何元素，并被视为一个对象。  
  
-   您尝试访问代码内`With...End With`阻止在初始化块之前。   一个`With...End With`块必须通过执行初始化`With`语句入口点。  
  
> [!NOTE]
>  在早期版本的 Visual Basic 或 VBA 此错误也通过分配给一个变量的值，而无需使用触发`Set`关键字 (`x = "name"`而不是`Set x = "name"`)。 `Set`关键字不再是有效 Visual Basic.Net 中。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  设置`Option Strict`到`On`通过将以下代码添加到该文件的开头：  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  如果不想要启用`Option Strict`，搜索你的代码没有类型指定了任何变量 (`Dim x`而不是`Dim x As String`) 并将预期的类型添加到声明。  
  
3.  请确保不指已被设置为的对象变量`Nothing`。  关键字在代码中搜索`Nothing`，并修改你的代码，以便该对象未设置为`Nothing`直到您在引用它。  
  
4.  请确保访问它们之前创建的任何数组变量。 首次创建数组时，既可以分配一个维度 (`Dim x(5) As String`而不是`Dim x() As String`)，或使用`ReDim`关键字可以在首次访问之前设置数组的维数。  
  
5.  请确保你`With`块初始化通过执行`With`语句入口点。  
  
## <a name="see-also"></a>请参阅

- [对象变量声明](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim 语句](../../../visual-basic/language-reference/statements/redim-statement.md)
- [With...End With 语句](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
