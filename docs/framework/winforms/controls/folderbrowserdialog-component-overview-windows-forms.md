---
title: FolderBrowserDialog 组件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: aae18167b29c71ad692cc6ba447457cd079374b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074126"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>FolderBrowserDialog 组件概述（Windows 窗体）
Windows 窗体<xref:System.Windows.Forms.FolderBrowserDialog>组件是一个模式对话框，用于浏览和选择文件夹。 此外可以在创建新文件夹<xref:System.Windows.Forms.FolderBrowserDialog>组件。  
  
> [!NOTE]
>  若要选择文件，而不是文件夹，请使用[OpenFileDialog](openfiledialog-component-windows-forms.md)组件。  
  
 <xref:System.Windows.Forms.FolderBrowserDialog>组件，系统会在运行的时使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。 设置<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>属性来确定最顶层的文件夹，然后将对话框中的树视图中显示的任何子文件夹。 一旦已显示对话框中，可以使用<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>属性以获取所选的文件夹的路径。  
  
 添加到窗体时<xref:System.Windows.Forms.FolderBrowserDialog>组件在 Windows 窗体设计器底部的任务栏中显示。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [如何：使用 Windows 窗体 FolderBrowserDialog 组件选择文件夹](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [FolderBrowserDialog 组件](folderbrowserdialog-component-windows-forms.md)
