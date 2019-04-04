---
title: 事件“<eventname1>”无法实现接口“<eventname2>”上的事件“<interface>”，因为它们的委托类型“<delegate1>”和“<delegate2>”不匹配
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 9581168fa86f8f0715e004b60c2eb2a813cd38ab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840518"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a>事件\<eventname1 > 不能实现事件\<eventname2 > 接口上 '\<界面 > 因为它们的委托类型的\<delegate1 > 和\<delegate2 > 不匹配
Visual Basic 不能实现某个事件，因为该事件的委托类型与该接口中的事件的委托类型不匹配。 如果在接口中定义了多个事件，然后试图用一个事件同时实现这些事件，则可能发生此错误。 只有当所有要实现的事件都使用 `As` 语法进行声明并指定相同的委托类型时，事件才能实现两个或更多个事件。  
  
 **错误 ID:** BC31423  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   单独实现事件。  
  
     - 或 -  
  
-   使用在接口中定义的事件`As`语法，并指定相同的委托类型。  
  
## <a name="see-also"></a>请参阅

- [Event 语句](../../../visual-basic/language-reference/statements/event-statement.md)
- [Delegate 语句](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
