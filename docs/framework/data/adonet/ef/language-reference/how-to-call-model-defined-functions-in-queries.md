---
title: 如何：在查询中调用模型定义的函数
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: abab705c7ea83318949cf0d75e491905da7896e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099724"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>如何：在查询中调用模型定义的函数
本主题介绍如何在 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查询中调用在概念模型中定义的函数。  
  
 下面的过程高度概括了有关在 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查询中调用模型定义函数的信息。 后面的示例提供了有关该过程中各个步骤的更多详细信息。 这些过程假定您在概念模型中定义了一个函数。 有关详细信息，请参阅[如何：概念模型中定义自定义函数](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))。  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>调用在概念模型中定义的函数  
  
1.  向应用程序中添加一个公共语言运行时 (CLR) 方法，该方法将映射到概念模型中定义的函数。 若要映射方法，必须将 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 应用于此方法。 请注意，此特性的 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> 和 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> 参数分别是概念模型的命名空间名称和概念模型中的函数名称。 LINQ 的函数名称解析区分大小写。  
  
2.  在 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查询中调用该函数。  
  
## <a name="example"></a>示例  
 下面的示例演示如何在 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查询中调用概念模型中定义的函数。 本示例使用 School 模型。 有关 School 模型的信息，请参阅[创建 School 示例数据库](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))并[生成 School.edmx 文件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100))。  
  
 以下概念模型函数返回教师已聘用的年数。 有关向概念模型添加函数的信息，请参阅[如何：概念模型中定义自定义函数](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))。)  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>示例  
 接下来，向应用程序添加以下方法，并使用 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 将其映射到概念模型函数：  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>示例  
 现在，可以在 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查询中调用概念模型函数了。 下面的代码调用该方法以显示十年前雇佣的所有教师：  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>请参阅

- [.edmx 文件概述](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [LINQ to Entities 中的查询](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [在 LINQ to Entities 查询中调用函数](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [如何：调用模型定义的函数作为对象方法](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
