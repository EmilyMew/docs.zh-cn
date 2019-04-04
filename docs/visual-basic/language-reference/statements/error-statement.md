---
title: Error 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 8ac7cee2f9959bc75df165d00d3a0a67e1dd9af0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837528"
---
# <a name="error-statement"></a>Error 语句
模拟错误的匹配项。  
  
## <a name="syntax"></a>语法  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>部件  
 `errornumber`  
 必需。 可以是任何有效的错误号。  
  
## <a name="remarks"></a>备注  
 `Error`语句支持向后兼容性。 在新代码，尤其是在创建对象时，使用`Err`对象的`Raise`方法以生成运行时错误。  
  
 如果`errornumber`定义，则`Error`语句的属性后调用错误处理程序`Err`对象分配以下默认值：  
  
|属性|值|  
|--------------|-----------|  
|`Number`|值指定为参数`Error`语句。 可以是任何有效的错误号。|  
|`Source`|当前的 Visual Basic 项目的名称。|  
|`Description`|字符串表达式的返回值对应`Error`函数为指定`Number`，如果存在此字符串。 如果字符串不存在，`Description`包含一个零长度字符串 ("")。|  
|`HelpFile`|完全限定的驱动器、 路径和相应的 Visual Basic 帮助文件的文件名。|  
|`HelpContext`|相应的 Visual Basic 帮助文件上下文 ID 的错误相对应的`Number`属性。|  
|`LastDLLError`|为零。|  
  
 如果没有错误处理程序存在，或者如果未启用，一条错误消息创建并显示从`Err`对象属性。  
  
> [!NOTE]
>  某些 Visual Basic 主机应用程序无法创建对象。 请参阅主机应用程序的文档以确定其是否可以创建类和对象。  
  
## <a name="example"></a>示例  
 此示例使用`Error`语句生成错误号 11。  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>要求  
 **命名空间：**[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **程序集：** Visual Basic 运行库（在 Microsoft.VisualBasic.dll 中）  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error 语句](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Resume 语句](../../../visual-basic/language-reference/statements/resume-statement.md)
- [错误消息](../../../visual-basic/language-reference/error-messages/index.md)
