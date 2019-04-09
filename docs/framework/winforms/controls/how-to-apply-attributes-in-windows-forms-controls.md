---
title: 如何：应用 Windows 窗体控件中的特性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: e86277c06e515b28bada3331cf4fd63e536319a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079586"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>如何：应用 Windows 窗体控件中的特性
若要开发的组件和控件的设计环境与正确交互，并在运行时正确执行，需要正确地将特性应用于类和成员。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何使用自定义控件上的多个属性。 控件演示简单的日志记录功能。 如果该控件绑定到数据源，则会显示发送中的数据源的值<xref:System.Windows.Forms.DataGridView>控件。 如果值超过指定的值`Threshold`属性，`ThresholdExceeded`引发事件。  
  
 `AttributesDemoControl`值与记录`LogEntry`类。 `LogEntry`类是一种模板类，这意味着它参数化的类型的记录。 例如，如果`AttributesDemoControl`是类型的日志记录值`float`，则每个`LogEntry`实例进行声明和使用，如下所示。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  因为`LogEntry`已参数化的任意类型，它必须使用反射来操作参数类型。 若要运行的参数类型的阈值功能`T`必须实现<xref:System.IComparable>接口。  
  
 承载的窗体`AttributesDemoControl`定期查询的性能计数器。 每个值中打包`LogEntry`适当类型的并且添加到窗体的<xref:System.Windows.Forms.BindingSource>。 `AttributesDemoControl`通过其数据绑定接收的值，并显示中的值<xref:System.Windows.Forms.DataGridView>控件。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 第一个代码示例是`AttributesDemoControl`实现。 第二个代码示例演示如何使用的窗体`AttributesDemoControl`。  
  
## <a name="class-level-attributes"></a>类级别属性  
 某些属性是在类级别应用。 下面的代码示例显示了通常应用于的 Windows 窗体控件的属性。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>TypeConverter 属性  
 <xref:System.ComponentModel.TypeConverterAttribute> 是常用的另一个类级别属性。 下面的代码示例显示了其在将成为`LogEntry`类。 此示例还演示一种实现<xref:System.ComponentModel.TypeConverter>有关`LogEntry`类型，名为`LogEntryTypeConverter`。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>成员级别的属性  
 在成员级别应用某些属性。 下面的代码示例显示通常应用于 Windows 窗体控件的属性的某些属性。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>AmbientValue 属性  
 下面的示例演示<xref:System.ComponentModel.AmbientValueAttribute>并且会显示支持与在设计环境交互的代码。 这种交互称为*环境*。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>数据绑定属性  
 下面的示例演示复杂数据绑定的实现。 在类级别<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>，显示以前，指定`DataSource`和`DataMember`用于数据绑定属性。 <xref:System.ComponentModel.AttributeProviderAttribute>指定为的类型`DataSource`属性将绑定。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>编译代码  
  
-   承载的窗体`AttributesDemoControl`需要引用`AttributesDemoControl`若要生成的程序集。  
  
## <a name="see-also"></a>请参阅

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [使用 .NET Framework 开发自定义 Windows 窗体控件](developing-custom-windows-forms-controls.md)
- [Windows 窗体控件中的特性](attributes-in-windows-forms-controls.md)
- [如何：序列化使用 DesignerSerializationVisibilityAttribute 标准类型的集合](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
