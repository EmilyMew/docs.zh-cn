---
title: 如何：使用设计器在 Windows 窗体 ListView 控件中启用平铺视图
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 7f7e3f0fadeccafc867c49d76f6f6cf11300fddc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102474"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>如何：使用设计器在 Windows 窗体 ListView 控件中启用平铺视图
磁贴视图功能<xref:System.Windows.Forms.ListView>控件使您可以提供一种视觉平衡图形和文本信息之间。 磁贴视图中，为项目显示的文本信息与为详细信息视图定义的列信息相同。 磁贴视图功能结合的分组或插入标记中的功能<xref:System.Windows.Forms.ListView>控件。  
  
 磁贴视图使用 32x32 图标和若干行文本，如在下图中所示。  
  
 ![使用平铺视图的 ListView 控件中](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "磁贴视图图标和文本")  
  
 平铺视图属性和方法使您能够指定哪些列字段显示的每个项，并共同控制的大小和磁贴视图窗口中的所有项的外观。 为清楚起见，将磁贴中的第一行始终是文本的项的名称;不能更改它。  
  
 下面的过程需要**Windows 应用程序**包含一个窗体，其中包含项目<xref:System.Windows.Forms.ListView>控件。 有关设置此类项目的信息，请参阅[如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：将控件添加到 Windows 窗体](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  当应用程序调用 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法时，磁贴视图仅适用于 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)]。 在早期的操作系统上，任何与磁贴视图相关的代码都不起作用，且 <xref:System.Windows.Forms.ListView> 控件将显示在大图标视图中。 有关详细信息，请参阅 <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>。  
>   
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-set-tile-view-in-the-designer"></a>若要在设计器中设置平铺视图  
  
1.  选择<xref:System.Windows.Forms.ListView>窗体上的控件。  
  
2.  在中**属性**窗口中，选择<xref:System.Windows.Forms.ListView.View%2A>属性，然后选择**磁贴**。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView 控件概述](listview-control-overview-windows-forms.md)
