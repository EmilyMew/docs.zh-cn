---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: 372e4128667a0ab1288372ce0ec077b3a4ee2ec6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842065"
---
# <a name="customchannelstester"></a>CustomChannelsTester
`CustomChannelsTester` 是一个可用于依据一组预定义的服务协定测试自定义通道实现的工具。 可以通过使用 XML 文件选择这组服务协定并将其传递给该工具。 然后，该工具将生成服务和客户端，该客户端会在消息交换过程中测试您的自定义通道实现。  
  
### <a name="to-build-the-tool"></a>生成工具  
  
1.  若要生成解决方案，请按照中的说明[生成 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
2.  生成解决方案将生成三个文件：CustomChannelsTester.exe、 TestSpec.xml 和 SampleRun.cmd。 SampleRun.cmd 文件有一个示例命令行，演示如何使用此工具来测试[传输：UDP](../../../../docs/framework/wcf/samples/transport-udp.md)示例。  
  
### <a name="to-run-the-tool"></a>运行此工具  
  
-   在命令提示符处，键入下列命令：  
  
    ```  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     需要使用 `/binding` 选项。  
  
     `/dll` 如果"绑定"不是通过 Windows Communication Foundation (WCF) 提供系统提供的绑定，是必需的。  
  
     `/testspec` 是可选的。  
  
     这将根据测试规范和绑定创建服务器和客户端。  
  
     执行该客户端和服务器并返回结果。  
  
     下面是用于描述测试规范的示例 XML (testspec.xml)：  
  
    ```xml  
    <TestSpec xmlns="http://WCF/TestSpec" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" >  
    <ServiceContract>  
    <!-- Test a contract which has oneway / twoway operations. If you set ExpandAll = true, both types of contracts are tested -->    <IsOneWay ExpandAll="true">true</IsOneWay>  
    <!-- Test a contract with Asynchronous / Synchronous Operations-->  
        <IsAsync>false</IsAsync>   
    <!-- Test a sessionful / sessionless contract-->      
        <IsSession ExpandAll="true">true</IsSession>  
    <!-- If the Service Contract includes a CallBack Contract-->      
        <IsCallBack ExpandAll="true">true</IsCallBack>  
    </ServiceContract>  
    <TestDetails>  
    <!-- Name of the machine that runs the server - required if you want to run the test crossmachine-->  
        <ServerName>ReplaceThisWithTheServerMachineName</ServerName>  
    <!-- Port Number - Optional-->  
        <Port>8000</Port>  
    <!--URI for the callBack address for the CLient. The client will receive the messages from the server on this address in case of a CallBack Contract-->  
        <ClientCallBackAddress/>      
    <!-- Duration (in sec) after the server has started, it times out - optional(default = 300sec) -->  
        <ServerTimeout>300</ServerTimeout>  
    <!-- Duration (in sec) before the Client initializes -optional(default = 60sec) -->  
        <ClientTimeout>60</ClientTimeout>  
    <!-- Number of clients for each service - optional(default = 1) -->  
        <NumberOfClients>1</NumberOfClients>  
    <!-- Number of messages each client sends to the service - optional(default = 1) -->  
        <MessagesPerClient>1</MessagesPerClient>  
    </TestDetails>  
    </TestSpec>  
    ```  
  
