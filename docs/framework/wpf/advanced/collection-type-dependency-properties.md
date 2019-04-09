---
title: 集合类型依赖项属性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], dependency
- properties [WPF], collection-type
- dependency properties [WPF]
- collection-type properties [WPF]
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
ms.openlocfilehash: 9ce0b70bfdd70b47857167ff14e62ed2bbda569d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077454"
---
# <a name="collection-type-dependency-properties"></a>集合类型依赖项属性
本主题就如何实现属性类型为集合类型的依赖属性提供相应指导和建议模式。  

<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>实现集合类型依赖属性  
 依赖属性的一般情况下，遵循的实现模式是您定义[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]属性的包装器，该属性由<xref:System.Windows.DependencyProperty>标识符而不是字段或其他构造。 实现集合类型属性时也应按照此相同模式。 但是，集合类型属性带来了一些复杂性的模式时该集合内包含的类型本身<xref:System.Windows.DependencyObject>或<xref:System.Windows.Freezable>派生的类。  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>不使用默认值初始化集合  
 创建依赖属性时，不要将属性默认值指定为初始字段值。 相反，应通过依赖属性元数据指定默认值。 如果属性为引用类型，则依赖属性元数据中指定的默认值不是每个实例分别的默认值，而是应用到类型的所有实例的默认值。 因此，对于类型的新创建实例，必须小心，不要将集合属性元数据定义的单个静态集合用作工作默认值。 相反，必须确保有意将集合值设置为唯一（实例）集合，作为类构造函数逻辑的一部分。 否则，你会创建一个不需要的单例类。  
  
 请看下面的示例。 示例的以下部分显示类 `Aquarium` 的定义。 类定义集合类型依赖属性`AquariumObjects`，它使用泛型<xref:System.Collections.Generic.List%601>类型具有<xref:System.Windows.FrameworkElement>类型约束。 在中<xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29>依赖属性元数据的调用会建立此默认值为一个新的泛型<xref:System.Collections.Generic.List%601>。  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 但是，如果仅如上所示保留代码，该单一列表默认值会对 `Aquarium` 的所有实例共享。 如果运行以下测试代码（用于演示如何实例化两个单独的 `Aquarium` 实例并向二者皆添加一个不同的 `Fish`），则其结果可能出乎意料：  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 每个集合具有两个计数，而不是一个！ 这是因为，每个 `Aquarium` 将其 `Fish` 添加到默认值集合，此默认值集合因元数据中单个构造函数调用而产生，因此会在所有实例之间共享。 而你全然不希望出现这种情况。  
  
 为纠正此问题，必须将集合依赖属性值重置为唯一实例，作为类构造函数调用的一部分。 由于属性是只读的依赖项属性，因此使用<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29>方法以设置它，使用<xref:System.Windows.DependencyPropertyKey>，才可访问的类中。  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 现在，如果再次运行此相同测试代码，则每个 `Aquarium` 会仅支持自己的唯一集合，这样的结果更符合预期。  
  
 如果选择集合属性为读写，则此模式会稍有变化。 在这种情况下，您可以从构造函数来执行初始化，仍会调用的非键签名调用公共集访问器<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29>内集包装器，使用的是公共<xref:System.Windows.DependencyProperty>标识符。  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>报告集合属性中的绑定值更改  
 本身为依赖属性的集合属性不会自动将更改报告给其子属性。 如果将绑定创建到集合，这可阻止绑定报告更改，从而使某些数据绑定方案无效。 但是，如果使用的集合类型<xref:System.Windows.FreezableCollection%601>作为集合类型，然后在集合中包含的元素的子属性更改会正常报告，并按预期方式工作的绑定。  
  
 若要启用依赖项对象集合中的子属性绑定，将集合属性创建为类型<xref:System.Windows.FreezableCollection%601>，任何对该集合的类型约束<xref:System.Windows.DependencyObject>派生的类。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.FreezableCollection%601>
- [XAML 及 WPF 的自定义类](xaml-and-custom-classes-for-wpf.md)
- [数据绑定概述](../data/data-binding-overview.md)
- [依赖项属性概述](dependency-properties-overview.md)
- [自定义依赖项属性](custom-dependency-properties.md)
- [依赖项属性元数据](dependency-property-metadata.md)
