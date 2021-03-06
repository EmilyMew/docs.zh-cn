---
title: 如何：执行对象的延迟初始化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28463bfd3e54e49461d9ce785d26e5dfca62e438
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188957"
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a>如何：执行对象的延迟初始化
<xref:System.Lazy%601?displayProperty=nameWithType> 类可简化执行迟缓初始化和对象实例化的工作。 通过以迟缓方式初始化对象，可在不需要对象的情况下避免创建所有对象，或可在首次访问对象之后再进行迟缓初始化。 若要了解详细信息，请参阅[迟缓初始化](../../../docs/framework/performance/lazy-initialization.md)  
  
## <a name="example"></a>示例  
 以下示例演示如何使用 <xref:System.Lazy%601> 初始化值。 假定可能不需要迟缓变量，这取决于将 `someCondition` 变量设置为 true 或 false 的一些其他代码。  
  
```vb  
Dim someCondition As Boolean = False  
  
Sub Main()  
    'Initializing a value with a big computation, computed in parallel  
    Dim _data As Lazy(Of Integer) = New Lazy(Of Integer)(Function()  
                                                             Dim result =  
                                                                 ParallelEnumerable.Range(0, 1000).  
                                                                 Aggregate(Function(x, y)  
                                                                               Return x + y  
                                                                           End Function)  
                                                             Return result  
                                                         End Function)  
  
    '  do work that may or may not set someCondition to True  
    ' ...  
    '  Initialize the data only if needed  
    If someCondition = True Then  
  
        If (_data.Value > 100) Then  
  
            Console.WriteLine("Good data")  
        End If  
    End If  
End Sub  
```  
  
```csharp  
  static bool someCondition = false;    
  //Initializing a value with a big computation, computed in parallel  
  Lazy<int> _data = new Lazy<int>(delegate  
  {  
      return ParallelEnumerable.Range(0, 1000).  
          Select(i => Compute(i)).Aggregate((x,y) => x + y);  
  }, LazyExecutionMode.EnsureSingleThreadSafeExecution);  
  
  // Do some work that may or may not set someCondition to true.  
  //  ...  
  // Initialize the data only if necessary  
  if (someCondition)  
  {  
    if (_data.Value > 100)  
      {  
          Console.WriteLine("Good data");  
      }  
  }  
```  
  
## <a name="example"></a>示例  
 以下示例演示如何使用 <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> 类初始化仅对当前线程上的当前对象实例可见的类型。  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>
- [迟缓初始化](../../../docs/framework/performance/lazy-initialization.md)
