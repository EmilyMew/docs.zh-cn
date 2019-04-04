---
title: 代码中用作元素名称的关键字 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: c247ada67f6554362f287cf252dd49856c4995da
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841142"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>代码中用作元素名称的关键字 (Visual Basic)
任何程序元素，如变量、 类或成员，可以具有相同的名称与限制性关键字。 例如，可以创建一个名为变量`Loop`。 但是，来引用它的版本 — 有为受限制的相同名称`Loop`关键字，必须使用完全限定字符串在其之前或将其括在方括号 (`[ ]`)，如下面的示例所示。  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 如果不做其中一种，则 Visual Basic 假设使用的是内部`Loop`关键字，并生成错误，如以下示例所示：  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 指窗体和控件，以及在可以使用方括号声明的变量或与限制性关键字定义具有相同名称的过程。 它可以很容易忘记限定名称或包含方括号，并因此将错误引入到你的代码，使其难以阅读。 出于此原因，我们建议不使用受限制的关键字作为程序元素的名称。 但是，如果将来的 Visual Basic 版本定义了一个新的关键字冲突，与现有窗体或控件名称，然后您可以使用这种方法更新你的代码时以使用新版本。  
  
> [!NOTE]
>  程序还可能包括提供的其他引用的程序集的元素名称。 如果这些名称与受限制的关键字冲突，然后加上方括号括它们会导致 Visual Basic，若要将其解释为您定义的元素。  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命名约定](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [程序结构和代码约定](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [关键字](../../../visual-basic/language-reference/keywords/index.md)
