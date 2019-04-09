---
title: 如何：在运行时 （Windows 窗体） 中修改的大小或位置的图片
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
ms.openlocfilehash: 5d817d34e47253b2e35afa7bb41c59eea06e1f94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178823"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>如何：在运行时 （Windows 窗体） 中修改的大小或位置的图片
如果使用 Windows 窗体<xref:System.Windows.Forms.PictureBox>控件在窗体上可以设置<xref:System.Windows.Forms.PictureBox.SizeMode%2A>到其上的属性：  
  
-   将图片的左上的角的控件的左上角对齐  
  
-   使图片在控件内居中  
  
-   调整控件以适合其显示的图片的大小  
  
-   拉伸以适合控件显示的任何图片  
  
 拉伸图片 （尤其是一个位图格式） 可能导致丢失在图像质量。 图元文件，这是一系列有关在运行时绘制图像的图形说明的都更好地适合拉伸比位图。  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>若要在运行时设置的缩放模式属性  
  
1.  设置<xref:System.Windows.Forms.PictureBox.SizeMode%2A>到<xref:System.Windows.Forms.PictureBoxSizeMode.Normal>（默认值）， <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>， <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>，或<xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>。 <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> 映像是放置控件的左上角;如果图像大于该控件，将剪切其较低和右边缘。 <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> 表示该映像在控件中; 中居中如果图像大于该控件，将剪切图片的外边缘。 <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> 表示控件的大小调整为图像的大小。 <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> 相反，并表示图像的大小调整为该控件的大小。  
  
     在下面的示例中，设置的位置的路径是映像的 My Documents 文件夹。 此操作后，因为您可以假定大多数运行 Windows 操作系统的计算机都包含此目录。 这还使得具有最低系统访问级别的用户能够安全运行应用程序。 下面的示例假定窗体具有<xref:System.Windows.Forms.PictureBox>已添加的控件。  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.PictureBox>
- [如何：使用设计器加载图片](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [PictureBox 控件概述](picturebox-control-overview-windows-forms.md)
- [如何：在运行时设置图片](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox 控件](picturebox-control-windows-forms.md)
