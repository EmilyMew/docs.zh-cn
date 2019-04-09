---
title: 如何：列出数据对象中的数据格式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
ms.openlocfilehash: f8230eac33a18a0d99cc757d54c2b901c1afe977
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077740"
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a>如何：列出数据对象中的数据格式
下面的示例演示如何使用<xref:System.Windows.DataObject.GetFormats%2A>方法重载获取表示可在数据对象中每个数据格式的字符串数组。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例代码使用<xref:System.Windows.DataObject.GetFormats%2A>重载获取表示所有可用数据对象 （本机和可自动转换） 中的数据格式的字符串数组。  
  
### <a name="code"></a>代码  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例代码使用<xref:System.Windows.DataObject.GetFormats%2A>重载获取表示仅在数据对象 （可自动转换数据格式进行筛选） 中可用数据格式的字符串数组。  
  
### <a name="code"></a>代码  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.IDataObject>
- [拖放概述](drag-and-drop-overview.md)
