---
title: “<keyword>”只在实例方法中有效
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 5ff82b932f9bea4c7fd087651e34277ef94bc27c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820707"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a>\<关键字 > 只在实例方法中有效
`Me`， `MyClass`，和`MyBase`关键字是指特定类实例。 不能使用它们在共享内`Function`或`Sub`过程。  
  
 **错误 ID:** BC30043  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   从过程中删除关键字或删除`Shared`过程声明中的关键字。  
  
## <a name="see-also"></a>请参阅

- [对象变量赋值](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [继承的基础知识](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
