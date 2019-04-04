---
title: 使用 ASP.NET Core Web API 提供机器学习模型
description: 使用 ASP.NET Core Web API 通过 Internet 提供 ML.NET 情绪分析机器学习模型
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 0cc13ec22b3a8805ec4aa17bf10560b2564ccd63
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2019
ms.locfileid: "58307910"
---
# <a name="how-to-serve-machine-learning-model-through-aspnet-core-web-api"></a>操作说明：通过 ASP.NET Core Web API 提供机器学习模型

本操作说明介绍了如何使用 ASP.NET Core Web API 向 Web 提供预生成的 ML.NET 机器学习模型。 这样一来，用户可以通过标准 HTTP 方法将 API 用于预测目的。

> [!NOTE]
> 本主题引用 ML.NET（目前处于预览状态），且材料可能会更改。 有关详细信息，请访问 [ML.NET 简介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)。

此操作说明和相关示例目前使用的是 ML.NET 版本 0.10。 有关详细信息，请参阅 [dotnet/machinelearning GitHub 存储库](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)上的发行说明。

## <a name="prerequisites"></a>系统必备

- 安装了“.NET Core 跨平台开发”工作负载的 [Visual Studio 2017 15.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。
- PowerShell。
- 预先定型的模型。
    - 根据 [ML.NET 情绪分析教程](../tutorials/sentiment-analysis.md)生成你自己的模型。
    - 下载此[预先定型的情绪分析机器学习模型](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>创建 ASP.NET Core Web API 项目

1. 打开 Visual Studio 2017。 从菜单栏中依次选择“文件”>“新建”>“项目”。 在“新项目”对话框中，依次选择“Visual C#”节点和“Web”节点。 然后，选择“ASP.NET Core Web 应用程序”项目模板。 在“名称”文本框中，键入“SentimentAnalysisWebAPI”，再选择“确定”按钮。
1. 在显示不同类型 ASP.NET Core 项目的窗口中，依次选择“API”和“确定”按钮。
1. 在项目中创建“MLModels”目录，用于保存预生成的机器学习模型文件：

    在“解决方案资源管理器”中，右键单击项目，并依次选择“添加”>“新文件夹”。 键入“MLModels”，再按 Enter。

1. 安装“Microsoft.ML NuGet 包”：

    在“解决方案资源管理器”中，右键单击项目，然后选择“管理 NuGet 包”。 选择“nuget.org”作为“包源”，选择“浏览”选项卡并搜索“Microsoft.ML”，再依次选择列表中的相应包和“安装”按钮。 选择“预览更改”对话框中的“确定”按钮；如果同意所列包的许可条款，请选择“接受许可”对话框中的“我接受”按钮。

### <a name="add-model-to-aspnet-core-web-api-project"></a>将模型添加到 ASP.NET Core Web API 项目

1. 将预生成的模型复制到 MLModels 目录
1. 在“解决方案资源管理器”中，右键单击模型 zip 文件，并选择“属性”。 在“高级”下，将“复制到输出目录”的值更改为“如果较新则复制”。

## <a name="build-data-models"></a>生成数据模型

需要为输入数据和预测创建一些类。 向项目添加一个新类：

1. 在项目中创建“DataModels”目录，用于保存数据模型：

    在“解决方案资源管理器”中，右键单击项目，并依次选择“添加”>“新文件夹”。 键入“DataModels”，再按 Enter。

2. 在“解决方案资源管理器”中，右键单击“DataModels”目录，再依次选择“添加”>“新项”。
3. 在“添加新项”对话框中，选择“类”并将“名称”字段更改为“SentimentData.cs”。 然后，选择“添加”按钮。 “SentimentData.cs”文件随即在代码编辑器中打开。 将以下 using 语句添加到 SentimentData.cs 顶部：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

删除现有类定义，并将以下代码添加到 SentimentData.cs 文件：

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }   
}
```

4. 在“解决方案资源管理器”中，右键单击“DataModels”目录，再依次选择“添加”>“新项”。
5. 在“添加新项”对话框中，选择“类”，并将“名称”字段更改为“SentimentPrediction.cs”。 然后，选择“添加”按钮。 此时，SentimentPrediction.cs 文件在代码编辑器中打开。 将以下 using 语句添加到 SentimentPrediction.cs 顶部：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

删除现有类定义，并将以下代码添加到 SentimentPrediction.cs 文件：

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

## <a name="register-predictionengine-for-use-in-application"></a>注册 PredictionEngine 以便在应用程序中使用

若要进行单一预测，可以使用 `PredictionEngine`。 必须在每次需要使用 `PredictionEngine` 时创建它，才能在应用程序中使用。 在这种情况下，建议的最佳做法是 ASP.NET Core 依赖关系注入。

若要详细了解[依赖关系注入](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1)，请单击下面的链接。

1. 打开 Startup.cs 类，并将以下 using 语句添加到文件顶部：

```csharp
using System.IO;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using SentimentAnalysisWebAPI.DataModels;
```

2. 将以下代码行添加到 ConfigureServices 方法：

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);

    services.AddScoped<MLContext>();
    services.AddScoped<PredictionEngine<SentimentData, SentimentPrediction>>((ctx) =>
    {
        MLContext mlContext = ctx.GetRequiredService<MLContext>();
        string modelFilePathName = "MLModels/sentiment_model.zip";

        //Load model from file
        ITransformer model;
        using (var stream = File.OpenRead(modelFilePathName))
        {
            model = mlContext.Model.Load(stream);
        }

        // Return prediction engine
        return model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);
    });
}
```

