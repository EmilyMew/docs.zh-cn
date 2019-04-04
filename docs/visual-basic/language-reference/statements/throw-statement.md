---
title: Throw 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: 2494eac2f61f112f3ba6321ada7404f8cd618049
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821361"
---
# <a name="throw-statement-visual-basic"></a>Throw 语句 (Visual Basic)
引发异常过程中。  
  
## <a name="syntax"></a>语法  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a>部件  
 `expression`  
 提供有关要引发的异常信息。 驻留在中时是可选的`Catch`语句，另有要求。  
  
## <a name="remarks"></a>备注  
 `Throw`语句将引发异常，您可以使用结构化异常处理代码来处理 (`Try`...`Catch`...`Finally`) 或非结构化的异常处理代码 (`On Error GoTo`)。 可以使用`Throw`语句来捕获在代码中的错误，因为直到找到相应的异常处理代码，Visual Basic 调用堆栈向上移动。  
  
 一个`Throw`不包含表达式的语句仅可在`Catch`语句，在其中 case 语句重新引发当前处理的异常`Catch`语句。  
  
 `Throw`语句将重置的调用堆栈`expression`异常。 如果`expression`未提供，调用堆栈将保持不变。 您可以访问通过异常的调用堆栈<xref:System.Exception.StackTrace%2A>属性。  
  
## <a name="example"></a>示例  
 下面的代码使用`Throw`语句引发异常：  
  
 [!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]  
  
## <a name="requirements"></a>要求  
 **命名空间：**[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **模块：** `Interaction`  
  
 **程序集：** Visual Basic 运行库（在 Microsoft.VisualBasic.dll 中）  
  
## <a name="see-also"></a>请参阅

- [Try...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [On Error 语句](../../../visual-basic/language-reference/statements/on-error-statement.md)
