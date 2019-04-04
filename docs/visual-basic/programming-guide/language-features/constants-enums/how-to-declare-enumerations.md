---
title: 如何：声明枚举 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: 1e6ec63688899533b64a6fc5215f77019b64b49c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830157"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>如何：声明枚举 (Visual Basic)
创建一个枚举，其中`Enum`声明部分中的类或模块的语句。 不能声明一个方法中的枚举。 若要指定适当的访问级别，请使用`Private`， `Protected`， `Friend`，或`Public`。  
  
 `Enum`类型具有名称、 一个基础类型，以及一组字段，每个资源表示常量。 该名称必须是有效的 Visual Basic.NET 限定符。 基础类型必须是一种整数类型-`Byte`， `Short`，`Long`或`Integer`。 `Integer` 默认值。 枚举为始终强类型，不能互换与整数类型。  
  
 枚举不能具有浮点值。 如果枚举已分配与浮点值`Option Strict On`，导致编译器错误。 如果`Option Strict`是`Off`，值自动转换为`Enum`类型。  
  
 有关如何使用和信息的名称，`Imports`语句使名称限定不必要的请参阅[枚举和名称限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。  
  
### <a name="to-declare-an-enumeration"></a>若要声明枚举  
  
1.  编写的声明，包括代码访问级别，`Enum`关键字，并且有效的名称，如下面的示例，其中每个声明一个不同`Enum`。  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2.  枚举中定义常量。 默认情况下，枚举中的第一个常数初始化为`0`，而后续的常量将初始化为一个多个前面的常数的值。 例如，以下枚举`Days`，包含一个名为常量`Sunday`的值`0`，一个名为常量`Monday`的值`1`，一个名为常量`Tuesday`值为`2`，依次类推。  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3.  可以使用赋值语句，显式枚举中的常量中分配的值。 可以分配任何整数值，包括负数。 例如，你可能想常量与值小于零，表示错误条件。 在下面的枚举常量`Invalid`显式分配值`–1`，和常量`Sunday`的值赋给`0`。 因为它是在枚举中的第一个常数`Saturday`还会初始化为值`0`。 值`Monday`是`1`(一的值大于`Sunday`); 的值`Tuesday`是`2`，依次类推。  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>若要声明为显式类型枚举  
  
-   使用指定的枚举类型`As`子句，如下面的示例中所示。  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>请参阅

- [枚举和名称限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [如何：为枚举成员，请参阅](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [如何：循环访问在 Visual Basic 中枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [如何：确定与枚举值关联的字符串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [何时使用枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [常量概述](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [常量和文本数据类型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [常量和枚举](../../../../visual-basic/language-reference/constants-and-enumerations.md)