> [!WARNING]
> `PredictionEngine` 不是线程安全。 一种可限制创建对象成本的方法就是，将对象的服务生命周期限制在一定范围内。 有作用域的对象在一个请求内是相同的，但在请求之间是不同的。 请访问以下链接，了解有关[服务生命周期](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1#service-lifetimes)的更多信息。

概括地讲，此代码在应用程序请求时自动初始化对象和服务，你无需手动执行初始化。

## <a name="create-predict-controller"></a>创建预测控制器

必须创建控制器，才能处理传入 HTTP 请求。

1. 在“解决方案资源管理器”中，右键单击“Controllers”目录，再依次选择“添加”>“控制器”。
1. 在“添加新项”对话框中，依次选择“空 API 控制器”和“添加”。
1. 在提示窗口中，将“控制器名称”字段更改为“PredictController.cs”。 然后，选择“添加”按钮。 此时，PredictController.cs 文件在代码编辑器中打开。 将以下 using 语句添加到 PredictController.cs 顶部：

```csharp
using System;
using Microsoft.AspNetCore.Mvc;
using SentimentAnalysisWebAPI.DataModels;
using Microsoft.ML;
```

删除现有类定义，并将以下代码添加到 PredictController.cs 文件：

```csharp
public class PredictController : ControllerBase
{
    
    private readonly PredictionEngine<SentimentData,SentimentPrediction> _predictionEngine;

    public PredictController(PredictionEngine<SentimentData, SentimentPrediction> predictionEngine)
    {
        _predictionEngine = predictionEngine; //Define prediction engine
    }

    [HttpPost]
    public ActionResult<string> Post([FromBody]SentimentData input)
    {
        if(!ModelState.IsValid)
        {
            return BadRequest();
        }

        // Make a prediction
        SentimentPrediction prediction = _predictionEngine.Predict(input);

        //If prediction is true then it is toxic. If it is false, the it is not.
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        return Ok(isToxic);
    }
    
}
```

这是在将 `PredictionEngine` 传递给通过依赖关系注入获取的控制器构造函数，从而分配该引擎。 然后，在此控制器的 POST 方法中，使用 `PredictionEngine` 进行预测；如果成功，它会将结果返回给用户。

## <a name="test-web-api-locally"></a>本地测试 Web API

完成所有设置后，是时候测试应用程序了。

1. 运行该应用程序。
1. 打开 Powershell，并输入以下代码（其中，PORT 是应用程序正在侦听的端口）。

```powershell
Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

如果成功，输出文本应如下所示：

```powershell
Toxic
```

祝贺你！ 你已成功使用 ASP.NET Core API 通过 Internet 提供模型进行预测。

## <a name="next-steps"></a>后续步骤

- [部署到 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)