---
title: <include> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: d9c1c1a50f0e3530c842a6058e288b8d2be15f95
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832536"
---
# <a name="include-visual-basic"></a>\<包括 > (Visual Basic)
表示描述的类型和成员在源代码中的另一个文件。  
  
## <a name="syntax"></a>语法  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a>参数  
 `filename`  
 必需。 包含文档的文件的名称。 可使用路径来限定文件名。 将`filename`在双引号 ("")。  
  
 `tagpath`  
 必需。 `filename` 中标记的路径，它指向标记 `name`。 将该路径括在双引号 ("")。  
  
 `name`  
 必需。 中位于注释前的标记的名称说明符。 `Name` 将具有`id`。  
  
 `id`  
 必需。 标记的 ID（位于注释之前）。 将 ID 括在单引号 (' ')。  
  
## <a name="remarks"></a>备注  
 使用`<include>`标记引用另一个文件中描述的类型的注释和你的源代码中的成员。 这是对直接在源代码文件中放入文档注释的替代方法。  
  
 `<include>`标记使用 W3C XML 路径语言 (XPath) 1.0 版建议。 详细了解如何自定义你`<include>`使用，请参阅<https://www.w3.org/TR/xpath>。  
  
## <a name="example"></a>示例  
 此示例使用`<include>`标记从名为的文件导入成员文档注释`commentFile.xml`。  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 格式`commentFile.xml`如下所示。  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a>请参阅

- [XML 注释标记](../../../visual-basic/language-reference/xmldoc/index.md)
