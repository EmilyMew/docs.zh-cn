---
title: 推断列
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 53e77f624c5af8f61a32d5b1399d2728f32011a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107194"
---
# <a name="inferring-columns"></a>推断列
ADO.NET 从 XML 文档中确定了哪些元素要作为 <xref:System.Data.DataSet> 的表进行推断后，即开始推断这些表的列。 ADO.NET 2.0 引入了一个新的架构推断引擎，推断每个强类型化的数据类型**simpleType**元素。 在以前版本的数据类型推断**simpleType**元素始终是**xsd: string**。  
  
## <a name="migration-and-backward-compatibility"></a>迁移和向后兼容性  
 **ReadXml**方法采用一个类型的参数**InferSchema**。 使用此自变量可以指定与以前的版本兼容的推断行为。 可用值**InferSchema**枚举下表中所示。  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 通过始终将简单类型作为 <xref:System.String> 进行推断，提供向后兼容性。  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 推断强类型化的数据类型。 如果与 <xref:System.Data.DataTable> 一起使用，会发生异常。  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 忽略任何内联架构并将数据读入现有的 <xref:System.Data.DataSet> 架构。  
  
## <a name="attributes"></a>特性  
 中定义[推断表](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)，该元素具有属性将被推断为表。 然后，该元素的属性将被推断为该表的列。 **ColumnMapping**列的属性将设置为**MappingType.Attribute**，以确保如果该架构将写回 XML 的列名称将作为特性写入。 这些属性的值存储在表的行中。 例如，考虑以下 XML：  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 推断过程将生成名为的表**Element1**包含两个列**attr1**并**attr2**。 **ColumnMapping**这两个列的属性将设置为**MappingType.Attribute**。  
  
 **数据集：** DocumentElement  
  
 **表：** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>不具有属性或子元素的元素  
 如果元素不具有子元素或属性，它将被推断为列。 **ColumnMapping**的列的属性将设置为**MappingType.Element**。 子元素的文本存储在表的行中。 例如，考虑以下 XML：  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推断过程将生成名为的表**Element1**包含两个列**ChildElement1**并**ChildElement2**。 **ColumnMapping**这两个列的属性将设置为**MappingType.Element**。  
  
 **数据集：** DocumentElement  
  
 **表：** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Text2|  
  
## <a name="see-also"></a>请参阅

- [从 XML 推断数据集关系结构](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [从 XML 加载数据集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [从 XML 加载数据集架构信息](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [在数据集中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [数据集、数据表和数据视图](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
