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
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="21a9d-103">如何：向 DataGrid 控件中添加行详细信息</span><span class="sxs-lookup"><span data-stu-id="21a9d-103">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="21a9d-104">使用控件时 <xref:System.Windows.Controls.DataGrid> ，可以通过添加行详细信息部分来自定义数据演示。</span><span class="sxs-lookup"><span data-stu-id="21a9d-104">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="21a9d-105">通过添加行详细信息部分，可以对模板中的某些数据进行分组（可选择可见或折叠）。</span><span class="sxs-lookup"><span data-stu-id="21a9d-105">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="21a9d-106">例如，您可以将行详细信息添加到 <xref:System.Windows.Controls.DataGrid> 中，后者仅为中的每行提供数据的摘要 <xref:System.Windows.Controls.DataGrid> ，但当用户选择行时将显示更多数据字段。</span><span class="sxs-lookup"><span data-stu-id="21a9d-106">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="21a9d-107">您可以在属性中为行详细信息部分定义模板 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 。</span><span class="sxs-lookup"><span data-stu-id="21a9d-107">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="21a9d-108">下图显示行详细信息部分的示例。</span><span class="sxs-lookup"><span data-stu-id="21a9d-108">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="21a9d-109">![与行详细信息一起显示的 DataGrid](./media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="21a9d-109">![DataGrid shown with row details](./media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="21a9d-110">将行详细信息模板定义为内联 XAML 或资源。</span><span class="sxs-lookup"><span data-stu-id="21a9d-110">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="21a9d-111">下面的过程演示了这两种方法。</span><span class="sxs-lookup"><span data-stu-id="21a9d-111">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="21a9d-112">作为资源添加的数据模板可在整个项目中使用，而无需重新创建模板。</span><span class="sxs-lookup"><span data-stu-id="21a9d-112">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="21a9d-113">添加为内联 XAML 的数据模板只能从定义它的控件进行访问。</span><span class="sxs-lookup"><span data-stu-id="21a9d-113">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="21a9d-114">使用内联 XAML 显示行详细信息</span><span class="sxs-lookup"><span data-stu-id="21a9d-114">To display row details by using inline XAML</span></span>  
  
1. <span data-ttu-id="21a9d-115">创建一个 <xref:System.Windows.Controls.DataGrid> 显示数据源中的数据的。</span><span class="sxs-lookup"><span data-stu-id="21a9d-115">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="21a9d-116">在 <xref:System.Windows.Controls.DataGrid> 元素内，添加一个 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 元素。</span><span class="sxs-lookup"><span data-stu-id="21a9d-116">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3. <span data-ttu-id="21a9d-117">创建一个 <xref:System.Windows.DataTemplate> ，用于定义行详细信息部分的外观。</span><span class="sxs-lookup"><span data-stu-id="21a9d-117">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="21a9d-118">下面的 XAML 演示了 <xref:System.Windows.Controls.DataGrid> 和如何定义 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 内联。</span><span class="sxs-lookup"><span data-stu-id="21a9d-118">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="21a9d-119">在 <xref:System.Windows.Controls.DataGrid> 每行中显示三个值，在选择行时显示另外三个值。</span><span class="sxs-lookup"><span data-stu-id="21a9d-119">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="21a9d-120">下面的代码演示了用于选择中显示的数据的查询 <xref:System.Windows.Controls.DataGrid> 。</span><span class="sxs-lookup"><span data-stu-id="21a9d-120">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="21a9d-121">在此示例中，查询从包含客户信息的实体中选择数据。</span><span class="sxs-lookup"><span data-stu-id="21a9d-121">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="21a9d-122">使用资源显示行详细信息</span><span class="sxs-lookup"><span data-stu-id="21a9d-122">To display row details by using a resource</span></span>  
  
1. <span data-ttu-id="21a9d-123">创建一个 <xref:System.Windows.Controls.DataGrid> 显示数据源中的数据的。</span><span class="sxs-lookup"><span data-stu-id="21a9d-123">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="21a9d-124">向 <xref:System.Windows.FrameworkElement.Resources%2A> 根元素（例如控件或控件）添加元素 <xref:System.Windows.Window> <xref:System.Windows.Controls.Page> ，或将 <xref:System.Windows.Application.Resources%2A> 元素添加到 <xref:System.Windows.Application> app.xaml （或应用程序 .xaml）文件中的类。</span><span class="sxs-lookup"><span data-stu-id="21a9d-124">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3. <span data-ttu-id="21a9d-125">在 resources 元素中，创建一个 <xref:System.Windows.DataTemplate> ，用于定义行详细信息部分的外观。</span><span class="sxs-lookup"><span data-stu-id="21a9d-125">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="21a9d-126">以下 XAML 显示了 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 在类中定义的 <xref:System.Windows.Application> 。</span><span class="sxs-lookup"><span data-stu-id="21a9d-126">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. <span data-ttu-id="21a9d-127">在上 <xref:System.Windows.DataTemplate> ，将[x：Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)设置为唯一标识数据模板的值。</span><span class="sxs-lookup"><span data-stu-id="21a9d-127">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5. <span data-ttu-id="21a9d-128">在 <xref:System.Windows.Controls.DataGrid> 元素中，将 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 属性设置为在前面的步骤中定义的资源。</span><span class="sxs-lookup"><span data-stu-id="21a9d-128">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="21a9d-129">将资源指定为静态资源。</span><span class="sxs-lookup"><span data-stu-id="21a9d-129">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="21a9d-130">下面的 XAML 演示了 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 如何将属性设置为上一示例中的资源。</span><span class="sxs-lookup"><span data-stu-id="21a9d-130">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="21a9d-131">设置可见性并防止水平滚动行详细信息</span><span class="sxs-lookup"><span data-stu-id="21a9d-131">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1. <span data-ttu-id="21a9d-132">如果需要，请将 <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> 属性设置为 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> 值。</span><span class="sxs-lookup"><span data-stu-id="21a9d-132">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="21a9d-133">默认情况下，该值设置为 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>。</span><span class="sxs-lookup"><span data-stu-id="21a9d-133">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="21a9d-134">您可以将其设置为， <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> 以显示所有行的详细信息或 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> 隐藏所有行的详细信息。</span><span class="sxs-lookup"><span data-stu-id="21a9d-134">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2. <span data-ttu-id="21a9d-135">如果需要，请将 <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> 属性设置为， `true` 以防止行详细信息部分水平滚动。</span><span class="sxs-lookup"><span data-stu-id="21a9d-135">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
