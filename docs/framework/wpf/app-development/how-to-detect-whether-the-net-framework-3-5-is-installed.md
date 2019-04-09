---
title: 如何：检测是否安装了 .NET Framework 3.5
ms.date: 03/30/2017
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
ms.openlocfilehash: af2428ece79803953b8c90431d905824dd18fec8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074633"
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a>如何：检测是否安装了 .NET Framework 3.5
管理员可部署的系统上的 Windows Presentation Foundation (WPF) 应用程序之前[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]，它们必须先确认[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]运行时已存在。 本主题提供了编写的脚本在 HTML/JavaScript，管理员可以用于确定是否[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]系统上存在。  
  
> [!NOTE]
>  有关更多详细信息上安装、 部署和检测[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]，请参阅[安装面向开发人员的.NET Framework](../../install/guide-for-developers.md)。  
  
## <a name="example"></a>示例  
 当[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]是安装，MSI 向".NET CLR"和版本号的 UserAgent 字符串。 下面的示例演示一个简单的 HTML 页面中嵌入的脚本。 脚本搜索用户代理字符串以确定是否[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]安装，并在搜索结果中显示的状态消息。  
  
> [!NOTE]
>  此脚本旨在为 Internet 资源管理器。 其他浏览器可能不包括用户代理字符串中的.NET CLR 的信息。  
  
```  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.5</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.5.0.0";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.5."  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.5." +  
          " The required version is v" + dotNETRuntimeVersion + ".";  
      }  
      result.innerText += "\n\nThis machine's userAgent string is: " +   
        navigator.userAgent + ".";  
    }  
  
    //  
    // Retrieve the version from the user agent string and   
    // compare with the specified version.  
    //  
    function HasRuntimeVersion(versionToCheck)  
    {  
      var userAgentString =   
        navigator.userAgent.match(/.NET CLR [0-9.]+/g);  
  
      if (userAgentString != null)  
      {  
        var i;  
  
        for (i = 0; i < userAgentString.length; ++i)  
        {  
          if (CompareVersions(GetVersion(versionToCheck),   
            GetVersion(userAgentString[i])) <= 0)  
            return true;  
        }  
      }  
  
      return false;  
    }  
  
    //  
    // Extract the numeric part of the version string.  
    //  
    function GetVersion(versionString)  
    {  
      var numericString =   
        versionString.match(/([0-9]+)\.([0-9]+)\.([0-9]+)/i);  
      return numericString.slice(1);  
    }  
  
    //  
    // Compare the 2 version strings by converting them to numeric format.  
    //  
    function CompareVersions(version1, version2)  
    {  
      for (i = 0; i < version1.length; ++i)  
      {  
        var number1 = new Number(version1[i]);  
        var number2 = new Number(version2[i]);  
  
        if (number1 < number2)  
          return -1;  
  
        if (number1 > number2)  
          return 1;  
      }  
  
      return 0;  
    }  
  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY>  
    <div id="result" />  
  </BODY>  
</HTML>  
```  
  
 如果为".NET CLR"版本搜索成功，将显示以下类型的状态消息：  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 否则，将显示以下类型的状态消息：  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a>请参阅

- [检测是否安装了 .NET Framework 3.0](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
