---
title: 按位置和名称传递自变量 (Visual Basic)
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: b872eda97d1e349ad781b12810e4b166d6e46fe1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837307"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>按位置和名称传递自变量 (Visual Basic)
当您调用`Sub`或`Function`过程中，您可以将参数传递*按位置*— 过程的定义中出现的顺序，或将它们传递*按名称*，而无需考虑位置。  
  
 如果按名称传递参数，指定自变量的声明名称后, 跟一个冒号和等号 (`:=`) 后, 跟参数值。 你可以提供按任意顺序的命名的参数。  
  
 例如，以下`Sub`过程使用三个参数：  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 在调用此过程时，可以提供的参数按位置、 名称，或通过使用这两者的混合。  
  
## <a name="passing-arguments-by-position"></a>按位置传递参数  
 您可以调用`Display`方法及其参数按位置传递，并且用逗号分隔，如下面的示例中所示：  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 如果省略位置自变量列表中的可选自变量，必须保留它以一个逗号后的位置。 下面的示例调用`Display`方法，而`age`参数：  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a>按名称传递自变量  
 或者，可以调用`Display`使用按名称传递参数，还以逗号分隔，如下面的示例中所示：  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 按这种方式中的名称传递自变量时，尤其是调用具有多个可选参数的过程。 如果按名称提供实参，你无需使用连续的逗号来表示缺少位置自变量。 按名称传递自变量还可以更轻松地跟踪的传递以及哪些省略的参数。  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>混合参数按位置和名称  

下面的示例中所示，可以提供参数按位置和通过在单个过程调用中，名称：  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 在前面的示例中，没有多余的逗号，才可保存的位置的省略`age`自变量，因为`birth`按名称传递了。  
  
在 Visual Basic 15.5 之前的版本，在你的混合位置和名称、 位置自变量形式提供参数时都必须放在第一个。 按名称提供参数后, 剩下的自变量必须所有传递的名称。  例如，以下调用到`Display`方法会显示编译器错误[BC30241:需要命名参数](../../../misc/bc30241.md)。

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

从 Visual Basic 15.5 开始，位置自变量可以按照命名的自变量的结束位置自变量是否在正确的位置。 如果在 Visual Basic 15.5 中，以前调用下编译`Display`方法已成功编译并不再生成编译器错误[BC30241](../../../misc/bc30241.md)。  

当你想要使用命名的参数以使代码更具可读性时，此能力混合和匹配命名参数和位置参数按任意顺序是特别有用。 例如，以下`Person`类构造函数需要两个参数的类型`Person`，这两种可能`Nothing`。 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

使用混合命名参数和位置参数有助于使代码意图清除时的值`father`并`mother`自变量是`Nothing`:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

若要执行使用命名参数的位置参数，必须将以下元素添加到 Visual Basic 项目 (\*.vbproj) 文件：

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

有关详细信息请参阅[设置的 Visual Basic 语言版本](../../../language-reference/configure-language-version.md)。

## <a name="restrictions-on-supplying-arguments-by-name"></a>通过名称提供参数的限制  

不能按名称来避免输入所需的参数传递参数。 可以省略仅的可选参数。  
  
不能按名称传递参数数组。 这是因为时调用该过程，你会提供以逗号分隔参数数组的参数数量不确定，编译器不能将多个自变量关联与单个名称。  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [如何：将参数传递给过程](./how-to-pass-arguments-to-a-procedure.md)
- [按值和按引用传递自变量](./passing-arguments-by-value-and-by-reference.md)
- [可选参数](./optional-parameters.md)
- [参数数组](./parameter-arrays.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
