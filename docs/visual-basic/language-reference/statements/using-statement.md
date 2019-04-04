---
title: Using 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: fe53ea58dc98a4de793fe9dad1c3ceeac71622fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843196"
---
# <a name="using-statement-visual-basic"></a>Using 语句 (Visual Basic)
声明的开头`Using`阻止并根据需要获取块控制的系统资源。  
  
## <a name="syntax"></a>语法  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`resourcelist`|如果未提供所需`resourceexpression`。 该列表的一个或多个系统资源`Using`阻止控件，由逗号分隔。|  
|`resourceexpression`|如果未提供所需`resourcelist`。 引用变量或表达式中引用系统资源，以控制此`Using`块。|  
|`statements`|可选。 语句块的`Using`块将运行。|  
|`End Using`|必需。 终止的定义`Using`块和控制的所有资源。|  
  
 在每个资源`resourcelist`部分具有以下语法和部分：  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 或  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>resourcelist 部件  
  
|术语|定义|  
|---|---|  
|`resourcename`|必需。 指的是一种系统资源的引用变量的`Using`阻止控件。|  
|`New`|如果使用`Using`语句将获取该资源。 如果你已获取资源，使用第二个语法替代方法。|  
|`resourcetype`|必需。 资源的类。 类必须实现<xref:System.IDisposable>接口。|  
|`arglist`|可选。 要传递给要创建的实例的构造函数的参数列表的`resourcetype`。 请参阅[参数列表](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`resourceexpression`|必需。 为满足要求的系统资源引用变量或表达式`resourcetype`。 如果使用第二个语法替代方法，您必须将控制权传递给之前获取资源`Using`语句。|  
  
## <a name="remarks"></a>备注  
 有时你的代码需要非托管的资源，如文件句柄、 COM 包装器或 SQL 连接。 一个`Using`块确保一个或多个此类资源的释放你的代码完成与之时。 这使它们可用于其他代码使用。  
  
 托管的资源释放由.NET Framework 垃圾回收器 (GC) 而无需您采取任何额外的编码。 不需要`Using`托管资源的块。 但是，仍可以使用`Using`块以强制释放托管资源而不是等待垃圾回收器。  
  
 一个`Using`块都有三个部分： 获取、 使用情况和可供使用。  
  
-   *获取*意味着创建变量并将其初始化，以便向系统资源，请参阅。 `Using`语句可以获取一个或多个资源，也可以在进入块之前获取恰好一个资源，其提供给`Using`语句。 如果你提供`resourceexpression`，必须在将控制权传递给之前获取资源`Using`语句。  
  
-   *使用情况*意味着访问资源并使用它们执行操作。 之间的语句`Using`和`End Using`表示资源的使用。  
  
-   *处置*方法调用<xref:System.IDisposable.Dispose%2A>方法中的对象上`resourcename`。 这允许要明确终止其资源的对象。 `End Using`语句释放的资源下`Using`块的控件。  
  
## <a name="behavior"></a>行为  
 一个`Using`块的行为类似于`Try`...`Finally`中的构造`Try`块使用的资源和`Finally`块释放它们。 正因为如此，`Using`块可保证可供使用的资源，不管您如何退出块。 即使发生未经处理的异常，也是如此除<xref:System.StackOverflowException>。  
  
 获取的每个资源变量的作用域`Using`语句仅限于`Using`块。  
  
 如果指定多个中的系统资源`Using`语句，效果是相同像您嵌套`Using`块相互。  
  
 如果`resourcename`是`Nothing`，没有调用<xref:System.IDisposable.Dispose%2A>进行，并且不会引发异常。  
  
## <a name="structured-exception-handling-within-a-using-block"></a>结构化的异常处理在使用块  
 如果需要处理中可能发生的异常`Using`块中，你可以添加整个`Try`...`Finally`到它的构造。 如果您需要处理这种情况其中`Using`语句不是成功地获取资源，可以进行测试以查看是否`resourcename`是`Nothing`。  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>结构化的异常处理而不使用块  
 如果您需要的资源，获取更好地控制或者需要其他代码中的`Finally`块中，您可以重写`Using`作为阻止`Try`...`Finally`构造。 下面的示例演示主干`Try`并`Using`构造等效中获取和释放`resource`。  
  
```vb  
Using resource As New resourceType   
    ' Insert code to work with resource.  
End Using  
  
' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.  
Dim resource As New resourceType  
Try   
    ' Insert code to work with resource.  
Finally   
    If resource IsNot Nothing Then  
        resource.Dispose()   
    End If  
End Try   
```  
  
> [!NOTE]
>  中的代码`Using`块中的对象不分配`resourcename`到另一个变量。 当您退出`Using`块时，资源将被释放，和另一个变量不能访问它所指向的资源。  
  
## <a name="example"></a>示例  
 以下示例创建名为 log.txt 和两行文本写入文件的文件。 该示例还读取该同一个文件，并显示的文本行。  
  
 因为<xref:System.IO.TextWriter>并<xref:System.IO.TextReader>类将实现<xref:System.IDisposable>接口，该代码可以使用`Using`语句，以确保该文件正确关闭后写入和读取操作。  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.IDisposable>
- [Try...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [如何：释放系统资源](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
