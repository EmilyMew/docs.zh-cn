---
title: 如何：重载带有可选参数 (Visual Basic 中) 的过程
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 070d641d5a8b683ddfe06039117cc4a8507102df
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827623"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>如何：重载带有可选参数 (Visual Basic 中) 的过程
如果过程具有一个或多个[可选](../../../../visual-basic/language-reference/modifiers/optional.md)参数，不能定义任何其隐式重载匹配的重载的版本。 详细信息，请参阅"隐式重载可选参数的"中[中重载过程注意事项](./considerations-in-overloading-procedures.md)。  
  
## <a name="one-optional-parameter"></a>一个可选参数  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>若要重载采用一个可选参数的过程  
  
1.  编写`Sub`或`Function`包含可选参数在参数列表中的声明语句。 不要使用`Optional`此重载版本中的关键字。  
  
2.  前加上`Sub`或`Function`关键字[重载](../../../../visual-basic/language-reference/modifiers/overloads.md)关键字。  
  
3.  编写调用代码提供的可选参数时应执行的过程代码。  
  
4.  终止与过程`End Sub`或`End Function`语句作为相应。  
  
5.  编写用于等同于第一个声明，只不过它不包括可选参数在参数列表中的第二个声明语句。  
  
6.  编写调用代码不会提供的可选参数时应执行的过程代码。 终止与过程`End Sub`或`End Function`语句作为相应。  
  
     以下示例显示带可选参数，一组等效的两个重载的过程，以及最后无效且有效的重载版本的示例定义的过程。  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>多个可选参数  
 对于具有多个可选参数的过程，通常需要两个以上的重载的版本。 例如，如果有两个可选参数，并且调用代码可以提供或省略独立于其他每个，你需要四个重载的版本，一个针对每个可能提供的参数的组合。  
  
 可选参数的数量增加时，会增加重载的复杂性。 除非提供的参数的某些组合不是可接受的对于 N 个可选参数中需要 2 ^ N 重载版本。 具体取决于该过程的性质，可能会发现的逻辑清晰度对齐定义所有重载的版本的额外的工作。  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>若要重载采用多个可选参数的过程  
  
1.  确定过程的逻辑可以接受提供的可选自变量的组合。 如果依赖于另一个可选参数，则可能会出现不可接受的组合。 例如，如果一个参数接受配偶的名称，而另一个接受配偶的年龄，是不可接受的参数提供年龄，但省略名称组合。  
  
2.  对于提供的可选自变量的每个可接受组合，编写`Sub`或`Function`定义相应的参数列表的声明语句。 不要使用`Optional`关键字。  
  
3.  在每个声明中前, 加上`Sub`或`Function`关键字[重载](../../../../visual-basic/language-reference/modifiers/overloads.md)关键字。  
  
4.  以下每个声明，编写调用代码提供该声明的参数列表相对应的参数列表时应执行的过程代码。  
  
5.  终止与每个过程`End Sub`或`End Function`语句作为相应。  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [可选参数](./optional-parameters.md)
- [参数数组](./parameter-arrays.md)
- [过程重载](./procedure-overloading.md)
- [过程疑难解答](./troubleshooting-procedures.md)
- [如何：定义一个过程的多个版本](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：调用重载的过程](./how-to-call-an-overloaded-procedure.md)
- [如何：重载的参数数量不确定的过程](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [重载决策](./overload-resolution.md)
