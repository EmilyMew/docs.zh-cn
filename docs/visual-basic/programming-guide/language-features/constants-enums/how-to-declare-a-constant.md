---
title: 如何：声明常量 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: 95bfa3da5499c518dad0c235b539784fee2bb522
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843404"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>如何：声明常量 (Visual Basic)
您使用`Const`语句声明一个常量，并将其值设置。 通过声明一个常量，您将有意义的名称分配给一个值。 一旦声明一个常量，不能修改或分配一个新值。  
  
 声明是固定的过程中或在模块、 类或结构的声明部分。 类或结构级别的常数`Private`默认情况下，但也可能作为声明`Public`， `Friend`， `Protected`，或`Protected Friend`的适当级别的代码访问。  
  
 常量必须具有有效的符号名称 （规则是与用于创建变量的名称相同） 和的数值或字符串常量和运算符 （但不包括函数调用） 组成的表达式。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>若要声明常量  
  
-   编写包含访问说明符声明`Const`关键字和一个表达式，如以下示例所示：  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     当[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)是`Off`并[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)是`On`，您必须通过指定数据类型显式声明常量 (`Boolean`， `Byte`， `Char`， `DateTime`， `Decimal`， `Double`， `Integer`， `Long`， `Short`， `Single`，或`String`)。  
  
     当`Option Infer`是`On`或`Option Strict`是`Off`，你可以声明变量，而无需指定数据类型为`As`子句。 编译器确定的常量表达式的类型的类型。 有关详细信息，请参阅[常量和文本数据类型](constant-and-literal-data-types.md)。  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>若要声明一个常量，它具有显式声明的数据类型  
  
-   编写的声明，包括`As`关键字和显式数据类型，如以下示例所示：  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     虽然你的代码是声明单个常量每行更具可读性，可以在单个行上声明多个常量。 如果在单个行上声明多个常量，它们必须都具有相同的访问级别 (`Public`， `Private`， `Friend`， `Protected`，或`Protected Friend`)。  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>若要在单个行上声明多个常量  
  
-   单独使用一个逗号和空格，如以下示例所示的声明：  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>请参阅

- [Const 语句](../../../../visual-basic/language-reference/statements/const-statement.md)
- [常量和文本数据类型](constant-and-literal-data-types.md)
- [常量概述](constants-overview.md)
- [如何：声明常量](how-to-declare-a-constant.md)
- [用户定义的常量](user-defined-constants.md)
- [常量和文本数据类型](constant-and-literal-data-types.md)
- [如何：相关的常量值组合在一起](how-to-group-related-constant-values-together.md)
- [枚举概述](enumerations-overview.md)
- [如何：声明枚举](how-to-declare-enumerations.md)
- [如何：为枚举成员，请参阅](how-to-refer-to-an-enumeration-member.md)
- [枚举和名称限定](enumerations-and-name-qualification.md)
- [如何：循环访问枚举](how-to-iterate-through-an-enumeration.md)
- [如何：确定与枚举值关联的字符串](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [何时使用枚举](when-to-use-an-enumeration.md)

- [枚举概述](enumerations-overview.md)
- [常量概述](constants-overview.md)
- [如何：声明枚举](how-to-declare-enumerations.md)
- [枚举和名称限定](enumerations-and-name-qualification.md)
- [Option Strict 语句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [常量和枚举](../../../../visual-basic/language-reference/constants-and-enumerations.md)
