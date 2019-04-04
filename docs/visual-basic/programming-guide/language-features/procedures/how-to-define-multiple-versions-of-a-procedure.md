---
title: 如何：定义多个版本的过程 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: c31c9ad05af04aec5dc41790aea530c62611f500
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841160"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>如何：定义多个版本的过程 (Visual Basic)
你可以通过多个版本中定义的过程*重载*它为每个版本使用相同名称但不同的参数列表。 重载的目的是定义一个过程的几个密切相关的版本而无需将它们按名称区分开。  
  
 有关更多信息，请参见 [Procedure Overloading](./procedure-overloading.md)。  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>若要定义一个过程的多个版本  
  
1.  编写`Sub`或`Function`你想要定义的过程的每个版本的声明语句。 在每个声明中使用相同的过程名称。  
  
2.  前加上`Sub`或`Function`具有每个声明中的关键字[重载](../../../../visual-basic/language-reference/modifiers/overloads.md)关键字。 可以选择性地省略`Overloads`在声明中，但如果您将其包含在任何声明，您必须将其包括在每个声明。  
  
3.  以下每个声明语句中，编写过程代码以处理其中调用代码提供该版本的参数列表匹配的实参的特定情况。 无需测试提供的参数调用的代码具有控制权。 Visual Basic 将控制传递给您的过程的匹配版本。  
  
4.  终止与过程的每个版本`End Sub`或`End Function`语句作为相应。  
  
## <a name="example"></a>示例  
 下面的示例定义`Sub`过程发送针对客户的帐户余额的事务。 它使用`Overloads`关键字来定义两个版本的过程中，一个接受由名称和其他客户的帐号。  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 调用代码可以获取为客户标识号`String`或`Integer`，然后在任一情况下使用相同的调用语句。  
  
 有关如何调用这些版本的信息`post`过程中，请参阅[如何：调用重载的过程](./how-to-call-an-overloaded-procedure.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 请确保每个重载版本都有相同的过程名称但不同的参数列表。  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [过程疑难解答](./troubleshooting-procedures.md)
- [如何：重载带有可选参数的过程](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：重载的参数数量不确定的过程](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [重载过程注意事项](./considerations-in-overloading-procedures.md)
- [重载决策](./overload-resolution.md)
