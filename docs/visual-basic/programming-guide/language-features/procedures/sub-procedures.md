---
title: Sub 过程 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: b70594e002bbf08f0890586e78df901ccb26c7ce
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843097"
---
# <a name="sub-procedures-visual-basic"></a>Sub 过程 (Visual Basic)
一个`Sub`过程是 Visual Basic 语句括在一系列`Sub`和`End Sub`语句。 `Sub`过程执行一项任务，再将控制权返回到调用代码，但它不会向调用代码返回值。  
  
 每次调用该过程时，其执行语句，开头的第一个可执行语句后`Sub`语句，并与第一个结束`End Sub`， `Exit Sub`，或`Return`遇到语句。  
  
 您可以定义`Sub`模块、 类和结构中的过程。 默认情况下，它是`Public`，这意味着您可以调用它从任何位置有权访问模块、 类或结构定义它在应用程序中。 字词*方法*，介绍`Sub`或`Function`从其定义的外部访问的过程模块、 类或结构。 有关详细信息，请参阅[过程](./index.md)。  
  
 一个`Sub`过程可以采用自变量，如常量、 变量或表达式，通过调用代码传递给它。  
  
## <a name="declaration-syntax"></a>声明语法  
 声明的语法`Sub`过程如下所示：  
  
 `[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers`可以指定访问级别和重载、 重写、 共享和隐藏有关的信息。 有关详细信息，请参阅[Sub 语句](../../../../visual-basic/language-reference/statements/sub-statement.md)。  
  
## <a name="parameter-declaration"></a>参数声明  
 声明类似于如何声明一个变量，指定参数名称和数据类型的每个过程参数。 此外可以指定的传递机制，和的参数是否可选或参数数组。  
  
 在参数列表中每个参数的语法如下所示：  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*  
  
 如果参数是可选的您还必须提供一个默认值作为其声明的一部分。 用于指定默认值的语法如下所示：  
  
 `Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*  
  
### <a name="parameters-as-local-variables"></a>为本地变量的参数  
 当控制权传递给该过程时，每个参数被视为本地变量。 也就是说，它的生存期即相同过程，并且其作用域是整个过程。  
  
## <a name="calling-syntax"></a>调用语法  
 调用`Sub`显式使用独立的调用语句的过程。 不能在表达式中使用其名称来调用它。 您必须是不可选的所有自变量提供值，必须将参数列表括在括号中。 如果未不提供任何参数，可以选择性地省略括号。 使用`Call`关键字是可选的但不是建议这样做。  
  
 对的调用语法`Sub`过程如下所示：  
  
 `[Call]`  *subname* `[(` *argumentlist* `)]`  
  
 您可以调用`Sub`从外部定义它的类的方法。 首先，您必须使用`New`关键字来创建类的实例或调用的方法返回类的实例。 有关详细信息，请参阅[New 运算符](../../../../visual-basic/language-reference/operators/new-operator.md)。 然后，可以使用以下语法来调用`Sub`实例对象上的方法：  
  
 *对象*。*methodname*`[(`*argumentlist*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>声明和调用的插图  
 以下`Sub`过程通知计算机运算符哪个任务应用程序即将执行，并且还显示时间戳。 而不是重复的每个任务开始时此代码，应用程序只需调用`tellOperator`从不同位置。 每次调用将一个字符串中的传递`task`标识要启动的任务的参数。  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 下面的示例演示对典型调用`tellOperator`。  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [Function 过程](./function-procedures.md)
- [属性过程](./property-procedures.md)
- [运算符过程](./operator-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [Sub 语句](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [如何：调用不返回值的过程](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [如何：在 Visual Basic 中调用事件处理程序](./how-to-call-an-event-handler.md)
