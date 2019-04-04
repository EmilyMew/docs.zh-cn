---
title: On Error 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
ms.openlocfilehash: 0a5a5261e6b71178adce02a5635c1f91a1469f3d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834257"
---
# <a name="on-error-statement-visual-basic"></a>On Error 语句 (Visual Basic)
启用错误处理例程，并指定该例程在过程; 中的位置此外可以用于禁用错误处理例程。  
  
 如果错误处理，不会发生任何运行时错误是致命： 显示一条错误消息，并且停止执行。  
  
 只要有可能，我们建议您同时使用结构化的异常处理在代码中，而不使用非结构化的异常处理和`On Error`语句。 有关详细信息，请参阅 [Try...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
> [!NOTE]
>  `Error`关键字还用于[Error 语句](../../../visual-basic/language-reference/statements/error-statement.md)，这为了向后兼容受支持。  
  
## <a name="syntax"></a>语法  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`GoTo` `line`|启用指定在所需的行开始的错误处理例程`line`参数。 `line`参数是任意行标签或行号。 如果出现运行时错误，则控制分支到指定的行，使错误处理程序处于活动状态。 指定的行必须采用与相同的步骤`On Error`语句或编译时错误会发生。|  
|`GoTo` 0|禁用当前过程中启用的错误处理和重置为`Nothing`。|  
|`GoTo` -1|禁用当前过程中已启用的异常和重置为`Nothing`。|  
|`Resume Next`|指定语句出现运行时错误时，控件跳转到紧跟其中发生错误，并从该点继续执行该语句的语句。 使用此窗体而非`On Error GoTo`访问对象时。|  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  我们建议使用只要有可能，在代码中的结构化的异常处理，而不是使用非结构化的异常处理和`On Error`语句。 有关详细信息，请参阅 [Try...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
 "已启用"的错误处理程序是指已开启，`On Error`语句。 "活动"的错误处理程序是一个已启用的处理程序的过程中处理错误。  
  
 错误处理程序处于活动状态时如果发生错误 (错误的匹配项之间和一个`Resume`， `Exit Sub`， `Exit Function`，或`Exit Property`语句)，当前过程的错误处理程序无法处理该错误。 控制权返回给调用的过程。  
  
 如果调用过程具有一个已启用的错误处理程序，它被激活以处理错误。 如果调用过程的错误处理程序还处于活动状态，控制将传递回通过前一个调用过程中，直到找到已启用，但非活动状态，错误处理程序。 如果不找到任何此类错误处理程序，则这个错误是致命它实际发生的时候。  
  
 错误处理程序将控制传递回调用过程时，每次该过程将成为当前的过程。 一旦通过任何过程中的错误处理程序处理错误，则执行将在由指定的位置的当前过程`Resume`语句。  
  
> [!NOTE]
>  不是错误处理例程`Sub`过程或`Function`过程。 它是一段代码标记行标签或行号。  
  
## <a name="number-property"></a>Number 属性  
 错误处理例程依赖于中的值`Number`属性的`Err`对象，以确定错误的原因。 例程应测试或保存相关的属性值中`Err`对象之前可能出现其他错误或错误调用之前可能会导致的过程。 中的属性值`Err`对象只反映最新的错误。 与相关联的错误消息`Err.Number`中包含`Err.Description`。  
  
## <a name="throw-statement"></a>Throw 语句  
 与引发的错误`Err.Raise`方法设置`Exception`属性设置为新创建的实例<xref:System.Exception>类。 为了支持派生的异常类型的异常引发`Throw`语句支持的语言。 这将是要引发的异常实例的单个参数。 下面的示例演示如何使用现有的异常处理支持使用这些功能：  
  
 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 请注意，`On Error GoTo`语句捕获所有错误，而不考虑异常类。  
  
## <a name="on-error-resume-next"></a>On Error Resume Next  
 `On Error Resume Next` 会导致执行继续后立即导致运行时错误，该语句的语句或使用紧跟最新的语句调用带过程包含`On Error Resume Next`语句。 此语句允许执行继续运行时错误。 您可以将会出现错误的错误处理例程，而不是将控制转移到过程内的另一个位置。 `On Error Resume Next`语句变为非活动状态时调用另一个过程，因此应执行`On Error Resume Next`中每个语句调用例程，如果你想在该例程处理内联错误。  
  
> [!NOTE]
>  `On Error Resume Next`构造可能优于`On Error GoTo`处理期间对其他对象的访问生成的错误时。 检查`Err`与对象的每个交互清楚地了解对象所访问的代码之后。 可以确定哪个对象放置中的错误代码`Err.Number`，以及哪个对象最初生成错误 (中指定的对象`Err.Source`)。  
  
## <a name="on-error-goto-0"></a>Error GoTo 0 上  
 `On Error GoTo 0` 禁用当前过程中的错误处理。 它不会作为错误处理代码的开头指定 0 行，即使过程包含编号为 0 的行。 无需`On Error GoTo 0`退出一个过程时，会自动禁用语句中，错误处理程序。  
  
## <a name="on-error-goto--1"></a>在错误 GoTo-1  
 `On Error GoTo -1` 禁用当前过程中的异常。 它不指定行-1 作为开头的错误处理代码，即使过程包含的行号为-1。 无需`On Error GoTo -1`退出一个过程时，会自动禁用语句中，异常。  
  
 若要阻止运行时未发生错误的错误处理代码，请将置于`Exit Sub`， `Exit Function`，或`Exit Property`语句之前的错误处理例程，如以下片段中所示：  
  
 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]  
  
 在这里，错误处理代码如下所示`Exit Sub`语句位于`End Sub`语句以将其与过程流。 可以将错误处理代码放在过程中的任意位置。  
  
## <a name="untrapped-errors"></a>无法捕获的错误  
 无法捕获的对象中的错误返回到控制应用程序作为可执行文件运行时对象。 在开发环境中，无法捕获的错误返回到控制应用程序仅当设置了适当的选项。 请参阅的说明这些选项应该设置在调试过程中的、 如何进行设置，以及主机是否可以创建类的主机应用程序的文档。  
  
 如果创建了访问其他对象的对象，应尝试处理它们可能传回任何未处理的错误。 如果您不能映射中的错误代码`Err.Number`到某个你自己的错误，然后传递它们重新添加到您的对象的调用方。 应通过添加到您的错误代码来指定错误`VbObjectError`常量。 例如，如果您的错误代码为 1052年，将其分配，如下所示：  
  
 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]  
  
