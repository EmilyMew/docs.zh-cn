---
title: 已声明的元素名称 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: 5b1f8ccc402f7f5928a33f434664b0f28d108e6d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814063"
---
# <a name="declared-element-names-visual-basic"></a>已声明的元素名称 (Visual Basic)
每个已声明的元素有一个名称，也称为*标识符*，这是代码使用来对其进行引用。  
  
## <a name="rules"></a>规则  
 在 Visual Basic 中的元素名称必须遵守以下规则：  
  
-   它必须以字母字符或下划线开头 (`_`)。  
  
-   它必须仅包含字母字符、 十进制数字和下划线。  
  
-   如果以下划线开头，它必须包含至少一个字母字符或十进制数。  
  
-   它不能超过 1023年个字符。  
  
 1023 个字符的长度限制也适用于整个字符串的完全限定的名称，例如`outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`。  
  
 下面的示例显示了一些有效的元素名称。  
  
 `aB123__45`  
  
 `_567`  
  
 下面的示例演示一些无效的元素名称。 第一个仅包含一个下划线、 十进制数字，以开始第二个和第三个包含无效字符 （$）。  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  以下划线开头的元素名称 (`_`) 不属于[语言独立性和与语言无关的组件](../../../../standard/language-independence-and-language-independent-components.md)(CLS)，因此符合 cls 的代码不能使用一个组件，它定义此类名称。 但是，在中任何其他位置中的元素名称以下划线是符合 CLS 規格。  
  
### <a name="name-length-guidelines"></a>名称长度准则  
 在实践中，你的名称应尽可能短时仍然能够清楚地标识元素的特性。 这可提高你的代码的可读性，并减少行长度和源文件大小。  
  
 但是，你的名称不应太短，它不会不充分描述该元素表示和你的代码如何使用它。 这一点对于提高代码的可读性。 如果其他人正在尝试理解它，或者如果您自己正在寻求通过它您在编写之后很长时间，合适的元素名称可以节省相当长的时间。  
  
## <a name="escaped-names"></a>转义的名称  
 通常情况下，元素名称必须与任何不匹配的 Visual Basic 中，如保留的关键字`Case`或`Friend`。 但是，可以定义*转义名称*，这括在方括号 (`[ ]`)。 转义的名称可以与匹配任何 Visual Basic 关键字，因为括号消除不明确性。 在引用名称在代码中更高版本时，还可以使用括号。  
  
 一般情况下，应使用转义后名称时，才：  
  
-   从以前版本的 Visual Basic 的没有保留关键字用作名称; 迁移你的代码或  
  
-   您正在使用中则不保留给定的关键字的另一种语言编写的代码。  
  
 否则，应考虑重命名该元素，如果其名称与关键字冲突。 集成的开发环境 (IDE) 提供了执行此操作的简单办法。 有关详细信息，请参阅[重构](/visualstudio/vb-ide/refactoring-vb)。  
  
## <a name="case-sensitivity-in-names"></a>在名称中区分大小写  
 在 Visual Basic 中的元素名称不区分大小写。 这意味着当编译器在比较两个不同的字母大小写的名称，将它们解释为相同的名称。 例如，它认为 `ABC` 和 `abc` 指的是同一个声明的元素。  
  
 但是，公共语言运行时 (CLR) 使用区分大小写的绑定。 因此，当你生成程序集或 DLL 并使其可供其他程序集使用时，则名称将不再不区分大小写。 例如，如果你用名为 `ABC`的元素定义类，而其他程序集通过公共语言运行时使用你的类，则元素必须指的是 `ABC`。 如果以后要重新编译您的类并将该元素的名称改为`abc`，使用你的类的其他程序集将无法再访问该元素。 因此，发布程序集的更新版本时，不应该更改公共元素的字母大小写。  
  
## <a name="names-and-locales"></a>名称和区域设置  
 比较的名称是独立于区域设置。 如果两个名称匹配在一个区域设置中，可确保在所有区域设置匹配。  
  
## <a name="see-also"></a>请参阅

- [已声明的元素](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [已声明元素的特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [对已声明元素的引用](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [语句](../../../../visual-basic/language-reference/statements/index.md)
