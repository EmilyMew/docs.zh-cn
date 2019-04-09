---
title: 如何：更改 Windows 窗体的边框
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: d2e5dd761b2422f6d7e92e7bb97dbdf425b8fedf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080106"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>如何：更改 Windows 窗体的边框
当确定 Windows 窗体的外观和行为时，有几种边框样式可供选择。 通过更改 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 属性，可控制窗体调整大小的行为。 此外，设置 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 会影响标题栏的显示方式以及其上出现的按钮布局。 有关详细信息，请参阅 <xref:System.Windows.Forms.FormBorderStyle>。  
  
 Visual Studio 中对此任务提供广泛支持。  
  
 另请参阅[如何：更改使用设计器的 Windows 窗体的边框](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100))。  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>以编程方式设置 Windows 窗体的边框样式  
  
-   将 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 属性设置为所需的样式。 下面的代码示例设置窗体的边框样式`DlgBx1`到<xref:System.Windows.Forms.FormBorderStyle.FixedDialog>。  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     另请参阅[如何：在设计时创建对话框](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100))。  
  
     此外，如果已选择提供可选的窗体的边框样式**最小化**并**最大化**按钮，可以指定是否希望一个或两个这些按钮正常工作。 当想要密切控制用户体验时，这些按钮会非常有用。 **最小化**并**最大化**按钮默认启用，而且其功能操作通过**属性**窗口。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [Windows 窗体入门](getting-started-with-windows-forms.md)
