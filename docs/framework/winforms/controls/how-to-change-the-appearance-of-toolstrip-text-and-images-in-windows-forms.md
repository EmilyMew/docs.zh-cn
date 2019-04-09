---
title: 如何：在 Windows 窗体中更改 ToolStrip 文本和图像的外观
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: 5c326c8f6a56c934d317305f85f4c88e95e75f8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088466"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>如何：在 Windows 窗体中更改 ToolStrip 文本和图像的外观
您可以控制是否在显示的文本和图像<xref:System.Windows.Forms.ToolStripItem>和它们相对于彼此的对齐方式和<xref:System.Windows.Forms.ToolStrip>。  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>若要定义 ToolStripItem 上显示的内容  
  
-   设置<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>属性设置为所需的值。 可能的值为`Image`， `ImageAndText`， `None`，和`Text`。 默认值为 `ImageAndText`。  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>若要使 ToolStripItem 上的文本对齐  
  
-   设置<xref:System.Windows.Forms.ToolStripItem.TextAlign%2A>属性设置为所需的值。 可能的值为 top、 中间颜色和底部使用 left、 center 和右侧的任意组合。 默认值为 `MiddleCenter`。  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>若要对齐 ToolStripItem 上的图像  
  
-   设置<xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>属性设置为所需的值。 可能的值为 top、 中间颜色和底部使用 left、 center 和右侧的任意组合。 默认值为 `MiddleLeft`。  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>若要定义 ToolStripItem 文本和图像相对于彼此的显示方式  
  
-   设置<xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>属性设置为所需的值。 可能的值为`ImageAboveText`， `ImageBeforeText`， `Overlay`， `TextAboveImage`，和`TextBeforeImage`。 默认值为 `ImageBeforeText`。  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ToolStrip>
- [ToolStrip 控件概述](toolstrip-control-overview-windows-forms.md)
- [ToolStrip 控件体系结构](toolstrip-control-architecture.md)
- [ToolStrip 技术摘要](toolstrip-technology-summary.md)
