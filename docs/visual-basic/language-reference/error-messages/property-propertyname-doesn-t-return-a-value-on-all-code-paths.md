---
title: 属性“<propertyname>”并非在所有代码路径上都返回值
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: a535a6b951dc9872109527f78d7de5f3fcdd3292
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821876"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a>属性 '\<属性名称 > 没有在所有代码路径上返回一个值
属性 '\<属性名称 > 没有在所有代码路径上返回一个值。 使用该结果时，可能会在运行时发生 null 引用异常。  
  
 属性`Get`过程包含至少一个可能不会返回一个值的代码路径。  
  
 可以从属性中返回值`Get`处于以下任一过程：  
  
-   将值分配给属性名称，然后执行`Exit Property`语句。  
  
-   将值分配给属性名称，然后执行`End Get`语句。  
  
-   包括中的值[Return 语句](../../../visual-basic/language-reference/statements/return-statement.md)。  
  
 控制权将传递给`Exit Property`或`End Get`并且没有分配任何值的属性名称，`Get`返回属性的数据类型的默认值。 详细信息，请参阅"行为"中[Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的详细信息，请参见 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **错误 ID:** BC42107  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   检查控制流逻辑，并确保分配导致返回每个语句前的值。  
  
     它是更轻松地保证每个返回从过程返回一个值，如果始终使用`Return`语句。 如果之前的最后一个语句执行此操作，`End Get`应为`Return`语句。  
  
## <a name="see-also"></a>请参阅

- [属性过程](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)
- [Get 语句](../../../visual-basic/language-reference/statements/get-statement.md)
