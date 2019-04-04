---
title: 枚举的基础类型 <typename> 不符合 CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 636fcc36e7bac52467998dc9c59f14ba1bedead3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831483"
---
# <a name="underlying-type-typename-of-enum-is-not-cls-compliant"></a>基础类型\<类型名称 > 的枚举不符合 cls 的
为此枚举不是指定的数据类型的一部分[语言独立性和与语言无关的组件](../../../standard/language-independence-and-language-independent-components.md)(CLS)。 这不是在组件中，一个错误，因为[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]和 Visual Basic 支持此数据类型。 但是，在严格符合 cls 的代码中编写的另一个组件可能不支持此数据类型。 此类组件可能不能成功与您的组件进行交互。  
  
 以下 Visual Basic 数据类型不符合 CLS 規格：  
  
-   [SByte 数据类型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger 数据类型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong 数据类型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort 数据类型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的详细信息，请参见 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **错误 ID:** BC40032  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   如果你的组件接口与其他[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]组件，或者在不与任何其他组件接口中，不需要进行任何更改。  
  
-   如果你没有为编写的组件与交互[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]，您可能能够确定，请通过反射或从文档中，它是否支持此数据类型。 如果是这样，您不需要更改任何内容。  
  
-   如果你与不支持此数据类型的组件交互，您必须将其替换的最接近的符合 cls 的类型。 例如，如果不需要 2147483647 以上的数值范围，可以使用 `UInteger` 取代 `Integer` 。 如果确实需要更大范围，可以用 `UInteger` 代替 `Long`。  
  
-   如果在与自动化或 COM 对象对接，请记住，某些类型具有与 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 中不同的数据宽度。 例如，`uint` 在其他环境中通常为 16 位。 如果您将 16 位自变量传递给此类组件，将其作为声明`UShort`而不是`UInteger`中托管的 Visual Basic 代码。  
  
## <a name="see-also"></a>请参阅

- [反射 (Visual Basic)](../../programming-guide/concepts/reflection.md)
- [反射](../../../framework/reflection-and-codedom/reflection.md)
