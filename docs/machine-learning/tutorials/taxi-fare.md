---
title: 在 ML.NET 中使用回归学习器预测费用
description: 在 ML.NET 中使用回归学习器预测费用。
author: aditidugar
ms.author: johalex
ms.date: 03/20/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 0a027b3b4930f7dda48d884faf0484cf33856c8d
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2019
ms.locfileid: "58307975"
---
# <a name="tutorial-predict-prices-using-a-regression-learner-with-mlnet"></a>教程：在 ML.NET 中使用回归学习器预测费用

本教程演示如何使用 ML.NET 构建[回归模型](../resources/glossary.md#regression)来预测费用，特别是纽约市出租车费。

> [!NOTE]
> 本主题引用 ML.NET（目前处于预览状态），且材料可能会更改。 有关详细信息，请参阅 [ML.NET 简介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)。

此教程和相关示例目前使用的是 ML.NET 版本 0.11。 有关详细信息，请参阅 [dotnet/machinelearning GitHub 存储库](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)上的发行说明。

在本教程中，你将了解：
> [!div class="checklist"]
> * 了解问题
> * 选择适当的机器学习任务
> * 准备和了解数据
> * 创建学习管道
> * 加载和转换数据
> * 选择学习算法
> * 定型模型
> * 评估模型
> * 使用预测模型

## <a name="prerequisites"></a>系统必备

* 安装了“.NET Core 跨平台开发”工作负载的 [Visual Studio 2017 15.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

## <a name="understand-the-problem"></a>了解问题

此问题是有关“预测纽约市的出租车行程费用”。 从表面看，似乎只取决于行程距离。 但是，由于其他因素（比如额外的乘客或使用信用卡而非现金付款），纽约的出租车供应商收费不同。

## <a name="select-the-appropriate-machine-learning-task"></a>选择适当的机器学习任务

你想要预测价格值，该值是基于数据集中的其他因素的实际值。 要执行此操作，选择[回归](../resources/glossary.md#regression)机器学习任务。

## <a name="create-a-console-application"></a>创建控制台应用程序

1. 打开 Visual Studio 2017。 从菜单栏中选择“文件” > “新建” > “项目”。 在“新项目”对话框中，依次选择“Visual C#”和“.NET Core”节点。 然后，选择“控制台应用程序(.NET Core)”项目模板。 在“名称”文本框中，键入“TaxiFarePrediction”，然后选择“确定”按钮。

1. 在项目中创建一个名为“数据”的目录来保存数据集和模型文件：

    在“解决方案资源管理器”中，右键单击项目，然后选择“添加” > “新文件夹”。 键入“Data”，然后按 Enter。

1. 安装“Microsoft.ML”NuGet 包：

    在“解决方案资源管理器”中，右键单击项目，然后选择“管理 NuGet 包”。 将“nuget.org”选择为“包源”，选择“浏览”选项卡并搜索“Microsoft.ML”，在列表中选择该包，然后选择“安装”按钮。 选择“预览更改”对话框上的“确定”按钮，如果你同意所列包的许可条款，则选择“接受许可”对话框上的“我接受”按钮。

## <a name="prepare-and-understand-the-data"></a>准备和了解数据

1. 下载 [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) 和 [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) 数据集，并将它们保存到先前创建的“数据”文件夹。 我们使用这些数据集定型机器学习模型，然后评估模型的准确性。 这些数据集最初来自 [NYC TLC 出租车行程数据集](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)。

1. 在“解决方案资源管理器”中，右键单击每个 \*.csv 文件，然后选择“属性”。 在“高级”下，将“复制到输出目录”的值更改为“如果较新则复制”。

1. 打开“taxi-fare-train.csv”数据集并查看第一行中的列标题。 查看每个列。 了解数据并确定哪些列是“特征”以及哪些是“标签”。

“标签”是希望预测的列的标识符。 标识的“特征”用于预测标签。

提供的数据集包含以下列：

* **vendor_id：** 出租车供应商的 ID 是一项特征。
* **rate_code：** 出租车行程的费率类型是一项特征。
* **passenger_count：** 行程中的乘客人数是一项特征。
* **trip_time_in_secs：** 这次行程所花的时间。 希望在行程完成前预测行程费用。 当时并不知道行程有多长。 因此，行程时间不是一项特征，需要从模型删除此列。
* **trip_distance：** 行程距离是一项特征。
* **payment_type：** 付款方式（现金或信用卡）是一项特征。
* **fare_amount：** 支付的总出租车费用是一个标签。

## <a name="create-data-classes"></a>创建数据类

创建输入数据和预测类：

1. 在“解决方案资源管理器”中，右键单击项目，然后选择“添加” > “新项”。
1. 在“添加新项”对话框中，选择“类”并将“名称”字段更改为“TaxiTrip.cs”。 然后，选择“添加”按钮。
1. 将以下 `using` 指令添加到新文件：

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

删除现有类定义并向“TaxiTrip.cs”文件添加以下代码，其中有两个类 `TaxiTrip` 和 `TaxiTripFarePrediction`：

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` 是输入数据类且具有针对每个数据集列的定义。 使用 <xref:Microsoft.ML.Data.LoadColumnAttribute> 属性在数据集中指定源列的索引。

`TaxiTripFarePrediction` 类表示预测的结果。 它应用了单个浮动 `FareAmount` 字段，附带 `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> 属性。 对于回归任务，“分数”列包含预测的标签值。

> [!NOTE]
> 使用 `float` 类型来表示输入和预测数据类中的浮点值。

## <a name="define-data-and-model-paths"></a>定义数据和模型路径

将以下附加的 `using` 语句添加到“Program.cs”文件顶部：

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

需要创建三个字段，用于保留有数据集的文件的路径，以及用于保存模型的文件的路径：

* `_trainDataPath` 包含具有用于定型模型的数据集的文件的路径。
* `_testDataPath` 包含具有用于评估模型的数据集的文件的路径。
* `_modelPath` 包含用于存储定型模型的文件的路径。

将以下代码添加到 `Main` 方法正上方，以指定这些路径和 `_textLoader` 变量：

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

使用 ML.NET 生成模型时，首先要创建 ML 上下文。 这在概念上相当于在实体框架中使用 `DbContext`。 该环境为机器学习作业提供一个上下文，可以用于异常情况跟踪和日志记录。

### <a name="initialize-variables-in-main"></a>在 Main 中初始化变量

创建一个名为 `mlContext` 的变量并将其初始化为 `MLContext` 的新实例。  用下面 `Main` 方法中的代码替换 `Console.WriteLine("Hello World!")` 行：

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

在 `Main` 方法中添加以下代码作为调用 `Train` 方法的下一行代码：

[!code-csharp[Train](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

`Train` 方法执行以下任务：

* 加载数据。
* 提取并转换数据。
* 定型模型。
* 将模型保存为 .zip 文件。
* 返回模型。

`Train` 方法定型模型。 使用以下代码在 `Main` 下创建该方法：

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

我们会将两个参数传递到 `Train` 方法；`MLContext` 用于上下文 (`mlContext`)，字符串用于数据集路径 (`dataPath`)。 我们将重用此方法来加载数据集。

## <a name="load-and-transform-data"></a>加载和转换数据

使用 [LoadFromTextFile 方法](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29)的 `MLContext.Data.LoadFromTextFile` 包装器加载数据。 它将返回 <xref:Microsoft.Data.DataView.IDataView>。 

作为 `Transforms` 的输入和输出，`DataView` 是基本的数据管道类型，与 `LINQ` 中的 `IEnumerable` 类似。

在 ML.NET 中，数据类似于 SQL 视图。 它是异源数据，会延迟计算并进行架构化。 该对象是管道的第一部分，并加载数据。 本教程会加载具有出租车行程定价信息的数据集。 这用于创建模型并对其进行定型。

将以下代码添加为 `Train` 方法的首行：

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

在后续步骤中，我们按 `TaxiTrip` 类中定义的名称引用列。

定型和评估模型时，默认情况下，将“标签”列中的值视为要预测的正确值。 希望预测出租车费时，将 `FareAmount` 列复制到“标签”列。 若要执行此操作，请使用 `CopyColumnsEstimator` 转换类，并添加以下代码：

[!code-csharp[CopyColumnsEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

定型模型的算法需要数字特性，所以必须将分类数据（`VendorId`、`RateCode` 和 `PaymentType`）值转换为数字（`VendorIdEncoded`、`RateCodeEncoded` 和 `PaymentTypeEncoded`）。 为此，请使用 Microsoft.ML.Transforms.OneHotEncodingTransformer> 转换类（它将不同的数字键值分配到每列的不同值），并添加以下代码：

[!code-csharp[OneHotEncodingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

数据准备最后一步使用 `mlContext.Transforms.Concatenate` 转换类将所有功能列合并到“功能”列。 默认情况下，学习算法仅处理“特征”列的特征。 添加以下代码：

[!code-csharp[ColumnConcatenatingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>选择学习算法

在将数据添加到管道，并将其转换为正确的输入格式之后，可以选择学习算法（学习器）。 学习器定型模型。 为此问题选择了“回归任务”，所以使用 `FastTreeRegressionTrainer` 学习器（ML.NET 提供的一种回归学习器）。

`FastTreeRegressionTrainer` 定型算法使用梯度提升。 梯度提升是针对回归问题的一项机器学习技术。 它将以步进方式生成每个回归树。 它使用预定义的损失函数测量每个步骤中的错误，并在下一步中对其进行校正。 其结果是一种预测模型，实际上是一组较弱的预测模型。 有关梯度提升的详细信息，请参阅[提升的决策树回归](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression)。

将下面的代码添加到 `Train` 方法以将 `FastTreeRegressionTrainer` 添加到在上一步中添加的数据处理代码：

[!code-csharp[FastTreeRegressionTrainer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>定型模型

最后一步是定型模型。 根据已加载和转换的数据集定型模型 <xref:Microsoft.ML.Data.TransformerChain>。 一旦定义了估算器，我们将使用 <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> 定型模型，同时提供已经加载的定型数据。 这将返回要用于预测的模型。 `pipeline.Fit()` 定型管道，并返回基于传入的 `DataView` 的 `Transformer`。 在发生这种情况之前不会执行此试验。

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

### <a name="save-the-model"></a>保存模型

此时，你具有可以集成到任何现有或新 .NET 应用程序的 <xref:Microsoft.ML.Data.TransformerChain> 类型模型。 要将模型保存到 .zip 文件中，请在 `Train` 方法的末尾添加以下代码：

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Save the model as a .zip file and return the model")]

## <a name="save-the-model-as-a-zip-file"></a>将模型保存为 .zip 文件

使用下面的代码紧随 `Train` 方法后创建 `SaveModelAsFile` 方法：

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` 方法执行以下任务：

* 将模型保存为 .zip 文件。

我们需要创建一个方法来保存模型，以便它可以在其他应用程序中重用和使用。 `ITransformer` 有一个在 `_modelPath` 全局字段中采用的 <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> 方法和一个 <xref:System.IO.Stream> 方法。 由于我们想将其保存为 zip 文件，我们将在调用 `SaveTo` 方法之前立即创建 `FileStream`。 将以下代码作为下一行添加到 `SaveModelAsFile` 方法中：

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Add the SaveTo Method")]

我们还可以使用以下代码通过使用 `_modelPath` 编写控制台消息来显示文件的写入位置：

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a>评估模型

评估是检查模型预测标签值情况的过程。 模型对定型模型中未使用的数据做出好的预测非常重要。 执行此操作的一种方法是将数据拆分到定型和测试数据集，如此教程中所示。 你已在定型数据上定型模型，现在可以看到它在测试数据上的表现。

`Evaluate` 方法评估模型。 若要创建该方法，请将以下代码添加到 `Train` 方法下：

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```
`Evaluate` 方法执行以下任务：

* 加载测试数据集。
* 创建回归计算器。
* 评估模型并创建指标。
* 显示指标。

使用下面的代码，在 `Train` 方法调用的正下方，从 `Main` 方法中添加对新方法的调用：

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

使用 `MLContext.Data.LoadFromTextFile` 包装器加载测试数据集。 可以将此数据集作为质量检查来评估模型。 将以下代码添加到 `Evaluate` 方法中：

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

接下来，使用机器学习 `model` 参数（转换器）来输入特性，并返回预测。 将以下代码作为下一行添加到 `Evaluate` 方法中：

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

`RegressionContext.Evaluate` 方法使用指定数据集计算 `PredictionModel` 的质量指标。 它返回一个 <xref:Microsoft.ML.Data.RegressionMetrics> 对象，其中包含由回归计算器计算出的总体指标。 若要显示这些指标来确定模型质量，需要先获取指标。 将以下代码作为下一行添加到 `Evaluate` 方法中：

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

添加以下代码以评估模型并生成评估模型：

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) 是回归模型的另一种评估指标。 RSquared 在 0 和 1 之间取值。 值越接近 1，模型就越好。 将以下代码添加到 `Evaluate` 方法以显示 RSquared 值：

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) 是回归模型的一种评估指标。 指标越低，模型就越好。 将以下代码添加到 `Evaluate` 方法以显示 RMS 值：

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>使用预测模型


## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a>使用模型和单个注释预测测试数据结果

使用下面的代码紧随 `Evaluate` 方法后创建 `TestSinglePrediction` 方法：

```csharp
private static void TestSinglePrediction(MLContext mlContext)
{

}
```

`TestSinglePrediction` 方法执行以下任务：

* 创建测试数据的单个注释。
* 根据测试数据预测费用。
* 结合测试数据和预测进行报告。
* 显示预测结果。

使用下面的代码，在 `Evaluate` 方法调用的正下方，从 `Main` 方法中添加对新方法的调用：

[!code-csharp[CallTestSinglePrediction](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

由于我们想从保存的 zip 文件加载模型，我们将在创建 `FileStream` 之后立即调用 `Load` 方法。 将以下代码作为下一行添加到 `TestSinglePrediction` 方法中：

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#21 "Load the model")]

虽然 `model` 是对多行数据进行操作的 `transformer`，但是一个非常常见的生产场景是，需要对单个示例进行预测。 <xref:Microsoft.ML.PredictionEngine%602> 是从 `CreatePredictionEngine` 方法返回的包装器。 让我们添加以下代码来创建 `PredictionEngine`，作为 `TestSinglePrediction` 方法中的下一行：

[!code-csharp[MakePredictionEngine](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]
  
本教程使用此类中的一个测试行程。 稍后可以添加其他方案，以尝试使用此模型。 通过创建一个 `TaxiTrip` 实例，在 `TestSinglePrediction` 方法中添加一个行程来测试定型模型的成本预测：

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

 我们可以使用它根据出租车行程数据的单个实例来预测费用。 要获得预测，请对数据使用 <xref:Microsoft.ML.PredictionEngine%602.Predict%2A>。 请注意，输入数据是一个字符串，且模型包含特征化。 管道在定型和预测期间同步。 不必专门为预测编写预处理/特征化代码，并且相同 API 负责批处理和一次性预测。

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

若要显示指定行程的预测费用，请将下面的代码添加到 `TestSinglePrediction` 方法中：

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

运行此程序，查看测试用例的预测出租车费。

祝贺你！ 你已成功生成用于预测出租车费的机器学习模型、评估其准确性，并用其进行预测。 可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub 存储库中找到本教程的源代码。

## <a name="next-steps"></a>后续步骤

在本教程中，你将了解：
> [!div class="checklist"]
> * 了解问题
> * 选择适当的机器学习任务
> * 准备和了解数据
> * 创建学习管道
> * 加载和转换数据
> * 选择学习算法
> * 定型模型
> * 评估模型
> * 使用预测模型

进入下一教程了解详细信息。
> [!div class="nextstepaction"]
> [Iris 聚类分析](iris-clustering.md)
