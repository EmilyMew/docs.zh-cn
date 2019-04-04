---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c5c088472ae09a416953d9c0829cad1cb48646b8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833485"
---
# <a name="remarks-visual-basic"></a>\<备注 > (Visual Basic)
指定成员的备注部分。  
  
## <a name="syntax"></a>语法  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a>参数  
 `description`  
 对成员的说明。  
  
## <a name="remarks"></a>备注  
 使用`<remarks>`标记添加有关某个类型，对与指定的信息进行了补充[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)。  
  
 此信息显示在对象浏览器中。 对象浏览器有关的信息，请参阅[查看代码结构](/visualstudio/ide/viewing-the-structure-of-code)。  
  
 使用 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 进行编译可以将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 此示例使用`<remarks>`标记解释`UpdateRecord`方法执行。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>请参阅

- [XML 注释标记](../../../visual-basic/language-reference/xmldoc/index.md)
