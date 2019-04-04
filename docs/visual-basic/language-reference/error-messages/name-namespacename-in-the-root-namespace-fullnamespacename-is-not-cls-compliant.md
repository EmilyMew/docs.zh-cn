---
title: 根命名空间 <namespacename> 中的名称 <fullnamespacename> 不符合 CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 84706719d151ea8df478f88610df34842f6f8702
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841532"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a>名称\<命名空间名称 > 的根命名空间\<fullnamespacename > 不符合 cls 的
程序集标记为`<CLSCompliant(True)>`，但名称以下划线开头的根命名空间名称元素 (`_`)。  
  
 编程元素可以包含一个或多个下划线，但要符合[语言独立性和与语言无关的组件](../../../standard/language-independence-and-language-independent-components.md)(CLS)，它必须不以下划线开头。 请参阅 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
 当将 <xref:System.CLSCompliantAttribute> 应用到编程元素中时，需要将该特性的 `isCompliant` 参数设置为 `True` 或 `False` 来指示符合或不符合性。 此参数没有默认值，必须为其提供一个值。  
  
 如果不将 <xref:System.CLSCompliantAttribute> 应用到元素，则它将被视为不符合规范。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的信息，请参见 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **错误 ID:** BC40039  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   如果你需要 CLS 符合性，更改根命名空间名称，以便无其元素以下划线开头。  
  
-   如果你需要命名空间名称保持不变，然后删除<xref:System.CLSCompliantAttribute>从程序集或将其标记为`<CLSCompliant(False)>`。  
  
## <a name="see-also"></a>请参阅

- [Namespace 语句](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [在 Visual Basic 中的命名空间](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [“项目设计器”->“应用程序”页 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [已声明的元素名称](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic 命名约定](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
