---
title: 如何：将快捷菜单与 Windows 窗体 NotifyIcon 组件关联
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], for background processes
- NotifyIcon component [Windows Forms], associating shortcut menus
- shortcut menus [Windows Forms], for background processes
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
ms.openlocfilehash: 702a848631ce45c0efcb8eadfdf64074b454ac7d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097985"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>如何：将快捷菜单与 Windows 窗体 NotifyIcon 组件关联
> [!NOTE]
>  尽管<xref:System.Windows.Forms.MenuStrip>和<xref:System.Windows.Forms.ContextMenuStrip>替换并将功能添加到<xref:System.Windows.Forms.MainMenu>并<xref:System.Windows.Forms.ContextMenu>的早期版本中，控件<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>也可选择将保留向后兼容性和将来使用。  
  
 <xref:System.Windows.Forms.NotifyIcon>组件在任务栏的状态通知区域显示一个图标。 通常情况下，应用程序，可右键单击此图标以将命令发送到它表示应用程序。 通过将相关联<xref:System.Windows.Forms.ContextMenu>组件与<xref:System.Windows.Forms.NotifyIcon>组件，可以将此功能添加到你的应用程序。  
  
> [!NOTE]
>  如果你想要最小化在启动时显示的实例时应用程序<xref:System.Windows.Forms.NotifyIcon>组件在任务栏中，设置主窗体<xref:System.Windows.Forms.Form.WindowState%2A>属性设置为<xref:System.Windows.Forms.FormWindowState.Minimized>并确保<xref:System.Windows.Forms.NotifyIcon>组件的<xref:System.Windows.Forms.NotifyIcon.Visible%2A>属性设置为`true`。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>若要在设计时使用 NotifyIcon 组件关联快捷菜单  
  
1.  添加<xref:System.Windows.Forms.NotifyIcon>向窗体，组件和设置的重要属性，如<xref:System.Windows.Forms.NotifyIcon.Icon%2A>和<xref:System.Windows.Forms.NotifyIcon.Visible%2A>属性。  
  
     有关详细信息，请参阅[如何：添加到与 Windows 任务栏的应用程序图标窗体 NotifyIcon 组件](app-icons-to-the-taskbar-with-wf-notifyicon.md)。  
  
2.  添加<xref:System.Windows.Forms.ContextMenu>向 Windows 窗体组件。  
  
     将菜单项添加到表示想要在运行时提供的命令的快捷菜单。 这也是将菜单的增强功能添加到这些菜单项，例如访问密钥的好时机。  
  
3.  设置<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>属性的<xref:System.Windows.Forms.NotifyIcon>组件添加的快捷菜单。  
  
     设置此属性，单击任务栏上的图标时，将显示的快捷菜单。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>若要以编程方式使用 NotifyIcon 组件关联快捷菜单  
  
1.  创建的实例<xref:System.Windows.Forms.NotifyIcon>类和一个<xref:System.Windows.Forms.ContextMenu>类的任何属性设置所需的应用程序 (<xref:System.Windows.Forms.NotifyIcon.Icon%2A>并<xref:System.Windows.Forms.NotifyIcon.Visible%2A>属性<xref:System.Windows.Forms.NotifyIcon>组件、 菜单项<xref:System.Windows.Forms.ContextMenu>组件）。  
  
2.  设置<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>属性的<xref:System.Windows.Forms.NotifyIcon>组件添加的快捷菜单。  
  
     设置此属性，单击任务栏上的图标时，将显示的快捷菜单。  
  
    > [!NOTE]
    >  下面的代码示例创建基本菜单结构。 需要将自定义为适合您开发的应用程序的菜单选项。 此外，你将想要编写代码来处理<xref:System.Windows.Forms.MenuItem.Click>这些菜单项的事件。  
  
    ```vb  
    Public ContextMenu1 As New ContextMenu  
    Public NotifyIcon1 As New NotifyIcon  
  
    Public Sub CreateIconMenuStructure()  
       ' Add menu items to shortcut menu.  
       ContextMenu1.MenuItems.Add("&Open Application")  
       ContextMenu1.MenuItems.Add("S&uspend Application")  
       ContextMenu1.MenuItems.Add("E&xit")  
  
       ' Set properties of NotifyIcon component.  
       NotifyIcon1.Icon = New System.Drawing.Icon _   
          (System.Environment.GetFolderPath _   
          (System.Environment.SpecialFolder.Personal)  _   
          & "\Icon.ico")  
       NotifyIcon1.Text = "Right-click me!"  
       NotifyIcon1.Visible = True  
       NotifyIcon1.ContextMenu = ContextMenu1  
    End Sub  
    ```  
  
```csharp  
public NotifyIcon notifyIcon1 = new NotifyIcon();  
public ContextMenu contextMenu1 = new ContextMenu();  
  
public void createIconMenuStructure()  
{  
   // Add menu items to shortcut menu.  
   contextMenu1.MenuItems.Add("&Open Application");  
   contextMenu1.MenuItems.Add("S&uspend Application");  
   contextMenu1.MenuItems.Add("E&xit");  
  
   // Set properties of NotifyIcon component.  
   notifyIcon1.Icon = new System.Drawing.Icon  
      (System.Environment.GetFolderPath  
      (System.Environment.SpecialFolder.Personal)  
      + @"\Icon.ico");  
   notifyIcon1.Visible = true;  
   notifyIcon1.Text = "Right-click me!";  
   notifyIcon1.Visible = true;  
   notifyIcon1.ContextMenu = contextMenu1;  
}  
```  
  
```cpp  
public:  
   System::Windows::Forms::NotifyIcon ^ notifyIcon1;  
   System::Windows::Forms::ContextMenu ^ contextMenu1;  
  
   void createIconMenuStructure()  
   {  
      // Add menu items to shortcut menu.  
      contextMenu1->MenuItems->Add("&Open Application");  
      contextMenu1->MenuItems->Add("S&uspend Application");  
      contextMenu1->MenuItems->Add("E&xit");  
  
      // Set properties of NotifyIcon component.  
      notifyIcon1->Icon = gcnew System::Drawing::Icon  
          (String::Concat(System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::Personal),  
          "\\Icon.ico"));  
      notifyIcon1->Text = "Right-click me!";  
      notifyIcon1->Visible = true;  
      notifyIcon1->ContextMenu = contextMenu1;  
   }  
```  
  
> [!NOTE]
>  必须初始化`notifyIcon1`和`contextMenu1,`您可以通过在你的窗体的构造函数中包含以下语句来执行此操作：  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [如何：使用 Windows 窗体 NotifyIcon 组件向任务栏添加应用程序图标](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [NotifyIcon 组件](notifyicon-component-windows-forms.md)
- [NotifyIcon 组件概述](notifyicon-component-overview-windows-forms.md)
