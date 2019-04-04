---
title: 使用非文本文件数据训练机器学习模型 - ML.NET
description: 了解如何使用 ML.NET 加载非文件训练数据，用于预测管道中的机器学习模型培训。
ms.date: 03/18/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 32de37e45b9e19669ea06d74c7f252ec885fe004
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "58186086"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a>使用非文本文件数据训练机器学习模型 - ML.NET

> [!NOTE]
> 本主题引用 ML.NET（目前处于预览状态），且材料可能会更改。 有关详细信息，请访问 [ML.NET 简介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)。

此操作说明和相关示例目前使用的是“ML.NET 版本 0.11”。 有关详细信息，请参阅 [dotnet/machinelearning GitHub 存储库](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)上的发行说明。

ML.NET 的常见演示用例是使用 `TextLoader` 读取文件中的培训数据。
但是，在实际训练情景中，数据可能位于其他位置，例如：

* SQL 表中
* JSON/XML
* 从日志文件中提取
* 动态生成

使用[架构理解](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md)将现有 C# `IEnumerable`作为 `DataView` 引入 ML.NET。

在此示例中，你将生成客户改动预测模型，并从生产系统中提取以下功能：

* 客户 ID（被模型忽略）
* 客户是否有改动（目标“标签”）
* “人口统计类别”（一个字符串，如“年轻成人”等。）
* 最近 5 天访问次数。

```csharp
private class CustomerChurnInfo
{
    public string CustomerID { get; set; }
    public bool HasChurned { get; set; }
    public string DemographicCategory { get; set; }
    // Visits during last 5 days, latest to newest.
    [VectorType(5)]
    public float[] LastVisits { get; set; }
}
```

将数据加载到 `DataView`，使用以下代码训练模型：

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging,
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// Let's assume that 'GetChurnData()' fetches and returns the training data from somewhere.
IEnumerable<CustomerChurnInfo> churnData = GetChurnInfo();

// Turn the data into the ML.NET data view.
// We can use CreateDataView or CreateStreamingDataView, depending on whether 'churnData' is an IList,
// or merely an IEnumerable.
var trainData = mlContext.Data.LoadFromEnumerable(churnData);

// Build the learning pipeline.
// In our case, we will one-hot encode the demographic category, and concatenate that with the number of visits.
// We apply our FastTree binary classifier to predict the 'HasChurned' label.

var pipeline = mlContext.Transforms.Categorical.OneHotEncoding("DemographicCategory")
    .Append(mlContext.Transforms.Concatenate("Features", "DemographicCategory", "LastVisits"))
    .Append(mlContext.BinaryClassification.Trainers.FastTree("HasChurned", "Features", numTrees: 20));

var model = pipeline.Fit(trainData);
```
