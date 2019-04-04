---
title: 声明和引发事件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 0f48c90232c00f53007e7d2f8f08e2107406ecad
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840999"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>演练：声明和引发事件 (Visual Basic)
本演练演示如何声明和引发事件的类名为`Widget`。 完成步骤后，你可能想要读取的配套主题，[演练：处理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)，其中说明了如何使用从事件`Widget`对象提供的应用程序中的状态信息。  
  
## <a name="the-widget-class"></a>小组件类  
 假定您有目前`Widget`类。 你`Widget`类有一个方法，可能需要很长时间才能执行，并且希望你的应用程序要能够提供某种进度指示器。  
  
 当然，您可以制作`Widget`对象显示完成百分比的对话框中，但这样您将会使用该对话框中，在您使用的每个项目`Widget`类。 好的对象设计原则是让使用对象句柄的用户界面的应用程序，除非该对象的总体目的就是管理窗体或对话框。  
  
 目的`Widget`是执行其他任务，所以最好添加`PercentDone`事件并让调用该过程`Widget`的方法处理事件和显示状态更新。 `PercentDone`事件还可以提供用于取消该任务的机制。  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>若要生成本主题的代码示例  
  
1.  打开一个新的 Visual Basic Windows 应用程序项目，并创建名为的`Form1`。  
  
2.  添加两个按钮和标签与`Form1`。  
  
3.  按下表所示命名对象。  
  
    |对象|属性|设置|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|启动任务|  
    |`Button2`|`Text`|取消|  
    |`Label`|`(Name)`， `Text`|lblPercentDone, 0|  
  
4.  上**项目**菜单中，选择**添加类**若要添加一个名为类`Widget.vb`到项目。  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>若要声明的小组件类的事件  
  
-   使用`Event`关键字来声明中的事件`Widget`类。 请注意，事件可以具有`ByVal`并`ByRef`自变量，作为`Widget`的`PercentDone`事件所示：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 当调用的对象收到`PercentDone`事件，`Percent`参数中包含的任务已完成的百分比。 `Cancel`参数可以设置为`True`取消引发该事件的方法。  
  
> [!NOTE]
>  您可以声明事件自变量，就像您处理过程，但存在以下例外的：事件不能有`Optional`或`ParamArray`参数，且事件不具有返回值。  
  
 `PercentDone`引发事件`LongTask`方法的`Widget`类。 `LongTask` 采用两个参数： 要执行的工作和之前的最小时间间隔的时间长度方法伪装`LongTask`暂停以引发`PercentDone`事件。  
  
#### <a name="to-raise-the-percentdone-event"></a>若要引发 PercentDone 事件  
  
1.  以简化对访问`Timer`使用此类的属性添加`Imports`的类模块中，声明部分顶部的语句上方`Class Widget`语句。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2.  将下面的代码添加到 `Widget` 类中:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 当应用程序调用`LongTask`方法，`Widget`类所引发`PercentDone`事件每个`MinimumInterval`秒。 该事件在返回时，`LongTask`检查以查看是否`Cancel`参数设置为`True`。  
  
 一些免责声明此处是必需的。 为简单起见，`LongTask`过程假定您事先知道该任务将花费多长时间。 这几乎不会是这种情况。 将任务分割成大小相等的区块可能很困难，并且通常最重要的内容的用户只需在获得发生了某些内容的指示之前经过的时间量。  
  
 您可能已经发现了另一个缺陷在此示例中。 `Timer`属性返回的自午夜以来经过的秒数; 因此，应用程序时遇到困难如果只是在午夜之前启动。 更仔细的测量时间方法会采用边界条件，例如此纳入考虑范围，或根本不用它们，如使用属性`Now`。  
  
 现在，`Widget`类可以引发事件，您可以将移动到下一个演练。 [演练：处理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)演示了如何使用`WithEvents`关联的事件处理程序`PercentDone`事件。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [演练：处理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
