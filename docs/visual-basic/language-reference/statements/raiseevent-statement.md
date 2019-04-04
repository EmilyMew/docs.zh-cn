---
title: RaiseEvent 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: 5d8fd6adf33c992341324e07bcd2ad12986bbdf2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821005"
---
# <a name="raiseevent-statement"></a>RaiseEvent 语句
触发器在类、 窗体或文档中的模块级声明的事件。  
  
## <a name="syntax"></a>语法  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>部件  
 `eventname`  
 必需。 要触发的事件的名称。  
  
 `argumentlist`  
 可选。 变量、 数组或表达式的以逗号分隔列表。 `argumentlist`参数必须括在圆括号。 如果没有任何自变量，必须省略括号。  
  
## <a name="remarks"></a>备注  
 所需`eventname`模块中声明的事件名称。 它遵循 Visual Basic 变量命名约定。  
  
 如果尚未在其中引发的模块中声明事件，就会出错。 下面的代码段演示了一个事件声明和引发该事件的过程。  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 不能使用`RaiseEvent`引发未在模块中显式声明的事件。 例如，所有窗体继承<xref:System.Windows.Forms.Control.Click>从事件<xref:System.Windows.Forms.Form?displayProperty=nameWithType>，不能提升使用`RaiseEvent`派生窗体中。 如果声明`Click`事件在窗体模块中，它会隐藏窗体的自己<xref:System.Windows.Forms.Control.Click>事件。 还可调用窗体的<xref:System.Windows.Forms.Control.Click>通过调用事件<xref:System.Windows.Forms.Control.OnClick%2A>方法。  
  
 默认情况下，在 Visual Basic 中定义的事件引发其事件处理程序建立连接的顺序。 因为事件可以具有`ByRef`参数，晚期连接的进程可能会收到已被较早的事件处理程序更改的参数。 事件处理程序执行后，控制权就会归还引发该事件的子例程。  
  
> [!NOTE]
>  不应在声明它们的类的构造函数中引发非共享事件。 尽管此类事件不会导致运行时错误，但它们可能无法由关联的事件处理程序捕获。 使用`Shared`修饰符来创建共享的事件，如果您需要从一个构造函数中引发事件。  
  
> [!NOTE]
>  你可以通过定义自定义事件的事件的默认行为。 用于自定义事件`RaiseEvent`语句调用事件的`RaiseEvent`访问器。 自定义事件的详细信息，请参阅[Event 语句](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用事件从 10 秒到 0 秒进行倒计时。 该代码演示了几个与事件相关的方法、 属性和语句，其中包括`RaiseEvent`语句。  
  
 引发事件的类是事件源，处理事件的方法是事件处理程序。 事件源对于它生成的事件可以具有多个处理程序。 类引发事件时，会在选择用于为对象的该实例处理事件的每个类上引发该事件。  
  
 该示例还使用一个窗体 (`Form1`)，其中包含一个按钮 (`Button1`) 和一个文本框 (`TextBox1`)。 单击该按钮时，第一个文本框显示从 10 秒到 0 秒的倒计时。 经过了全部时间（10 秒）之后，第一个文本框会显示“Done”。  
  
 `Form1` 的代码指定窗体的初始和最终状态。 它还包含引发事件时执行的代码。  
  
 若要使用此示例中，打开一个新的 Windows 应用程序项目中，添加名为的按钮`Button1`和一个名为文本框`TextBox1`到主窗体，名为`Form1`。 右键单击窗体，然后单击**查看代码**以打开代码编辑器。  
  
 添加`WithEvents`变量的声明部分`Form1`类。  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a>示例  
 将下面的代码添加到 `Form1` 的代码： 替换可能存在，例如任何重复过程`Form_Load`，或`Button_Click`。  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 按 F5 以运行上述示例中，并单击标记的按钮**启动**。 第一个文本框中开始倒计时秒数。 经过了全部时间（10 秒）之后，第一个文本框会显示“Done”。  
  
> [!NOTE]
>  `My.Application.DoEvents`窗体一样方法不会完全相同的方式处理事件。 若要使表单能够直接处理事件，可以使用多线程处理。 有关详细信息，请参阅[托管线程处理](../../../standard/threading/index.md)。  
  
## <a name="see-also"></a>请参阅

- [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
- [Event 语句](../../../visual-basic/language-reference/statements/event-statement.md)
- [AddHandler 语句](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [RemoveHandler 语句](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
