---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: e7b4ebc58b6fe9850b92ef945cb0d715e4369efe
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820902"
---
# <a name="-bugreport"></a>-bugreport
创建提交 bug 报告时，可以使用一个文件。  
  
## <a name="syntax"></a>语法  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`file`|必需。 将包含 bug 报告文件的名称。 将文件名括在引号 ("") 如果名称包含空格。|  
  
## <a name="remarks"></a>备注  
 以下信息添加到`file`:  
  
-   在编译中的所有源代码文件的副本。  
  
-   编译器选项编译中使用的列表。  
  
-   有关编译器、 公共语言运行时和操作系统的版本信息。  
  
-   编译器输出（如有）。  
  
-   说明问题，这向您发出提示。  
  
-   应修复所预期的问题的说明，这向您发出提示。  
  
 因为所有源代码文件的副本包含在`file`，可能想要重现在尽可能短小的程序 （可疑的） 代码缺陷。  
  
> [!IMPORTANT]
>  `-bugreport`选项将生成包含潜在敏感信息的文件。 这包括当前时间，编译器版本[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]版本、 OS 版本、 用户名称、 与其编译器已运行，所有源代码和二进制形式的任何引用的程序集的命令行参数。 可以通过命令行选项指定的服务器端汇集在 Web.config 文件中访问此选项[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]应用程序。 若要防止此情况，修改 Machine.config 文件不允许用户在服务器上进行编译。  
  
 如果将此选项用于`-errorreport:prompt`， `-errorreport:queue`，或`-errorreport:send`，和你的应用程序时遇到内部编译器错误中的信息`file`发送到 Microsoft Corporation。 该信息将帮助确定错误的原因的 Microsoft 工程师以及可帮助提高下一版本的 Visual Basic。 默认情况下，任何信息不发送给 Microsoft。 但是，当编译应用程序使用`-errorreport:queue`，默认情况下启用，应用程序收集其错误报告。 然后，在计算机的管理员登录，错误报告系统将显示一个弹出窗口，使管理员能够将转发到任何错误报告的 Microsoft 自登录以来发生的。  
  
> [!NOTE]
>  `/bugreport`选项不是可从 Visual Studio 开发环境中; 它是可仅在编译时从命令行。  
  
## <a name="example"></a>示例  
 下面的示例将编译`T2.vb`并将错误报告的所有信息都放入该文件`Problem.txt`。  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-调试 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [（ASP.NET 设置架构） securityPolicy 的 trustLevel 元素](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
