---
title: 编程模型项树
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: 428012cf483595a280ef70b488ed1f344474948a
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653842"
---
# <a name="programming-model-item-tree"></a>编程模型项树
此示例演示如何导航<xref:System.Activities.Presentation.Model.ModelItem>树使用的 Windows Presentation Foundation (WPF) 树视图中的声明性数据绑定。

## <a name="sample-details"></a>示例详细信息
 <xref:System.Activities.Presentation.Model.ModelItem> 树是 [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] 基础结构用来公开有关要编辑的基础实例的数据的抽象。 下图描述了 [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] 中的基础结构的各层。

 ![显示工作流设计器体系结构的关系图。](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <xref:System.Activities.Presentation.Model.ModelItem> 包含一个指向基础值的指针和一个 <xref:System.Activities.Presentation.Model.ModelProperty> 对象的集合。 反过来，<xref:System.Activities.Presentation.Model.ModelProperty> 对象又包含诸如属性的名称和类型这样的数据，而指向值的指针又是另一个 <xref:System.Activities.Presentation.Model.ModelItem>。 值转换器用于操作从 <xref:System.Activities.Presentation.Model.ModelItem> 返回的某些 <xref:System.Activities.Presentation.Model.ModelProperty>，使它们在树视图中正确显示。 然后，此示例演示如何使用命令性语法对 <xref:System.Activities.Presentation.Model.ModelItem> 树进行命令式编程，如下面的示例所示。

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>使用此示例

1.  在 Visual Studio 2010 中打开 ProgrammingModelItemTree.sln 解决方案。

2.  通过选择生成解决方案**生成解决方案**从**生成**菜单。

3.  按 F5 运行该应用程序。 这将显示 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 格式。

4.  单击**加载 WF**按钮以加载<xref:System.Activities.Presentation.Model.ModelItem>并将其绑定到树视图。

5.  单击**更改模型项树**按钮执行前面的代码，将项添加到树并设置一个属性。

> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Data.IValueConverter>
