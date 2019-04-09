---
title: Windows 窗体中更加安全的文件和数据访问
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [Windows Forms], file access
- registry [Windows Forms]
- data access [Windows Forms]
- database access (Windows Forms security)
- data [Windows Forms], secure access
- file access [Windows Forms]
- security [Windows Forms], data access
ms.assetid: 3cd3e55b-2f5e-40dd-835d-f50f7ce08967
ms.openlocfilehash: 557c3296310a7eb3922a6c18b7b3de19ffac953c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115760"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Windows 窗体中更加安全的文件和数据访问
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 使用权限帮助保护资源和数据。 你的应用程序可以读取或写入数据的位置取决于授予该应用程序的权限。 在部分信任环境中运行应用程序时，可能不具有对数据的访问权限，或可能必须更改访问数据的方式。  
  
 遇到安全限制时，你有两个选择：断言该权限（假设已将该权限授予你的应用程序），或者使用编写为用于部分信任中的功能版本。 以下各节探讨如何使用文件、数据库和在部分信任环境中运行的应用程序中的注册表访问。  
  
> [!NOTE]
>  默认情况下，生成 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 部署的工具默认这些部署从在其上运行的计算机请求完全信任。 如果您决定要在部分信任环境中运行的更高的安全性优势，则必须更改此默认值在 Visual Studio 或其中一个[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]工具 （Mage.exe 或 MageUI.exe）。 有关 Windows 窗体安全性以及如何确定您的应用程序的适当的信任级别的详细信息，请参阅[中的安全性 Windows 窗体概述](security-in-windows-forms-overview.md)。  
  
## <a name="file-access"></a>文件访问  
 <xref:System.Security.Permissions.FileIOPermission> 类控制 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中的文件和文件夹访问。 默认情况下，安全系统不会向本地 Intranet 和 Internet 区域等部分信任环境授予 <xref:System.Security.Permissions.FileIOPermission>。 但是，如果修改应用程序的设计或使用不同的方法访问文件，那么需要文件访问权限的应用程序仍可以在这些环境中正常工作。 默认情况下，将向本地 Intranet 区域授予以下权限：具有相同的站点访问权限和相同的目录访问权限、连回其源站点、从其安装目录进行读取。 默认情况下，仅向 Internet 区域授予连回其源站点的权限。  
  
### <a name="user-specified-files"></a>用户指定的文件  
 针对不具有文件访问权限的一种应对方法是：提示用户通过使用 <xref:System.Windows.Forms.OpenFileDialog> 或 <xref:System.Windows.Forms.SaveFileDialog> 类提供特定文件信息。 这种用户交互有助于在一定程度上确保应用程序无法恶意加载专用文件或覆盖重要文件。 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 和 <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> 方法通过打开用户指定的文件的文件流提供读写文件访问权限。 这些方法还有助于通过隐藏文件路径保护用户文件。  
  
> [!NOTE]
>  这些权限根据应用程序是位于 Internet 区域中还是 Intranet 区域中而有所不同。 Internet 区域的应用程序只能使用 <xref:System.Windows.Forms.OpenFileDialog>，而 Intranet 应用程序则具有不受限制的文件对话框权限。  
  
 <xref:System.Security.Permissions.FileDialogPermission> 类指定应用程序可使用的文件对话框类型。 下表显示使用每种 <xref:System.Windows.Forms.FileDialog> 类所必须具有的值。  
  
|类|所需的访问值|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
>  实际调用 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法前并不需要这一特定权限。  
  
 显示文件对话框的权限不会授予应用程序对 <xref:System.Windows.Forms.FileDialog>、<xref:System.Windows.Forms.OpenFileDialog> 和 <xref:System.Windows.Forms.SaveFileDialog> 类所有成员的完全访问权限。 有关调用每个方法所需的确切权限的信息，请参阅 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 类库文档中该方法的参考主题。  
  
 以下代码示例使用 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法将用户指定的文件打开为 <xref:System.Windows.Forms.RichTextBox> 控件。 该示例需要 <xref:System.Security.Permissions.FileDialogPermission> 和关联的 <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> 枚举值。 该示例演示如何处理 <xref:System.Security.SecurityException> 以确定是否应禁用保存功能。 此示例要求你的 <xref:System.Windows.Forms.Form> 具有名为 `ButtonOpen` 的 <xref:System.Windows.Forms.Button> 控件和名为 `RtfBoxMain` 的 <xref:System.Windows.Forms.RichTextBox> 控件。  
  
> [!NOTE]
>  在示例中未展示保存功能的编程逻辑。  
  
