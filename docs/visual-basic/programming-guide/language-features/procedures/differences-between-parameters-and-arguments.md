---
title: 参数和变量之间的差异 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: a69b956c7cffcc2a26916d6fc92f23dd4e2322d7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838971"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>参数和变量之间的差异 (Visual Basic)
在大多数情况下，一个过程必须有已在其中调用它的情况有关的一些信息。 执行重复或共享任务的过程为每个调用使用不同的信息。 此信息包括变量、 常量和表达式在调用时传递给该过程。  
  
 将此信息传递给该过程，该过程定义*参数*，然后调用代码将传递*自变量*给该参数。 您可以将参数作为一个停车和当作一辆汽车的参数。 就像在不同的时间，不同的汽车可以放置停车空间中，调用代码可传递不同的参数相同的参数每次调用该过程。  
  
## <a name="parameters"></a>参数  
 一个*参数*表示该过程希望你传递时调用它的值。 该过程的声明定义其参数。  
  
 在定义`Function`或`Sub`过程中，指定*参数列表*在紧跟过程名称的括号中。 对于每个参数，请指定一个名称、 数据类型，并传递机制 ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md))。 您还可以指示参数是可选。 这意味着调用代码不需要传递的值。  
  
 每个参数的名称用作*局部变量*过程中。 使用参数名称使用任何其他变量的方法相同。  
  
## <a name="arguments"></a>自变量  
 *自变量*表示在调用过程时传递给过程参数的值。 当调用该过程时，调用代码将提供参数。  
  
 当您调用`Function`或`Sub`过程，包括*自变量列表*在紧跟过程名称的括号中。 每个自变量对应于列表中的同一位置中的参数。  
  
 与参数定义不同的参数没有名称。 每个自变量是一个表达式，它可以包含零或多个变量、 常量和文本。 表达式的计算结果的数据类型通常应匹配定义的相应参数的数据类型，并在任何情况下它都可以转换为参数类型。  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [Sub 过程](./sub-procedures.md)
- [Function 过程](./function-procedures.md)
- [属性过程](./property-procedures.md)
- [运算符过程](./operator-procedures.md)
- [如何：为过程定义参数](./how-to-define-a-parameter-for-a-procedure.md)
- [如何：将参数传递给过程](./how-to-pass-arguments-to-a-procedure.md)
- [按值和按引用传递自变量](./passing-arguments-by-value-and-by-reference.md)
- [递归过程](./recursive-procedures.md)
- [过程重载](./procedure-overloading.md)
