---
title: 机器学习术语表 - ML.NET
description: 一个重要的机器学习术语表，可在 ML.NET 中生成自定义模型时使用。
ms.custom: seodec18
ms.date: 03/05/2019
ms.openlocfilehash: cc236aaa99fd8a7b05af666a5b96f657d8bd3ad4
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410233"
---
# <a name="machine-learning-glossary-of-important-terms"></a>机器学习重要术语词汇表

以下列表是重要的机器学习术语编译，可在 ML.NET 中生成自定义模型时使用。

> [!NOTE]
> 本文档引用 ML.NET（目前为预览版）。 材料可能会有所变化。 有关详细信息，请参阅 [ML.NET 简介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)。

## <a name="accuracy"></a>准确性

在[分类](#classification)中，准确性是正确分类的项数目除以测试集内的项总数。 范围从 0（最不准确）到 1（最准确）。 准确性是模型性能的评估指标之一。 将其与[精度](#precision)、[撤回](#recall)和 [F 分数](#f-score)结合考虑。

## <a name="area-under-the-curve-auc"></a>曲线下面积 (AUC)

[二元分类](#binary-classification)中的一项评估指标，即曲线下面积值，它绘制真阳性率（y 轴）与误报率（x 轴）进行对照。 范围从 0.5（最差）到 1（最佳）。 也称为 ROC 曲线下面积，即，接受者操作特征曲线。 有关详细信息，请参阅 Wikipedia 上的[接受者操作特征](https://en.wikipedia.org/wiki/Receiver_operating_characteristic)一文。

## <a name="binary-classification"></a>二元分类

一个[分类](#classification)事例，其中[标签](#label)仅为两个类中的一个。 有关详细信息，请参阅[机器学习任务](tasks.md)主题的[二元分类](tasks.md#binary-classification)部分。

## <a name="classification"></a>分类

当使用这些数据来预测某一类别，[监管式机器学习](#supervised-machine-learning)任务被称为“分类”。 [二元分类](#binary-classification)指的是仅预测两个类别（例如，将图像划分为“猫”或“狗”图片）。 [多类分类](#multiclass-classification)指的是预测多个类别（例如，当将图像划分为特定品种狗的图片）。

## <a name="coefficient-of-determination"></a>决定系数

[回归](#regression)中的一项评估指标，表明数据与模型的匹配程度。 范围从 0 到 1。 值 0 表示数据是随机的，否则就无法与模型相匹配。 值 1 表示模型与数据完全匹配。 这通常称为 <sup>2</sup>、R<sup>2</sup> 或 r 平方值。

## <a name="feature"></a>功能

正在对其进行度量的现象的一个可度量属性，通常是一个数（双精度）值。 多个特征被称为“特征向量”且通常存储为 `double[]`。 这些特征定义所度量现象的重要特性。 有关详细信息，请参阅 Wikipedia 上的[特征](https://en.wikipedia.org/wiki/Feature_(machine_learning))一文。

## <a name="feature-engineering"></a>特征工程

特征工程是涉及定义一组[特征](#feature)和开发软件以从可用现象数据中生成特征向量（即特征提取）的过程。 有关详细信息，请参阅 Wikipedia 上的[特征工程](https://en.wikipedia.org/wiki/Feature_engineering)一文。

## <a name="f-score"></a>F 分数

[分类](#classification)中的一项评估指标，它平衡[精度](#precision)和[撤回](#recall)。

## <a name="hyperparameter"></a>超参数

机器学习算法的参数。 示例包括在决策林中学习的树的数量，或者梯度下降算法中的步长。 在对模型进行定型之前，先设置超参数的值，并控制查找预测函数参数的过程，例如，决策树中的比较点或线性回归模型中的权重。 有关详细信息，请参阅 Wikipedia 上的[超参数](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning))一文。

## <a name="label"></a>Label

使用机器学习模型进行预测的元素。 例如，狗的品种或将来的股票价格。

## <a name="log-loss"></a>对数损失

在[分类](#classification)中，描述分类器准确性的评估指标。 对数损失越小，分类器越准确。

## <a name="mean-absolute-error-mae"></a>平均绝对误差 (MAE)

[回归](#regression)中的一项评估指标，即所有模型误差的平均值，其中模型误差是预测[标签](#label)值和正确标签值之间的差距。

## <a name="model"></a>模型

就传统意义而言，它是预测函数的参数。 例如，线性回归模型中的权重或决策树中的拆分点。 在 ML.NET 中，一个模型包含预测域对象[标签](#label)所需的所有信息（例如，图像或文本）。 这意味着 ML.NET 模型包括所需的特征化步骤以及预测函数参数。

## <a name="multiclass-classification"></a>多类分类

一个[分类](#classification)事例，其中[标签](#label)是三个或更多类中的一个。 有关详细信息，请参阅[机器学习任务](tasks.md)主题的[多类分类](tasks.md#multiclass-classification)部分。

## <a name="n-gram"></a>N 元语法

文本数据的特征提取方案：N 个单词的任何序列都将转变为[特征](#feature)值。

## <a name="numerical-feature-vector"></a>数字特征向量

只包含数值的[特征](#feature)向量。 这与 `double[]` 非常类似。

## <a name="pipeline"></a>管道

要将模型与数据集相匹配所需的所有操作。 管道由数据导入、转换、特征化和学习步骤组成。 对管道进行定型后，它会转变为模型。

## <a name="precision"></a>精度

在[分类](#classification)中，类的精度是正确预测为属于该类的项目的数量，除以预测为属于该类的项目的总数。

## <a name="recall"></a>撤回

在[分类](#classification)中，类的撤回是正确预测为属于该类的项目的数量，除以实际属于该类的项目的总数。

## <a name="regression"></a>回归测试

[监管式机器学习](#supervised-machine-learning)任务，其中输出是一个实际值，例如，双精度值。 示例包括预测股票价格。 有关详细信息，请参阅[机器学习任务](tasks.md)主题的[回归](tasks.md#regression)部分。

## <a name="relative-absolute-error"></a>相对绝对误差

[回归](#regression)中的一项评估指标，即所有绝对误差总和除以正确[标签](#label)值和所有正确标签值的平均值之间的差值总和。

## <a name="relative-squared-error"></a>相对平方误差

[回归](#regression)中的一项评估指标，即所有绝对平方误差总和除以正确[标签](#label)值和所有正确标签值的平均值之间的平方差值总和。

## <a name="root-of-mean-squared-error-rmse"></a>均方误差根 (RMSE)

[回归](#regression)中的一项评估指标，即误差平方平均值的平方根。

## <a name="supervised-machine-learning"></a>监管式机器学习

机器学习的一个子类，其中所需的模型预测尚不可见的数据标签。 示例包括分类、回归以及结构化预测。 有关详细信息，请参阅 Wikipedia 上的[监管式学习](https://en.wikipedia.org/wiki/Supervised_learning)一文。

## <a name="training"></a>训练

识别给定定型数据集[模型](#model)的过程。 对于线性模型，这意味着查找权重。 有关树信息，这涉及到标识拆分点。

## <a name="transform"></a>Transform

转换数据的[管道](#pipeline)组件。 例如，从文本到数字向量。

## <a name="unsupervised-machine-learning"></a>非监管式机器学习

机器学习的子类，其中所需的模型查找数据中的隐藏（或潜在）结构。 示例包括聚类分析、主题建模和维数约简。 有关详细信息，请参阅 Wikipedia 上的[非监管式学习](https://en.wikipedia.org/wiki/Unsupervised_learning)一文。