```vb  
Private Sub ButtonOpen_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles ButtonOpen.Click   
  
    Dim editingFileName as String = ""  
    Dim saveAllowed As Boolean = True  
  
    ' Displays the OpenFileDialog.  
    If (OpenFileDialog1.ShowDialog() = DialogResult.OK) Then  
        Dim userStream as System.IO.Stream  
        Try   
            ' Opens the file stream for the file selected by the user.  
            userStream =OpenFileDialog1.OpenFile()   
            Me.RtfBoxMain.LoadFile(userStream, _  
                RichTextBoxStreamType.PlainText)  
        Finally  
            userStream.Close()  
        End Try  
  
        ' Tries to get the file name selected by the user.  
        ' Failure means that the application does not have  
        ' unrestricted permission to the file.  
        Try   
            editingFileName = OpenFileDialog1.FileName  
        Catch ex As Exception  
            If TypeOf ex Is System.Security.SecurityException Then   
                ' The application does not have unrestricted permission   
                ' to the file so the save feature will be disabled.  
                saveAllowed = False   
            Else   
                Throw ex  
            End If  
        End Try  
    End If  
End Sub  
```  
  
```csharp  
private void ButtonOpen_Click(object sender, System.EventArgs e)   
{  
    String editingFileName = "";  
    Boolean saveAllowed = true;  
  
    // Displays the OpenFileDialog.  
    if (openFileDialog1.ShowDialog() == DialogResult.OK)   
    {  
        // Opens the file stream for the file selected by the user.  
        using (System.IO.Stream userStream = openFileDialog1.OpenFile())   
        {  
            this.RtfBoxMain.LoadFile(userStream,  
                RichTextBoxStreamType.PlainText);  
            userStream.Close();  
        }  
  
        // Tries to get the file name selected by the user.  
        // Failure means that the application does not have  
        // unrestricted permission to the file.  
        try   
        {  
            editingFileName = openFileDialog1.FileName;  
        }   
        catch (Exception ex)   
        {  
            if (ex is System.Security.SecurityException)   
            {  
                // The application does not have unrestricted permission   
                // to the file so the save feature will be disabled.  
                saveAllowed = false;   
            }   
            else   
            {  
                throw ex;  
            }  
        }  
    }  
}  
```  
  
> [!NOTE]
>  在 Visual C# 中，确保将添加代码以启用事件处理程序。 通过使用来自前面的示例代码，以下代码演示如何启用事件处理程序。`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>其他文件  
 有时你将需要读取或写入到用户未指定的文件，例如当你必须保存应用程序设置时。 在本地 Intranet 和 Internet 区域中，你的应用程序将无权在本地文件中存储数据。 但是，它将能够在独立存储中存储数据。 独立存储是一个抽象的数据隔离舱（而非具体的存储位置），它包含一个或多个独立存储文件（称为存储区），这些文件包含存储数据的实际目录位置。 文件访问权限（如 <xref:System.Security.Permissions.FileIOPermission>）不是必须具有的权限；<xref:System.Security.Permissions.IsolatedStoragePermission> 类控制独立存储权限。 默认情况下，在本地 Intranet 和 Internet 区域中运行的应用程序可以使用独立存储来存储数据；但是，磁盘配额等设置可能有所不同。 有关独立存储的详细信息，请参阅[独立存储](../../standard/io/isolated-storage.md)。  
  
 下面的示例使用独立存储将数据写入位于某个存储区中的文件。 该示例需要 <xref:System.Security.Permissions.IsolatedStorageFilePermission> 和 <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> 枚举值。 该示例演示了将 <xref:System.Windows.Forms.Button> 控件的某些属性值读取和写入到独立存储中的文件。 应用程序启动后将调用 `Read` 函数，将在应用程序结束之前调用 `Write` 函数。 该示例需要`Read`并`Write`函数作为的成员存在<xref:System.Windows.Forms.Form>，其中包含<xref:System.Windows.Forms.Button>控件命名为`MainButton`。  
  
```vb  
' Reads the button options from the isolated storage. Uses Default values   
' for the button if the options file does not exist.  
Public Sub Read()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try  
        ' Checks to see if the options.txt file exists.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
  
            ' Opens the file because it exists.  
            Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
                 (filename, IO.FileMode.Open,isoStore)  
            Dim reader as System.IO.StreamReader  
            Try   
                reader = new System.IO.StreamReader(isos)  
  
                ' Reads the values stored.  
                Dim converter As System.ComponentModel.TypeConverter  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Color))  
  
                Me.MainButton.BackColor = _   
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
                me.MainButton.ForeColor = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Font))  
                me.MainButton.Font = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Font)  
  
            Catch ex As Exception  
                Debug.WriteLine("Cannot read options " + _  
                    ex.ToString())  
            Finally  
                reader.Close()  
            End Try  
        End If  
  
    Catch ex As Exception  
        Debug.WriteLine("Cannot read options " + ex.ToString())  
    End Try  
End Sub  
  
' Writes the button options to the isolated storage.  
Public Sub Write()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try   
        ' Checks if the file exists, and if it does, tries to delete it.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
            isoStore.DeleteFile(filename)  
        End If  
    Catch ex As Exception  
        Debug.WriteLine("Cannot delete file " + ex.ToString())  
    End Try  
  
    ' Creates the options.txt file and writes the button options to it.  
    Dim writer as System.IO.StreamWriter  
    Try   
        Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
             (filename, IO.FileMode.CreateNew, isoStore)  
  
        writer = New System.IO.StreamWriter(isos)  
        Dim converter As System.ComponentModel.TypeConverter  
  
        converter = System.ComponentModel.TypeDescriptor.GetConverter _   
           (GetType(Color))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.BackColor))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.ForeColor))  
  
        converter = System.ComponentModel TypeDescriptor.GetConverter _   
           (GetType(Font))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.Font))  
  
    Catch ex as Exception  
        Debug.WriteLine("Cannot write options " + ex.ToString())  
  
    Finally  
        writer.Close()  
    End Try  
End Sub  
```  
  
