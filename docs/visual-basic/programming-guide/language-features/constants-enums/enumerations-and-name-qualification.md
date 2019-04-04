---
title: 枚举和名称限定 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: f0a806b040720cf6682f8a72025a0590dd4d91f7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818431"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>枚举和名称限定 (Visual Basic)
通常情况下，在引用枚举成员，必须限定为枚举名称的成员名称。 例如，若要引用`Sunday`的成员在`Days`枚举，请使用以下语法：  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a>使用 Imports 语句  
 您可以通过避免使用完全限定的名称添加`Imports`语句向你的代码，如以下示例所示的命名空间声明部分：  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 `Imports`语句导入的命名空间名称，从引用的项目和程序集和与该语句将出现的模块相同的项目。 一旦添加此语句，也可以引用到枚举成员，而无需限定，如以下示例所示：  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 通过组织在枚举中的相关常量集，可以使用不同的上下文中相同的常量名称。 例如，可以使用相同的名称为在工作日的常数`Days`和`WorkDays`枚举。 如果使用`Imports`与枚举一起语句，您必须小心，避免不明确的引用。 请看下面的示例：  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 假设`Monday`是两个成员`Days`枚举和`Workdays`枚举，此代码将生成编译器错误。 若要避免不明确的引用，当涉及到单个常量时，有资格使用其枚举常量的名称。 下面的代码是指`Saturday`中的常量`Days`和`WorkDays`枚举。  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a>请参阅

- [常量和枚举](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [如何：声明枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [如何：为枚举成员，请参阅](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [如何：循环访问在 Visual Basic 中枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [如何：确定与枚举值关联的字符串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [何时使用枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [常量和文本数据类型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Enum 语句](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Imports 语句（.NET 命名空间和类型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [数据类型](../../../../visual-basic/language-reference/data-types/index.md)
