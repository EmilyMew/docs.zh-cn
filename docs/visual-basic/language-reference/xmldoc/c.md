---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 9be9f9e96fc1b79ea97d54c54352da63b93ef264
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838035"
---
# <a name="c-visual-basic"></a>\<c > (Visual Basic)
指示说明中的文本是代码。  
  
## <a name="syntax"></a>语法  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>参数  
  
|参数|描述|  
|---|---|  
|`text`|要指示为代码的文本。|  
  
## <a name="remarks"></a>备注  
 `<c>`标记为您提供了一种方法，以指示说明中的文本应标记为代码。 使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 指示作为代码的多行文本。  
  
 使用 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 进行编译可以将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 此示例使用`<c>`指示的摘要部分中的标记`Counter`是代码。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>请参阅

- [XML 注释标记](../../../visual-basic/language-reference/xmldoc/index.md)