```csharp  
// Reads the button options from the isolated storage. Uses default values   
// for the button if the options file does not exist.  
public void Read()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try  
    {  
        // Checks to see if the options.txt file exists.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            // Opens the file because it exists.  
            System.IO.IsolatedStorage.IsolatedStorageFileStream isos =   
                new System.IO.IsolatedStorage.IsolatedStorageFileStream  
                    (filename, System.IO.FileMode.Open,isoStore);  
            System.IO.StreamReader reader = null;  
            try   
            {  
                reader = new System.IO.StreamReader(isos);  
  
                // Reads the values stored.  
                TypeConverter converter ;  
                converter = TypeDescriptor.GetConverter(typeof(Color));  
  
                this.MainButton.BackColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
                this.MainButton.ForeColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
  
                converter = TypeDescriptor.GetConverter(typeof(Font));  
                this.MainButton.Font =   
                  (Font)(converter.ConvertFromString(reader.ReadLine()));  
            }  
            catch (Exception ex)  
            {   
                System.Diagnostics.Debug.WriteLine  
                     ("Cannot read options " + ex.ToString());  
            }  
            finally  
            {  
                reader.Close();  
            }  
        }  
    }   
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot read options " + ex.ToString());  
    }  
}  
  
// Writes the button options to the isolated storage.  
public void Write()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try   
    {  
        // Checks if the file exists and, if it does, tries to delete it.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            isoStore.DeleteFile(filename);  
        }  
    }  
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot delete file " + ex.ToString());  
    }  
  
    // Creates the options file and writes the button options to it.  
    System.IO.StreamWriter writer = null;  
    try   
    {  
        System.IO.IsolatedStorage.IsolatedStorageFileStream isos = new   
            System.IO.IsolatedStorage.IsolatedStorageFileStream(filename,   
            System.IO.FileMode.CreateNew,isoStore);  
  
        writer = new System.IO.StreamWriter(isos);  
        TypeConverter converter ;  
  
        converter = TypeDescriptor.GetConverter(typeof(Color));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.BackColor));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.ForeColor));  
  
        converter = TypeDescriptor.GetConverter(typeof(Font));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.Font));  
  
    }  
    catch (Exception ex)  
    {   
        System.Diagnostics.Debug.WriteLine  
           ("Cannot write options " + ex.ToString());  
    }  
    finally  
    {  
        writer.Close();  
    }  
}  
```  
  
## <a name="database-access"></a>数据库访问权限  
 访问数据库所需的权限因数据库提供程序而异；但是，只有使用相应权限运行的应用程序可以通过数据连接访问数据库。 有关访问数据库所需的权限的详细信息，请参阅[代码访问安全性和 ADO.NET](../data/adonet/code-access-security.md)。  
  
 如果因为要使应用程序以部分信任权限运行而不能直接访问数据库，作为一种替代方法，可将 Web 服务作为备份方法来访问你的数据。 Web 服务是一种软件，可通过网络以编程方式进行访问。 通过 Web 服务，应用程序可以跨代码组区域共享数据。 默认情况下，本地 Intranet 和 Internet 区域中的应用程序被授予了访问其源站点的权限，使其能够调用同一台服务器上托管的 Web 服务。 有关详细信息请参阅[ASP.NET AJAX 中的 Web 服务](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100))或[Windows Communication Foundation](../wcf/index.md)。  
  
## <a name="registry-access"></a>注册表访问  
 <xref:System.Security.Permissions.RegistryPermission> 类控制对操作系统注册表的访问。 默认情况下，只有在本地运行的应用程序可以访问注册表。  <xref:System.Security.Permissions.RegistryPermission> 仅授予应用程序尝试访问注册表; 的权限它不保证访问一定成功，因为操作系统仍将强制对注册表的安全。  
  
 由于无法在部分信任环境下访问注册表，所以可能需要寻找其他方法来存储你的数据。 存储应用程序设置时，请使用独立存储而非注册表。 独立存储也可用于存储其他特定于应用程序的文件。 由于默认授予了应用程序访问其源站点的权限，因此还可以存储有关服务器或源站点的全局应用程序信息。  
  
## <a name="see-also"></a>请参阅

- [Windows 窗体中的更加安全的打印](more-secure-printing-in-windows-forms.md)
- [Windows 窗体中额外的安全注意事项](additional-security-considerations-in-windows-forms.md)
- [Windows 窗体中的安全性概述](security-in-windows-forms-overview.md)
- [Windows 窗体安全](windows-forms-security.md)
- [Mage.exe（清单生成和编辑工具）](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe（图形化客户端中的清单生成和编辑工具）](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
