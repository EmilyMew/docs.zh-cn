---
title: 其他控件结构 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c42070ce2ea866e59e1b2e190f7c05e1ee7cc922
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819315"
---
# <a name="other-control-structures-visual-basic"></a>其他控件结构 (Visual Basic)
Visual Basic 提供的控制结构，可帮助您释放资源，或减少必须重复的对象引用的次数。  
  
## <a name="usingend-using-construction"></a>使用...使用构造结束  
 `Using...End Using`构造建立可在其中一个语句块使用的 SQL 连接等资源。 您可以根据需要获取与资源`Using`语句。 当您退出`Using`块中，Visual Basic 会自动释放的资源，这样就可用于其他代码使用。 资源必须是本地的和可释放。 有关详细信息，请参阅 [Using 语句](../../../../visual-basic/language-reference/statements/using-statement.md)。  
  
## <a name="withend-with-construction"></a>使用...最终构造  
 `With...End With`构造可以一次指定的对象引用，然后运行一系列访问其成员的语句。 这可以简化代码，并提高性能，因为 Visual Basic 不需要重新建立访问每个语句的引用。 有关详细信息，请参阅[使用...使用语句结束](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)。  
  
## <a name="see-also"></a>请参阅

- [控制流](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [决策结构](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [循环结构](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [嵌套的控件结构](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using 语句](../../../../visual-basic/language-reference/statements/using-statement.md)
- [With...End With 语句](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
