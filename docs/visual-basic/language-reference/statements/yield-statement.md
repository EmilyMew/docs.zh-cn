---
title: Yield 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: fea91731694f18625e43c5545b353851e72234a6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821083"
---
# <a name="yield-statement-visual-basic"></a>Yield 语句 (Visual Basic)
将发送到集合的下一个元素`For Each...Next`语句。  
  
## <a name="syntax"></a>语法  
  
```  
Yield expression  
```  
  
## <a name="parameters"></a>参数  
  
|术语|定义|  
|---|---|  
|`expression`|必需。 隐式转换为迭代器函数的类型的表达式或`Get`访问器，它包含`Yield`语句。|  
  
## <a name="remarks"></a>备注  
 `Yield`语句返回的集合一次一个元素。 `Yield`语句包含在迭代器函数或`Get`访问器，它对集合执行自定义迭代。  
  
 通过使用迭代器函数[为每个...下一条语句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)或 LINQ 查询。 每次迭代`For Each`循环调用迭代器函数。 当`Yield`语句到达迭代器函数中`expression`返回，并保留在代码中当前的位置。 下次调用迭代器函数时，将从该位置重新开始执行。  
  
 必须存在从类型的隐式转换`expression`在`Yield`到迭代器的返回类型的语句。  
  
 可以使用`Exit Function`或`Return`语句来终止迭代。  
  
 "Yield"不是保留的字且仅当使用中时，它具有特殊含义`Iterator`函数或`Get`访问器。  
  
 有关迭代器函数的详细信息和`Get`访问器，请参阅[迭代器](../../programming-guide/concepts/iterators.md)。  
  
## <a name="iterator-functions-and-get-accessors"></a>迭代器函数和 Get 访问器  
 迭代器函数的声明或`Get`访问器必须满足以下要求：  
  
-   它必须包括[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)修饰符。  
  
-   返回类型必须为 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。  
  
-   它不能有任何`ByRef`参数。  
  
 迭代器函数不能在事件、 实例构造函数、 静态构造函数或静态析构函数中。  
  
 迭代器函数可以是匿名函数。 有关更多信息，请参见 [迭代器](../../programming-guide/concepts/iterators.md)。  
  
## <a name="exception-handling"></a>异常处理  
 一个`Yield`语句可以是内部`Try`块[尝试...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。 一个`Try`具有的块`Yield`语句可以有`Catch`阻止，并且可以具有`Finally`块。  
  
 一个`Yield`语句不能包含在内`Catch`块或`Finally`块。  
  
 如果`For Each`正文 （之外的迭代器函数） 会引发异常，`Catch`未执行迭代器函数中的块，但`Finally`执行迭代器函数中的块。 一个`Catch`迭代器函数内的块将捕获在迭代器函数内部发生的异常。  
  
## <a name="technical-implementation"></a>技术实现  
 下面的代码返回`IEnumerable (Of String)`从迭代器函数，然后循环访问的元素`IEnumerable (Of String)`。  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 对调用`MyIteratorFunction`不会执行该函数的主体。 相反，该调用会将 `IEnumerable(Of String)` 返回到 `elements` 变量中。  
  
 在 `For Each` 循环迭代时，将为 <xref:System.Collections.IEnumerator.MoveNext%2A> 调用 `elements` 方法。 此调用将执行 `MyIteratorFunction` 的主体，直至到达下一个 `Yield` 语句。 `Yield`语句返回一个表达式，用于确定的值不仅`element`循环体使用的变量，但还<xref:System.Collections.Generic.IEnumerator%601.Current%2A>属性的元素，它是`IEnumerable (Of String)`。  
  
 在 `For Each` 循环的每个后续迭代中，迭代器主体的执行将从它暂停的位置继续，直至到达 `Yield` 语句后才会停止。 `For Each`循环完成时的迭代器函数末尾或`Return`或`Exit Function`到达语句。  
  
## <a name="example"></a>示例  
 下面的示例有`Yield`内的语句[为...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)循环。 每次迭代[为每个](../../../visual-basic/language-reference/statements/for-each-next-statement.md)在语句体`Main`会调用`Power`迭代器函数。 对迭代器函数的每个调用将继续到 `Yield` 语句的下一次执行（在 `For…Next` 循环的下一次迭代期间发生）。  
  
 迭代器方法的返回类型是<xref:System.Collections.Generic.IEnumerable%601>，迭代器接口类型。 当调用迭代器方法时，它将返回一个包含数字幂的可枚举对象。  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>示例  
 下面的示例演示一个作为迭代器的 `Get` 访问器。 属性声明包含`Iterator`修饰符。  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 有关其他示例，请参阅[迭代器](../../programming-guide/concepts/iterators.md)。  
  
## <a name="see-also"></a>请参阅

- [语句](../../../visual-basic/language-reference/statements/index.md)
