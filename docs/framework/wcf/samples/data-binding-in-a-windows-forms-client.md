---
title: Windows 窗体客户端中的数据绑定
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: d41310108bfffedc38297f2c981e90007b59fb9a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832146"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Windows 窗体客户端中的数据绑定
此示例演示如何将绑定到 Windows 窗体应用程序中的 Windows Communication Foundation (WCF) 服务所返回的数据。  
  
> [!NOTE]
>  本文的最后介绍了此示例的设置过程和生成说明。  
  
 本示例演示一个服务，该服务可实现定义“请求-答复”通信模式的协定。 此示例由客户端 Windows 窗体应用程序 (.exe) 和由 Internet 信息服务 (IIS) 承载的 WCF 服务组成。  
  
 协定由 `IWeatherService` 接口定义，该接口公开一个名为 `GetWeatherData` 的操作。 此操作接受一个城市数组并返回一个 `WeatherData` 对象数组，这些对象表示城市的预报高温和预报低温。  
  
 在 Windows 窗体应用程序中的客户端上进行数据绑定。 在 Windows 窗体设计器中定义一个 `DataGridView`（它是数据的图形化表示形式）。 还会创建一个名为 `BindingSource` 的中间媒介。 将 `BindingSource` 的数据源设置为由服务返回的数据数组。 `BindingSource` 的用途是提供数据与数据视图之间的间接层。 与数据的所有交互（如导航、排序、筛选和更新）都是通过调用 `BindingSource` 组件来完成的。 若要完成对 `DataGridView` 的数据绑定，请将 `datasource` 的 `DataGridView` 设置为 `BindingSource` 对象。 所有从 WCF 服务返回的数据随后会以图形方式向用户。  每当用户单击按钮时，会在数据绑定的 `DataGridView` 中自动更新返回的数据。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1.  请确保您具有执行[的 Windows Communication Foundation 示例的一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的说明进行操作。  
  
3.  若要在单或跨计算机配置中运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
