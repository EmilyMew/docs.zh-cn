---
title: End 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: 4fc4fd36fb6b057195e9d8a79eb0a5b3ac9ff95c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832016"
---
# <a name="end-statement"></a>End 语句
立即终止执行。  
  
## <a name="syntax"></a>语法  
  
```  
End  
```  
  
## <a name="remarks"></a>备注  
 可以将放置`End`强制停止正在运行的整个应用程序的过程中的任意位置的语句。 `End` 关闭打开的任何文件`Open`语句，并清除应用程序的所有变量。 在应用程序关闭在没有保存对其对象的引用其他程序并无其代码运行。  
  
> [!NOTE]
>  `End`语句突然停止执行代码并不会调用`Dispose`或`Finalize`方法或任何其他 Visual Basic 代码。 保留由其他程序的对象引用都将失效。 如果`End`语句中遇到`Try`或`Catch`块中，控件不会将传递给相应`Finally`块。  
  
 `Stop`语句将暂停执行，但不同于`End`，它不会关闭任何文件或清除任何变量，除非遇到编译可执行文件 (.exe) 文件中。  
  
 因为`End`终止而不顾及应用程序对任何可能处于打开状态的资源，您应尝试彻底关闭然后再使用它。 例如，如果你的应用程序具有打开的任何窗体，您应关闭它们再控制达到`End`语句。  
  
 应使用`End`尽量少，且仅当需要立即停止。 终止一个过程的正常方法 ([Return 语句](../../../visual-basic/language-reference/statements/return-statement.md)并[退出语句](../../../visual-basic/language-reference/statements/exit-statement.md)) 不仅彻底关闭该过程，但也使调用代码有机会彻底关闭。 控制台应用程序，例如，可以只需`Return`从`Main`过程。  
  
> [!IMPORTANT]
>  `End`语句也会调用<xref:System.Environment.Exit%2A>方法<xref:System.Environment>类中<xref:System>命名空间。 <xref:System.Environment.Exit%2A> 要求具有`UnmanagedCode`权限。 如果没有，<xref:System.Security.SecurityException>发生错误。  
  
 当其他关键字后, 跟[最终\<关键字 > 语句](../../../visual-basic/language-reference/statements/end-keyword-statement.md)描述相应的过程或块定义的末尾。 例如，`End Function`终止的定义`Function`过程。  
  
## <a name="example"></a>示例  
 下面的示例使用`End`语句终止执行代码，如果用户请求它。  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>智能设备开发人员说明  
 不支持此语句。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop 语句](../../../visual-basic/language-reference/statements/stop-statement.md)
- [结束\<关键字 > 语句](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
