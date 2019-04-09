---
title: 如何：禁用选项卡页
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: ace713a635b5d9c4b73f85cd3d378c0f1ff3dba1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107570"
---
# <a name="how-to-disable-tab-pages"></a>如何：禁用选项卡页
在某些情况下，将想要限制可在 Windows 窗体应用程序中的数据访问。 一个例子可能具有选项卡控件，则选项卡页中显示的数据时管理员可能想要限制从来宾或较低级别的用户的选项卡页的信息。  
  
### <a name="to-disable-tab-pages-programmatically"></a>若要以编程方式禁用选项卡页  
  
1.  编写代码来处理选项卡控件的<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>事件。 这是用户从一个选项卡切换到下一步时引发的事件。  
  
2.  检查凭据。 根据提供的信息，你可能想要检查用户已登录时使用的用户名或某种其他形式的凭据，然后允许用户查看该选项卡。  
  
3.  如果用户具有适当的凭据，显示单击选项卡。 如果用户不具有适当的凭据，显示一个消息框或其他用户界面，该值指示用户具有访问权限，并返回到初始的选项卡。  
  
    > [!NOTE]
    >  在生产应用程序中实现此功能，可以在窗体的过程在执行此凭据检查<xref:System.Windows.Forms.Form.Load>事件。 这样，您可以隐藏选项卡，显示任何用户界面，即更简洁的编程方法之前。 使用下面的方法 (检查凭据并禁用过程选项卡<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>事件) 是用于说明目的。  
  
4.  （可选） 如果你有两个以上的选项卡页，显示原始版本不同的选项卡页。  
  
     在以下示例中，<xref:System.Windows.Forms.CheckBox>控件代替检查凭据，与条件访问选项卡将因应用程序而异。 时<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>引发事件时，如果凭据检查为 true （也就是说，选中复选框） 和所选的选项卡`TabPage2`（在此示例中的机密信息的选项卡），然后`TabPage2`显示。 否则为`TabPage3`会显示一个消息框显示给用户，指出他们没有适当的访问权限。 下面的代码假定具有的窗体<xref:System.Windows.Forms.CheckBox>控件 (`CredentialCheck`) 和一个<xref:System.Windows.Forms.TabControl>带有三个选项卡页的控件。  
  
    ```vb  
    Private Sub TabControl1_SelectedIndexChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles TabControl1.SelectedIndexChanged  
       ' Check Credentials Here  
  
       If CredentialCheck.Checked = True And _   
       TabControl1.SelectedTab Is TabPage2 Then  
          TabControl1.SelectedTab = TabPage2  
       ElseIf CredentialCheck.Checked = False _   
       And TabControl1.SelectedTab Is TabPage2 Then  
          MessageBox.Show _   
         ("Unable to load tab. You have insufficient access privileges.")  
          TabControl1.SelectedTab = TabPage3  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void tabControl1_SelectedIndexChanged(object sender, System.EventArgs e)  
    {  
        // Check Credentials Here  
  
        if ((CredentialCheck.Checked == true) && (tabControl1.SelectedTab == tabPage2))   
        {  
            tabControl1.SelectedTab = tabPage2;  
        }  
        else if ((CredentialCheck.Checked == false) && (tabControl1.SelectedTab == tabPage2))  
        {  
            MessageBox.Show("Unable to load tab. You have insufficient access privileges.");  
            tabControl1.SelectedTab = tabPage3;  
        }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void tabControl1_SelectedIndexChanged(  
          System::Object ^ sender,  
          System::EventArgs ^  e)  
       {  
          // Check Credentials Here  
          if ((CredentialCheck->Checked == true) &&  
              (tabControl1->SelectedTab == tabPage2))  
          {  
             tabControl1->SelectedTab = tabPage2;  
          }  
          else if ((CredentialCheck->Checked == false) &&  
                   (tabControl1->SelectedTab == tabPage2))  
          {  
             MessageBox::Show(String::Concat("Unable to load tab. ",  
                "You have insufficient access privileges."));  
             tabControl1->SelectedTab = tabPage3;  
          }  
       }  
    ```  
  
     (Visual C#，Visual c + +)将以下代码放在窗体的构造函数中以注册事件处理程序。  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>请参阅

- [TabControl 控件概述](tabcontrol-control-overview-windows-forms.md)
- [如何：将控件添加到选项卡页](how-to-add-a-control-to-a-tab-page.md)
- [如何：使用 Windows 窗体 TabControl 添加和移除选项卡](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [如何：更改 Windows 窗体 TabControl 的外观](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
