---
title: 如何：向 Windows 窗体添加控件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 72b5931a79284a93a4e0fdf3cb2cc3b03157f5f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106478"
---
# <a name="how-to-add-controls-to-windows-forms"></a>如何：向 Windows 窗体添加控件
大多数窗体旨在通过将控件添加到窗体的面，用于定义用户界面 (UI) 中。 一个*控制*是用于显示信息或接受用户输入的窗体上的组件。 有关控件的详细信息，请参阅[Windows 窗体控件](index.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-draw-a-control-on-a-form"></a>若要绘制的控件在窗体上  
  
1.  打开窗体。 有关详细信息，请参阅[如何：在设计器中显示 Windows 窗体](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))。  
  
2.  在中**工具箱**，单击你想要添加到窗体的控件。  
  
3.  在表单上，单击希望要定位，控件的左上角的位置和拖动到希望要定位的控件的右下角。  
  
     该控件添加到具有指定的位置和大小的窗体。  
  
    > [!NOTE]
    >  每个控件具有定义的默认大小。 可以向控件的默认大小在窗体添加控件，通过将其从**工具箱**到窗体。  
  
### <a name="to-drag-a-control-to-a-form"></a>若要将控件拖动到窗体  
  
1.  打开窗体。 有关详细信息，请参阅[如何：在设计器中显示 Windows 窗体](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))。  
  
2.  在中**工具箱**，单击所需的控件并将其拖动到窗体。  
  
     该控件添加到窗体，请在其默认大小的指定位置。  
  
    > [!NOTE]
    >  你可以双击中的控件**工具箱**将其添加到其默认大小中的窗体的左上角。  
  
     您可以在运行时动态地将控件添加到窗体中。 在下面的代码示例中，<xref:System.Windows.Forms.TextBox>控件将被添加到窗体时<xref:System.Windows.Forms.Button>单击控件。  
  
    > [!NOTE]
    >  下面的过程需要一个具有窗体是否存在**按钮**控件， `Button1`、 已放置在其上。  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a>若要以编程方式向窗体添加控件  
  
1.  处理按钮的方法中`Click`事件在窗体的类，类似于以下内容，以添加到您的控制变量的引用插入代码中设置控件的`Location`，并添加控件。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  此外可以添加代码以初始化控件的其他属性。  
  
    > [!IMPORTANT]
    >  可能会通过引用恶意公开您的本地计算机通过网络安全风险`UserControl`。 这只能在恶意的用户创建一个具有破坏性的自定义控件，跟您错误地将其添加到你的项目的情况下一个问题。  
  
## <a name="see-also"></a>请参阅

- [Windows 窗体控件](index.md)
- [排列 Windows 窗体上的控件](arranging-controls-on-windows-forms.md)
- [如何：调整 Windows 窗体上控件的大小](how-to-resize-controls-on-windows-forms.md)
- [如何：设置 Windows 窗体控件显示的文本](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [在 Windows 窗体上使用的控件](controls-to-use-on-windows-forms.md)
