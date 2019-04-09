---
title: 如何：在运行时 （Windows 窗体） 设置图片
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
ms.openlocfilehash: 8ed3ba9050a9117a53b5f4f1cccd26381f55ab32
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073593"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>如何：在运行时 （Windows 窗体） 设置图片
你可以以编程方式设置 Windows 窗体显示的图像<xref:System.Windows.Forms.PictureBox>控件。  
  
### <a name="to-set-a-picture-programmatically"></a>若要以编程方式设置图片  
  
-   设置<xref:System.Windows.Forms.PictureBox.Image%2A>属性使用<xref:System.Drawing.Image.FromFile%2A>方法的<xref:System.Drawing.Image>类。  
  
     在下面的示例中，设置的位置的路径是映像的 My Documents 文件夹。 此操作后，因为您可以假定大多数运行 Windows 操作系统的计算机都包含此目录。 这还使得具有最低系统访问级别的用户能够安全运行应用程序。 下面的示例假定窗体具有<xref:System.Windows.Forms.PictureBox>已添加的控件。  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a>若要清除图形  
  
-   首先，释放正在使用的映像的内存，然后清除该图形。 垃圾回收将释放的内存更高版本如果内存管理成为问题。  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)   
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    >  有关原因的详细信息应使用<xref:System.Drawing.Image.Dispose%2A>方法以这种方式，请参阅[清理了非托管资源](../../../standard/garbage-collection/unmanaged.md)。  
  
     即使图形已加载到控件在设计时，此代码将清除该映像。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [PictureBox 控件概述](picturebox-control-overview-windows-forms.md)
- [如何：使用设计器加载图片](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [如何：在运行时修改图片的大小或位置](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [PictureBox 控件](picturebox-control-windows-forms.md)
