---
title: 变量“<variablename>”在赋值前被使用
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 46551a917aeb794c8d35985076b67a315386f628
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819354"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a>变量\<变量名 > 在赋值前被使用
变量\<变量名 > 在赋值前被使用。 可能在运行时导致 null 引用异常。  
  
 应用程序能够通过其代码，用于读取变量之前为其分配任何值至少一个可能的路径。  
  
 如果从未为变量赋值，则它保持其数据类型的默认值。 对于引用数据类型，默认值是 [Nothing](../../../visual-basic/language-reference/nothing.md)。 在某些情况下，读取具有 `Nothing` 值的引用变量可能导致 <xref:System.NullReferenceException> 。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的详细信息，请参见 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **错误 ID:** BC42104  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   检查控制流逻辑，并确保该变量具有有效的值，控制权将传递给读取它的任何语句之前。  
  
-   若要保证变量始终具有有效的值的一种方法是初始化其作为其声明的一部分。 请参阅中的"初始化" [Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
## <a name="see-also"></a>请参阅

- [Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)
- [变量声明](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [变量疑难解答](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
