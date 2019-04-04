---
title: <example> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 510b00d2220b9c65b0e2b8fa3ead70925a9f54ba
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821915"
---
# <a name="example-visual-basic"></a>\<示例 > (Visual Basic)
指定成员的一个示例。  
  
## <a name="syntax"></a>语法  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>参数  
 `description`  
 代码示例的说明。  
  
## <a name="remarks"></a>备注  
 `<example>`标记，可以指定如何使用方法或其他库成员的示例。 这通常涉及到使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 标记。  
  
 使用 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 进行编译可以将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 此示例使用`<example>`标记包含有关使用示例`ID`字段。  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>请参阅

- [XML 注释标记](../../../visual-basic/language-reference/xmldoc/index.md)
