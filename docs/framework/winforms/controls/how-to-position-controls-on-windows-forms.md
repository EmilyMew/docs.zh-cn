---
title: 如何：在 Windows 窗体上定位控件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
ms.openlocfilehash: 22225c97ec082022cb609e47d3cafcdcc052143d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132790"
---
# <a name="how-to-position-controls-on-windows-forms"></a>如何：在 Windows 窗体上定位控件
若要定位控件，使用 Windows 窗体设计器中，或指定<xref:System.Windows.Forms.Control.Location%2A>属性。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>若要定位的 Windows 窗体设计器设计图面上的控件  
  
-   将控件拖动到用鼠标的适当位置。  
  
    > [!NOTE]
    >  选择控件并移动它带有箭头键以更精确地放置。 此外，*对齐线*帮助您在放置在窗体上精确的控制。 有关详细信息，请参见[演练：在 Windows 上排列控件窗体使用对齐线](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。  
  
### <a name="to-position-a-control-using-the-properties-window"></a>若要使用属性窗口将控件放  
  
1.  单击你想要定位的控件。  
  
2.  在中**属性**窗口中，类型值<xref:System.Windows.Forms.Control.Location%2A>属性，由逗号分隔，以放置在其容器内的控件。  
  
     第一个数字 (X) 是容器的从左边框; 的距离第二个数字 (Y) 是上边界的容器区域中，以像素为单位的距离。  
  
    > [!NOTE]
    >  您可以展开<xref:System.Windows.Forms.Control.Location%2A>属性键入**X**并**Y**单独值。  
  
### <a name="to-position-a-control-programmatically"></a>若要以编程方式定位控件  
  
1.  设置<xref:System.Windows.Forms.Control.Location%2A>到控件属性<xref:System.Drawing.Point>。  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  更改控件的位置的 X 坐标使用<xref:System.Windows.Forms.Control.Left%2A>子属性。  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a>若要以编程方式递增控件的位置  
  
1.  设置<xref:System.Windows.Forms.Control.Left%2A>子属性要递增的控件的 X 坐标。  
  
    ```vb  
    Button1.Left += 200  
    ```  
  
    ```csharp  
    button1.Left += 200;  
    ```  
  
    ```cpp  
    button1->Left += 200;  
    ```  
  
    > [!NOTE]
    >  使用<xref:System.Windows.Forms.Control.Location%2A>要设置控件的 X 和 Y 属性将同时定位。 若要单独设置位置，请使用控件的<xref:System.Windows.Forms.Control.Left%2A>(**X**) 或<xref:System.Windows.Forms.Control.Top%2A>(**Y**) 子属性。 不要尝试隐式设置的 X 和 Y 坐标<xref:System.Drawing.Point>结构，它表示该按钮的位置，因为此结构包含按钮的坐标的副本。  
  
## <a name="see-also"></a>请参阅

- [Windows 窗体控件](index.md)
- [演练：使用对齐线在 Windows 窗体上排列控件](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [演练：使用 TableLayoutPanel 在 Windows 窗体上排列控件](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [演练：使用 FlowLayoutPanel 在 Windows 窗体上排列控件](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [排列 Windows 窗体上的控件](arranging-controls-on-windows-forms.md)
- [标记单个 Windows 窗体控件并提供它们的快捷方式](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows 窗体上使用的控件](controls-to-use-on-windows-forms.md)
- [根据功能列出的 Windows 窗体控件](windows-forms-controls-by-function.md)
- [如何：设置 Windows 窗体的屏幕位置](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
