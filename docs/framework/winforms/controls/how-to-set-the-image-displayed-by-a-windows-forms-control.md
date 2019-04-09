---
title: 如何：设置 Windows 窗体控件显示的图像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 031ddcb3b852e75353fed7420735350e79f23df3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085085"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>如何：设置 Windows 窗体控件显示的图像
多个 Windows 窗体控件可以显示图像。 这些映像可以是阐明用途的控件，例如上按钮表示的磁盘图标的图标**保存**命令。 或者，图标可以是为控件提供的外观和行为所需的背景图像。  
  
### <a name="to-set-the-image-displayed-by-a-control"></a>若要设置控件所显示的图像  
  
1.  设置控件的`Image`或`BackgroundImage`类型的对象的属性<xref:System.Drawing.Image>。 通常情况下，你会将图像从文件加载使用<xref:System.Drawing.Image.FromFile%2A>方法。  
  
     在下面的代码示例中，将路径设置的映像的位置是**My Pictures**文件夹。 大多数运行 Windows 操作系统的计算机将包含此目录。 这还使具有最少的系统访问级别的用户安全地运行应用程序。 下面的代码示例要求您已有一个具有窗体<xref:System.Windows.Forms.PictureBox>添加控件。  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
