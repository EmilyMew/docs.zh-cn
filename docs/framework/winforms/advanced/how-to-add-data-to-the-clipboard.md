---
title: 如何：将数据添加到剪贴板
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: 896f5bd503c53041e2fed1401fd4455049e62449
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109091"
---
# <a name="how-to-add-data-to-the-clipboard"></a>如何：将数据添加到剪贴板
<xref:System.Windows.Forms.Clipboard>类提供了可用于与 Windows 操作系统剪贴板功能进行交互的方法。 许多应用程序的数据用作临时存储库使用剪贴板。 例如，文字处理器剪切和粘贴操作期间使用剪贴板。 剪贴板功能也将数据传输到另一个应用程序中很有用。  
  
 当将数据添加到剪贴板时，您可以指示数据格式，以便其他应用程序能够识别数据，如果用户可以使用该格式。 此外可以将数据添加到剪贴板中多个不同的格式，以增加数据有可能使用其他应用程序的数量。  
  
 剪贴板格式是一个字符串，以便使用该格式的应用程序可以检索关联的数据格式进行标识。 <xref:System.Windows.Forms.DataFormats>类提供了供你使用的预定义的格式名称。 此外可以使用自己的格式名称，或使用其格式与对象的类型。  
  
 若要将数据添加到一个或多个格式在剪贴板中，使用<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>方法。 可以将任何对象传递给此方法，但若要添加多个格式数据，您必须首先将数据添加到一个单独的对象设计成可使用多种格式。 通常情况下，您将添加到你的数据<xref:System.Windows.Forms.DataObject>，但你可以使用实现的任何类型<xref:System.Windows.Forms.IDataObject>接口。  
  
 在[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]，可以直接向剪贴板添加数据，通过使用为简化基本剪贴板任务而设计的新方法。 当处理单一的通用格式，例如文本中的数据时，请使用这些方法。  
  
> [!NOTE]
>  所有基于 Windows 的应用程序共享剪贴板。 因此，可能会有所变动时切换到另一个应用程序。  
>   
>  <xref:System.Windows.Forms.Clipboard>类仅可在线程设置为单线程单元 (STA) 模式。 若要使用此类，请确保你`Main`方法将标有<xref:System.STAThreadAttribute>属性。  
>   
>  对象必须可序列化，才能将其放到剪贴板上。 若要使类型可序列化，将其与标记<xref:System.SerializableAttribute>属性。 如果向剪贴板方法传递了非可序列化对象，该方法将失败而不引发异常。 有关序列化的详细信息，请参阅<xref:System.Runtime.Serialization>。  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>若要将数据添加到剪贴板中单个常见的格式  
  
1.  使用<xref:System.Windows.Forms.Clipboard.SetAudio%2A>， <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>， <xref:System.Windows.Forms.Clipboard.SetImage%2A>，或<xref:System.Windows.Forms.Clipboard.SetText%2A>方法。 这些方法是仅适用于[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>若要将数据添加到剪贴板中的自定义格式  
  
1.  使用<xref:System.Windows.Forms.Clipboard.SetData%2A>具有自定义格式名称的方法。 此方法是仅适用于[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]。  
  
     此外可以使用具有预定义的格式名称<xref:System.Windows.Forms.Clipboard.SetData%2A>方法。 有关详细信息，请参阅 <xref:System.Windows.Forms.DataFormats>。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>若要将数据添加到多个格式剪贴板  
  
1.  使用<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>方法并传入<xref:System.Windows.Forms.DataObject>，其中包含你的数据。 必须使用此方法将数据添加到剪贴板上版本早于[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>请参阅

- [拖放操作和剪贴板支持](drag-and-drop-operations-and-clipboard-support.md)
- [如何：从剪贴板检索数据](how-to-retrieve-data-from-the-clipboard.md)