> [!CAUTION]
>  系统对 Windows 动态链接库 (Dll) 的调用过程中出现错误不会引发异常并不能与 Visual Basic 错误捕获捕获。 当调用 DLL 函数，应检查成功或失败 （根据 API 规范），每个返回值和出现故障时，检查值`Err`对象的`LastDLLError`属性。  
  
## <a name="example"></a>示例  
 此示例首先使用`On Error GoTo`语句指定的位置的过程中的错误处理例程。 在示例中，尝试除以零将产生错误编号为 6。 在错误处理例程中，处理该错误，然后将控件返回到导致该错误的语句。 `On Error GoTo 0`语句关闭错误捕获。 然后`On Error Resume Next`语句用于延迟错误捕获，以确保可以为某些已知的下一个语句所生成错误的上下文。 请注意，`Err.Clear`用于清除`Err`之后处理该错误的对象的属性。  
  
 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]  
  
## <a name="requirements"></a>要求  
 **命名空间：**[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **程序集：** Visual Basic 运行库（在 Microsoft.VisualBasic.dll 中）  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [End 语句](../../../visual-basic/language-reference/statements/end-statement.md)
- [Exit 语句](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Resume 语句](../../../visual-basic/language-reference/statements/resume-statement.md)
- [错误消息](../../../visual-basic/language-reference/error-messages/index.md)
- [Try...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
