---
title: 堆栈空间不足 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 25905e65e74b11d167d3ce2ad258599fb958eb88
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814596"
---
# <a name="out-of-stack-space-visual-basic"></a>堆栈空间不足 (Visual Basic)
堆栈是内存的动态与正在执行程序的需求的增长和压缩的工作区域。 已超出其限制。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  检查不太深嵌套过程。  
  
2.  请确保正确终止递归过程。  
  
3.  如果本地变量所需的本地变量空间大于可用空间，请尝试在模块级别声明一些变量。 您也可以声明该过程中的所有变量静态通过前面`Property`， `Sub`，或`Function`关键字与`Static`。 也可以使用`Static`语句声明过程内的单个静态变量。  
  
4.  重新定义的一些可变长度字符串，作为你固定长度字符串作为固定长度字符串使用比可变长度字符串的更多堆栈空间。 此外可以定义在模块级别，它不需要堆栈空间的字符串。  
  
5.  检查的数量嵌套`DoEvents`通过使用函数调用，`Calls`对话框，以便查看活动在堆栈上的过程。  
  
6.  请确保你不会通过触发的事件的事件过程调用堆栈上的已导致"事件级联"。 级联事件类似于未终止的递归过程调用，但是它不太明显，因为默认情况下，调用由 Visual Basic 而不是在代码中显式调用。 使用`Calls`对话框，以便查看活动在堆栈上的过程。  
  
## <a name="see-also"></a>请参阅

- [“内存”窗口](/visualstudio/debugger/memory-windows)
