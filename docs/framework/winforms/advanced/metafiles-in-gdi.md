---
title: GDI+ 中的图元文件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
ms.openlocfilehash: bb972f158496192aa38f10564209bb2781837414
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119855"
---
# <a name="metafiles-in-gdi"></a>GDI+ 中的图元文件
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供了<xref:System.Drawing.Imaging.Metafile>类，使您可以记录和显示图元文件。 图元文件，也称为矢量图像，是存储为一系列绘图命令和设置的映像。 在中记录的命令和设置<xref:System.Drawing.Imaging.Metafile>对象可以存储在内存中或保存到文件或流。  
  
## <a name="metafile-formats"></a>图元文件格式  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可以显示图元文件的已存储在以下格式：  
  
-   Windows Metafile (WMF)  
  
-   增强型图元文件 (EMF)  
  
-   EMF+  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可以记录图元文件中的 EMF 和 EMF + 格式，但不是在 WMF 格式。  
  
 EMF + 是允许的 EMF 扩展[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]要存储的记录。 有两种变体的 EMF + 格式：EMF + 仅和 EMF + 双重。 EMF + 仅图元文件仅包含[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]记录。 此类图元文件可由显示[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]而不是按[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]。 EMF + 双重图元文件包含[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]记录。 每个[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]记录 EMF + 双重中图元文件与配对备用[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]记录。 此类图元文件可由显示[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]或通过[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]。  
  
 以下示例显示图元文件的以前保存为文件。 与在其左上角显示图元文件 （100，100）。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>请参阅

- [图像、位图和图元文件](images-bitmaps-and-metafiles.md)
