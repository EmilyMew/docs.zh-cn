---
title: BindingSource 组件
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
ms.openlocfilehash: 54639edb512a8bc6c5909282d5e4c210439e2a6e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717591"
---
# <a name="bindingsource-component"></a>BindingSource 组件
封装数据源以绑定到控件。  
  
 <xref:System.Windows.Forms.BindingSource> 组件有两个用途。 首先，将一个窗体的控件绑定到数据时，该组件会提供一个间接层。 这是通过将 <xref:System.Windows.Forms.BindingSource> 组件与你的数据源绑定，然后将窗体上的控件绑定到 <xref:System.Windows.Forms.BindingSource> 组件完成的。 与数据的所有进一步交互（包括导航、排序、筛选和更新）都是通过调用 <xref:System.Windows.Forms.BindingSource> 组件来完成的。  
  
 第二，<xref:System.Windows.Forms.BindingSource> 组件可以充当强类型的数据源。 通过使用 <xref:System.Windows.Forms.BindingSource.Add%2A> 方法向 <xref:System.Windows.Forms.BindingSource> 组件添加一个类型来创建该类型的列表。  
  
## <a name="in-this-section"></a>本节内容  
 [BindingSource 组件概述](bindingsource-component-overview.md)  
 介绍 <xref:System.Windows.Forms.BindingSource> 组件的一般概念，这些概念使你能将数据源绑定到控件。  
  
 [如何：将 Windows 窗体控件绑定到 DBNull 数据库值](how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 演示如何使用 <xref:System.Windows.Forms.BindingSource> 组件处理数据源的 <xref:System.DBNull>值。  
  
 [如何：排序和筛选 ADO.NET 数据与 Windows 窗体 BindingSource 组件](sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 演示如何使用 <xref:System.Windows.Forms.BindingSource> 组件将排序和筛选应用到显示的数据上。  
  
 [如何：将绑定到使用 Windows 窗体 BindingSource 的 Web 服务](how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 演示如何使用 <xref:System.Windows.Forms.BindingSource> 组件绑定到 Web 服务。  
  
 [如何：处理错误和因数据绑定而发生的异常](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 演示如何使用 <xref:System.Windows.Forms.BindingSource> 组件妥善处理数据在绑定操作中发生的错误。  
  
 [如何：将 Windows 窗体控件绑定到类型](how-to-bind-a-windows-forms-control-to-a-type.md)  
 演示如何使用 <xref:System.Windows.Forms.BindingSource> 组件绑定到一种类型。  
  
 [如何：Windows 窗体控件绑定到 Factory 对象](how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 演示如何使用 <xref:System.Windows.Forms.BindingSource> 组件绑定到 Factory 对象或方法。  
  
 [如何：使用自定义项添加 Windows 窗体 BindingSource](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 演示如何使用 <xref:System.Windows.Forms.BindingSource> 组件创建新项并将它们添加到数据源。  
  
 [如何：使用 BindingSource ResetItem 方法引发更改通知](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 演示如何使用 <xref:System.Windows.Forms.BindingSource> 组件引发对不支持更改通知的数据源的更改通知事件。  
  
 [如何：使用 BindingSource 和 INotifyPropertyChanged 接口引发更改通知](raise-change-notifications--bindingsource.md)  
 演示如何将继承自 <xref:System.ComponentModel.INotifyPropertyChanged> 的类型用于 <xref:System.Windows.Forms.BindingSource> 控件。  
  
 [如何：反映在使用 BindingSource 的 Windows 窗体控件中的数据源更新](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 演示如何使用 <xref:System.Windows.Forms.BindingSource> 组件响应数据源中的更改。  
  
 [如何：使用 BindingSource 组件跨窗体共享绑定数据](how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 演示如何使用 <xref:System.Windows.Forms.BindingSource> 将多个窗体绑定到相同的数据源。  
  
## <a name="reference"></a>参考  
 <xref:System.Windows.Forms.BindingSource>  
 提供关于 <xref:System.Windows.Forms.BindingSource> 组件的参考文档。  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 提供关于 <xref:System.Windows.Forms.BindingNavigator> 控件的参考文档。  
  
## <a name="related-sections"></a>相关章节  
 [Windows 窗体数据绑定](../windows-forms-data-binding.md)  
 包含描述 Windows 窗体数据绑定体系结构的主题链接。  
  
 另请参阅[在 Visual Studio 中将控件绑定到数据](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)。
