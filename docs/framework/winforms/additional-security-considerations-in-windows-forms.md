---
title: Windows 窗体中额外的安全注意事项
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
ms.openlocfilehash: 6ab7b4d8fe8366a214d70cd73e7e33cafcc584f8
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409388"
---
# <a name="additional-security-considerations-in-windows-forms"></a>Windows 窗体中额外的安全注意事项
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 安全设置可能导致应用程序在部分信任环境中运行与在本地计算机上运行有所不同。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 限制对关键本地资源的访问，如文件系统、网络和非托管 API 等。 安全设置会影响 Microsoft Windows API 或其他无法验证由安全系统的 Api 调用的能力。 安全性还会影响应用程序的其他方面，包括文件和数据访问以及打印。 有关在部分信任环境中访问文件和数据的详细信息，请参阅 [Windows 窗体中更加安全的文件和数据访问](more-secure-file-and-data-access-in-windows-forms.md)。 有关在部分信任环境中进行打印的详细信息，请参阅 [Windows 窗体中更加安全的打印](more-secure-printing-in-windows-forms.md)。  
  
 以下部分介绍如何使用剪贴板、 执行窗口操作和从部分信任环境中运行的应用程序调用 Windows API。  
  
## <a name="clipboard-access"></a>剪贴板访问  
 <xref:System.Security.Permissions.UIPermission>类控制对剪贴板，并显示关联的访问<xref:System.Security.Permissions.UIPermissionClipboard>枚举值指示的访问级别。 下表显示可能的权限级别。  
  
|UIPermissionClipboard 值|描述|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|可以不受限制地使用剪贴板。|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|使用剪贴板时有某些限制。 将数据放置到剪贴板中的能力（“复制”或“剪切”命令操作）是不受限制的。 接受粘贴的固有控件（例如文本框）可接受剪贴板数据，但用户控件无法以编程方式从剪贴板读取数据。|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|不能使用剪贴板。|  
  
 默认情况下，本地 Intranet 区域接收<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>访问权限和 Internet 区域接收<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>访问。 这意味着，应用程序可以将数据复制到剪贴板，但无法通过编程方式进行粘贴或从剪贴板进行读取。 这些限制可以防止不完全受信任的程序读取另一应用程序复制到剪贴板的内容。 如果应用程序需要完全的剪贴板访问权限，但你又不具有这些权限，则必须提升应用程序的权限。 有关提升权限的详细信息，请参阅[常规安全策略管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))。  
  
## <a name="window-manipulation"></a>窗口操作  
 <xref:System.Security.Permissions.UIPermission>类还控制执行窗口操作和其他与 UI 相关的操作，和关联的权限<xref:System.Security.Permissions.UIPermissionWindow>枚举值指示的访问级别。 下表显示可能的权限级别。  
  
 默认情况下，本地 Intranet 区域接收<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>访问权限和 Internet 区域接收<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>访问。 这意味着，在“Internet”区域中，应用程序可以执行大多数窗口操作和 UI 操作，但窗口的外观将被修改。 修改后的窗口在第一次运行时会显示一条气球状通知，包含修改的标题栏文本，并需要标题栏上有一个关闭按钮。 气球状通知和标题栏会向应用程序的用户指示：应用程序正在部分信任环境下运行。  
  
|UIPermissionWindow 值|描述|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|用户可以不受限制地使用所有窗口和用户输入事件。|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|用户只能使用较安全的顶级窗口和子窗口进行绘制，并且只能在这些顶级窗口和子窗口中使用用户界面的用户输入事件。 这些较安全窗口具有明显的标签，并具有最小化和最大化限制。 限制防止潜在的有害欺骗攻击，例如模拟系统登录屏幕或系统桌面，并将限制编程访问以父窗口、 与焦点相关的 Api 和使用<xref:System.Windows.Forms.ToolTip>控件，|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|用户只能使用较安全子窗口进行绘制，并且只能在该子窗口中使用用户界面的用户输入事件。 浏览器中显示的控件就是一个较安全子窗口的示例。|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|用户不能使用任何窗口或用户界面事件。 不能使用任何用户界面。|  
  
 由标识每个权限级别<xref:System.Security.Permissions.UIPermissionWindow>枚举允许其上面的级别比更少的操作。 以下各表指示受限制的操作<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>和<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>值。 有关每个成员所需的确切权限，请参阅 .NET Framework 类库文档中有关该成员的参考资料。  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> 权限限制下表中列出的操作。  
  
