---
title: 如何：验证文件的名称和在 Visual Basic 中的路径
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: c8e01a0f5a3f99fdbc424d6cd7d224367c7bad08
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835799"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>如何：验证文件的名称和在 Visual Basic 中的路径
此示例返回`Boolean`值，该值指示字符串是否表示文件名称或路径。 验证检查名称是否包含不允许使用的文件系统的字符。  
  
## <a name="example"></a>示例  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 此示例不会检查，如果名称不正确放置冒号或目录没有名称或名称的长度超过系统定义的最大长度。 它也不会检查应用程序是否具有指定名称的文件系统资源的访问权。  
  
## <a name="see-also"></a>请参阅

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [在 Visual Basic 中验证字符串](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
