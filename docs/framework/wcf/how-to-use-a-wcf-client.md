---
title: 教程：使用 Windows Communication Foundation 客户端
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 4d883277f795ea84c59aee91ffcb9b9802b0933b
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411715"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a>教程：使用 Windows Communication Foundation 客户端

本教程介绍了五个任务创建一个基本的 Windows Communication Foundation (WCF) 应用程序所需的最后一个。 有关教程的概述，请参阅[教程：开始使用 Windows Communication Foundation 应用程序](getting-started-tutorial.md)。

已创建并配置 Windows Communication Foundation (WCF) 代理后，创建客户端实例，并编译客户端应用程序。 然后将它与 WCF 服务进行通信。 

在本教程中，你将了解：
> [!div class="checklist"]
> - 添加代码以使用 WCF 客户端。
> - 测试 WCF 客户端。

## <a name="add-code-to-use-the-wcf-client"></a>添加代码以使用 WCF 客户端

客户端代码执行以下步骤操作：
- 实例化 WCF 客户端。
- 从生成的代理调用服务操作。
- 完成操作调用后关闭客户端。

打开**Program.cs**或**Module1.vb**从文件**GettingStartedClient**项目，其代码替换为以下代码：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GettingStartedClient.ServiceReference1;

namespace GettingStartedClient
{
    class Program
    {
        static void Main(string[] args)
        {
            //Step 1: Create an instance of the WCF proxy.
            CalculatorClient client = new CalculatorClient();

            // Step 2: Call the service operations.
            // Call the Add service operation.
            double value1 = 100.00D;
            double value2 = 15.99D;
            double result = client.Add(value1, value2);
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

            // Call the Subtract service operation.
            value1 = 145.00D;
            value2 = 76.54D;
            result = client.Subtract(value1, value2);
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

            // Call the Multiply service operation.
            value1 = 9.00D;
            value2 = 81.25D;
            result = client.Multiply(value1, value2);
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

            // Call the Divide service operation.
            value1 = 22.00D;
            value2 = 7.00D;
            result = client.Divide(value1, value2);
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

            // Step 3: Close the client to gracefully close the connection and clean up resources.
            Console.WriteLine("\nPress <Enter> to terminate the client.");
            Console.ReadLine();
            client.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.ServiceModel
Imports GettingStartedClient.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy.
        Dim Client As New CalculatorClient()

        ' Step 2: Call the service operations.
        ' Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        ' Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        ' Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        ' Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Close the client to gracefully close the connection and clean up resources.
        Console.WriteLine()
        Console.WriteLine("Press <Enter> to terminate the client.")
        Console.ReadLine()
        Client.Close()

    End Sub

End Module
```

请注意`using`(视觉对象C#) 或`Imports`（对于 Visual Basic) 语句导入`GettingStartedClient.ServiceReference1`。 此语句将导入 Visual Studio 使用生成的代码**添加服务引用**函数。 该代码实例化 WCF 代理，并调用每个计算器服务公开的服务操作。 然后，关闭代理并结束程序。

## <a name="test-the-wcf-client"></a>测试 WCF 客户端

### <a name="test-the-application-from-visual-studio"></a>测试从 Visual Studio 应用程序

1. 保存并生成解决方案。

2. 选择**GettingStartedLib**文件夹，，然后选择**设为启动项目**从快捷菜单。

3. 从**启动项目**，选择**GettingStartedLib**从下拉列表中，然后选择**运行**或按**F5**。

### <a name="test-the-application-from-a-command-prompt"></a>测试应用程序从命令提示符

1. 打开命令提示符以管理员身份，，然后导航到你的 Visual Studio 解决方案目录。 

2. 若要启动服务：输入*GettingStartedHost\bin\Debug\GettingStartedHost.exe*。

3. 若要启动客户端：打开另一个命令提示符，导航到 Visual Studio 解决方案目录，然后输入*GettingStartedClient\bin\Debug\GettingStartedClient.exe*。

   *GettingStartedHost.exe*生成以下输出：

   ```text
   The service is ready.
   Press <Enter> to terminate the service.

   Received Add(100,15.99)
   Return: 115.99
   Received Subtract(145,76.54)
   Return: 68.46
   Received Multiply(9,81.25)
   Return: 731.25
   Received Divide(22,7)
   Return: 3.14285714285714
   ```

   *GettingStartedClient.exe*生成以下输出：

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a>后续步骤

现在已在 WCF 入门教程中完成所有任务。 在本教程中，你将了解：

在本教程中，你将了解：
> [!div class="checklist"]
> - 添加代码以使用 WCF 客户端。
> - 测试 WCF 客户端。

如果您有问题或错误中的任何步骤，按照要解决这些问题的故障排除文章中的步骤。

> [!div class="nextstepaction"]
> [排查 Get 开始使用 WCF 教程](troubleshooting-the-getting-started-tutorial.md)

