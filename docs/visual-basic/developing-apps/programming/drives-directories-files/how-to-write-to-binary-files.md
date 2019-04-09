---
title: 如何：在 Visual Basic 中写入二进制文件
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: e8aa1c96766fc1b63326415c879e9821dc1de7f6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833680"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>如何：在 Visual Basic 中写入二进制文件
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> 方法向二进制文件写入数据。 如果 `append` 参数为 `True`，会将数据追加到文件中；否则将覆盖文件中的数据。  
  
 如果指定的路径（不包括文件名）无效，则将引发 <xref:System.IO.DirectoryNotFoundException> 异常。 如果该路径有效，但文件不存在，则将创建文件。  
  
### <a name="to-write-to-a-binary-file"></a>写入二进制文件  
  
-   使用 `WriteAllBytes` 方法，并提供文件路径和名称以及要写入的字节数。 本示例将数据组 `CustomerData` 追加到名为 `CollectedData.dat` 的文件中。  
  
     [!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]  
  
## <a name="robust-programming"></a>可靠编程  
 以下情况可能会导致异常：  
  
-   路径由于以下原因之一而无效：是零长度字符串；仅包含空白；包含无效字符。 (<xref:System.ArgumentException>).  
  
-   路径无效，因为它是 `Nothing` (<xref:System.ArgumentNullException>)。  
  
-   `File` 指向不存在的路径（<xref:System.IO.FileNotFoundException> 或 <xref:System.IO.DirectoryNotFoundException>）。  
  
-   文件正由另一个进程使用，或者出现 I/O 错误 (<xref:System.IO.IOException>)。  
  
-   路径超过了系统定义的最大长度 (<xref:System.IO.PathTooLongException>)。  
  
-   路径中的文件名或目录名包含冒号 (:)，或格式无效 (<xref:System.NotSupportedException>)。  
  
-   该用户缺少查看该路径所必需的权限 (<xref:System.Security.SecurityException>)。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [如何：向文件写入文本](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
