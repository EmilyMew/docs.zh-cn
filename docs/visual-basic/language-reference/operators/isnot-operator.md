---
title: IsNot 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: e07a775eec003a3e488f6909181aed3f742b4b91
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833511"
---
# <a name="isnot-operator-visual-basic"></a>IsNot 运算符 (Visual Basic)
两个对象引用变量进行比较。  
  
## <a name="syntax"></a>语法  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>部件  
 `result`  
 必需。 一个 `Boolean` 值。  
  
 `object1`  
 必需。 任何`Object`变量或表达式。  
  
 `object2`  
 必需。 任何`Object`变量或表达式。  
  
## <a name="remarks"></a>备注  
 `IsNot`运算符确定两个对象引用是否引用不同的对象。 但是，它不会执行值的比较。 如果`object1`并`object2`都是指完全相同的对象实例`result`是`False`; 如果不是这样，`result`是`True`。  
  
 `IsNot` 与完全相反`Is`运算符。 利用`IsNot`是可以避免使用的笨拙语法`Not`和`Is`，这可能很难阅读。  
  
 可以使用`Is`和`IsNot`运算符来测试早期绑定和后期绑定对象。  
  
> [!NOTE]
>  `IsNot`运算符不能用于比较表达式返回从`TypeOf`运算符。 相反，必须使用`Not`和`Is`运算符。  
  
## <a name="example"></a>示例  
 下面的代码示例使用这两个`Is`运算符和`IsNot`运算符，以完成相同的比较。  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a>请参阅

- [Is 运算符](../../../visual-basic/language-reference/operators/is-operator.md)
- [TypeOf 运算符](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [如何：测试两个对象是否相同](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
