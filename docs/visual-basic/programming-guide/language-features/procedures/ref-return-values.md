---
title: Ref 返回值 (Visual Basic)
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: d0600f7d9030324160343e800c37e0f5e68bff61
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133973"
---
# <a name="support-for-reference-return-values-visual-basic"></a>支持引用返回值 (Visual Basic)

从C#7.0 中，C#语言支持*引用返回值*。 若要了解引用返回值的方法之一是它们是相反的方法引用传递参数。 修改通过引用传递的参数后，所做的更改将在该变量的值反映在调用方中。 在一种方法提供给调用方的引用返回值，将引用返回值由调用方所做的修改将反映在被调用的方法的数据。

Visual Basic 不允许您对具有引用作者方法返回的值，但它的确允许你以使用引用返回值。 换而言之，可以调用具有引用返回值的方法并修改该返回值，并对引用返回值的更改反映在被调用的方法的数据。

## <a name="modifying-the-ref-return-value-directly"></a>直接修改 ref 返回值

对于方法，始终成功，并且没有任何`ByRef`参数，您可以直接修改引用返回值。 通过将新值分配给返回引用返回值的表达式来执行此操作。 

以下C#的示例定义了`NumericValue.IncrementValue`方法的内部值递增并将其返回作为引用返回值。 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

引用返回调用方在下面的 Visual Basic 示例然后修改值。 请注意，在行的`NumericValue.IncrementValue`方法调用不会分配给该方法的一个值。 相反，它将值分配给该方法返回的引用返回值。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>使用一个帮助器方法

在其他情况下，直接修改引用返回值的方法调用可能不总是需要。 例如，返回的字符串搜索方法可能无法始终找到匹配项。 在这种情况下，你想要修改引用返回值，如果搜索成功。

以下C#的示例演示了此方案。 它定义`Sentence`类编写的C#包括`FindNext`方法，用于以指定子字符串开头的句子中查找下一个词。 该字符串作为引用返回值返回，方法引用传递的 `Boolean` 变量指示搜索是否成功。 引用返回值指示调用方可以仅读取返回的值;他或她还可以修改它，并在内部中包含的数据中反映所做的修改`Sentence`类。

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

直接修改引用返回值在此情况下是不可靠，由于方法调用可能无法找到匹配项并返回该句中的第一个单词。 在这种情况下，调用方无意间修改句子的第一个单词。 这可能由调用方返回阻止`null`(或`Nothing`在 Visual Basic 中)。 在这种情况下，尝试修改其值是一个字符串，但是`Nothing`引发<xref:System.NullReferenceException>。 返回调用方还可能禁止<xref:System.String.Empty?displayProperty=nameWithType>，但这需要调用方定义其值是一个字符串变量<xref:System.String.Empty?displayProperty=nameWithType>。 当调用方可以修改该字符串时，修改本身没有任何用处，因为修改后的字符串中存储的句子之间没有任何关系的词`Sentence`类。

处理这种情况的最佳方式是通过对一个帮助器方法的引用传递引用返回值。 帮助器方法然后包含逻辑，以便确定是否调用该方法成功，如果有的话，若要修改引用返回值。 下面的示例提供了一种可能实现。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>请参阅

- [按值和按引用传递自变量](passing-arguments-by-value-and-by-reference.md)
- [Visual Basic 中的过程](index.md)
