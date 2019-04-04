---
title: 如何：初始化数组变量在 Visual Basic 中
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 4aa783d6179c72760a12d0259d587b5b38bb9140
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832237"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>如何：初始化数组变量在 Visual Basic 中
通过包括数组文本中初始化数组变量`New`子句并指定数组的初始值。 你可以指定的类型，或允许其从数组文本中的值推断出来。 有关如何推断出的类型的详细信息，请参阅"填充数组初始值"中[数组](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>若要通过使用数组文本初始化数组变量  
  
-   在`New`子句，或分配的数组值时，提供在大括号内的元素值 (`{}`)。 下面的示例演示如何声明、 创建和初始化一个变量来包含包含类型的元素的数组的几个`Char`。  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     每个语句执行后，创建的数组长度为 3，在索引 0 到 2 包含初始值的元素。 如果你提供上限和值，则必须包含从 0 到上限的每个元素的值。  
  
     请注意，不需要指定索引上限，如果您提供了数组文本中的元素值。 如果指定没有上限，则根据数组文本中的值的数量推断数组的大小。  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>若要使用数组文本初始化多维数组变量  
  
-   嵌套在括号内的值 (`{}`) 大括号内。 请确保嵌套的数组文本全都推断为相同类型和长度的数组。 下面的代码示例显示了多维数组初始化的几个示例。  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
-   可以显式指定数组界限或省略这些并让编译器推断数组界限的数组文本中的值。 如果你提供上限和值，则必须在每个维度中包含从 0 到上限的每个元素的值。 下面的示例演示几种方法声明、 创建和初始化一个变量来包含一个二维数组具有类型的元素。 `Short`  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     每个语句执行后，创建的数组包含六个初始化的元素的索引`(0,0)`， `(0,1)`， `(0,2)`， `(1,0)`， `(1,1)`，并`(1,2)`。 每个数组位置都包含值`10`。  
  
-   下面的示例循环访问多维数组。 在用 Visual Basic 编写的 Windows 控制台应用程序，将粘贴的代码将在`Sub Main()`方法。 最后一个注释显示输出。  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>若要使用数组文本初始化交错的数组变量  
  
-   将大括号内的对象值嵌套 (`{}`)。 尽管您还可以嵌套指定不同长度，对于交错数组的数组的数组文本，但请确保嵌套的数组文本括在小括号 (`()`)。 括号强制先计算嵌套的数组文本，并生成数组将用作交错数组的初始值。 下面的代码示例演示了交错的数组初始化的两个示例。  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
-   下面的示例循环访问交错数组。 在用 Visual Basic 编写的 Windows 控制台应用程序，将粘贴的代码将在`Sub Main()`方法。  在代码中的最后一个注释显示输出。  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>请参阅

- [数组](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [数组疑难解答](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
