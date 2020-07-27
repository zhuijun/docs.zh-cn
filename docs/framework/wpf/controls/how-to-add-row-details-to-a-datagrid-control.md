---
title: 如何：向 DataGrid 控件中添加行详细信息
description: 通过添加行详细信息部分来了解如何使用 Windows Presentation Foundation DataGrid 控件自定义数据演示。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 8fd6b07f454681a0eed70d7a6208cfcc426dc920
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164957"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>如何：向 DataGrid 控件中添加行详细信息
使用控件时 <xref:System.Windows.Controls.DataGrid> ，可以通过添加行详细信息部分来自定义数据演示。 通过添加行详细信息部分，可以对模板中的某些数据进行分组（可选择可见或折叠）。 例如，您可以将行详细信息添加到 <xref:System.Windows.Controls.DataGrid> 中，后者仅为中的每行提供数据的摘要 <xref:System.Windows.Controls.DataGrid> ，但当用户选择行时将显示更多数据字段。 您可以在属性中为行详细信息部分定义模板 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 。 下图显示行详细信息部分的示例。  
  
 ![与行详细信息一起显示的 DataGrid](./media/ndp-rowdetails.png "NDP_RowDetails")  
  
 将行详细信息模板定义为内联 XAML 或资源。 下面的过程演示了这两种方法。 作为资源添加的数据模板可在整个项目中使用，而无需重新创建模板。 添加为内联 XAML 的数据模板只能从定义它的控件进行访问。  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>使用内联 XAML 显示行详细信息  
  
1. 创建一个 <xref:System.Windows.Controls.DataGrid> 显示数据源中的数据的。  
  
2. 在 <xref:System.Windows.Controls.DataGrid> 元素内，添加一个 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 元素。  
  
3. 创建一个 <xref:System.Windows.DataTemplate> ，用于定义行详细信息部分的外观。  
  
     下面的 XAML 演示了 <xref:System.Windows.Controls.DataGrid> 和如何定义 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 内联。 在 <xref:System.Windows.Controls.DataGrid> 每行中显示三个值，在选择行时显示另外三个值。  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     下面的代码演示了用于选择中显示的数据的查询 <xref:System.Windows.Controls.DataGrid> 。 在此示例中，查询从包含客户信息的实体中选择数据。  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>使用资源显示行详细信息  
  
1. 创建一个 <xref:System.Windows.Controls.DataGrid> 显示数据源中的数据的。  
  
2. 向 <xref:System.Windows.FrameworkElement.Resources%2A> 根元素（例如控件或控件）添加元素 <xref:System.Windows.Window> <xref:System.Windows.Controls.Page> ，或将 <xref:System.Windows.Application.Resources%2A> 元素添加到 <xref:System.Windows.Application> app.xaml （或应用程序 .xaml）文件中的类。  
  
3. 在 resources 元素中，创建一个 <xref:System.Windows.DataTemplate> ，用于定义行详细信息部分的外观。  
  
     以下 XAML 显示了 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 在类中定义的 <xref:System.Windows.Application> 。  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. 在上 <xref:System.Windows.DataTemplate> ，将[x：Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)设置为唯一标识数据模板的值。  
  
5. 在 <xref:System.Windows.Controls.DataGrid> 元素中，将 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 属性设置为在前面的步骤中定义的资源。 将资源指定为静态资源。  
  
     下面的 XAML 演示了 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 如何将属性设置为上一示例中的资源。  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>设置可见性并防止水平滚动行详细信息  
  
1. 如果需要，请将 <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> 属性设置为 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> 值。  
  
     默认情况下，该值设置为 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>。 您可以将其设置为， <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> 以显示所有行的详细信息或 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> 隐藏所有行的详细信息。  
  
2. 如果需要，请将 <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> 属性设置为， `true` 以防止行详细信息部分水平滚动。
