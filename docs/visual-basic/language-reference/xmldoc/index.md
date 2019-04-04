---
title: 建议的用于文档注释的 XML 标记 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: e59ee25b22c51e47dc83233af33099e6c55de87b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814934"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>建议的用于文档注释的 XML 标记 (Visual Basic)
Visual Basic 编译器可以处理 XML 文件在代码中的文档注释。 可以使用其他工具来处理到文档中的 XML 文件。  
  
 XML 注释类型等代码构造允许和类型成员。 分部类型只有一个部件类型的有 XML 注释，但没有注释其成员没有限制。  
  
> [!NOTE]
>  文档注释不能应用于命名空间。 原因是一个命名空间可以跨多个程序集，并不是所有的程序集具有要同时加载。  
  
 编译器处理任何为有效的 XML 标记。 以下标记提供用户文档中的常用的功能。  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup>编译器验证语法。)  
  
> [!NOTE]
>  如果你想的文档注释文本中显示尖括号，使用`&lt;`和`&gt;`。 例如，字符串`"&lt;text in angle brackets&gt;"`将显示为`<text in angle brackets>`。  
  
## <a name="see-also"></a>请参阅

- [使用 XML 记录代码](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [如何：创建 XML 文档](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
