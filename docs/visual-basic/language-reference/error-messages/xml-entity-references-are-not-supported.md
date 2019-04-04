---
title: 不支持 XML 实体引用
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: dd7add295641e6a27c361c663d6075413b0f499c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824684"
---
# <a name="xml-entity-references-are-not-supported"></a>不支持 XML 实体引用
实体引用 (例如， `©`) 未定义在 XML 1.0 规范是包括，作为 XML 文本值。 仅`&`， `"`， `<`， `>`，和`'`XML 文本中支持 XML 实体引用。  
  
 **错误 ID:** BC31180  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   删除不受支持的实体引用。  
  
## <a name="see-also"></a>请参阅

- [XML 文本和 XML 1.0 规范](../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [XML 文本](../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