|组件|受限制的操作|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-   设置 <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A> 属性。|  
|<xref:System.Windows.Forms.Control>|-获取<xref:System.Windows.Forms.Control.Parent%2A>属性。<br />-   设置 `Region` 属性。<br />-调用<xref:System.Windows.Forms.Control.FindForm%2A>， <xref:System.Windows.Forms.Control.Focus%2A>，<xref:System.Windows.Forms.Control.FromChildHandle%2A>并<xref:System.Windows.Forms.Control.FromHandle%2A>， <xref:System.Windows.Forms.Control.PreProcessMessage%2A>， <xref:System.Windows.Forms.Control.ReflectMessage%2A>，或<xref:System.Windows.Forms.Control.SetTopLevel%2A>方法。<br />-调用<xref:System.Windows.Forms.Control.GetChildAtPoint%2A>方法如果返回的控件不是调用控件的子级。<br />-   修改容器控件内部的控件焦点。|  
|<xref:System.Windows.Forms.Cursor>|-   设置 <xref:System.Windows.Forms.Cursor.Clip%2A> 属性。<br />-调用<xref:System.Windows.Forms.Control.Hide%2A>方法。|  
|<xref:System.Windows.Forms.DataGrid>|-调用<xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A>方法。|  
|<xref:System.Windows.Forms.Form>|-获取<xref:System.Windows.Forms.Form.ActiveForm%2A>或<xref:System.Windows.Forms.Form.MdiParent%2A>属性。<br />-设置<xref:System.Windows.Forms.Form.ControlBox%2A>， <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>，或<xref:System.Windows.Forms.Form.TopMost%2A>属性。<br />-设置<xref:System.Windows.Forms.Form.Opacity%2A>低于 50%的属性。<br />-设置<xref:System.Windows.Forms.Form.WindowState%2A>属性设置为<xref:System.Windows.Forms.FormWindowState.Minimized>以编程方式。<br />-调用<xref:System.Windows.Forms.Form.Activate%2A>方法。<br />-使用<xref:System.Windows.Forms.FormBorderStyle.None>， <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>，并<xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow><xref:System.Windows.Forms.FormBorderStyle>枚举值。|  
|<xref:System.Windows.Forms.NotifyIcon>|-使用<xref:System.Windows.Forms.NotifyIcon>组件是完全受限制。|  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>在以下表中，除了限制到列出的操作<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>值。  
  
|组件|受限制的操作|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-显示一个对话框派生自<xref:System.Windows.Forms.CommonDialog>类。|  
|<xref:System.Windows.Forms.Control>|-调用<xref:System.Windows.Forms.Control.CreateGraphics%2A>方法。<br />-   设置 <xref:System.Windows.Forms.Control.Cursor%2A> 属性。|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-   设置 <xref:System.Windows.Forms.Cursor.Current%2A> 属性。|  
|<xref:System.Windows.Forms.MessageBox>|-调用<xref:System.Windows.Forms.Form.Show%2A>方法。|  
  
### <a name="hosting-third-party-controls"></a>承载第三方控件  
 如果窗体承载第三方控件，可能会发生另一种窗口操作。 第三方控件是任何自定义<xref:System.Windows.Forms.UserControl>不具有自己开发和编译。 尽管承载方案难以侵入，但第三方控件理论上仍有可能扩展其呈现图面以覆盖整个窗体区域。 此控件随后即可模仿关键对话框，并从你的用户那里请求用户名/密码组合或银行帐号等信息。  
  
 若要限制这种潜在风险，应仅使用来自可信任的供应商的第三方控件。 如果所使用的第三方控件是从无法验证的源下载的，则建议检查源代码是否有潜在侵入风险。 确认源无恶意后，应自己编译程序集以确保源与程序集匹配。  
  
