---
title: 如何：使用 Windows 窗体 BindingSource 绑定到 Web 服务
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Web services [Windows Forms], binding controls
- BindingSource component [Windows Forms], binding to a Web service
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to Web service
- BindingSource component [Windows Forms], examples
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
ms.openlocfilehash: cf5352ff60aabe45473c3c9103e8369597db2e8d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106751"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a>如何：使用 Windows 窗体 BindingSource 绑定到 Web 服务
如果想要将 Windows 窗体控件绑定到因调用 XML Web 服务获取的结果，可使用 <xref:System.Windows.Forms.BindingSource> 组件。 此过程类似于将 <xref:System.Windows.Forms.BindingSource> 组件绑定到类型。 必须创建客户端代理，其中包含 Web 服务公开的方法和类型。 从 Web 服务 (.asmx) 本身或其 Web 服务描述语言 (WSDL) 文件生成客户端代理。 此外，客户端代理必须公开 Web 服务用作公共属性的复杂类型字段。 然后将 <xref:System.Windows.Forms.BindingSource> 绑定到 Web 服务代理中公开的某个类型。  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a>若要创建并绑定到客户端代理  
  
1.  在所选目录中创建 Windows 窗体，同时创建适当的命名空间。  
  
2.  将 <xref:System.Windows.Forms.BindingSource> 组件添加到窗体。  
  
3.  打开 [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] 命令提示符，并导航到与你的窗体位置相同的目录。  
  
4.  使用 WSDL 工具输入 Web 服务的 .asmx 文件或 WSDL 文件的 `wsdl` 和 URL，后接应用程序的命名空间，并可选择性地接正在使用的语言。  
  
     下面的代码示例使用 Web 服务位于 `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`。 例如，对于 C# 类型，位于 `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`，对于 Visual Basic 类型，则位于 `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`。 将路径作为参数传递到 WSDL 工具将以指定语言在与应用程序相同的目录和命名空间中生成客户端代理。 如果使用的 Visual Studio，将文件添加到你的项目。  
  
5.  选择客户端代理中要将绑定到的类型。  
  
     这通常是由 Web 服务提供的方法返回的类型。 出于绑定目的，所选类型的字段必须公开为公共属性。  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  将 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 属性设置为包含在 Web 服务客户端代理中的所需类型。  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a>若要将控件绑定到 BindingSource（已绑定到 Web 服务）  
  
-   将控件绑定到 <xref:System.Windows.Forms.BindingSource>，将 Web 服务类型中的所需的公共属性作为参数传递。  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a>示例  
 以下代码示例演示了如何将 <xref:System.Windows.Forms.BindingSource> 组件绑定到 Web 服务，然后如何将文本框绑定到 <xref:System.Windows.Forms.BindingSource> 组件。 单击按钮后，将调用 Web 服务方法且结果将显示在 `textbox1` 中。  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 这是完整的示例，其中包括 `Main` 方法和客户端代理代码的缩写版本。  
  
 此示例需要：  
  
-   对 System, System.Drawing、System.Web.Services、System.Windows.Forms 和 System.Xml 程序集的引用。  
  
 Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。  
  
## <a name="see-also"></a>请参阅

- [BindingSource 组件](bindingsource-component.md)
- [如何：将 Windows 窗体控件绑定到类型](how-to-bind-a-windows-forms-control-to-a-type.md)
