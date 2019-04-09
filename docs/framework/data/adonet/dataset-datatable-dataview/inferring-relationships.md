---
title: 推断关系
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: f8a9aba493dfe82466608ea60932ddfec5ef64f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127876"
---
# <a name="inferring-relationships"></a>推断关系
如果被推断为表的元素具有一个同样被推断为表的子元素，则将在这两个表之间创建 <xref:System.Data.DataRelation>。 名称的新列**ParentTableName_Id**将添加到父元素中，创建的表和子元素创建的表。 **ColumnMapping**此标识列的属性将设置为**MappingType.Hidden**。 列将为父表中，已自动递增主关键字和将用于**DataRelation**两个表之间。 添加的标识列的数据类型将是**System.Int32**，这是与所有其他推断列的数据类型，不同**System.String**。 一个<xref:System.Data.ForeignKeyConstraint>与**DeleteRule** = **级联**还将在父和子表中使用新的列创建。  
  
 例如，考虑以下 XML：  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推理过程将生成两个表：**Element1**并**ChildElement1**。  
  
 **Element1**表具有两个列：**Element1_Id**并**ChildElement2**。 **ColumnMapping**的属性**Element1_Id**列将设置为**MappingType.Hidden**。 **ColumnMapping**的属性**ChildElement2**列将设置为**MappingType.Element**。 **Element1_Id**列将设置为的主键**Element1**表。  
  
 **ChildElement1**表具有三个列： **attr1**， **attr2**并**Element1_Id**。 **ColumnMapping**属性**attr1**并**attr2**列将设置为**MappingType.Attribute**。 **ColumnMapping**的属性**Element1_Id**列将设置为**MappingType.Hidden**。  
  
 一个**DataRelation**并**ForeignKeyConstraint**将使用创建**Element1_Id**这两个表中的列。  
  
 **数据集：** DocumentElement  
  
 **表：** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **表：** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|value1|value2|0|  
  
 **DataRelation:** Element1_ChildElement1  
  
 **ParentTable:** Element1  
  
 **ParentColumn:** Element1_Id  
  
 **ChildTable:** ChildElement1  
  
 **ChildColumn:** Element1_Id  
  
 **嵌套：** True  
  
 **ForeignKeyConstraint:** Element1_ChildElement1  
  
 **列：** Element1_Id  
  
 **ParentTable:** Element1  
  
 **ChildTable:** ChildElement1  
  
 **DeleteRule:** Cascade  
  
 **AcceptRejectRule:** None  
  
## <a name="see-also"></a>请参阅

- [从 XML 推断数据集关系结构](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [从 XML 加载数据集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [从 XML 加载数据集架构信息](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [嵌套 DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)
- [在数据集中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [数据集、数据表和数据视图](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
