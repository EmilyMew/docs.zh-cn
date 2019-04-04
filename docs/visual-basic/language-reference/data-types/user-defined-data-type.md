---
title: 用户定义数据类型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 5fe12d18c7f403c1a50ed548a260ba39e83280eb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814185"
---
# <a name="user-defined-data-type"></a>用户定义的数据类型
在您定义的格式保存数据。 `Structure`语句定义的格式。  
  
 早期版本的 Visual Basic 支持用户定义类型 (UDT)。 当前版本扩展了到 UDT*结构*。 结构是一个或多个串联*成员*的各种数据类型。 Visual Basic 将结构作为单个单元，尽管您还可以单独访问其成员。  
  
## <a name="remarks"></a>备注  
 定义和使用结构数据类型，或无基本数据类型满足你的需求时您需要将各种数据类型组合到单个单元。  
  
 结构的数据类型的默认值由其每个成员的默认值的组合组成。  
  
## <a name="declaration-format"></a>声明格式  
 在结构声明开头[Structure 语句](../../../visual-basic/language-reference/statements/structure-statement.md)结尾`End Structure`语句。 `Structure`语句提供的结构，这也是该结构定义的数据类型的标识符的名称。 代码的其他部分可以使用此标识符来声明变量、 参数和函数返回值为此结构的数据类型。  
  
 之间的声明`Structure`和`End Structure`语句定义的结构的成员。  
  
## <a name="member-access-levels"></a>成员访问级别  
 必须声明使用每个成员[Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)或指定访问级别，例如语句[公共](../../../visual-basic/language-reference/modifiers/public.md)，[友元](../../../visual-basic/language-reference/modifiers/friend.md)，或[专用](../../../visual-basic/language-reference/modifiers/private.md). 如果使用`Dim`语句中，为公共访问级别默认设置。  
  
## <a name="programming-tips"></a>编程提示  
  
-   **内存占用情况。** 与所有复合数据类型，不能安全地通过同时添加其成员的名义存储分配计算结构的内存总消耗。 此外，不能安全地假定已在内存中存储的顺序声明的顺序相同。 如果需要控制结构的存储布局，你可以申请<xref:System.Runtime.InteropServices.StructLayoutAttribute>属性为`Structure`语句。  
  
-   **互操作注意事项。** 如果你与不是为.NET Framework 编写的组件交互，如自动化或 COM 对象，请记住，在其他环境中的用户定义类型都不兼容使用 Visual Basic 的结构类型。  
  
-   **扩大转换。** 没有自动转换到或从任何结构的数据类型。 可以使用在结构上定义转换运算符[Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)，并可以声明为每个转换运算符`Widening`或`Narrowing`。  
  
-   **类型字符。** 结构的数据类型不具有文本类型字符或标识符类型字符。  
  
-   **Framework 类型。** .NET Framework 中没有相应类型。 从.NET Framework 类继承的所有结构<xref:System.ValueType?displayProperty=nameWithType>，但没有单个结构对应于<xref:System.ValueType?displayProperty=nameWithType>。  
  
## <a name="example"></a>示例  
 下面的示例演示一种结构的声明的大纲。  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [数据类型](../../../visual-basic/language-reference/data-types/index.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Structure 语句](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [结构](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
