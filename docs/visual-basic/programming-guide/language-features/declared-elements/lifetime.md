---
title: Visual Basic 中的生存期
ms.date: 07/20/2015
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
ms.openlocfilehash: 7a8730834c5241ddb1271d689cdda8942741f15f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824918"
---
# <a name="lifetime-in-visual-basic"></a>Visual Basic 中的生存期
*生存期*已声明元素的是的时间段期间它是可供使用。 变量是唯一具有生存期的元素。 为此，编译器将过程参数和函数返回值视为变量的特殊情况。 变量的生存期表示，它可以在此期间保存值的时间的段。 其值可以更改其生存期内，但它始终保持某些值。  
  
## <a name="different-lifetimes"></a>不同的生存期  
 一个*成员变量*（在模块级别，任何过程之外声明） 通常具有相同的生存期在其中声明的元素。 作为类或结构声明它的每个实例的单独副本存在的类或结构中声明的非共享的变量。 每个此类变量具有相同的生存期与它的实例。 但是，`Shared`变量仅有一个生存期，即持续运行你的应用程序的整个时间。  
  
 一个*局部变量*（在过程内声明） 的过程声明它的运行时才存在。 这同样适用于该过程的参数和返回任何函数。 但是，如果该过程调用其他过程，本地变量保留其值在被调用的过程运行时。  
  
## <a name="beginning-of-lifetime"></a>生存期的开头  
 当控件进入在其中声明该过程，本地变量的生存期开始。 每个本地变量初始化为其数据类型的默认值，只要该过程开始运行。 当该过程遇到`Dim`语句中指定初始值，它将设置这些变量为这些值，即使你的代码必须向其分配了其他值。  
  
 就像一个单独的变量初始化结构变量的每个成员。 同样，分别初始化数组变量的每个元素。  
  
 在过程内的块内声明变量 (如`For`循环) 初始化过程的条目。 曾经执行过你的代码块，这些初始化才会生效。  
  
## <a name="end-of-lifetime"></a>生存期结束  
 当一个过程终止时，不保留其本地变量的值，和 Visual Basic 将回收其内存。 下一次调用该过程中，所有本地变量不用重新创建和重新初始化。  
  
 如果类或结构的实例终止时，其非共享的变量丢失它们的内存以及它们的值。 类或结构的每个新实例创建并重新初始化其非共享的变量。 但是，`Shared`变量被保留，直到你的应用程序停止运行。  
  
## <a name="extension-of-lifetime"></a>生存期的扩展  
 如果声明的本地变量`Static`关键字，它的生存期即时间超过其过程的执行时间。 下表显示了如何在过程声明确定多长时间`Static`变量存在。  
  
|过程位置和共享|静态变量的生存期开始|静态变量的生存期结束|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|（默认情况下共享） 模块中|第一次调用该过程|你的应用程序停止运行时|  
|在类中， `Shared` （过程不是实例成员）|第一次调用该过程的特定实例或类或结构名称本身|你的应用程序停止运行时|  
|类的实例中不`Shared`（过程是一个实例成员）|第一次特定实例上调用该过程|该实例进行垃圾回收 (GC) 的发布时|  
  
## <a name="static-variables-of-the-same-name"></a>具有相同名称的静态变量  
 您可以声明具有多个过程中具有相同名称的静态变量。 如果执行此操作时，Visual Basic 编译器会考虑每个此类变量视为一个单独的元素。 初始化这些变量中的一个不会影响其他值。 这同样适用如果定义有一组重载的过程并声明每个重载中具有相同名称的静态变量。  
  
## <a name="containing-elements-for-static-variables"></a>静态变量的包含元素  
 可以在该类中的过程，即声明在类中，静态局部变量。 但是，不能声明为静态局部变量结构中，为结构成员或为该结构内的一个过程的局部变量。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例声明的变量[静态](../../../../visual-basic/language-reference/modifiers/static.md)关键字。 (请注意，不需要`Dim`关键字时[Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)使用修饰符，如`Static`。)  
  
### <a name="code"></a>代码  
 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>注释  
 在前面的示例中，变量`applesSold`继续执行步骤后存在`runningTotal`返回到调用代码。 下一次`runningTotal`调用时，`applesSold`会保留其以前计算的值。  
  
 如果`applesSold`而无需使用已声明了`Static`，每次调用将不会保留以前的累积的值`runningTotal`。 下一次`runningTotal`调用，则`applesSold`本来会被重新创建和初始化为 0，和`runningTotal`将只返回相同的值与调用它。  
  
### <a name="compiling-the-code"></a>编译代码  
 您可以初始化为其声明的一部分的静态本地变量的值。 如果声明数组为`Static`，可以初始化它的秩 （维数）、 每个维的长度和各个元素的值。  
  
### <a name="security"></a>安全性  
 在前面的示例中，您可以通过声明生成相同的生存期`applesSold`在模块级别。 如果发生这种方式更改变量的作用域，但是，该过程将不再具有独占访问权限。 因为无法访问其他过程`applesSold`并将其值更改、 运行总计可能是不可靠和代码可能会更难以维护。  
  
## <a name="see-also"></a>请参阅

- [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [已声明的元素名称](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [对已声明元素的引用](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [在 Visual Basic 中的作用域](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [在 Visual Basic 中的访问级别](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [变量](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [变量声明](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [数据类型疑难解答](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
