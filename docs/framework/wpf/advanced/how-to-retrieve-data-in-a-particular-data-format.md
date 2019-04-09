---
title: 如何：以特定数据格式检索数据
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
ms.openlocfilehash: b3ec1b8fa873fd449956912e9e77e98b0362cb0e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080015"
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a>如何：以特定数据格式检索数据
以下示例演示如何从指定的格式中的数据对象中检索数据。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的代码示例使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>重载，以首先检查是否指定的数据格式 （本机或通过自动转换）; 如果指定的格式不可用，该示例通过检索数据<xref:System.Windows.DataObject.GetData%28System.String%29>方法。  
  
### <a name="code"></a>代码  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例代码使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>重载来首先检查指定的数据格式是否可用本机 （自动转换的数据格式已筛选的）; 如果指定的格式不可用，该示例通过使用检索数据<xref:System.Windows.DataObject.GetData%28System.String%29>方法。  
  
### <a name="code"></a>代码  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.IDataObject>
- [拖放概述](drag-and-drop-overview.md)
