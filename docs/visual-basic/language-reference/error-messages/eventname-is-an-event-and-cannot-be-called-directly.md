---
title: “<eventname>”是事件，不能直接调用
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: eb0b40a80d37788bcab32791d7ed701a77505371
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831423"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a>\<事件名称 > 是一种事件，而且不能直接调用
<`eventname`> 是一种事件，并因此不能直接调用。 使用`RaiseEvent`语句引发事件。  
  
 过程调用指定的事件的过程名称。 事件处理程序是一个过程，但事件本身的信号的设备，必须引发并处理。  
  
 **错误 ID:** BC32022  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  使用`RaiseEvent`语句发出信号事件并调用过程或对其进行处理的过程。  
  
## <a name="see-also"></a>请参阅

- [RaiseEvent 语句](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
