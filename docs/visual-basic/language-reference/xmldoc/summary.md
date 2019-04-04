---
title: <summary> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 0fbe07884f55b7e6f460929e54520de5f718e1af
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814998"
---
# <a name="summary-visual-basic"></a>\<摘要 > (Visual Basic)
指定的成员的摘要。  
  
## <a name="syntax"></a>语法  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>参数  
 `description`  
 对象的摘要。  
  
## <a name="remarks"></a>备注  
 使用`<summary>`标记来描述类型或类型成员。 使用 [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) 可针对某个类型说明添加补充信息。  
  
 文本`<summary>`标记是在 IntelliSense 中，类型信息的唯一源，并还会显示在对象浏览器。 对象浏览器有关的信息，请参阅[查看代码结构](/visualstudio/ide/viewing-the-structure-of-code)。  
  
 使用 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 进行编译可以将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 此示例使用`<summary>`标记来描述`ResetCounter`方法和`Counter`属性。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>请参阅

- [XML 注释标记](../../../visual-basic/language-reference/xmldoc/index.md)
