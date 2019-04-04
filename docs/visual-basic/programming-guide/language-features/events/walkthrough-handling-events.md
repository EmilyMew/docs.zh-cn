---
title: 处理事件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 2a8b515f500884d743b7dcca41ffe8c1607375a9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840921"
---
# <a name="walkthrough-handling-events-visual-basic"></a>演练：处理事件 (Visual Basic)
这是演示如何使用事件的两个主题的第二个。 第一个主题，[演练：声明和引发事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)，演示如何声明和引发事件。 本部分使用窗体和该演练中的类来显示如何处理时其发生的事件。  
  
 `Widget`类的示例使用传统的事件处理语句。 Visual Basic 提供了用于处理事件的其他技术。 作为练习，您可以修改此示例以使用`AddHandler`和`Handles`语句。  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>若要处理的 PercentDone 事件的小组件类  
  
1.  将以下代码中的放置`Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     `WithEvents`关键字指定变量`mWidget`用于处理对象的事件。 通过提供将从其创建该对象的类的名称指定的对象的类型。  
  
     在变量`mWidget`中声明`Form1`因为`WithEvents`变量必须是类级别。 这是类的将其放置的类型无关，则返回 true。  
  
     在变量`mblnCancel`用于取消`LongTask`方法。  
  
## <a name="writing-code-to-handle-an-event"></a>编写代码来处理事件  
 声明变量的使用时，就立即`WithEvents`，变量名称将显示在左侧的下拉列表的类的**代码编辑器**。 当选择`mWidget`，则`Widget`类的事件显示在右侧下拉列表中。 选择一个事件将显示相应事件过程中的，使用前缀`mWidget`和一条下划线。 与关联的所有事件过程`WithEvents`变量可以作为前缀的变量名称。  
  
#### <a name="to-handle-an-event"></a>若要处理的事件  
  
1.  选择`mWidget`左侧的下拉列表中从**代码编辑器**。  
  
2.  选择`PercentDone`右侧下拉列表中的事件。 **代码编辑器**将打开`mWidget_PercentDone`事件过程。  
  
    > [!NOTE]
    >  **代码编辑器**很有用，但不是必需，用于插入新的事件处理程序。 在本演练中，它是更直接，只是事件处理程序将直接复制到你的代码。  
  
3.  将以下代码添加到 `mWidget_PercentDone` 事件处理程序中：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     每当`PercentDone`引发事件、 事件过程会显示在完成百分比`Label`控件。 `DoEvents`方法允许标签重新绘制，并且还提供了用户单击的机会**取消**按钮。  
  
4.  添加以下代码为`Button2_Click`事件处理程序：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 如果用户单击**取消**按钮，同时`LongTask`正在运行，`Button2_Click`执行事件就立即`DoEvents`语句可用于对发生的事件处理。 在类级别变量`mblnCancel`设置为`True`，并`mWidget_PercentDone`事件然后测试它，并将`ByRef Cancel`参数`True`。  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>连接到一个对象的 WithEvents 变量  
 `Form1` 现在已设置来处理`Widget`对象的事件。 剩下的就是查找`Widget`某个位置。  
  
 当你声明一个变量`WithEvents`在设计时，没有对象，则与之相关联。 一个`WithEvents`变量就像任何其他对象变量。 您必须创建一个对象，并为其分配一个引用`WithEvents`变量。  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>若要创建一个对象，并将分配给它的引用  
  
1.  选择 **（Form1 事件）** 从左侧的下拉列表中**代码编辑器**。  
  
2.  选择`Load`右侧下拉列表中的事件。 **代码编辑器**将打开`Form1_Load`事件过程。  
  
3.  添加以下代码`Form1_Load`创建事件过程`Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 此代码执行时，Visual Basic 创建`Widget`对象，并将其事件连接到与关联的事件过程`mWidget`。 自此以后，每当`Widget`引发其`PercentDone`事件，`mWidget_PercentDone`事件过程中执行。  
  
#### <a name="to-call-the-longtask-method"></a>若要调用 LongTask 方法  
  
-   将以下代码添加到 `Button1_Click` 事件处理程序中：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 之前`LongTask`调用方法时，必须初始化的显示完成百分比的标签和类级别`Boolean`标记为取消该方法必须设置为`False`。  
  
 `LongTask` 调用任务持续时间为 12.2 秒。 `PercentDone`引发事件一次每个有三分之一的第二个。 引发事件时，每次`mWidget_PercentDone`事件过程中执行。  
  
 当`LongTask`操作后，`mblnCancel`测试以查看是否`LongTask`正常结束，或如果它已停止，因为`mblnCancel`设置为`True`。 仅在前一种情况中更新的完成百分比。  
  
#### <a name="to-run-the-program"></a>运行程序  
  
1.  按 F5，在运行模式下将该项目。  
  
2.  单击**启动任务**按钮。 每次`PercentDone`引发事件时，使用的任务的完成百分比更新标签。  
  
3.  单击**取消**按钮以停止任务。 请注意的外观**取消**按钮并不立即单击时更改。 `Click`事件不会发生直到`My.Application.DoEvents`语句可用于事件处理。  
  
    > [!NOTE]
    >  `My.Application.DoEvents`窗体一样方法不会完全相同的方式处理事件。 例如，在本演练中，您必须单击**取消**按钮两次。 若要使表单能够直接处理事件，可以使用多线程处理。 有关详细信息，请参阅[托管线程处理](../../../../standard/threading/index.md)。
  
 您可能会发现有意义，按 f11 键运行该程序并单步执行代码行一次。 您可以清楚地看到如何执行进入`LongTask`，，然后简要重新进入`Form1`每次`PercentDone`引发事件。  
  
 会发生什么情况 if、 执行过程中的代码重新`Form1`，则`LongTask`再次调用方法？ 如果堆栈溢出可能会出现最坏的情形，`LongTask`每次引发事件时调用。  
  
 您可能会导致在变量`mWidget`来处理事件的不同`Widget`对象的引用分配给新`Widget`到`mWidget`。 事实上，可以进行中的代码`Button1_Click`每次单击按钮时执行此操作。  
  
#### <a name="to-handle-events-for-a-different-widget"></a>若要处理不同的小组件的事件  
  
-   添加以下代码行`Button1_Click`过程中，读取的行前面紧邻`mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 上面的代码创建一个新`Widget`每次单击按钮。 只要`LongTask`方法完成后，对引用`Widget`发布后，和`Widget`被销毁。  
  
 一个`WithEvents`变量可以包含一次只有一个对象引用，如果你分配一个不同`Widget`对象传递给`mWidget`上, 一个`Widget`对象的事件将无法再进行处理。 如果`mWidget`是唯一的对象变量包含对旧的引用`Widget`，该对象被销毁。 如果你想要处理来自多个事件`Widget`对象，请使用`AddHandler`语句分别处理每个对象中的事件。  
  
> [!NOTE]
>  您可以声明任意多个`WithEvents`需要为您的变量，但数组`WithEvents`不支持变量。  
  
## <a name="see-also"></a>请参阅

- [演练：声明和引发事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
