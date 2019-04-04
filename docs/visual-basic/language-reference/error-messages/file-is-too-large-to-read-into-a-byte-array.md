---
title: 文件太大，无法读取到字节数组中
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 0c7d35e08eeb42e35c4c40e47434a64393d829b1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831509"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>文件太大，无法读取到字节数组中
尝试读取到字节数组的文件的大小超过 4 GB。 `My.Computer.FileSystem.ReadAllBytes`方法不能读取超过此大小的文件。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   使用<xref:System.IO.StreamReader>读取该文件。 有关详细信息，请参阅[基础知识的.NET Framework 文件 I/O 和文件系统 (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [使用 Visual Basic 访问文件](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
- [如何：从文件使用 StreamReader 读取文本](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
