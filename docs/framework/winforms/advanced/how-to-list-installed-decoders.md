---
title: 如何：列出已安装的解码器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
ms.openlocfilehash: c92b8010def2f77f859ee0bd9cdb1ed51dd15f27
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079405"
---
# <a name="how-to-list-installed-decoders"></a>如何：列出已安装的解码器
你可能要列出可用的计算机上的图像解码器，以确定你的应用程序是否可以读取特定图像文件格式。 <xref:System.Drawing.Imaging.ImageCodecInfo>类提供了<xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>静态方法，以便你可以确定哪个图像解码器可供使用。 <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> 返回一个数组<xref:System.Drawing.Imaging.ImageCodecInfo>对象。  
  
## <a name="example"></a>示例  
 下面的代码示例输出已安装的解码器的列表和其属性值。  
  
 [!code-csharp[UsingImageEncodersDecoders#2](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   Windows 窗体应用程序。  
  
-   一个<xref:System.Windows.Forms.PaintEventArgs>，这是一个参数的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>请参阅

- [如何：列出已安装的编码器](how-to-list-installed-encoders.md)
- [在托管 GDI+ 中使用图像编码器和解码器](using-image-encoders-and-decoders-in-managed-gdi.md)
