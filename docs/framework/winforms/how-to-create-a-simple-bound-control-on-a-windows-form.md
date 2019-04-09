---
title: 如何：在 Windows 窗体上创建简单绑定控件
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: 85b19c43441650789eed6b92a771d2f2433c6a10
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094058"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>如何：在 Windows 窗体上创建简单绑定控件
与*简单绑定*，可以在控件中显示单个数据元素，如从数据集表中列的值。 可以将控件属性简单绑定到数据值。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-simple-bind-a-control"></a>简单绑定控件  
  
1.  连接到数据源。 有关详细信息，请参阅[连接到数据源](../data/adonet/connecting-to-a-data-source.md)。  
  
2.  在表单中，选择控件并显示**属性**窗口。  
  
3.  展开 **(DataBindings)** 属性。  
  
     最常绑定的属性将显示下面 **(DataBindings)** 属性。 例如，在大多数控件而言**文本**最经常绑定属性。  
  
4.  如果该属性要绑定不经常绑定的属性之一，请单击**省略号**按钮 (![VisualStudioEllipsesButton 屏幕快照](./media/vbellipsesbutton.png "vbEllipsesButton")) 中 **（高级）** 框，以显示**格式设置和高级绑定**为该控件的属性的完整列表对话框。  
  
5.  选择你想要绑定，并单击下的下拉箭头的属性**绑定**。  
  
     此时将显示可用数据源的列表。  
  
6.  展开要绑定到的数据源，直到找到所需的单个数据元素。 例如，如果你正在绑定到数据集表中的列值，请展开该数据集的名称，然后展开表名以显示列名。  
  
7.  单击要绑定到的元素的名称。  
  
8.  如果您正在处理**格式设置和高级绑定**对话框中，单击**确定**回到**属性**窗口。  
  
9. 如果你想要将绑定控件的其他属性，请重复步骤 3 至 7。  
  
    > [!NOTE]
    >  由于简单绑定控件显示单个数据元素，它是非常典型，若要在具有简单绑定控件的 Windows 窗体中包含导航逻辑。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Binding>
- [Windows 窗体数据绑定](windows-forms-data-binding.md)
- [数据绑定和 Windows 窗体](data-binding-and-windows-forms.md)
