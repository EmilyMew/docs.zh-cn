---
title: 如何：重载的参数 (Visual Basic 中) 的数量不确定的过程
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: bae420e88a74fbe3f7e8ad3592133fdcaf191029
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838984"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>如何：重载的参数 (Visual Basic 中) 的数量不确定的过程
如果某个过程带有[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)参数，不能定义采用一维数组的参数数组的重载的版本。 有关详细信息，请参阅"隐式重载为 ParamArray 参数"中[中重载过程注意事项](./considerations-in-overloading-procedures.md)。  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>若要重载采用可变数量的参数的过程  
  
1.  确定该过程，并调用代码逻辑受益于重载从多个版本`ParamArray`参数。 请参阅中"重载和参数"[重载过程注意事项](./considerations-in-overloading-procedures.md)。  
  
2.  确定提供的值的数字应接受过程的参数列表的可变部分中。 这可能包括没有值，这种情况，并且它可能包含单个的一维数组的大小写。  
  
3.  对于每个可接受提供的值数，将写入`Sub`或`Function`定义相应的参数列表的声明语句。 不使用任一`Optional`或`ParamArray`此重载版本中的关键字。  
  
4.  在每个声明中前, 加上`Sub`或`Function`关键字[重载](../../../../visual-basic/language-reference/modifiers/overloads.md)关键字。  
  
5.  以下每个声明，编写调用代码提供对应于该声明的参数列表的值时应执行的过程代码。  
  
6.  终止与每个过程`End Sub`或`End Function`语句作为相应。  
  
## <a name="example"></a>示例  
 下面的示例演示使用定义的过程[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)参数，然后一组等效的重载的过程。  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 不能重载采用一维数组的参数数组的参数列表的此类的过程。 但是，可以使用其他隐式重载的签名。 下面的声明说明这一点。  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 在重载版本中的代码不需要测试调用代码提供的一个或多个值是否`ParamArray`参数，或如果是这样，多少。 Visual Basic 将控制传递给调用的参数列表匹配的版本。  
  
## <a name="compiling-the-code"></a>编译代码  
 因为与过程`ParamArray`参数相当于一组重载版本，不能重载带有对应到任何这些隐式重载的参数列表的此类的过程。 有关详细信息，请参阅[中重载过程注意事项](./considerations-in-overloading-procedures.md)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 每当处理数组可以是无限期较大，则存在无限大的某种内部容量的应用程序的风险。 如果接受一个参数数组时，应测试调用代码传递给它，该数组的长度，并采取相应措施，如果你的应用程序太大。  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [可选参数](./optional-parameters.md)
- [参数数组](./parameter-arrays.md)
- [过程重载](./procedure-overloading.md)
- [过程疑难解答](./troubleshooting-procedures.md)
- [如何：定义一个过程的多个版本](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：调用重载的过程](./how-to-call-an-overloaded-procedure.md)
- [如何：重载带有可选参数的过程](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [重载决策](./overload-resolution.md)
