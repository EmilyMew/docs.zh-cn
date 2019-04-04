---
title: 延迟的执行和迟缓计算在 LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: b5c3e2a484aa16df22742ddf77d6438ec2a699bb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839026"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>延迟的执行和迟缓计算在 LINQ to XML (Visual Basic)
实现查询和轴操作通常是为了使用延迟执行。 本主题解释延迟执行的要求和优点，以及某些实现注意事项。  
  
## <a name="deferred-execution"></a>延迟执行  
 延迟执行意味着表达式的计算延迟，直到真正需要其实现值为止。 当必须操作大型数据集合，特别是在包含一系列链接的查询或操作的程序中操作时，延迟执行可以大大改善性能。 在最佳情况下，延迟执行只允许对源集合的单个循环访问。  
  
 LINQ 技术广泛应用了延迟执行，包括在核心 <xref:System.Linq?displayProperty=nameWithType> 类的成员和不同 LINQ 命名空间中的扩展方法（如 <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>）中使用。  
  
## <a name="eager-vs-lazy-evaluation"></a>积极计算与迟缓计算  
 当您编写实现延迟执行的方法时，还必须确定是使用迟缓计算还是积极计算来实现该方法。  
  
-   在迟缓计算中，每次调用迭代器时都会处理源集合的一个元素。 这是实现迭代器的典型方式。  
  
-   在积极计算中，第一次调用迭代器时就会对整个集合进行处理。 还可能需要源集合的临时副本。 例如，<xref:System.Linq.Enumerable.OrderBy%2A> 方法必须在返回第一个元素前对整个集合进行排序。  
  
 迟缓计算通常产生更好的性能，因为它将系统开销处理平均分配到整个集合的计算中，并将临时数据的使用降至最低。 当然，对于某些操作，除了具体化中间结果之外，再没有其他选择。  
  
## <a name="next-steps"></a>后续步骤  
 本教程的下一个主题将解释延迟执行：  
  
-   [延迟的执行示例 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>请参阅

- [教程：延迟的执行 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
- [概念和术语 （功能转换） (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)
- [聚合操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
