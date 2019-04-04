---
title: 类型“<typename>”的“For Each”不明确，因为此类型实现了“System.Collections.Generic.IEnumerable(Of T)”的多个实例化
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 6c34ca43decc3c5d8c72b529d8f51d7cc3b0c6b3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833381"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a>For Each 类型\<类型名称 > 不明确，因为该类型实现多个实例化的 System.Collections.Generic.IEnumerable (Of T)
一个`For Each`语句指定具有多个迭代器变量<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。  
  
 迭代器变量必须实现的类型<xref:System.Collections.IEnumerable?displayProperty=nameWithType>或<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>中的一个接口`Collections`的命名空间[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。 就可以实现多个构造的泛型接口，使用不同的类型参数对每个构造的类。 如果执行此类用于迭代器变量，该变量将包含多个<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。 在这种情况下，Visual Basic 不能选择要调用的方法。  
  
 **错误 ID:** BC32096  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   使用[DirectCast 运算符](../../../visual-basic/language-reference/operators/directcast-operator.md)或[TryCast 运算符](../../../visual-basic/language-reference/operators/trycast-operator.md)若要强制转换为接口定义的迭代器变量类型<xref:System.Collections.IEnumerable.GetEnumerator%2A>你想要使用的方法。  
  
## <a name="see-also"></a>请参阅

- [For Each...Next 语句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [接口](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
