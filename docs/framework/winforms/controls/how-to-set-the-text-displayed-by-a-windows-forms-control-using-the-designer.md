---
title: 如何：使用设计器设置 Windows 窗体控件显示的文本
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
ms.openlocfilehash: 645ddedcb0de560737ee05db1375f09cfa2cd7ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123833"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a>如何：使用设计器设置 Windows 窗体控件显示的文本
Windows 窗体控件通常显示与该控件的主要功能相关的一些文本。 例如，<xref:System.Windows.Forms.Button>控件通常显示的标题，该值指示当单击该按钮时，将执行什么操作。 对于所有控件而言，都可通过使用 <xref:System.Windows.Forms.Control.Text%2A> 属性来设置或返回文本。 可以使用 <xref:System.Windows.Forms.Control.Font%2A> 属性更改字体。  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a>若要设置的文本和字体与设计器  
  
1.  在属性窗口中设置<xref:System.Windows.Forms.Control.Text%2A>为适当的字符串控件属性。  
  
     若要创建带下划线的快捷键，包含一个 & 号 (&) 将是快捷键的字母前。  
  
2.  在属性窗口中，单击省略号按钮 (![VisualStudioEllipsesButton 屏幕快照](../media/vbellipsesbutton.png "vbEllipsesButton")) 旁边<xref:System.Windows.Forms.Control.Font%2A>属性。  
  
     在标准字体对话框中，选择字体、 字体样式、 大小、 效果 （如删除线或下划线） 和脚本所需。  
  
## <a name="see-also"></a>请参阅

- [如何：设置 Windows 窗体控件显示的文本](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [使用字体和文本](../advanced/using-fonts-and-text.md)
- [标记单个 Windows 窗体控件并提供它们的快捷方式](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
