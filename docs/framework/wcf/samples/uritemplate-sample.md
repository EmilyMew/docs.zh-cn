---
title: UriTemplate 示例
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: 0d0fa339cb4c8feab3c8341b4508826ca75d4259
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083772"
---
# <a name="uritemplate-sample"></a>UriTemplate 示例
<xref:System.UriTemplate> 类提供了用于处理共享公共结构的 URI 组的方法。 此示例演示与 `UriTemplate` 相关的以下关键概念：  
  
-   创建模板的语法。  
  
-   使用 `UriTemplate` 和 <xref:System.UriTemplate.BindByName%2A> 实例化 <xref:System.UriTemplate.BindByPosition%2A> 中的 URI。  
  
-   <xref:System.UriTemplateTable.Match%2A>它是相反的运算`BindByName`和`BindByPosition`。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1.  若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的说明进行操作。  
  
2.  若要在单或跨计算机配置中运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a>请参阅

- [UriTemplate 表](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [UriTemplate 表调度程序](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
