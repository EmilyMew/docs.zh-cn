---
title: Resume 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: 796342d17b0d0f1a642aff381274746d1fda3559
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816442"
---
# <a name="resume-statement"></a>Resume 语句
错误处理例程完成后恢复执行。  
  
 我们建议你使用只要有可能，在代码中的结构化的异常处理，而不是无需使用非结构化的异常处理和`On Error`和`Resume`语句。 有关详细信息，请参阅 [Try...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## <a name="syntax"></a>语法  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>部件  
 `Resume`  
 必需。 如果错误发生在同一过程中作为错误处理程序，将导致错误的语句处继续执行。 如果被调用过程中发生错误的在上一次调用不包含错误处理例程的过程的语句处继续执行。  
  
 `Next`  
 可选。 如果错误发生的错误处理程序与相同的步骤中，将紧跟导致错误的语句的语句处继续执行。 如果被调用过程中发生错误的与上一次调用不包含错误处理例程的过程在语句后立即语句处继续执行 (或`On Error Resume Next`语句)。  
  
 `line`  
 可选。 指定所需的代码行处继续执行`line`参数。 `line`参数是行标签或行号，必须在同一过程中作为错误处理程序。  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  我们建议使用只要有可能，在代码中的结构化的异常处理，而不是使用非结构化的异常处理和`On Error`和`Resume`语句。 有关详细信息，请参阅 [Try...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
 如果使用`Resume`语句中任何位置以外的其他错误处理例程中，将出错。  
  
 `Resume`语句不能包含任何过程中使用`Try...Catch...Finally`语句。  
  
## <a name="example"></a>示例  
 此示例使用`Resume`语句来结束的错误处理过程中，然后继续执行导致错误的语句。 错误号 55 生成举例说明使用`Resume`语句。  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>要求  
 **命名空间：**[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **程序集：** Visual Basic 运行库（在 Microsoft.VisualBasic.dll 中）  
  
## <a name="see-also"></a>请参阅

- [Try...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Error 语句](../../../visual-basic/language-reference/statements/error-statement.md)
- [On Error 语句](../../../visual-basic/language-reference/statements/on-error-statement.md)
