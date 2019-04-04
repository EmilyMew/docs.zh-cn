---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 4e2f441863d6a8677593a257cdb2cc841634d47c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820236"
---
# <a name="exception-visual-basic"></a>\<异常 > (Visual Basic)
指定可引发哪些异常。  
  
## <a name="syntax"></a>语法  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a>参数  
 `member`  
 对当前编译环境中出现的一个异常的引用。 编译器检查是否存在给定的异常，并将 `member` 转换为输出 XML 中的规范的元素名称。 `member` 必须出现在双引号 (" ") 内。  
  
 `description`  
 描述。  
  
## <a name="remarks"></a>备注  
 使用`<exception>`标记来指定可以引发哪些异常。 这是适用于方法定义的标记。  
  
 使用 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 进行编译可以将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 此示例使用`<exception>`标记来描述异常的`IntDivide`函数可以引发。  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>请参阅

- [XML 注释标记](../../../visual-basic/language-reference/xmldoc/index.md)
