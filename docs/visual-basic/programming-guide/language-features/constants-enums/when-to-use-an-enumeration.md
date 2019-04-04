---
title: 何时使用枚举 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ff2d8c324aee8bbccef050c020e5392368b05b1c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825092"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>何时使用枚举 (Visual Basic)
枚举提供了使用相关常量集的简单方法。 一个枚举，或`Enum`，是一组值的符号名称。 枚举被视为数据类型，并可用于创建用变量和属性使用的常数的集。  
  
## <a name="when-to-use-an-enumeration"></a>何时使用枚举  
 当一个过程接受一组有限的变量时，请考虑使用一个枚举。 枚举可使更明确且更具可读性的代码，尤其是在使用有意义的名称时。  
  
 使用枚举的优点包括：  
  
-   这样可以减少错误引起的转置或键入数字。  
  
-   便于将来更改值。  
  
-   使代码易于阅读，这意味着它不太可能的错误将蔓延到其中。  
  
-   可确保向前兼容性。 借助枚举、 你的代码是不太可能会失败，如果有人在将来更改的成员名称与对应的值。  
  
## <a name="naming-enumerations"></a>命名枚举  
 枚举成员使用的命名约定。 当 Visual Basic 遇到的枚举成员名称时，如果其他引用的类型库包含相同的名称可能会引发异常。 使用唯一的前缀，用于标识您的应用程序或组件中的值。  
  
 当引用枚举成员，必须限定为枚举名称的成员名称，否则使用`Imports`语句。 有关详细信息，请参阅[枚举和名称限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。  
  
## <a name="predefined-enumerations"></a>预定义的枚举  
 Visual Basic 提供了大量预定义的枚举，如`FirstDayOfWeek`和`MsgBoxResult`，以便于您的代码。 有关这些列表请参阅[常量和枚举](../../../../visual-basic/language-reference/constants-and-enumerations.md)。  
  
## <a name="see-also"></a>请参阅

- [如何：声明枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [如何：为枚举成员，请参阅](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [枚举和名称限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [如何：循环访问在 Visual Basic 中枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [如何：确定与枚举值关联的字符串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Enum 语句](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [常量和枚举](../../../../visual-basic/language-reference/constants-and-enumerations.md)
