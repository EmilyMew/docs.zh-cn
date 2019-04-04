---
title: 在情绪分析二元分类方案中使用 ML.NET
description: 了解如何在二元分类方案中使用 ML.NET，以了解如何使用情绪预测来采取相应措施。
ms.date: 03/07/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: a88ed38b76a230095f35304aa2b52af0a7c9c22d
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2019
ms.locfileid: "58307936"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>教程：在情绪分析二元分类方案中使用 ML.NET

本示例教程通过在 Visual Studio 2017 中使用 C# 的 .NET Core 控制台应用程序，演示如何使用 ML.NET 创建情绪分类器来预测正面或负面的情绪。 在机器学习领域，这种类型的预测称为“二元分类”。

> [!NOTE]
> 本主题引用 ML.NET（目前处于预览状态），且材料可能会更改。 有关详细信息，请访问 [ML.NET 简介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)。

此教程和相关示例目前使用的是 ML.NET 版本 0.11。 有关详细信息，请参阅 [dotnet/machinelearning GitHub 存储库](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)上的发行说明

在本教程中，你将了解：
> [!div class="checklist"]
> * 了解问题
> * 选择适当的机器学习算法
> * 准备数据
> * 转换数据
> * 定型模型
> * 评估模型
> * 使用训练的模型预测
> * 使用加载模型部署和预测

## <a name="sentiment-analysis-sample-overview"></a>情绪分析示例概述

该示例是使用 ML.NET 定型模型的控制台应用，以将情绪分类和预测为正面或负面。 Yelp 情绪数据集来自加利福尼亚大学欧文分校 (UCI)，它分为训练数据集和测试数据集。 示例还使用测试数据集评估模型用于质量分析。 

可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存储库中找到本教程的源代码。

## <a name="prerequisites"></a>系统必备

