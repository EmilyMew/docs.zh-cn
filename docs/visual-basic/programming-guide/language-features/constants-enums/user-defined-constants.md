---
title: 用户定义的常量 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: f0196457235ad77df545a367573f62b43209269d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813907"
---
# <a name="user-defined-constants-visual-basic"></a>用户定义的常量 (Visual Basic)
常量是有意义的名称采用的数字或字符串不会更改的位置。 顾名思义，常量存储在应用程序的执行过程中保持不变的值。 您可以使用由该控件或组件，定义的常量或可以创建你自己。 创建自己的常量被称为*用户定义*。  
  
 声明与常量`Const`语句，用于创建变量的名称使用相同的规则。 如果`Option Strict`是`On`，必须显式声明常量的类型。  
  
## <a name="const-statement-usage"></a>Const 语句使用情况  
 一个`Const`语句可以表示数学或日期/时间数量：  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 它还可以定义`String`常量：  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 等号右侧的表达式 ( `=` ) 通常是一个数字或文本字符串，但它也可以是计算结果为数字或字符串 （尽管该表达式不能包含对函数的调用） 的表达式。 甚至可以定义根据以前定义的常数的常量：  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a>作用域的用户定义的常量  
 一个`Const`语句的作用域是在同一位置中声明的变量相同。 您可以通过以下方式之一指定作用域：  
  
-   若要创建过程中仅存在一个常量，请在该过程中声明。  
  
-   若要创建在类中，所有过程而不是属于该模块以外的任何代码都可用的常数，请将其声明的类的声明部分。  
  
-   若要创建一个常量，它是可用的程序集外部客户端程序集的所有成员而不可用，将使用其声明`Friend`类的声明部分中的关键字。  
  
-   若要创建可在整个应用程序使用的常量，将使用其声明`Public`关键字在下面的声明部分类。  
  
 有关详细信息，请参阅[如何：声明常量](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)。  
  
### <a name="avoiding-circular-references"></a>避免循环引用  
 由于可以在其他常量方面定义常量，它是可能无意中产生*周期*，或两个或多个常量之间的循环引用。 发生一次时有两个或多个公共常量，其中每个定义，根据其他的如以下示例所示：  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 如果发生一次，Visual Basic 生成编译器错误。  
  
## <a name="see-also"></a>请参阅

- [Const 语句](../../../../visual-basic/language-reference/statements/const-statement.md)
- [常量和文本数据类型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [常量和枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [常量和枚举](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [枚举概述](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [常量概述](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [如何：声明枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [枚举和名称限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Option Strict 语句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
