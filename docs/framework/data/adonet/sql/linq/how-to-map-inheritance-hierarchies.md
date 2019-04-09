---
title: 如何：映射继承层次结构
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: f75c7fe701c4a2fab1f993517828b38e5a26e2bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138081"
---
# <a name="how-to-map-inheritance-hierarchies"></a>如何：映射继承层次结构
若要在 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 中执行继承映射，您必须按以下步骤中的说明在继承层次结构的根类中指定属性 (Attribute) 和属性 (Attribute) 的属性 (Property)。 使用 Visual Studio 的开发人员可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]来映射继承层次结构。 请参阅[如何：使用 O/R 设计器配置继承](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)。  
  
> [!NOTE]
>  子类中不需要具有特殊属性 (Attribute) 或属性 (Property)。 请特别注意，子类不具有 <xref:System.Data.Linq.Mapping.TableAttribute> 属性。  
  
### <a name="to-map-an-inheritance-hierarchy"></a>映射继承层次结构  
  
1.  向根类添加 <xref:System.Data.Linq.Mapping.TableAttribute> 属性。  
  
2.  为层次结构中的每个类添加 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性，同样是添加到根类中。  
  
3.  为每个 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性 (Attribute)，定义一个 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 属性 (Property)。  
  
     此属性 (Property) 保存一个值，该值显示在数据库表的 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 列中，用来指示该行数据所属的类或子类。  
  
4.  为每个 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性 (Attribute)，也添加一个 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> 属性 (Property)。  
  
     此属性 (Property) 保存一个值，此值指定键值所表示的类或子类。  
  
5.  仅在其中一个 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性 (Attribute) 上，添加一个 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> 属性 (Property)。  
  
     此属性用于指定*回退*的映射，在数据库表中的鉴别器值不匹配任何<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>在继承映射中的值。  
  
6.  为 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 属性 (Attribute) 添加一个 <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性 (Property)。  
  
     此属性 (Property) 表示这是保存 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 值的列。  
  
## <a name="example"></a>示例  
  
> [!NOTE]
>  如果使用的 Visual Studio，则可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]配置继承。 请参阅[如何：使用 O/R 设计器配置继承](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 在下面的代码示例中，`Vehicle` 定义为根类，并且已执行前面的步骤来说明 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 的层次结构。  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>请参阅

- [层次结构支持](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)
- [如何：通过使用代码编辑器自定义实体类](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
