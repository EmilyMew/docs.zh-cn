---
title: 如何：在 Visual Basic 中创建 XML 文档
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 2f32847c1b3a0fdf1892d6b423bb33783b6bdfe3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814583"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>如何：在 Visual Basic 中创建 XML 文档
此示例演示如何将 XML 文档注释添加到你的代码。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>若要创建的类型或成员的 XML 文档  
  
1.  在中**代码编辑器**，将光标放置在你想要创建文档的类型或成员上面的行上。  
  
2.  类型`'''`（三个非单引号）。  
  
     在添加对类型或成员的 XML 主干**代码编辑器**。  
  
3.  添加相应的标记之间的描述性信息。  
  
    > [!NOTE]
    >  如果添加 XML 文档块中的其他行，每行必须以`'''`。  
  
4.  添加新的 XML 文档注释中使用的类型或成员的其他代码。  
  
     IntelliSense 将显示从文本\<摘要 > 标记的类型或成员。  
  
5.  编译代码，生成包含文档注释的 XML 文件。 有关详细信息，请参阅 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)。  
  
## <a name="see-also"></a>请参阅

- [使用 XML 记录代码](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [XML 注释标记](../../../visual-basic/language-reference/xmldoc/index.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
