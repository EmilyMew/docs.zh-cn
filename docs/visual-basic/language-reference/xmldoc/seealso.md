---
title: <seealso> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 0df999ef502bf61bdfb65cb472947b93efded36e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823475"
---
# <a name="seealso-visual-basic"></a>\<seealso > (Visual Basic)
指定的另请参见部分中显示的链接。  
  
## <a name="syntax"></a>语法  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a>参数  
 `member`  
 对可从当前编译环境调用的成员或字段的引用。 编译器检查是否存在给定的码位元素，并将 `member` 传递到输出 XML 中的元素名称。 `member` 必须出现在双引号 (" ") 内。  
  
## <a name="remarks"></a>备注  
 使用`<seealso>`标记指定你想要的另请参见部分中显示的文本。 使用 [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) 从文本内指定链接。  
  
 使用 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 进行编译可以将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 此示例使用`<seealso>`标记中的`DoesRecordExist`备注一节来指代`UpdateRecord`方法。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>请参阅

- [XML 注释标记](../../../visual-basic/language-reference/xmldoc/index.md)
