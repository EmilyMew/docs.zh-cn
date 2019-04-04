---
title: 类型“type1”的值无法转换为“type2”
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: c8480c6fab2bff931950ebc21d0a8affe3c41c66
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827141"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a>类型“type1”的值无法转换为“type2”
类型 type1 的值无法转换为 type2。 可以使用 Value 属性来获取第一个元素的字符串值\<parentElement >。  
  
 已尝试将 XML 文本隐式强制转换为特定类型。 XML 文本不能隐式强制转换为指定类型。  
  
 **错误 ID:** BC31194  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   使用 XML 文本的 `Value` 属性来将其值作为 `String`引用。 使用 `CType` 函数、另一个类型转换函数，或 <xref:System.Convert> 类将值强制转换为指定类型。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Convert>
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [XML 文本](../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
