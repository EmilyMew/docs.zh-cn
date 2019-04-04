---
title: 如何：枚举已安装的字体
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
ms.openlocfilehash: e56f06d6f7a762a1ef1ff85fa30751ea64f9f14b
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653738"
---
# <a name="how-to-enumerate-installed-fonts"></a>如何：枚举已安装的字体
<xref:System.Drawing.Text.InstalledFontCollection>类继承自<xref:System.Drawing.Text.FontCollection>抽象基类。 可以使用<xref:System.Drawing.Text.InstalledFontCollection>对象枚举在计算机上安装的字体。 <xref:System.Drawing.Text.FontCollection.Families%2A>的属性<xref:System.Drawing.Text.InstalledFontCollection>对象是一个数组<xref:System.Drawing.FontFamily>对象。  
  
## <a name="example"></a>示例  
 下面的示例列出所有计算机上安装的字体系列的名称。 代码检索<xref:System.Drawing.FontFamily.Name%2A>每个属性<xref:System.Drawing.FontFamily>中返回的数组对象<xref:System.Drawing.Text.FontCollection.Families%2A>属性。 如检索字体系列名称时，系统会将它们连接起来到窗体的逗号分隔列表。 然后<xref:System.Drawing.Graphics.DrawString%2A>方法的<xref:System.Drawing.Graphics>类在矩形中绘制的以逗号分隔列表。  
  
 如果你运行示例代码，输出将类似于下图中所示：  
  
 ![显示已安装的字体系列的屏幕截图。](./media/how-to-enumerate-installed-fonts/list-installed-font-families.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，并且它需要<xref:System.Windows.Forms.PaintEventArgs> `e`，这是一个参数的<xref:System.Windows.Forms.PaintEventHandler>。 此外，应导入<xref:System.Drawing.Text>命名空间。  
  
## <a name="see-also"></a>请参阅
- [使用字体和文本](using-fonts-and-text.md)
