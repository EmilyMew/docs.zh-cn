---
title: “<typename>”将对基 <type> 的访问扩展到程序集的外部，因此无法从 <basetypename>“<type>”继承
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: dc979a66c73fdf15a4349a003680156e0ce27ed3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838945"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>\<类型名称 > 不能继承自\<类型 >\<基类型名称 > 扩展的基本访问权限，因此\<类型 > 程序集外部的
类或接口继承自的基类或接口但具有限制性较弱的访问级别。  
  
 例如，`Public`接口继承自`Friend`接口，或`Protected`类继承自`Private`类。 这会公开的基类或接口来访问超出了预期的级别。  
  
 **错误 ID:** BC30910  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   更改派生的类或接口的基类或接口至少限制的访问级别。  
  
     或  
  
-   如果需要限制较少的访问级别，请删除`Inherits`语句。 不能从更受限制的基类或接口继承。  
  
## <a name="see-also"></a>请参阅

- [Class 语句](../../../visual-basic/language-reference/statements/class-statement.md)
- [Interface 语句](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Inherits 语句](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [在 Visual Basic 中的访问级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
