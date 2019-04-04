---
title: 特性列表 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 2399ec1342280df101e2818399e0f41f10d9606d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818406"
---
# <a name="attribute-list-visual-basic"></a>特性列表 (Visual Basic)
指定要应用于声明的编程元素的特性。 用逗号分隔多个属性。 下面是一个属性的语法。  
  
## <a name="syntax"></a>语法  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>部件  
|||
|---|---|
|`attributemodifier`|所需应用的源代码文件开头的属性。 可以是[程序集](../../../visual-basic/language-reference/modifiers/assembly.md)或[模块](../../../visual-basic/language-reference/modifiers/module-keyword.md)。|
|`attributename`| 必需。 属性的名称。|
|`attributearguments`|可选。 为此特性的位置自变量的列表。 由逗号分隔多个自变量。|
|`attributeinitializer`|可选。 此属性的变量或属性初始值设定项的列表。 由逗号分隔多个初始值设定项。|
  
## <a name="remarks"></a>备注  
 可以将一个或多个特性应用于几乎任何编程元素 （类型、 过程、 属性等）。 属性出现在程序集的元数据，并且它们可以帮助您批注代码，或指定如何使用特定的编程元素。 您可以应用由 Visual Basic 和.NET Framework 中，定义的特性，可以定义自己的属性。  

 有关何时使用属性的详细信息，请参阅[的特性概述](../../../visual-basic/programming-guide/concepts/attributes/index.md)。 属性名称的信息，请参阅[声明的元素名称](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## <a name="rules"></a>规则  
  
-   **放置。** 可以将特性应用于最声明的编程元素。 若要将应用一个或多个属性，将置于*特性块*元素声明的开头。 在属性列表中的每个条目指定你想要将应用，一个属性、 修饰符和自变量将用于此属性的调用。  
  
-   **尖括号。** 如果提供的属性列表，则必须将其括在尖括号中 ("`<`"和"`>`")。  
  
-   **声明的一部分。** 该属性必须是元素声明，而不是单独语句的一部分。 您可以使用行继续符序列 (" `_`") 来扩展到多个源代码行上的声明语句。  
  
-   **修饰符。** 特性修饰符 (`Assembly`或`Module`) 上应用到编程元素中的源文件开头的每个属性必需的。 应用于不在源文件开头的元素的特性不允许出现特性修饰符。  
  
-   **自变量。** 属性的所有位置参数必须位于任何变量或属性初始值设定项之前。  
  
## <a name="example"></a>示例  
 下面的示例应用<xref:System.Runtime.InteropServices.DllImportAttribute>属性的主干定义为`Function`过程。  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> 指示特性化的过程表示非托管动态链接库 (DLL) 中的入口点。 该属性提供的 DLL 名称作为位置自变量和变量初始值设定项与其他信息。  
  
## <a name="see-also"></a>请参阅

- [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)
- [Module \<关键字>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [属性概述](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [如何：在代码中拆分和合并语句](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