* 安装了“.NET Core 跨平台开发”工作负载的 [Visual Studio 2017 15.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

* [UCI Sentiment Labeled Sentences 数据集 zip 文件](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

## <a name="machine-learning-workflow"></a>机器学习工作流

本教程后面介绍了机器学习工作流，使该过程能够有序地进行。

工作流阶段如下所示：

1. **了解问题**
2. **准备数据**
   * **加载数据**
   * **提取功能（转换数据）**
3. **生成并定型** 
   * **定型模型**
   * **评估模型**
4. **部署模型**
   * **使用模型来预测**

### <a name="understand-the-problem"></a>了解问题

首先需要了解问题，因此可以将其分解为能够支持构建和定型模型的几个部分。 分解问题可以预测和评估结果。

本教程中的问题是了解传入网站评论情绪以采取相应的措施。

可以将问题分解为你想要对模型进行定型的数据的情绪文本和情绪值，以及可以评估和以操作状态使用的预期情绪值。

然后，需要确定情绪，这将帮助你进行机器学习任务选择。

## <a name="select-the-appropriate-machine-learning-algorithm"></a>选择适当的机器学习算法

通过此问题，你将了解以下情况：

训练数据：网站评论可以为正面 (1) 或负面 (0)（情绪）。

预测新网站评论的情绪，正面或负面，如以下示例所示：

* 我喜欢这里的服务员。 他们值得信赖。
* 这里的汤是最糟糕的。

分类机器学习算法最适合此方案。

### <a name="about-the-classification-algorithm"></a>关于分类算法

分类是一项机器学习算法，它使用数据来确定某个项或数据行的类别、类型或类。 例如，可以使用分类：

* 识别情绪为正面还是负面。
* 将电子邮件分类为垃圾邮件或正常邮件。
* 确定患者的实验室样本是否癌变。
* 根据客户对销售活动的反应倾向对客户进行分类。

分类算法通常为以下类型之一：

* 二元：A 或 B。
* 多类：可以通过使用单个模型来预测多个类别。

由于需要将网站评论分为正面或负面，因此使用二元分类算法。 

## <a name="create-a-console-application"></a>创建控制台应用程序

1. 打开 Visual Studio 2017。 从菜单栏中选择“文件” > “新建” > “项目”。 在“新项目”对话框中，依次选择“Visual C#”和“.NET Core”节点。 然后，选择“控制台应用程序(.NET Core)”项目模板。 在“名称”文本框中，键入“SentimentAnalysis”，然后选择“确定”按钮。

2. 在项目中创建一个名为“数据”的目录来保存数据集文件：

    在“解决方案资源管理器”中，右键单击项目，然后选择“添加” > “新文件夹”。 键入“Data”，然后按 Enter。

3. 安装“Microsoft.ML NuGet 包”：

    在“解决方案资源管理器”中，右键单击项目，然后选择“管理 NuGet 包”。 将“nuget.org”选择为“包源”，选择“浏览”选项卡并搜索“Microsoft.ML”，在列表中选择该包，然后选择“安装”按钮。 选择“预览更改”对话框上的“确定”按钮，如果你同意所列包的许可条款，则选择“接受许可”对话框上的“我接受”按钮。

### <a name="prepare-your-data"></a>准备数据

1. 下载 [UCI Sentiment Labeled Sentences 数据集 zip 文件（请参阅以下备注中的引文）](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)并解压缩文件。

2. 将 `yelp_labelled.txt` 文件复制到已创建的“数据”目录中。

> [!NOTE]
> 本教程使用的数据集摘自 KDD 2015 中由 Kotzias 等 提出的“From Group to Individual Labels using Deep Features”， 并托管在 UCI 机器学习存储库中（Dua, D. 和 Karra Taniskidou, E.(2017)）。 UCI 机器学习存储库 [http://archive.ics.uci.edu/ml]。 加利福尼亚州，加利福尼亚大学：欧文分校，信息与计算机科学学院。

3. 在“解决方案资源管理器”中，右键单击 `yelp_labeled.txt` 文件并选择“属性”。 在“高级”下，将“复制到输出目录”的值更改为“如果较新则复制”。

### <a name="create-classes-and-define-paths"></a>创建类和定义路径

将以下附加的 `using` 语句添加到“Program.cs”文件顶部：

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

需要创建两个全局字段来存储最近下载的数据集文件路径和已保存的模型文件路径：

* `_dataPath` 具有用于定型模型的数据集路径。
* `_modelPath` 具有在其中保存定型模型的路径。

将以下代码添加到 `Main` 方法上方的行中，以指定这些路径：

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

需要为输入数据和预测创建一些类。 向项目添加一个新类：

1. 在“解决方案资源管理器”中，右键单击项目，然后选择“添加” > “新项”。

1. 在“添加新项”对话框中，选择“类”并将“名称”字段更改为“SentimentData.cs”。 然后，选择“添加”按钮。

    “SentimentData.cs”文件随即在代码编辑器中打开。 将下面的 `using` 语句添加到 SentimentData.cs 的顶部：

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

删除现有类定义并向“SentimentData.cs”文件添加以下代码，其中有两个类 `SentimentData` 和 `SentimentPrediction`：

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

输入数据集类 `SentimentData` 具有带正面或负面情绪值的评论 (`SentimentText`) 和 `bool` (`Sentiment`) 的 `string`。 这两个字段均有随附的 <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> 属性。 此属性描述数据文件中每个字段的顺序。  此外，`Sentiment` 属性具有 <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A>，可将其指定为 `Label` 字段。 `SentimentPrediction` 是在定型模型后用于预测的类。 它有一个布尔值 (`Sentiment`) 和一个 `PredictedLabel` `ColumnName` 属性。 `Label` 用于创建和训练模型，并且与拆分测试数据集结合使用来评估模型。 `PredictedLabel` 在预测和评估过程中使用。 对于计算，将使用带定型数据的输入、预测值和模型。

使用 ML.NET 构建模型时，首先要创建一个 <xref:Microsoft.ML.MLContext>。 `MLContext` 在概念上相当于在实体框架中使用 `DbContext`。 该环境为 ML 作业提供一个上下文，可以用于异常情况跟踪和日志记录。

### <a name="initialize-variables-in-main"></a>在 Main 中初始化变量

创建一个名为 `mlContext` 的变量并将其初始化为 `MLContext` 的新实例。  用下面 `Main` 方法中的代码替换 `Console.WriteLine("Hello World!")` 行：

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

将以下代码作为下一行代码添加到 `Main` 方法中：

[!code-csharp[CallLoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

`LoadData` 方法执行以下任务：

* 加载数据。
* 将加载的数据集拆分为训练数据集和测试数据集。
* 返回拆分的训练数据集和测试数据集。

使用下面的代码紧随 `Main` 方法后创建 `LoadData` 方法：

```csharp
public static TrainCatalogBase.TrainTestData LoadData(MLContext mlContext)
{

}
```
## <a name="load-the-data"></a>加载数据

由于先前创建的 `SentimentData` 数据模型类型与数据集架构匹配，因此可使用 [LoadFromTextFile 方法](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29)的 `MLContext.Data.LoadFromTextFile` 包装器，将初始化、映射和数据集加载合并到一行代码中。 它将返回 <xref:Microsoft.Data.DataView.IDataView>。 

 作为 `Transforms` 的输入和输出，`DataView` 是基本的数据管道类型，与 `LINQ` 中的 `IEnumerable` 类似。

在 ML.NET 中，数据类似于 SQL 视图。 它是异源数据，会延迟计算并进行架构化。 该对象是管道的第一部分，并加载数据。 对于本教程，它会加载具有注释和相应正面或负面情绪的数据集。 这用于创建模型并对其进行定型。

 将以下代码添加为 `LoadData` 方法的首行：

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

### <a name="split-the-dataset-for-model-training-and-testing"></a>拆分数据集以进行模型训练和测试

接下来，需要使用训练数据集来训练型模型，也需要使用测试数据集来评估模型。 使用包装 <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> 的 `MLContext.BinaryClassification.TrainTestSplit` 将已加载的数据集拆分为训练数据集和测试数据集，并将它们返回到 <xref:Microsoft.ML.TrainCatalogBase.TrainTestData> 内。 可以使用 `testFraction` 参数指定测试集的部分数据。 默认为 10%，但在本例中使用 20% 的数据，通过更多数据进行评估。  

要将加载的数据拆分为所需的数据集，请添加以下代码作为 `LoadData` 方法中的下一行：

[!code-csharp[SplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

在 `LoadData` 方法末尾返回 `splitDataView`：

[!code-csharp[ReturnSplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>生成和定型模型

将以下调用添加到 `BuildAndTrainModel` 方法作为 `Main` 方法的下一行代码：

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` 方法执行以下任务：

* 提取并转换数据。
* 定型模型。
* 根据测试数据预测情绪。
* 返回模型。

使用下面的代码紧随 `Main` 方法后创建 `BuildAndTrainModel` 方法：

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

请注意，传递到 Train 方法的两个参数；`MLContext` 用于上下文 (`mlContext`)，`IDataView` 用于训练数据集 (`splitTrainSet`)。 

## <a name="extract-and-transform-the-data"></a>提取和转换数据

预处理和清除数据任务至关重要，需要首先执行才能将数据集有效地用于机器学习。 原始数据通常嘈杂不可靠，并且可能缺少值。 在没有这些建模任务的情况下使用数据会产生误导性结果。

ML.NET 的转换管道撰写一组自定义转换，在定型或测试数据之前将其应用到数据。 转换的主要目的是为了[特征化](../resources/glossary.md#feature-engineering)数据。 机器学习算法理解[特征化](../resources/glossary.md#feature)数据，因此下一步是将文本数据转换为 ML 算法识别的格式。 该格式是[数值向量](../resources/glossary.md#numerical-feature-vector)。

下一步，调用将文本列 (`SentimentText`) 列特征化为机器学习算法使用的名为 `Features` 的数值向量的 `mlContext.Transforms.Text.FeaturizeText`。 此为包装器调用，它返回实际上是管道的 <xref:Microsoft.ML.Data.EstimatorChain%601>。 命名此 `pipeline`，因为你将把定型程序附加到 `EstimatorChain`。 将此添加为下一个代码行：

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

>[!WARNING]
> ML.NET 版本 0.10 更改了转换参数的顺序。 在运行应用程序和生成模型之前，这不会出错。 使用用于转换的参数名称，如前面的代码片段中所示。

这是预处理/特征化步骤。 使用 ML.NET 中可用的其他组件可以在使用模型时生成更佳结果。

## <a name="choose-a-learning-algorithm"></a>选择学习算法

若要添加定型程序，调用返回 <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> 对象的 `mlContext.BinaryClassification.Trainers.FastTree` 包装器方法。 这是一个将在此管道中使用的决策树学习器。 `FastTreeBinaryClassificationTrainer` 追加到 `pipeline` 并接受特征化的 `SentimentText` (`Features`) 和 `Label` 输入参数，以便从历史数据中学习。

将以下代码添加到 `BuildAndTrainModel` 方法中：

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a>定型模型

根据已加载和转换的数据集定型模型 <xref:Microsoft.ML.Data.TransformerChain%601>。 一旦定义了估算器，将使用 <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> 方法训练模型，同时提供已加载的训练数据。 这将返回要用于预测的模型。 `pipeline.Fit()` 定型管道，并返回基于传入的 `DataView` 的 `Transformer`。 在 `.Fit()` 方法运行之前不会执行此试验。

将以下代码添加到 `BuildAndTrainModel` 方法中：

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>保存并返回定型模型以用于评估

此时，你具有可以集成到任何现有或新 .NET 应用程序的 <xref:Microsoft.ML.Data.TransformerChain%601> 类型模型。 在 `BuildAndTrainModel` 方法末尾返回模型。

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>评估模型

你已经创建和定型模型，现在需要使用不同的数据集对其进行评估以保证质量和进行验证。 在 `Evaluate` 方法中，将传入在 `BuildAndTrainModel` 中创建的模型以进行评估。 紧随 `BuildAndTrainModel` 后创建 `Evaluate` 方法，如以下代码所示：

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

`Evaluate` 方法执行以下任务：

* 加载测试数据集。
* 创建 binaryclassification 计算器。
* 评估模型并创建指标。
* 显示指标。

使用下面的代码，在 `Train` 方法调用的正下方，从 `Main` 方法中添加对新方法的调用：

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

接下来，将使用机器学习 `model` 参数（转换器）和 `splitTestSet` 参数来输入特性，并返回预测。 将以下代码作为下一行添加到 `Evaluate` 方法中：

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

`mlContext.BinaryClassification.Evaluate` 方法使用指定数据集计算 `PredictionModel` 的质量指标。 它返回 <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> 对象，其中包含由二元分类计算器计算出的总体指标。 若要显示这些指标来确定模型质量，需要先获取指标。 将以下代码作为下一行添加到 `Evaluate` 方法中：

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>显示用于模型验证的指标

使用下面的代码显示指标、共享结果，然后处理它们：

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

若要在返回之前将模型保存到 .zip 文件，请添加以下代码作为 `Evaluate` 中的下一行来调用 `SaveModelAsFile` 方法：

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallSaveModel "Save the model")]

## <a name="save-the-model-as-azip-file"></a>将模型保存为 .zip 文件

使用下面的代码紧随 `Evaluate` 方法后创建 `SaveModelAsFile` 方法：

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` 方法执行以下任务：

* 将模型保存为 .zip 文件。

接下来，创建一个方法来保存模型，以便它可以在其他应用程序中重用和使用。 `ITransformer` 有一个在 `_modelPath` 全局字段中采用的 <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> 方法和一个 <xref:System.IO.Stream> 方法。 要将其保存为 zip 文件，将在调用 `SaveTo` 方法之前立即创建 `FileStream`。 将以下代码作为下一行添加到 `SaveModelAsFile` 方法中：

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SaveModel "Add the SaveTo Method")]

还可以使用以下代码通过使用 `_modelPath` 编写控制台消息来显示文件的写入位置：

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a>使用保存的模型预测测试数据结果

使用下面的代码紧随 `Evaluate` 方法后创建 `UseModelWithSingleItem` 方法：

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

`UseModelWithSingleItem` 方法执行以下任务：

* 创建测试数据的单个注释。
* 根据测试数据预测情绪。
* 结合测试数据和预测进行报告。
* 显示预测结果。

使用下面的代码，在 `Evaluate` 方法调用的正下方，从 `Main` 方法中添加对新方法的调用：

[!code-csharp[CallUseModelWithSingleItem](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

虽然 `model` 是对多行数据进行操作的 `transformer`，但是一个非常常见的生产场景是，需要对单个示例进行预测。 <xref:Microsoft.ML.PredictionEngine%602> 是从 `CreatePredictionEngine` 方法返回的包装器。 让我们添加以下代码来创建 `PredictionEngine`，作为 `Predict` 方法中的第一行：

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
通过创建一个 `SentimentData` 实例，在 `Predict` 方法中添加一个注释来测试定型模型的预测：

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

 可以使用它来预测单个注释数据实例的正面或负面情绪。 要获得预测，请对数据使用 <xref:Microsoft.ML.PredictionEngine%602.Predict%2A>。 请注意，输入数据是一个字符串，且模型包含特征化。 管道在定型和预测期间同步。 不必专门为预测编写预处理/特征化代码，并且相同 API 负责批处理和一次性预测。

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

### <a name="use-the-model-prediction"></a>使用模型：预测

显示 `SentimentText` 和相应的情绪预测以便共享结果，并采取相应措施。 这称为操作化，使用返回的数据作为操作策略的一部分。 使用以下 <xref:System.Console.WriteLine?displayProperty=nameWithType> 代码创建结果显示：

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>使用加载模型部署和预测

使用下面的代码在 `SaveModelAsFile` 方法前创建 `UseLoadedModelWithBatchItems` 方法：

```csharp
public static void UseLoadedModelWithBatchItems(MLContext mlContext)
{

}
```

`UseLoadedModelWithBatchItems` 方法执行以下任务：

* 创建批处理测试数据。
* 根据测试数据预测情绪。
* 结合测试数据和预测进行报告。
* 显示预测结果。

使用下面的代码，在 `UseModelWithSingleItem` 方法调用的正下方，从 `Main` 方法中添加对新方法的调用：

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseLoadedModelWithBatchItems "Call the CallUseLoadedModelWithBatchItems method")]

添加一些评论，以测试 `UseLoadedModelWithBatchItems` 方法中的定型模型预测：

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

加载模型

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadModel "Load the model")]

现在你有一个模型，可以使用它来预测使用 <xref:Microsoft.ML.ITransformer.Transform%2A> 方法的评论数据的正面或负面情绪。 要获得预测，请使用新数据上的 `Predict`。 请注意，输入数据是一个字符串，且模型包含特征化。 管道在定型和预测期间同步。 不必专门为预测编写预处理/特征化代码，并且相同 API 负责批处理和一次性预测。 在用于预测的 `UseLoadedModelWithBatchItems` 方法中添加以下代码：

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="use-the-loaded-model-for-prediction"></a>使用加载后的模型进行预测

显示 `SentimentText` 和相应的情绪预测以便共享结果，并采取相应措施。 这称为操作化，使用返回的数据作为操作策略的一部分。 使用以下 <xref:System.Console.WriteLine?displayProperty=nameWithType> 代码创建结果标头：

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

在显示预测结果之前，将情绪和预测结合在一起以查看原始评论及其预测情绪。 下面的代码使用 <xref:System.Linq.Enumerable.Zip%2A> 方法来实现此目的，因此请在下一步添加以下代码：

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

将 `SentimentText` 和 `Sentiment` 合并到一个类后，现在可以使用 <xref:System.Console.WriteLine?displayProperty=nameWithType> 方法来显示结果：

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

因为推测的元组元素名称是 C# 7.1 中的新功能，且项目的默认语言版本为 C# 7.0，你需要将语言版本更改为 C# 7.1 或更高版本。
要完成此操作，右键单击“解决方案资源管理器”中的项目节点，然后选择“属性”。 选择**生成**选项卡并选择**高级**按钮。 在下拉列表中，选择“C# 7.1”（或更高版本）。 选择“确定”按钮。

## <a name="results"></a>结果

结果应如下所示。 管道处理期间，会显示消息。 你可能会看到警告或处理消息。 为清楚起见，已经从下面的结果中删除这些内容。

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 79.14%
Auc: 86.27%
F1Score: 80.60%

=============== End of model evaluation ===============
The model is saved to C:\Tutorials\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.4641322
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1391833
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9819039
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

祝贺你！ 现在，你已成功生成用于分类和预测消息情绪的机器学习模型。 

生成成功的模型是一个迭代过程。 由于本教程使用小型数据集来提供快速模型训练，因此该模型的初始质量较低。 如果对模型质量不满意，可以通过尝试提供更大的训练数据集，或通过为每种算法选择具有不同超参数的不同训练算法来改进它。

可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存储库中找到本教程的源代码。

## <a name="next-steps"></a>后续步骤

在本教程中，你将了解：
> [!div class="checklist"]
> * 了解问题
> * 选择适当的机器学习算法
> * 准备数据
> * 转换数据
> * 定型模型
> * 评估模型
> * 使用训练的模型预测
> * 使用加载模型部署和预测

进入下一教程了解详细信息
> [!div class="nextstepaction"]
> [问题分类](github-issue-classification.md)
