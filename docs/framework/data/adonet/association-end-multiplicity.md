---
title: 关联端重数
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 59eed56204543adf405cfc7c71a49697a9e18374
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135026"
---
# <a name="association-end-multiplicity"></a>关联端重数
*关联端重*定义的数字[实体类型](../../../../docs/framework/data/adonet/entity-type.md)一端可以存在的实例[关联](../../../../docs/framework/data/adonet/association-type.md)。  
  
 关联端重数可以具有下列值之一：  
  
-   一 (1):指示在关联端存在的一个实体类型实例。  
  
-   零或一 (0..1):指示在关联端存在零个或一个实体类型实例。  
  
-   很多 (\*):指示在关联端存在零行、 一行或多个实体类型实例。  
  
 关联的特征通常由关联端重数表示。 例如，如果关联端有一 （1） 和许多的重数 (\*)，该关联称为一个对多关联。 在下面的示例中，`PublishedBy` 关联是一个一对多关联（一个出版商可以出版很多书，而一本书只能由一个出版商出版）。 `WrittenBy` 关联是一个多对多关联（一本书可以有多位作者，而一位作者可以著有多本书）。  
  
## <a name="example"></a>示例  
 下图显示了一个具有两个关联的概念模型：`PublishedBy` 和 `WrittenBy`。 `PublishedBy` 关联的关联端是 `Book` 和 `Publisher` 实体类型。 多重性`Publisher`最终为一 (1) 和重数`Book`最终为多个 (\*)。  
  
 ![具有三个实体类型的示例模型](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 ADO.NET 实体框架使用称为概念性架构定义语言的特定于域的语言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 来定义概念模型。 下面的 CSDL 定义了上图中显示的 `PublishedBy` 关联：  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>请参阅

- [实体数据模型关键概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [实体数据模型](../../../../docs/framework/data/adonet/entity-data-model.md)
