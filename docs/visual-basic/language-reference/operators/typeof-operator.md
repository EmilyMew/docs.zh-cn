---
title: TypeOf 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 7162fcc24595bbb16d268d5d9e1ea4d82f6e67fb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829858"
---
# <a name="typeof-operator-visual-basic"></a>TypeOf 运算符 (Visual Basic)
将对象引用变量与数据类型进行比较。  
  
## <a name="syntax"></a>语法  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>部件  
 `result`  
 返回。 一个 `Boolean` 值。  
  
 `objectexpression`  
 必需。 计算结果为引用类型的任何表达式。  
  
 `typename`  
 必需。 任何数据类型名。  
  
## <a name="remarks"></a>备注  
 `TypeOf` 运算符确定 `objectexpression` 的运行时类型是否与 `typename` 兼容。 兼容性取决于 `typename` 的类型类别。 下表显示如何确定兼容性。  
  
|`typename` 的类型类别|兼容性条件|  
|---------------------------------|-----------------------------|  
|类|`objectexpression` 属于类型 `typename` 或继承自 `typename`|  
|结构|`objectexpression` 属于类型 `typename`|  
|接口|`objectexpression` 实现 `typename` 或继承自实现 `typename` 的类|  
  
 如果 `objectexpression` 的运行时类型满足兼容性条件，则 `result` 是 `True`。 否则 `result` 为 `False`。  如果 `objectexpression` 为 null，则 `TypeOf`...`Is` 返回 `False`，...`IsNot` 返回 `True`。  
  
 `TypeOf` 始终与 `Is` 关键字一起使用来构造 `TypeOf`...`Is` 表达式，或与 `IsNot` 关键字一起使用来构造 `TypeOf`...`IsNot` 表达式。  
  
## <a name="example"></a>示例  
 下面的示例使用 `TypeOf`...`Is` 表达式测试具有不同数据类型的两个对象引用变量的类型兼容性。  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 变量 `refInteger` 具有运行时类型 `Integer`。 它与 `Integer` 兼容，但不与 `Double` 兼容。 变量 `refForm` 具有运行时类型 <xref:System.Windows.Forms.Form>。 它与 <xref:System.Windows.Forms.Form> 兼容因为这是其类型，与 <xref:System.Windows.Forms.Control> 兼容因为 <xref:System.Windows.Forms.Form> 继承自 <xref:System.Windows.Forms.Control>，与 <xref:System.ComponentModel.IComponent> 兼容因为 <xref:System.Windows.Forms.Form> 继承自 <xref:System.ComponentModel.Component>（它实现 <xref:System.ComponentModel.IComponent>）。 但是，`refForm` 与 <xref:System.Windows.Forms.Label> 不兼容。  
  
## <a name="see-also"></a>请参阅

- [Is 运算符](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 运算符](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [在 Visual Basic 中的比较运算符](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [运算符和表达式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
