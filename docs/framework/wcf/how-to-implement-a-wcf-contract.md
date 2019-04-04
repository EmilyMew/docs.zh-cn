---
title: 教程：实现 Windows Communication Foundation 服务协定
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: fa8c5457c636d7f37215f0d4b4fdbb1c96c9481e
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463613"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>教程：实现 Windows Communication Foundation 服务协定

本教程介绍创建基本 Windows Communication Foundation (WCF) 应用程序所需的五个任务的第二个。 有关教程的概述，请参阅[教程：开始使用 Windows Communication Foundation 应用程序](getting-started-tutorial.md)。

创建 WCF 应用程序的下一步是添加代码以实现在上一步中创建的 WCF 服务接口。 在此步骤中，创建一个名为类`CalculatorService`，用于实现用户定义`ICalculator`接口。 下面的代码中的每个方法调用计算器操作，并将文本写入到控制台，以对其进行测试。 

在本教程中，你将了解：
> [!div class="checklist"]
> - 添加代码以实现 WCF 服务约定。
> - 生成解决方案。

## <a name="add-code-to-implement-the-wcf-service-contract"></a>添加代码以实现 WCF 服务约定

在中**GettingStartedLib**，打开**Service1.cs**或**Service1.vb**文件，其代码替换为以下代码：

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

## <a name="edit-appconfig"></a>编辑 App.config

编辑**App.config**中**GettingStartedLib**以反映所做的更改所做的代码。
- 视觉对象C#项目：
  - 更改第 14 行 `<service name="GettingStartedLib.CalculatorService">`
  - 更改到的第 17 行 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - 更改到第 22 行 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- 对于 Visual Basic 项目：
  - 更改第 14 行 `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - 更改到的第 17 行 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - 更改到第 22 行 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>编译代码

生成解决方案以验证已不存在任何编译错误。 如果在使用 Visual Studio 中，**构建**菜单中选择**生成解决方案**(或按**Ctrl**+**Shift** + **B**)。

## <a name="next-steps"></a>后续步骤

在本教程中，你将了解：
> [!div class="checklist"]
> - 添加代码以实现 WCF 服务约定。
> - 生成解决方案。

转到下一步的教程，了解如何运行 WCF 服务。

> [!div class="nextstepaction"]
> [教程：托管并运行基本的 WCF 服务](how-to-host-and-run-a-basic-wcf-service.md)
