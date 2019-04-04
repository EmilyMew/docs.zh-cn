---
title: '#如果......#Else 指令 (Visual Basic)'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
ms.openlocfilehash: 8c0aece749edf144fdd5c8ede9ec7e2e4c96ad54
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823384"
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else 指令
有条件地编译选定的 Visual Basic 代码块。  
  
## <a name="syntax"></a>语法  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a>部件  
 `expression`  
 所需`#If`和`#ElseIf`语句，可选其他位置。 任何表达式，只包含一个或多个条件编译器常量、 文本和运算符的计算结果为`True`或`False`。  
  
 `statements`  
 所需的`#If`块语句，可选其他位置。 Visual Basic 程序行或如果关联的表达式的计算结果为编译的编译器指令`True`。  
  
 `#End If`  
 终止`#If`语句块。  
  
## <a name="remarks"></a>备注  
 表面上看的行为`#If...Then...#Else`指令出现相同的`If...Then...Else`语句。 但是，`#If...Then...#Else`指令评估要编译的编译器，内容而`If...Then...Else`语句在运行时评估条件。  
  
 条件编译通常用于编译不同平台的同一个程序。 它还用来防止调试代码，使其不显示可执行文件。 在条件编译过程中排除的代码完全省略从最终的可执行文件，因此它具有大小或性能没有影响。  
  
 不考虑任何评估结果，将计算所有表达式使用`Option Compare Binary`。 `Option Compare`语句不会影响中的表达式`#If`和`#ElseIf`语句。  
  
> [!NOTE]
>  任何单行形式的`#If`， `#Else`， `#ElseIf`，和`#End If`指令存在。 没有其他代码可以出现在任何指令所在的行。 

条件编译块中的语句必须是完整逻辑语句。 例如，不能有条件地编译仅函数的属性，但可以有条件地声明以及其属性的函数：

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a>示例
 此示例使用`#If...Then...#Else`构造来确定是否编译某些语句。  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>请参阅

- [#Const 指令](../../../visual-basic/language-reference/directives/const-directive.md)
- [If...Then...Else 语句](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [条件编译](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
