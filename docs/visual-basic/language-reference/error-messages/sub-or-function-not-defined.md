---
title: 未定义 Sub 或 Function (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 6bca368e13a32559bcb7cbb028dcaa1dea0353e3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819783"
---
# <a name="sub-or-function-not-defined-visual-basic"></a>未定义 Sub 或 Function (Visual Basic)
一个`Sub`或`Function`必须定义即可调用。 此错误的可能原因包括：  
  
-   过程名称拼写错误。  
  
-   尝试从另一个项目中调用的过程，而无需显式添加对该项目中的引用**引用**对话框。  
  
-   指定对调用的过程不可见的过程。  
  
-   声明 Windows 动态链接库 (DLL) 例程或不在指定的库或代码资源的 Macintosh 代码资源例程。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  请确保过程名称拼写正确。  
  
2.  查找包含你想要调用的过程的项目的名称**引用**对话框。 如果未显示，请单击**浏览**按钮对其进行搜索。 选择左侧的项目名称，该复选框，然后单击**确定**。  
  
3.  检查的例程的名称。  
  
## <a name="see-also"></a>请参阅

- [错误类型](../../../visual-basic/programming-guide/language-features/error-types.md)
- [管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)
- [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)
