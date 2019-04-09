---
title: 如何：注册和配置服务名字对象
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: 364329954591199c4b0d3123c662c4e124c242fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141916"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>如何：注册和配置服务名字对象
必须在使用之前在 COM 应用程序中的 Windows Communication Foundation (WCF) 服务名字对象具有类型化协定中, 所需的特性化的类型向 COM 注册，并使用所需的绑定配置的 COM 应用程序和标记配置。  
  
### <a name="to-register-the-required-attributed-types-with-com"></a>向 COM 注册所需的属性化类型  
  
1.  使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具，用于从 WCF 服务中检索元数据协定。 这将生成 WCF 客户端程序集和客户端应用程序配置文件的源代码。  
  
2.  确保将程序集中的类型标记为 `ComVisible`。 为此，请将下面的属性添加到 Visual Studio 项目的 AssemblyInfo.cs 文件中。  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  编译具有强名称程序集作为托管的 WCF 客户端。 这要求使用加密密钥对进行签名。 有关详细信息，请参阅[为程序集使用强名称签名](https://go.microsoft.com/fwlink/?LinkId=94874).NET 开发人员指南中。  
  
4.  使用带有 `/tlb` 选项的程序集注册 (Regasm.exe) 工具向 COM 注册程序集中的类型。  
  
5.  使用全局程序集缓存 (Gacutil.exe) 工具将该程序集添加到全局程序集缓存中。  
  
    > [!NOTE]
    >  对程序集进行签名并将其添加到全局程序集缓存中是可选步骤，不过，这两个步骤可以简化在运行时从正确位置加载程序集的过程。  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>为 COM 应用程序和标记配置所需的绑定配置  
  
-   将绑定定义放置 (パ[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)生成的客户端应用程序配置文件中) 客户端应用程序的配置文件中。 例如，对于名为 CallCenterClient.exe 的 Visual Basic 6.0 可执行文件，配置应放置到该可执行文件所在目录中名为 CallCenterConfig.exe.config 的文件中。 此时，客户端应用程序就可以使用标记了。 请注意，如果使用的标准绑定 WCF 提供的类型之一，可能不是必需的绑定配置。  
  
     注册下面的类型。  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     使用 `wsHttpBinding` 绑定来公开应用程序。 对于给定的类型和应用程序配置，将使用以下的示例标记字符串。  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     在将引用添加到包含 `IMathService` 类型的程序集后，你可以使用 Visual Basic 6.0 应用程序中的这些标记字符串中的任何一个，如下面的示例代码中所示。  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     在本示例中，绑定配置 `Binding1` 的定义存储在该客户端应用程序的适当命名的配置文件中，如 vb6appname.exe.config。  
  
    > [!NOTE]
    >  你可以在 C#、C++ 或其他任何 .NET 语言的应用程序中使用类似的代码。  
  
    > [!NOTE]
    >  :如果标记格式不正确或者服务不可用，在调用`GetObject`返回的"语法无效"错误。 如果您收到此错误，请确保所使用的标记正确无误且服务可用。  
  
     尽管此主题重点介绍通过 VB 6.0 代码使用服务标记，你还是可以通过其他语言使用服务标记。 当通过 C++ 代码使用标记时，应使用“no_namespace named_guids raw_interfaces_only”导入 Svcutil.exe 生成的程序集，如下面的代码中所示。  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     这会修改导入的接口定义，以便所有方法均会返回一个 `HResult`。 其他任何返回值都将转换为 out 参数。 方法的总体执行情况保持不变。 这将允许您确定在代理上调用方法时出现异常的原因。 仅可通过 C++ 代码来使用此功能。  
  
## <a name="see-also"></a>请参阅

- [ServiceModel 元数据实用工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
