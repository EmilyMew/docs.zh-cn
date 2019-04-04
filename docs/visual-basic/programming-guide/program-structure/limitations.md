---
title: Visual Basic 限制
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 10f67c02d25ec275d1c3e98197d51c25aa250c19
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824905"
---
# <a name="visual-basic-limitations"></a>Visual Basic 限制
早期版本的 Visual Basic 强制执行在代码中，如变量的名称，在模块和模块大小允许的变量数的长度的边界。 在 Visual Basic.NET 中，这些限制已放宽，为您提供编写和安排你的代码以更大的自由度。  
  
 都依赖在编译时的注意事项的更多运行时内存比物理限制。 如果使用比较明智的做法的编程方法，并将大型应用程序划分为多个类和模块，则遇到了内部 Visual Basic 限制的可能性很小。  
  
 以下是在极端情况下可能会遇到一些限制：  
  
-   **名称的长度。** 没有最大为每个声明的编程元素的名称的字符数。 如果元素名称进行限定，此最大值适用于整个限定字符串。 请参阅 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
-   **行长度。** 没有源代码的物理行中的 65535 个字符的最大值。 逻辑源的代码行可以是使用行继续符的情况下更长。 请参阅[如何：拆分和合并代码中的语句](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。  
  
-   **数组维数。** 没有可以声明为数组的维度的最大数目。 这就限制了多少个索引可用于指定的数组元素。 请参阅[数组中 Visual Basic 的维度](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)。  
  
-   **字符串长度。** 没有可以在单个字符串中存储的 Unicode 字符的最大数目。 请参阅[字符串数据类型](../../../visual-basic/language-reference/data-types/string-data-type.md)。  
  
-   **环境字符串长度。** 没有 32768 个字符作为命令行参数使用任何环境字符串的最大值。 这是在所有平台上的限制。  
  
## <a name="see-also"></a>请参阅

- [程序结构和代码约定](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic 命名约定](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
