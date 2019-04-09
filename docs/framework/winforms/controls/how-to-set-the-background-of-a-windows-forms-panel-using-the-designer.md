---
title: 如何：使用设计器设置 Windows 窗体面板的背景
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: e66d8c81114a4550f0473f75a8101e79e8db2c76
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103709"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>如何：使用设计器设置 Windows 窗体面板的背景
Windows 窗体<xref:System.Windows.Forms.Panel>控件可以显示背景色和背景图像。 <xref:System.Windows.Forms.Control.BackColor%2A>属性设置为包含在面板中，例如标签和单选按钮控件的背景色。 如果<xref:System.Windows.Forms.Control.BackgroundImage%2A>未设置属性，<xref:System.Windows.Forms.Control.BackColor%2A>选择将填充所有面板。 如果<xref:System.Windows.Forms.Control.BackgroundImage%2A>属性设置，则图像将显示在面板中包含控件的后面。  
  
 下面的过程需要**Windows 应用程序**包含一个窗体项目<xref:System.Windows.Forms.Panel>控件。 有关如何设置此类项目的信息，请参阅[如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：将控件添加到 Windows 窗体](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a>若要在 Windows 窗体设计器中设置背景  
  
1.  选择 <xref:System.Windows.Forms.Panel> 控件。  
  
2.  在中**属性**窗口中，单击旁边的箭头按钮<xref:System.Windows.Forms.Control.BackColor%2A>属性来显示具有三个选项卡的窗口。  
  
3.  选择**自定义**选项卡以显示颜色的调色板。  
  
4.  选择**Web**或**系统**选项卡上显示一组预定义的颜色、 名称，然后选择一种颜色。  
  
5.  在中**属性**窗口中，单击旁边的箭头按钮<xref:System.Windows.Forms.Control.BackgroundImage%2A>属性。  
  
6.  在中**打开**对话框框中，选择你想要显示的文件。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel 控件](panel-control-windows-forms.md)
- [Panel 控件概述](panel-control-overview-windows-forms.md)
- [如何：通过使用设计器使用 Windows 窗体 Panel 控件对控件进行分组](group-controls-with-wf-panel-control-using-the-designer.md)
