---
title: Call 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 755443a99a1ad8b0430a76d2dba1ff27472d4c9d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832640"
---
# <a name="call-statement-visual-basic"></a>Call 语句 (Visual Basic)
将传输到的控件`Function`， `Sub`，或动态链接库 (DLL) 过程。  
  
## <a name="syntax"></a>语法  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>部件  
|||
|---|---|
|`procedureName`|必需。 要调用的过程的名称。|
|`argumentList`|可选。 变量或表达式表示被调用时传递给过程的参数的列表。 由逗号分隔多个自变量。 如果包含`argumentList`，必须将其括在括号中。|
|||
  
## <a name="remarks"></a>备注  
 可以使用`Call`关键字调用过程时。 对于大多数过程调用，无需使用此关键字。  
  
 通常使用`Call`关键字时被调用的表达式不会启动与的标识符。 使用`Call`作他用的关键字不建议。  
  
 如果该过程返回一个值，`Call`语句将其丢弃。  
  
## <a name="example"></a>示例  
 下面的代码演示两个示例其中`Call`关键字才可调用的过程。 在这两个示例中，被调用的表达式不会启动与的标识符。  
  
 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a>请参阅

- [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Declare 语句](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Lambda 表达式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
