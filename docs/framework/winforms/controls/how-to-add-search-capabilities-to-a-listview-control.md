---
title: 如何：向 ListView 控件添加搜索功能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- lists [Windows Forms], enabling searching
- list views [Windows Forms], enabling searching
- ListView control [Windows Forms], adding search capabilities
- searching [Windows Forms], adding search capabilities to ListView control
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
ms.openlocfilehash: c1c59c3d4bb5d0d35103371575ebdd49d3559bbe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108545"
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a>如何：向 ListView 控件添加搜索功能
使用中的项的大型列表时通常<xref:System.Windows.Forms.ListView>控件，你想要向用户提供搜索功能。 <xref:System.Windows.Forms.ListView>控制两个不同的方式提供此功能： 文本匹配和搜索位置。  
  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>方法，可对执行文本搜索<xref:System.Windows.Forms.ListView>在列表或详细信息视图中，给定搜索字符串和可选起始和结束索引。 与此相反，<xref:System.Windows.Forms.ListView.FindNearestItem%2A>方法，可查找中的项<xref:System.Windows.Forms.ListView>图标或磁贴视图中，在给定 x 和 y 坐标和要搜索的方向的一组。  
  
### <a name="to-find-an-item-using-text"></a>若要使用文本查找项  
  
1.  创建<xref:System.Windows.Forms.ListView>与<xref:System.Windows.Forms.ListView.View%2A>属性设置为<xref:System.Windows.Forms.View.Details>或<xref:System.Windows.Forms.View.List>，然后填充<xref:System.Windows.Forms.ListView>的项。  
  
2.  调用<xref:System.Windows.Forms.ListView.FindItemWithText%2A>方法，传入你想要查找的项的文本。  
  
3.  下面的代码示例演示如何创建基本<xref:System.Windows.Forms.ListView>、 填充项，并使用文本输入的用户列表中查找项。  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a>若要使用 x 和 y 坐标查找项  
  
1.  创建<xref:System.Windows.Forms.ListView>与<xref:System.Windows.Forms.View>属性设置为<xref:System.Windows.Forms.View.SmallIcon>或<xref:System.Windows.Forms.View.LargeIcon>，然后填充<xref:System.Windows.Forms.ListView>的项。  
  
2.  调用<xref:System.Windows.Forms.ListView.FindNearestItem%2A>方法，传递所需 x 坐标和 y 坐标和想要搜索的方向。  
  
3.  下面的代码示例演示如何创建基本图标<xref:System.Windows.Forms.ListView>，其中填充项，并捕获<xref:System.Windows.Forms.Control.MouseDown>事件向上方向中查找最近的项。  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.FindItemWithText%2A>
- <xref:System.Windows.Forms.ListView.FindNearestItem%2A>
- [ListView 控件](listview-control-windows-forms.md)
- [ListView 控件概述](listview-control-overview-windows-forms.md)
- [如何：使用 Windows 窗体 ListView 控件添加和移除项](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
