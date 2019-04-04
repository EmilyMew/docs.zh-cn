---
title: 常量概述 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 2939110de77718baf32e2a0d8f1aa52dba997cf3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841266"
---
# <a name="constants-overview-visual-basic"></a>常量概述 (Visual Basic)
常量是有意义的名称采用的数字或字符串不会更改的位置。 常量存储值，如名称所示，将保持不变的应用程序执行中。 可以极大地提高代码的可读性并使其更易于维护使用常量。 包含的值会重新出现的代码中使用它们，或这取决于一些很难记住或没有任何明显的意义的数字。  
  
## <a name="how-to-create-and-use-constants"></a>如何创建和使用常量  
 Visual Basic 包含大量预定义的常量，主要用于打印和显示。 您还可以创建您自己常量与`Const`语句，用于创建变量的名称使用相同的规则。 如果`Option Strict`是`On`，必须显式声明常量的类型。  
  
 常量的作用域，这是变量的组的所有代码都可以引用它而无需限定其名称，是变量的在同一位置中声明相同。 若要创建一个常量，它位于特定过程的作用域内，将其声明在该过程。 若要创建一个常量，它是整个应用程序可用，将使用其声明`Public`类的声明部分中的关键字。  
  
> [!NOTE]
>  虽然常数某种程度上类似于变量，不能对其进行修改，或如变量可以为它们分配新值。  
  
 在代码中使用的常量可以定义由对象模型的控件或组件，或它们可以是用户定义 （即，那些您自己创建）。  
  
## <a name="compile-time-and-run-time-constants"></a>编译时和运行时常量  
 编译时常量是在编译代码，而可以仅计算运行时常量，该应用程序运行时的时间计算的。 编译时常量将在每次运行应用程序，而运行时常量可能每次更改的时具有相同的值。 需要如数组界限、 case 表达式或枚举器初始值设定项的情况下编译时常量。  
  
## <a name="in-this-section"></a>本节内容  
  
|定义|术语|  
|---|---|  
|[如何：声明常量](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|说明如何使用`Const`语句声明一个常量，并将其值; 设置为值通过声明一个常量，分配有意义的名称。|  
|[用户定义的常量](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|介绍如何创建你自己的常量，包括有关范围的信息以及如何避免循环引用。|  
|[常量和文本数据类型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|提供有关 Visual Basic 编译器如何初始化常量的信息时`Option Explicit`处于关闭状态。|  
|[如何：相关的常量值组合在一起](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|演示如何对分组相关的常量值。|  
  
## <a name="reference"></a>参考  
  
|定义|术语|  
|---|---|  
|[常量和枚举](../../../../visual-basic/language-reference/constants-and-enumerations.md)|列出预定义的 Visual basic 的常量。|  
|[Const 语句](../../../../visual-basic/language-reference/statements/const-statement.md)|介绍`Const`语句和它的使用。|  
|[Option Strict 语句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|介绍`Option Strict`语句和它的使用。|  
  
## <a name="see-also"></a>请参阅

- [枚举概述](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [如何：初始化数组变量在 Visual Basic 中](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
