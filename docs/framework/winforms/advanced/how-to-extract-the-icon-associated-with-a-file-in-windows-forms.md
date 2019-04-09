---
title: 如何：提取与 Windows 窗体中的文件关联的图标
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: d754dc5e8a57b3c4e2e5439bb2524a22d44813c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112549"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>如何：提取与 Windows 窗体中的文件关联的图标
多个文件有嵌入提供关联的文件类型的可视表示形式的图标。 例如，Microsoft Word 文档包含标识为 Word 文档的图标。 当列表控件或表控件中显示文件，可能想要显示的图标表示每个文件名旁边的文件类型。 您可以轻松执行此操作通过使用<xref:System.Drawing.Icon.ExtractAssociatedIcon%2A>方法。  
  
## <a name="example"></a>示例  
 下面的代码示例演示了如何提取与文件关联的图标，并显示文件的名称和在其关联的图标<xref:System.Windows.Forms.ListView>控件。  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 若要编译示例：  
  
-   将上面的代码粘贴到 Windows 窗体，并调用`ExtractAssociatedIconExample`方法从窗体的构造函数或<xref:System.Windows.Forms.Form.Load>事件处理方法。  
  
     将需要确保你的窗体将导入<xref:System.IO>命名空间。  
  
## <a name="see-also"></a>请参阅

- [图像、位图和图元文件](images-bitmaps-and-metafiles.md)
- [ListView 控件](../controls/listview-control-windows-forms.md)
