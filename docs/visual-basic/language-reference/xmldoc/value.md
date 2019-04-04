---
title: <value> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 2938d485bf6c547c792431b93fc8959c9c36befa
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821408"
---
# <a name="value-visual-basic"></a>\<值 > (Visual Basic)
指定属性的说明。  
  
## <a name="syntax"></a>语法  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>参数  
 `property-description`  
 属性的说明。  
  
## <a name="remarks"></a>备注  
 使用`<value>`标记描述的属性。 请注意，当添加在 Visual Studio 开发环境中使用代码向导的属性时，它将添加[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)标记为新属性。 然后，应手动添加`<value>`标记来描述该属性表示的值。  
  
 使用 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 进行编译可以将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 此示例使用`<value>`标记来描述哪些值`Counter`属性保存。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>请参阅

- [XML 注释标记](../../../visual-basic/language-reference/xmldoc/index.md)
