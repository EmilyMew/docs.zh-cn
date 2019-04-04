---
title: 有效使用数据类型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 0b517bca3a9e296eb891e30df91c1d32eb357432
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830118"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>有效使用数据类型 (Visual Basic)
未声明的变量和数据类型未声明的变量分配`Object`数据类型。 这使得可以轻松编写程序快速，但它可能会导致它们执行速度更慢。  
  
## <a name="strong-typing"></a>强类型化  
 指定所有变量的数据类型被称为*强类型化*。 使用强类型化具有以下优点：  
  
-   这样，您的变量的 IntelliSense 支持。 这样可以查看其属性和其他成员，当你键入的代码。  
  
-   它可利用的编译器类型检查。 这将捕获在运行时因等溢出错误而失败的语句。 不支持它们的对象，它还捕获对方法的调用。  
  
-   这会导致代码更快地执行。  
  
## <a name="most-efficient-data-types"></a>最有效的数据类型  
 从不包含小数的变量，整数数据类型是比非整型类型效率更高。 在 Visual Basic 中，`Integer`和`UInteger`是最有效的数值类型。  
  
 对于分数，`Double`是最有效的数据类型，因为当前平台上的处理器执行以双精度浮点运算。 但是，与 operations`Double`不是与整型类型，如一样快`Integer`。  
  
## <a name="specifying-data-type"></a>指定数据类型  
 使用[Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)声明特定类型的变量。 同时可以通过指定其访问级别[公共](../../../../visual-basic/language-reference/modifiers/public.md)，[受保护](../../../../visual-basic/language-reference/modifiers/protected.md)，[友元](../../../../visual-basic/language-reference/modifiers/friend.md)，或者[专用](../../../../visual-basic/language-reference/modifiers/private.md)关键字，如下所示下面的示例。  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>字符转换  
 `AscW`和`ChrW`函数以 unicode 格式进行操作。 应使用它们优先于`Asc`和`Chr`，其必须在执行和跳出执行 Unicode 转换。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [数据类型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [数值数据类型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [变量声明](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [使用 IntelliSense](/visualstudio/ide/using-intellisense)
