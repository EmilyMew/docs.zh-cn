---
title: memberInfoCacheCreation MDA
ms.date: 03/30/2017
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90f59f4d593a8aa077a6710cc0f5c1747ac1a3ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103761"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation MDA
创建 <xref:System.Reflection.MemberInfo> 缓存时，将激活 `memberInfoCacheCreation` 托管调试助手 (MDA)。 这一点强烈表明程序正在使用资源昂贵的反射功能。  
  
## <a name="symptoms"></a>症状  
 由于程序正在使用资源昂贵的反射，所以程序的工作集增加。  
  
## <a name="cause"></a>原因  
 将涉及 <xref:System.Reflection.MemberInfo> 对象的反射操作视作资源昂贵的反射，因为这些操作必须读取存储在冷页中的元数据，并且通常指示程序正在使用某种类型的后期绑定方案。  
  
## <a name="resolution"></a>解决方法  
 先启用此 MDA，再在调试程序中运行代码或在激活 MDA 时附加一个调试程序，即可确定程序中正在使用反射的位置。 在调试程序下将获得堆栈跟踪，它显示创建 <xref:System.Reflection.MemberInfo> 缓存的位置，从该位置可以确定程序正在使用反射的位置。  
  
 该解决方案依赖代码的目标。 此 MDA 提醒你，程序具有后期绑定方案。 可能希望确定能否替换早期绑定方案，或考虑后期绑定方案的性能。  
  
## <a name="effect-on-the-runtime"></a>对运行时的影响  
 创建的每个 <xref:System.Reflection.MemberInfo> 缓存都可激活此 MDA。 性能影响可以忽略不计。  
  
## <a name="output"></a>Output  
 该 MDA 输出一条消息，指示已创建 <xref:System.Reflection.MemberInfo> 缓存。 使用调试程序器获取堆栈跟踪，堆栈跟踪显示程序正在使用反射的位置。  
  
## <a name="configuration"></a>配置  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>示例  
 此示例代码将激活 `memberInfoCacheCreation` MDA。  
  
```csharp
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Reflection.MemberInfo>
- [使用托管调试助手诊断错误](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
