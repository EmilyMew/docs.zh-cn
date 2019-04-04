---
title: 过程重载 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 6e8d1fa72c60c4fa3d2237ad24c2d1b4891a7bf2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828233"
---
# <a name="procedure-overloading-visual-basic"></a>过程重载 (Visual Basic)
*重载*过程是指在多个版本中，使用相同名称但不同的参数列表定义。 重载的目的是定义一个过程的几个密切相关的版本而无需将它们按名称区分开。 通过不同的参数列表执行此操作。  
  
## <a name="overloading-rules"></a>重载规则  
 当重载的过程时，以下规则适用：  
  
-   **相同的名称**。 每个重载的版本必须使用相同的过程名称。  
  
-   **不同的签名**。 每个重载的版本必须不同于至少一个以下方面中的所有其他重载版本：  
  
    -   参数数目  
  
    -   参数的顺序  
  
    -   参数的数据类型  
  
    -   （针对泛型过程） 的类型参数的数目  
  
    -   （仅适用于转换运算符） 的返回类型  
  
     前面的项目统称为过程名称，以及*签名*的过程。 当您调用重载的过程时，编译器将使用签名来检查在调用与定义正确匹配。  
  
-   **项不属于签名**。 如果不改变签名，不能重载的过程。 具体而言，不能通过只改变一个或多个以下各项的重载的过程：  
  
    -   过程修饰符关键字，如`Public`， `Shared`，和 `Static`  
  
    -   参数或类型参数名称  
  
    -   （针对泛型过程） 的类型参数约束  
  
    -   参数修饰符关键字，如`ByRef`和 `Optional`  
  
    -   它是否返回一个值  
  
    -   （除转换运算符） 的返回值数据类型  
  
     前面列表中的项不是签名的一部分。 虽然不能使用它们来区分重载版本，您可以更改它们之间按它们的签名正确区分的重载版本。  
  
-   **后期绑定的参数**。 如果你想要将后期绑定的对象变量传递给的重载版本，必须声明为适当的参数<xref:System.Object>。  
  
## <a name="multiple-versions-of-a-procedure"></a>一个过程的多个版本  
 假设您要编写`Sub`过程发送事务对客户的余额，和你想要能够按名称或帐户号码，请参阅客户。 若要解决此问题，可以定义两个不同`Sub`过程，如以下示例所示：  
  
 [!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]  
  
### <a name="overloaded-versions"></a>重载的版本  
 一种替代方法是重载的单个过程名称。 可以使用[重载](../../../../visual-basic/language-reference/modifiers/overloads.md)关键字来定义每个参数列表中，该过程的版本，如下所示：  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
#### <a name="additional-overloads"></a>其他重载  
 如果还想要接受在事务量`Decimal`或`Single`，可进一步重载`post`允许用于此变体。 如果执行此操作会为每个重载中前面的示例中，有四个`Sub`过程，所有具有相同名称但具有四个不同的签名。  
  
## <a name="advantages-of-overloading"></a>重载的优点  
 重载过程的优点是在调用的灵活性。 若要使用`post`过程声明在前面的示例中，调用代码可以获取为客户标识`String`或`Integer`，然后在任一情况下调用相同的过程。 下面的示例阐释了这一点：  
  
 [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
 [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [如何：定义一个过程的多个版本](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：调用重载的过程](./how-to-call-an-overloaded-procedure.md)
- [如何：重载带有可选参数的过程](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：重载的参数数量不确定的过程](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [重载过程注意事项](./considerations-in-overloading-procedures.md)
- [重载决策](./overload-resolution.md)
- [重载](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Visual Basic 中的泛型类型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
