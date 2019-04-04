---
title: 参数列表 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 651f08812032aa1c5aacc04fdb3d7f491f12b607
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836280"
---
# <a name="parameter-list-visual-basic"></a>参数列表 (Visual Basic)
指定过程需要被调用时的参数。 由逗号分隔多个参数。 下面是一个参数的语法。  
  
## <a name="syntax"></a>语法  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a>部件  
 `attributelist`  
 可选。 将应用于此参数的特性的列表。 必须将[属性列表](../../../visual-basic/language-reference/statements/attribute-list.md)括进尖括号 ("`<`"和"`>`")。  
  
 `Optional`  
 可选。 指定此参数不需要时调用该过程。  
  
 `ByVal`  
 可选。 指定该过程不能替换或重新分配基础调用代码中的相应参数的变量元素。  
  
 `ByRef`  
 可选。 指定该过程可以用相同的方式与调用代码本身可以修改调用代码中的基础变量元素。  
  
 `ParamArray`  
 可选。 指定的参数列表中的最后一个参数是指定的数据类型的元素的可选数组。 这允许将任意数量的参数传递给过程的调用代码。  
  
 `parametername`  
 必需。 表示参数的本地变量的名称。  
  
 `parametertype`  
 需要`Option Strict`是`On`。 表示参数的本地变量的数据类型。  
  
 `defaultvalue`  
 所需的`Optional`参数。 任何常量或常量表达式的计算结果为该参数的数据类型。 如果类型为`Object`，或类、 接口、 数组或结构，默认值只能是`Nothing`。  
  
## <a name="remarks"></a>备注  
 参数是用括号括起来，并且用逗号隔开。 可以使用任何数据类型声明的参数。 如果未指定`parametertype`，则默认为`Object`。  
  
 当调用的代码调用该过程时，会传递*自变量*到每个所需的参数。 有关详细信息，请参阅[差异之间形参和实参](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)。  
  
 调用代码将传递给每个参数的参数是指向中调用代码的基础元素。 如果此元素是*不可变元素*（常量、 文本、 枚举或表达式），就无法更改它的任何代码。 如果它是*变量*元素 （声明的变量、 字段、 属性、 数组元素或结构元素），调用代码可以对其进行更改。 有关详细信息，请参阅[差异之间可修改和不可修改自变量](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)。  
  
 如果传递的变量元素`ByRef`，该过程它也可以进行更改。 有关详细信息，请参阅[差异之间传递参数值和按引用来](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
## <a name="rules"></a>规则  
  
-   **括号。** 如果指定的参数列表，则必须将其括在括号中。 如果没有任何参数，仍可以使用括号内包含一个空列表。 这将通过清晰化元素一个过程提高代码的可读性。  
  
-   **可选参数。** 如果您使用`Optional`参数的修饰符，列表中的所有后续参数也是可选和通过使用声明`Optional`修饰符。  
  
     每个可选参数声明必须提供`defaultvalue`子句。  
  
     有关详细信息，请参阅[可选参数](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)。  
  
-   **参数数组。** 必须指定`ByVal`为`ParamArray`参数。  
  
     不能使用两者`Optional`和`ParamArray`相同的参数列表中。  
  
     有关详细信息，请参阅[参数数组](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)。  
  
-   **传递机制。** 每个参数的默认机制是`ByVal`，这意味着该过程不能更改基础变量元素。 但是，如果元素是引用类型，该过程可以修改内容或成员的基础对象，即使它不能替换或重新分配对象本身。  
  
-   **参数名称。** 如果参数的数据类型是一个数组，请按照`parametername`紧跟括号。 参数名称的详细信息，请参阅[声明的元素名称](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示`Function`定义两个参数的过程。  
  
 [!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Declare 语句](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Structure 语句](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [属性概述](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [如何：在代码中拆分和合并语句](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
