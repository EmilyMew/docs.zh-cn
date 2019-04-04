---
title: 打印概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print path [WPF], XPS
- printers [WPF], XPSDrv-based
- printing [WPF]
- PrintQueue class PrintServer class [WPF]
- XML Paper Specification (XPS) file format
- XPS (XML Paper Specification) file format
- XPSDrv-based printers
- GDI print path [WPF]
ms.assetid: 0de8ac41-9aa6-413d-a121-7aa6f41539b1
ms.openlocfilehash: c009d86deada690f673736e0e35eb710e25f7781
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654375"
---
# <a name="printing-overview"></a>打印概述
使用 Microsoft.NET Framework 中，使用 Windows Presentation Foundation (WPF) 应用程序开发人员拥有丰富的打印和打印系统管理新[!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]。 在 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] 中，还为创建 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 应用程序的开发人员和使用非托管代码的开发人员提供了这些打印系统增强功能中的某些功能。 此新功能的核心是新的 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] 文件格式和 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 打印路径。  
  
 本主题包含以下各节：  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>关于 XPS  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 是电子文档格式（即后台打印文件格式），并且采用的是页面描述语言。 此格式是开放文档格式，它使用 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]、[!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)] 及其他行业标准来创建跨平台的文档。 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 简化了创建、共享、打印、查看和存档数字文档的流程。 有关其他信息[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]，请参阅[XPS 文档](/windows/desktop/printdocs/documents)。  
  
 [以编程方式打印 XPS 文件](how-to-programmatically-print-xps-files.md)中演示了使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 打印基于 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 的内容的几种方法。 在查看本主题中的内容时，参考这些示例会很有帮助。 (非托管的代码开发人员应参阅文档[MXDC_ESCAPE 函数](/windows/desktop/printdocs/mxdc-escape)。 Windows 窗体开发人员必须使用[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]中<xref:System.Drawing.Printing>命名空间不支持完整[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]打印路径，但支持 GDI 到 XPS 的混合打印路径。 请参阅下面的**打印路径体系结构**。）  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>XPS 打印路径  
 [!INCLUDE[TLA#tla_metro](../../../../includes/tlasharptla-metro-md.md)]打印路径是一种新[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]重新定义如何在 Windows 应用程序中处理打印的功能。 因为 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 可以替换文档表示语言（如 RTF）、打印后台处理程序格式（如 WMF）和页面描述语言（如 PCL 和 Postscript），所以在打印机驱动程序或设备中，从应用程序发布到最终处理，新的打印路径都保持 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 格式。  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 打印路径是基于 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 打印机驱动程序模型 (XPSDrv) 生成的，该模型为开发人员带来了多个优点，如 [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] 打印、改进了颜色支持以及大大提高了打印性能。 (有关 XPSDrv 的详细信息，请参阅[Windows 驱动程序工具包文档](/windows-hardware/drivers/)。)  
  
 有关打印后台处理程序的操作[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]文档实质上是与以前版本的 Windows 中的相同。 但是，它已得到增强，除了现有的 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 打印路径外，还支持 [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 打印路径。 新的打印路径在本机使用 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 后台打印文件。 虽然为 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 的之前版本编写的用户模式打印机驱动程序将继续运行，但仍需要 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 打印机驱动程序 (XPSDrv)，以便使用 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 打印路径。  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 打印路径的优势巨大，其中包括：  
  
-   [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)] 打印支持  
  
-   对高级颜色配置文件的本机支持（包括 32 位/通道 (bpc)、CMYK、已命名的颜色、n 墨迹）以及对透明和渐变的本机支持。  
  
-   改进的打印性能的同时在.NET Framework 和[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]基于应用程序。  
  
-   行业标准 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 格式。  
  
 对于基本打印方案，提供了简单直观的 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]只需单一入口点即可进入用户界面、完成配置和作业提交。 对于高级方案，为 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 自定义（或根本没有 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]）、同步或异步打印以及批量打印功能添加了附加支持。 这两个选项在完全或部分信任模式下都提供打印支持。  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 的设计充分考虑了扩展性。 使用扩展性框架，可以将特性和功能以模块化方式添加到 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 中。 扩展性功能包括：  
  
-   打印架构。 公共架构将定期进行更新，并可以实现设备功能的迅速扩展。 （请参阅下面的 **PrintTicket 和 PrintCapabilities**。）  
  
-   可扩展筛选器管道。 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 打印机驱动程序 (XPSDrv) 筛选器管道设计用于启用直接和可缩放的 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 文档打印。 有关详细信息，请参阅[XPSDrv 的打印机驱动程序](/windows-hardware/drivers/print/xpsdrv-printer-drivers)。 
  
### <a name="print-path-architecture"></a>打印路径体系结构  
 虽然两个[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].NET Framework 应用程序都支持[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]，[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]和 Windows 窗体应用程序使用[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]到[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]转换来创建[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]格式的内容对于[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]打印机驱动程序 (XPSDrv)。 不要求这些应用程序使用 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 打印路径，而可以继续使用基于 [!INCLUDE[TLA#tla_emf](../../../../includes/tlasharptla-emf-md.md)] 的打印。 但是，大多数 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 功能和增强功能仅可用于面向 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 打印路径的应用程序。  
  
 若要启用使用的基于 XPSDrv 的打印机[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]和 Windows 窗体应用程序[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]打印机驱动程序 (XPSDrv) 支持的转换[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]到[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]格式。 XPSDrv 模型还提供从 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 到 [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 格式的转换器，以便 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 应用程序能够打印 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 文档。 有关[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]应用程序、 转换[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]到[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]会自动完成格式<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>和<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>方法<xref:System.Windows.Xps.XpsDocumentWriter>类只要写操作的目标打印队列没有XPSDrv 驱动程序。 (Windows 窗体应用程序不能打印[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]文档。)  
  
 下图描绘了打印子系统，并定义提供的部分[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]，以及由软件和硬件供应商定义的部分：  
  
 ![屏幕截图显示了 XPS 打印系统。](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>基本 XPS 打印  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 定义基本和高级 [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]。 对于不需要各种打印自定义或对 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 完整功能集的访问权限的应用程序，可以提供基本打印支持。 基本打印支持通过一个打印对话框控件公开，该控件要求最低的配置，并采用熟悉的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 可以通过此简化的打印模型来使用众多 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 功能。  
  
#### <a name="printdialog"></a>PrintDialog  
 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> 控件为 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、配置和 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 作业提交提供单一入口点。 若要了解如何实例化和使用该控件，请参阅[调用打印对话框](how-to-invoke-a-print-dialog.md)。  
  
### <a name="advanced-xps-printing"></a>高级 XPS 打印  
 若要访问完整的 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 功能集、必须使用高级打印 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]。 下面更详细地介绍了几个相关的 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]。 有关完整列表[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]打印路径[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，请参阅<xref:System.Windows.Xps>和<xref:System.Printing>命名空间的引用。  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket 和 PrintCapabilities  
 <xref:System.Printing.PrintTicket>并<xref:System.Printing.PrintCapabilities>类是高级基础[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]功能。 这两种类型的对象均是面向打印的功能（例如排序规则、双面打印、装订等）的 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 格式的结构。这些结构由打印架构定义。 <xref:System.Printing.PrintTicket> 指示打印机如何处理打印作业。 <xref:System.Printing.PrintCapabilities> 类定义打印机的各种功能。 通过查询打印机的功能，可以创建充分利用打印机的受支持功能的 <xref:System.Printing.PrintTicket>。 同样，可以避免不受支持的功能。  
  
 下面的示例演示如何使用代码查询打印机的 <xref:System.Printing.PrintCapabilities> 和创建 <xref:System.Printing.PrintTicket>。  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer 和 PrintQueue  
 <xref:System.Printing.PrintServer> 类表示一个网络打印服务器，而 <xref:System.Printing.PrintQueue> 类则表示一台打印机以及与其关联的输出作业队列。 结合使用这些 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，可以对服务器的打印作业进行高级管理。 <xref:System.Printing.PrintServer> 或其派生类之一用于管理 <xref:System.Printing.PrintQueue>。 <xref:System.Printing.PrintQueue.AddJob%2A> 方法用于将新的打印作业插入队列。  
  
 下面的示例演示如何使用代码创建 <xref:System.Printing.LocalPrintServer> 和访问其默认的 <xref:System.Printing.PrintQueue>。  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 <xref:System.Windows.Xps.XpsDocumentWriter> 及其众多 <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> 和 <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> 方法用于将 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 文档写入 <xref:System.Printing.PrintQueue>。 例如，<xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> 方法用于同步输出 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 文档和 <xref:System.Printing.PrintTicket>。 <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> 方法用于异步输出 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 文档和 <xref:System.Printing.PrintTicket>。  
  
 下面的示例演示如何使用代码创建 <xref:System.Windows.Xps.XpsDocumentWriter>。  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> 方法还提供打印方法。 请参阅[以编程方式打印 XPS 文件](how-to-programmatically-print-xps-files.md)。 了解详细信息。  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>GDI 打印路径  
 虽然[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]应用程序以本机方式支持[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]打印路径[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]和 Windows 窗体应用程序还可以充分利用一些[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]功能。 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 打印机驱动程序 (XPSDrv) 可以将基于 [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 的输出转换为 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 格式。 对于高级方案，自定义内容转换为支持使用[Microsoft XPS 文档转换器 (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)。 同样，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]应用程序也可以输出到[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]打印路径，方法是调用之一<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>或<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>方法的<xref:System.Windows.Xps.XpsDocumentWriter>类，并将非 XpsDrv 打印机指定为目标打印队列。  

对于不需要 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 功能或支持的应用程序，当前的 [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 打印路径保持不变。  
  
-   有关其他参考资料[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]打印路径和各种[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]转换选项，请参见[Microsoft XPS 文档转换器 (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)并[XPSDrv 的打印机驱动程序](/windows-hardware/drivers/print/xpsdrv-printer-drivers)。  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>XPSDrv 驱动程序模型  
 在打印到支持 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 的打印机或驱动程序时，[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 打印路径将 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 用作本机打印后台处理格式，从而提高打印后台处理程序的效率。 简化后的后台打印处理消除了在后台打印文档之前生成中间后台打印文件（如 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] 数据文件）的必要。 通过减小后台打印文件的大小，[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 打印路径可以减少网络流量并提高打印性能。  
  
 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] 是一种封闭格式，它将应用程序输出表示为对呈现服务的 [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 进行的一系列调用。 与 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] 不同的是，[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 后台打印格式呈现实际的文档，而无需在输出到基于 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 的打印机驱动程序 (XPSDrv) 时进行进一步的转译。 这些驱动程序可以用这种格式直接对数据进行操作。 此功能消除了在使用 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] 文件和基于 [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 的打印驱动程序时所需的数据和颜色空间转换。  
  
 当使用面向 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 打印机驱动程序 (XPSDrv) 的[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 文档时，与其 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] 等效项相比，后台打印文件的大小通常更小；不过，也存在例外情况：  
  
-   相当复杂、分为多层或者编写效率低下的向量图形可能比同一图形的位图图形更大。  
  
-   出于屏幕显示的目的，XPS 文件中嵌入了设备字体以及基于计算机的字体，而 GDI 打印后台文件未嵌入设备字体。 这两种字体都划分了子集（请参见下面的内容），而且打印机驱动程序可以在将文件传输给打印机之前删除这些设备字体。  
  
 可通过几种机制来减小后台打印文件的大小：  
  
-   **字体子集划分**。 只有在实际的文档中使用的字符才存储在 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 文件中。  
  
-   **高级图形支持**。 对透明和渐变基元的本机支持可避免 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 文档中的内容光栅化。  
  
-   **公共资源的识别**。 将多次使用的资源（如表示公司徽标的图像）视为共享资源，并且只加载一次。  
  
-   **ZIP 压缩**。 所有 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 文档均使用 ZIP 压缩。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [帮助主题](printing-how-to-topics.md)
- [WPF 中的文档](documents-in-wpf.md)
- [XPS 文档](/windows/desktop/printdocs/documents)
- [文档序列化和存储](document-serialization-and-storage.md)
- [Microsoft XPS 文档转换器 (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
