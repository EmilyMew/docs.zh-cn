---
title: 将唯一 XML 架构 (XSD) 约束映射到数据集约束
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 650cd6b8b8149529f115f22a11d19178fbd6d302
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108220"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>将唯一 XML 架构 (XSD) 约束映射到数据集约束
在 XML 架构定义语言 (XSD) 架构中，**唯一**元素指定的元素或属性的唯一性约束。 在将 XML 架构转换为关系架构的过程中，对 XML 架构中的元素或属性指定的唯一约束将映射到所生成的相应 <xref:System.Data.DataTable> 中的 <xref:System.Data.DataSet> 中的唯一约束。  
  
 下表概括**msdata**可以在指定的属性**唯一**元素。  
  
|特性名|描述|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|如果指定了该属性，它的值将用作约束名。 否则为**名称**属性提供值的约束名称。|  
|**msdata:PrimaryKey**|如果`PrimaryKey="true"`处在**唯一**元素，与创建唯一约束**IsPrimaryKey**属性设置为**true**。|  
  
 下面的示例显示使用一个 XML 架构**唯一**元素来指定唯一性约束。  
  
```xml  
<xs:schema id="SampleDataSet"   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"   
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"   
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 **唯一**架构中的元素指定所有**客户**实例的文档中的元素的值**CustomerID**必须是唯一的子元素。 在构建**数据集**，映射过程将读取此架构并生成下表：  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 映射过程还会创建唯一约束上**CustomerID**列，如下所示**数据集**。 （为简便起见，只显示相关属性。）  
  
```  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 在中**数据集**生成， **IsPrimaryKey**属性设置为**False**的唯一约束。 **唯一**列的属性指示**CustomerID**列的值必须是唯一 (但它们可以是空引用，由指定**AllowDBNull**列的属性）。  
  
 如果你修改架构并设置可选**msdata: primarykey**属性值为**True**，表上创建唯一约束。 **AllowDBNull**列属性设置为**False**，并**IsPrimaryKey**属性设置为该约束**True**，从而使**CustomerID**列主键列。  
  
 您可以对 XML 架构中元素或属性的组合指定唯一约束。 下面的示例演示如何指定的组合**CustomerID**并**CompanyName**的值必须是唯一的所有**客户**在任何情况下，通过添加另一个**xs:field**架构中的元素。  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 这是创建在随后出现的限制**数据集**。  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>请参阅

- [将关键 XML 架构 (XSD) 约束映射到数据集约束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [从 XML 架构生成数据集关系 (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
