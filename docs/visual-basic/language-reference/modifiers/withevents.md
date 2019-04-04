---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 75d118ee2bd4918c3a936cb341864ddc5315726b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826608"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
指定一个或多个声明的成员变量引用可以引发事件的类的实例。  
  
## <a name="remarks"></a>备注  
 当使用定义一个变量`WithEvents`，可以以声明方式指定一种方法处理使用的变量的事件`Handles`关键字。  
  
 可以使用`WithEvents`只能在类或模块级别。 这意味着声明上下文`WithEvents`变量必须是类或模块，且不能为源文件、 命名空间、 结构或过程。  
  
 不能使用`WithEvents`结构成员上。  
  
 您可以声明只有单个变量-不数组 — 与`WithEvents`。  
  
## <a name="rules"></a>规则  
  
-   **元素类型。** 必须声明`WithEvents`变量为对象变量，以便它们可以接受类实例。 但是，您不能将其声明为`Object`。 必须将它们声明为可引发事件的特定类。  
  
 `WithEvents`修饰符可用于在此上下文中：[Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>请参阅

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [关键字](../../../visual-basic/language-reference/keywords/index.md)
- [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
