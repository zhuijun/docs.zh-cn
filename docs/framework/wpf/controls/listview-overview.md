---
title: ListView 概述
description: 了解 Windows Presentation Foundation ListView 控件，该控件提供基础结构以显示不同布局或视图中的数据项。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 419c6216f0af696ec71e7607c79c2db637caa785
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164558"
---
# <a name="listview-overview"></a><span data-ttu-id="533c9-103">ListView 概述</span><span class="sxs-lookup"><span data-stu-id="533c9-103">ListView Overview</span></span>
<span data-ttu-id="533c9-104"><xref:System.Windows.Controls.ListView>控件提供基础结构，以显示不同布局或视图中的一组数据项。</span><span class="sxs-lookup"><span data-stu-id="533c9-104">The <xref:System.Windows.Controls.ListView> control provides the infrastructure to display a set of data items in different layouts or views.</span></span> <span data-ttu-id="533c9-105">例如，用户可能需要在表格中显示数据项，并同时对表格的列进行排序。</span><span class="sxs-lookup"><span data-stu-id="533c9-105">For example, a user may want to display data items in a table and also to sort its columns.</span></span>  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a><span data-ttu-id="533c9-106">什么是 ListView？</span><span class="sxs-lookup"><span data-stu-id="533c9-106">What Is a ListView?</span></span>  
 <span data-ttu-id="533c9-107"><xref:System.Windows.Controls.ListView>控件是 <xref:System.Windows.Controls.ItemsControl> 从派生的 <xref:System.Windows.Controls.ListBox> 。</span><span class="sxs-lookup"><span data-stu-id="533c9-107">The <xref:System.Windows.Controls.ListView> control is an <xref:System.Windows.Controls.ItemsControl> that is derived from <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="533c9-108">通常，其项是数据集合的成员，并表示为 <xref:System.Windows.Controls.ListViewItem> 对象。</span><span class="sxs-lookup"><span data-stu-id="533c9-108">Typically, its items are members of a data collection and are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="533c9-109"><xref:System.Windows.Controls.ListViewItem>是一个 <xref:System.Windows.Controls.ContentControl> ，只能包含一个子元素。</span><span class="sxs-lookup"><span data-stu-id="533c9-109">A <xref:System.Windows.Controls.ListViewItem> is a <xref:System.Windows.Controls.ContentControl> and can contain only a single child element.</span></span> <span data-ttu-id="533c9-110">但是，该子元素可以是任何视觉元素。</span><span class="sxs-lookup"><span data-stu-id="533c9-110">However, that child element can be any visual element.</span></span>  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a><span data-ttu-id="533c9-111">为 ListView 定义视图模式</span><span class="sxs-lookup"><span data-stu-id="533c9-111">Defining a View Mode for a ListView</span></span>  
 <span data-ttu-id="533c9-112">若要为控件的内容指定视图模式 <xref:System.Windows.Controls.ListView> ，请设置 <xref:System.Windows.Controls.ListView.View%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="533c9-112">To specify a view mode for the content of a <xref:System.Windows.Controls.ListView> control, you set the <xref:System.Windows.Controls.ListView.View%2A> property.</span></span> <span data-ttu-id="533c9-113">提供的一个视图模式 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 为 <xref:System.Windows.Controls.GridView> ，它在具有可自定义列的表中显示数据项的集合。</span><span class="sxs-lookup"><span data-stu-id="533c9-113">One view mode that [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides is <xref:System.Windows.Controls.GridView>, which displays a collection of data items in a table that has customizable columns.</span></span>  
  
 <span data-ttu-id="533c9-114">下面的示例演示如何为 <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView> 显示雇员信息的控件定义。</span><span class="sxs-lookup"><span data-stu-id="533c9-114">The following example shows how to define a <xref:System.Windows.Controls.GridView> for a <xref:System.Windows.Controls.ListView> control that displays employee information.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="533c9-115">下图演示上一个示例的数据显示方式。</span><span class="sxs-lookup"><span data-stu-id="533c9-115">The following illustration shows how the data appears for the previous example.</span></span>  
  
 ![显示带有 GridView 输出的 ListView 的屏幕截图。](./media/gridview-overview/listview-gridview-output.jpg)  
  
 <span data-ttu-id="533c9-117">您可以通过定义从类继承的类来创建自定义视图模式 <xref:System.Windows.Controls.ViewBase> 。</span><span class="sxs-lookup"><span data-stu-id="533c9-117">You can create a custom view mode by defining a class that inherits from the <xref:System.Windows.Controls.ViewBase> class.</span></span> <span data-ttu-id="533c9-118"><xref:System.Windows.Controls.ViewBase>类提供创建自定义视图所需的基础结构。</span><span class="sxs-lookup"><span data-stu-id="533c9-118">The <xref:System.Windows.Controls.ViewBase> class provides the infrastructure that you need to create a custom view.</span></span> <span data-ttu-id="533c9-119">有关如何创建自定义视图的详细信息，请参阅[为 ListView 创建自定义视图模式](how-to-create-a-custom-view-mode-for-a-listview.md)。</span><span class="sxs-lookup"><span data-stu-id="533c9-119">For more information about how to create a custom view, see [Create a Custom View Mode for a ListView](how-to-create-a-custom-view-mode-for-a-listview.md).</span></span>  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a><span data-ttu-id="533c9-120">将数据绑定到 ListView</span><span class="sxs-lookup"><span data-stu-id="533c9-120">Binding Data to a ListView</span></span>  
 <span data-ttu-id="533c9-121">使用 <xref:System.Windows.Controls.ItemsControl.Items%2A> 和 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 属性为控件指定项 <xref:System.Windows.Controls.ListView> 。</span><span class="sxs-lookup"><span data-stu-id="533c9-121">Use the <xref:System.Windows.Controls.ItemsControl.Items%2A> and <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> properties to specify items for a <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="533c9-122">下面的示例将 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 属性设置为一个被调用的数据集合 `EmployeeInfoDataSource` 。</span><span class="sxs-lookup"><span data-stu-id="533c9-122">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to a data collection that is called `EmployeeInfoDataSource`.</span></span>  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 <span data-ttu-id="533c9-123">在中 <xref:System.Windows.Controls.GridView> ， <xref:System.Windows.Controls.GridViewColumn> 对象将绑定到指定的数据字段。</span><span class="sxs-lookup"><span data-stu-id="533c9-123">In a <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn> objects bind to specified data fields.</span></span> <span data-ttu-id="533c9-124">下面的示例 <xref:System.Windows.Controls.GridViewColumn> 通过为属性指定，将对象绑定到数据字段 <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 。</span><span class="sxs-lookup"><span data-stu-id="533c9-124">The following example binds a <xref:System.Windows.Controls.GridViewColumn> object to a data field by specifying a <xref:System.Windows.Data.Binding> for the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property.</span></span>  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 <span data-ttu-id="533c9-125">您还可以指定 <xref:System.Windows.Data.Binding> 作为 <xref:System.Windows.DataTemplate> 定义的一部分，您可以使用该定义来对列中的单元格进行样式。</span><span class="sxs-lookup"><span data-stu-id="533c9-125">You can also specify a <xref:System.Windows.Data.Binding> as part of a <xref:System.Windows.DataTemplate> definition that you use to style the cells in a column.</span></span> <span data-ttu-id="533c9-126">在下面的示例中， <xref:System.Windows.DataTemplate> 用来标识的将 <xref:System.Windows.ResourceKey> 为设置 <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.GridViewColumn> 。</span><span class="sxs-lookup"><span data-stu-id="533c9-126">In the following example, the <xref:System.Windows.DataTemplate> that is identified with a <xref:System.Windows.ResourceKey> sets the <xref:System.Windows.Data.Binding> for a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="533c9-127">请注意，此示例未定义， <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 因为这样做会重写指定的绑定 <xref:System.Windows.DataTemplate> 。</span><span class="sxs-lookup"><span data-stu-id="533c9-127">Note that this example does not define the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> because doing so overrides the binding that is specified by <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a><span data-ttu-id="533c9-128">为实现 GridView 的 ListView 设置样式</span><span class="sxs-lookup"><span data-stu-id="533c9-128">Styling a ListView That Implements a GridView</span></span>  
 <span data-ttu-id="533c9-129"><xref:System.Windows.Controls.ListView>控件包含 <xref:System.Windows.Controls.ListViewItem> 对象，这些对象表示显示的数据项。</span><span class="sxs-lookup"><span data-stu-id="533c9-129">The <xref:System.Windows.Controls.ListView> control contains <xref:System.Windows.Controls.ListViewItem> objects, which represent the data items that are displayed.</span></span> <span data-ttu-id="533c9-130">可使用以下属性定义数据项的内容和样式：</span><span class="sxs-lookup"><span data-stu-id="533c9-130">You can use the following properties to define the content and style of data items:</span></span>  
  
- <span data-ttu-id="533c9-131">在 <xref:System.Windows.Controls.ListView> 控件上，使用 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 、 <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> 和 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="533c9-131">On the <xref:System.Windows.Controls.ListView> control, use the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>, and <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> properties.</span></span>  
  
- <span data-ttu-id="533c9-132">在 <xref:System.Windows.Controls.ListViewItem> 控件上，使用 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 和 <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="533c9-132">On the <xref:System.Windows.Controls.ListViewItem> control, use the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> and <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> properties.</span></span>  
  
 <span data-ttu-id="533c9-133">若要避免中的单元格之间的对齐问题 <xref:System.Windows.Controls.GridView> ，请不要使用 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 设置属性或添加影响中项的宽度的内容 <xref:System.Windows.Controls.ListView> 。</span><span class="sxs-lookup"><span data-stu-id="533c9-133">To avoid alignment issues between cells in a <xref:System.Windows.Controls.GridView>, do not use the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> to set properties or add content that affects the width of an item in a <xref:System.Windows.Controls.ListView>.</span></span> <span data-ttu-id="533c9-134">例如，在中设置属性时，可能会出现对齐问题 <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="533c9-134">For example, an alignment issue can occur when you set the <xref:System.Windows.FrameworkElement.Margin%2A> property in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>.</span></span> <span data-ttu-id="533c9-135">若要指定属性或定义影响中的项的宽度的内容 <xref:System.Windows.Controls.GridView> ，请使用 <xref:System.Windows.Controls.GridView> 类及其相关类的属性，如 <xref:System.Windows.Controls.GridViewColumn> 。</span><span class="sxs-lookup"><span data-stu-id="533c9-135">To specify properties or define content that affects the width of items in a <xref:System.Windows.Controls.GridView>, use the properties of the <xref:System.Windows.Controls.GridView> class and its related classes, such as <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 <span data-ttu-id="533c9-136">有关如何使用 <xref:System.Windows.Controls.GridView> 及其支持类的详细信息，请参阅[GridView 概述](gridview-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="533c9-136">For more information about how to use <xref:System.Windows.Controls.GridView> and its supporting classes, see [GridView Overview](gridview-overview.md).</span></span>  
  
 <span data-ttu-id="533c9-137">如果 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 为 <xref:System.Windows.Controls.ListView> 控件定义，并定义 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> ，则必须在样式中包含，以便 <xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 能够正常工作。</span><span class="sxs-lookup"><span data-stu-id="533c9-137">If you define an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for a <xref:System.Windows.Controls.ListView> control and also define an <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, you must include a <xref:System.Windows.Controls.ContentPresenter> in the style in order for the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> to work correctly.</span></span>  
  
 <span data-ttu-id="533c9-138">不要将 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> 和 <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> 属性用于 <xref:System.Windows.Controls.ListView> 通过使用显示的内容 <xref:System.Windows.Controls.GridView> 。</span><span class="sxs-lookup"><span data-stu-id="533c9-138">Do not use the <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> and <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> properties for <xref:System.Windows.Controls.ListView> content that is displayed by using a <xref:System.Windows.Controls.GridView>.</span></span> <span data-ttu-id="533c9-139">若要指定的列中的内容对齐方式 <xref:System.Windows.Controls.GridView> ，请定义 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> 。</span><span class="sxs-lookup"><span data-stu-id="533c9-139">To specify the alignment of content in a column of a <xref:System.Windows.Controls.GridView>, define a <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>.</span></span>  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a><span data-ttu-id="533c9-140">共享同一视图模式</span><span class="sxs-lookup"><span data-stu-id="533c9-140">Sharing the Same View Mode</span></span>  
 <span data-ttu-id="533c9-141">两个 <xref:System.Windows.Controls.ListView> 控件不能同时共享同一个视图模式。</span><span class="sxs-lookup"><span data-stu-id="533c9-141">Two <xref:System.Windows.Controls.ListView> controls cannot share the same view mode at the same time.</span></span> <span data-ttu-id="533c9-142">如果尝试使用与多个控件相同的视图模式，则 <xref:System.Windows.Controls.ListView> 会出现异常。</span><span class="sxs-lookup"><span data-stu-id="533c9-142">If you try to use the same view mode with more than one <xref:System.Windows.Controls.ListView> control, an exception occurs.</span></span>  
  
 <span data-ttu-id="533c9-143">若要指定可以同时使用多个视图模式 <xref:System.Windows.Controls.ListView> ，请使用模板或样式。</span><span class="sxs-lookup"><span data-stu-id="533c9-143">To specify a view mode that can be simultaneously used by more than one <xref:System.Windows.Controls.ListView>, use templates or styles.</span></span>
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a><span data-ttu-id="533c9-144">创建自定义视图模式</span><span class="sxs-lookup"><span data-stu-id="533c9-144">Creating a Custom View Mode</span></span>  
 <span data-ttu-id="533c9-145">自定义的视图（如） <xref:System.Windows.Controls.GridView> 派生自 <xref:System.Windows.Controls.ViewBase> 抽象类，该类提供了用于显示作为对象表示的数据项的工具 <xref:System.Windows.Controls.ListViewItem> 。</span><span class="sxs-lookup"><span data-stu-id="533c9-145">Customized views like <xref:System.Windows.Controls.GridView> are derived from the <xref:System.Windows.Controls.ViewBase> abstract class, which provides the tools to display data items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="533c9-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="533c9-146">See also</span></span>

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="533c9-147">GridView 概述</span><span class="sxs-lookup"><span data-stu-id="533c9-147">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="533c9-148">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="533c9-148">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="533c9-149">控制</span><span class="sxs-lookup"><span data-stu-id="533c9-149">Controls</span></span>](../advanced/optimizing-performance-controls.md)
