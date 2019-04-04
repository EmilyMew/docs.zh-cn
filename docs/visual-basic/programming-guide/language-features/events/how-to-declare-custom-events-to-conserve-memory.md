---
title: 如何：声明自定义事件以节省内存 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: e4132f51f4dd85ad964042d05f7c5bc0a2e6e3cd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826621"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>如何：声明自定义事件以节省内存 (Visual Basic)
重要应用程序保持其内存使用量较低时，有几种情况。 自定义事件允许应用程序内存仅用于其处理的事件。  
  
 默认情况下，当一个类声明事件时，编译器将内存分配给一个字段来存储事件信息。 如果类具有多个未使用的事件，它们将不必要地占用内存。  
  
 而不是使用 Visual Basic 提供的事件的默认实现，可以使用自定义事件以更加仔细地管理内存使用情况。  
  
## <a name="example"></a>示例  
 在此示例中，类使用的一个实例<xref:System.ComponentModel.EventHandlerList>类，存储在`Events`字段中，在使用中存储有关事件的信息。 <xref:System.ComponentModel.EventHandlerList>类是设计用来存放委托的优化的列表类。  
  
 类使用中的所有事件`Events`字段来跟踪哪些方法正处理的每个事件。  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.ComponentModel.EventHandlerList>
- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [如何：声明自定义事件以避免阻止](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
