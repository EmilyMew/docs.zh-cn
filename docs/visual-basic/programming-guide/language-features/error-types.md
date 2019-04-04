---
title: 错误类型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: 07db963ac3cf9d1c0d17c420480189d362cdaf2c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831561"
---
# <a name="error-types-visual-basic"></a>错误类型 (Visual Basic)
在 Visual Basic 中，错误 (也称为*异常*) 分为三个类别之一： 语法错误、 运行时错误和逻辑错误。  
  
## <a name="syntax-errors"></a>语法错误  
 *语法错误*是编写代码时出现。 Visual Basic 会检查你的代码，并在您键入**代码编辑器**窗口并向你发出警报，如果出现错误，例如拼错单词或不正确地使用一个语言元素。 语法错误则是最常见的错误类型。 解决方法轻松地在编码的环境中就立即发生。  
  
> [!NOTE]
>  `Option Explicit`语句是一种避免语法错误。 它会强制你提前声明要使用的应用程序中的所有变量。 因此，当在代码中使用这些变量时，版式的任何错误立即捕获，并且可以修复。  
  
## <a name="run-time-errors"></a>运行时错误  
 *运行时错误*是仅在编译和运行你的代码后出现。 这些技术包括可能看起来是正确的它不存在语法错误，但不是会执行的代码。 例如，可以正确编写一行代码打开文件。 如果该文件已损坏，无法执行该应用程序，但`Open`函数，并且它将停止运行。 通过重写了错误代码，然后重新编译和重新运行它，可以修复大多数运行时错误。  
  
## <a name="logic-errors"></a>逻辑错误  
 *逻辑错误*是使用应用程序后出现的。 它们是以响应用户操作的大多数通常不需要的或意外结果。 例如，错误键入的键或其他外部影响可能会导致你的应用程序停止工作中所需的参数，或完全。 逻辑错误通常是最难的类型，若要解决，因为它不是始终清除它们发生的位置。  
  
## <a name="see-also"></a>请参阅

- [Try...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [调试器基础知识](/visualstudio/debugger/debugger-basics)