## <a name="windows-api-calls"></a>Windows API 调用  
 如果您的应用程序设计需要从 Windows API 调用的函数，您正在访问非托管的代码。 在这种情况下使用 Windows API 调用或值时，无法确定到窗口或操作系统的代码的操作。 <xref:System.Security.Permissions.SecurityPermission>类和<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>的值<xref:System.Security.Permissions.SecurityPermissionFlag>枚举控制对非托管代码的访问。 应用程序可以访问非托管的代码，仅当向其授予<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>权限。 默认情况下，只有本地运行的应用程序才能调用非托管代码。  
  
 某些 Windows 窗体成员提供需要的非托管的访问<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>权限。 下表列出了中的成员<xref:System.Windows.Forms>需要权限的命名空间。 有关各个成员所需权限的详细信息，请参阅 .NET Framework 类库文档。  
  
|组件|成员|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.AddMessageFilter%2A> 方法<br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> 属性<br />-   `Exit` 方法<br />-   <xref:System.Windows.Forms.Application.ExitThread%2A> 方法<br />-   <xref:System.Windows.Forms.Application.ThreadException> 事件|  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog.HookProc%2A> 方法<br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\ 方法<br />-   <xref:System.Windows.Forms.CommonDialog.Reset%2A> 方法<br />-   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A> 方法|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateParams%2A> 方法<br />-   <xref:System.Windows.Forms.Control.DefWndProc%2A> 方法<br />-   <xref:System.Windows.Forms.Control.DestroyHandle%2A> 方法<br />-   <xref:System.Windows.Forms.Control.WndProc%2A> 方法|  
|<xref:System.Windows.Forms.Help>|-   <xref:System.Windows.Forms.Help.ShowHelp%2A> 方法<br />-   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A> 方法|  
|<xref:System.Windows.Forms.NativeWindow>|-   <xref:System.Windows.Forms.NativeWindow> 类|  
|<xref:System.Windows.Forms.Screen>|-   <xref:System.Windows.Forms.Screen.FromHandle%2A> 方法|  
|<xref:System.Windows.Forms.SendKeys>|-   <xref:System.Windows.Forms.SendKeys.Send%2A> 方法<br />-   <xref:System.Windows.Forms.SendKeys.SendWait%2A> 方法|  
  
 如果你的应用程序无权调用非托管的代码，你的应用程序必须请求<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>权限，或者您必须考虑实现这些功能的其他方法; 在许多情况下，Windows 窗体提供了 Windows 的托管替代方法API 函数。 如果不存在任何备选方法并且应用程序必须访问非托管代码，则必须提升应用程序的权限。  
  
 调用非托管代码的权限使应用程序几乎可以执行任何操作。 因此，应该只向来自于受信任源的应用程序授予调用非托管代码的权限。 另外，根据应用程序的不同，调用非托管代码的应用程序功能块可以是可选的，或者只在完全受信任的环境中启用。 有关危险权限的详细信息，请参阅[危险权限和策略管理](../misc/dangerous-permissions-and-policy-administration.md)。 有关提升权限的详细信息，请参阅[常规安全策略管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))。  
  
## <a name="see-also"></a>请参阅
- [在 Windows 窗体中提高文件和数据访问的安全性](more-secure-file-and-data-access-in-windows-forms.md)
- [Windows 窗体中更加安全的打印](more-secure-printing-in-windows-forms.md)
- [Windows 窗体中的安全性概述](security-in-windows-forms-overview.md)
- [Windows 窗体安全](windows-forms-security.md)
- [保护 ClickOnce 应用程序](/visualstudio/deployment/securing-clickonce-applications)
