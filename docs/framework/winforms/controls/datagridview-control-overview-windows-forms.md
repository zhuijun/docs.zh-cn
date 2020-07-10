---
title: DataGridView 控件概述
description: 了解如何使用 Windows 窗体 DataGridView 控件显示和编辑多种不同类型的数据源中的表格数据。
ms.date: 03/30/2017
f1_keywords:
- DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
ms.openlocfilehash: 3e68f536853081453f6ba746d342bc016bc8ca17
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174609"
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="a6e5e-103">DataGridView 控件概述（Windows 窗体）</span><span class="sxs-lookup"><span data-stu-id="a6e5e-103">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="a6e5e-104"><xref:System.Windows.Forms.DataGridView> 控件取代了 <xref:System.Windows.Forms.DataGrid> 控件并添加了功能；但是，可以选择保留 <xref:System.Windows.Forms.DataGrid> 控件以实现向后兼容并供将来使用。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-104">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="a6e5e-105">有关详细信息，请参阅 [Windows 窗体 DataGridView 控件与 DataGrid 控件之间的区别](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-105">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="a6e5e-106">借助 <xref:System.Windows.Forms.DataGridView> 控件，可以显示和编辑多种不同类型的数据源中的表格数据。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-106">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="a6e5e-107">将数据绑定到 <xref:System.Windows.Forms.DataGridView> 控件非常简单直观，在许多情况下，只需设置 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 属性即可。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-107">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="a6e5e-108">绑定到包含多个列表或表的数据源时，请将 <xref:System.Windows.Forms.DataGridView.DataMember%2A> 属性设置为指定要绑定到的列表或表的字符串。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-108">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="a6e5e-109">该 <xref:System.Windows.Forms.DataGridView> 控件支持标准 Windows 窗体数据绑定模型，因此它将绑定到以下列表中所述的类的实例：</span><span class="sxs-lookup"><span data-stu-id="a6e5e-109">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
- <span data-ttu-id="a6e5e-110">实现接口的任何类 <xref:System.Collections.IList> ，包括一维数组。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-110">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
- <span data-ttu-id="a6e5e-111">实现接口的任何类 <xref:System.ComponentModel.IListSource> ，如 <xref:System.Data.DataTable> 和 <xref:System.Data.DataSet> 类。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-111">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
- <span data-ttu-id="a6e5e-112">实现接口的任何类 <xref:System.ComponentModel.IBindingList> ，如 <xref:System.ComponentModel.BindingList%601> 类。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-112">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
- <span data-ttu-id="a6e5e-113">实现接口的任何类 <xref:System.ComponentModel.IBindingListView> ，如 <xref:System.Windows.Forms.BindingSource> 类。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-113">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="a6e5e-114"><xref:System.Windows.Forms.DataGridView> <xref:System.ComponentModel.ICustomTypeDescriptor> 如果在返回的对象上实现，则控件支持将数据绑定到由这些接口返回的对象的公共属性或由接口返回的 properties 集合。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-114">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="a6e5e-115">通常，你将绑定到一个 <xref:System.Windows.Forms.BindingSource> 组件，并将该 <xref:System.Windows.Forms.BindingSource> 组件绑定到另一个数据源，或者使用业务对象来填充它。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-115">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="a6e5e-116"><xref:System.Windows.Forms.BindingSource>组件是首选数据源，因为它可以绑定到各种数据源，并可自动解决许多数据绑定问题。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-116">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="a6e5e-117">有关详细信息，请参阅[BindingSource Component](bindingsource-component.md)。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-117">For more information, see [BindingSource Component](bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="a6e5e-118">该 <xref:System.Windows.Forms.DataGridView> 控件还可以用于*未绑定*模式，无基础数据存储区。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-118">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="a6e5e-119">有关使用未绑定控件的代码示例 <xref:System.Windows.Forms.DataGridView> ，请参阅[演练：创建未绑定的 Windows 窗体 DataGridView 控件](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-119">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="a6e5e-120"><xref:System.Windows.Forms.DataGridView>控件高度可配置且可扩展，并且提供了许多属性、方法和事件来自定义其外观和行为。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-120">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="a6e5e-121">如果希望 Windows 窗体应用程序显示表格数据，请考虑在 <xref:System.Windows.Forms.DataGridView> 其他人之前使用控件 (例如， <xref:System.Windows.Forms.DataGrid>) 。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-121">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="a6e5e-122">如果要显示只读值的小网格，或者如果你要使用户能够编辑包含数百万条记录的表，则该 <xref:System.Windows.Forms.DataGridView> 控件将为你提供一个易于编程的、内存有效的解决方案。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-122">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6e5e-123">本节内容</span><span class="sxs-lookup"><span data-stu-id="a6e5e-123">In This Section</span></span>  
 [<span data-ttu-id="a6e5e-124">DataGridView 控件技术摘要</span><span class="sxs-lookup"><span data-stu-id="a6e5e-124">DataGridView Control Technology Summary</span></span>](datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="a6e5e-125">汇总了 <xref:System.Windows.Forms.DataGridView> 控件概念和相关类的用法。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-125">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="a6e5e-126">DataGridView 控件体系结构</span><span class="sxs-lookup"><span data-stu-id="a6e5e-126">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="a6e5e-127">描述控件的体系结构 <xref:System.Windows.Forms.DataGridView> ，并说明其类型层次结构和继承结构。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-127">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="a6e5e-128">DataGridView 控件方案</span><span class="sxs-lookup"><span data-stu-id="a6e5e-128">DataGridView Control Scenarios</span></span>](datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="a6e5e-129">描述使用控件的最常见方案 <xref:System.Windows.Forms.DataGridView> 。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-129">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="a6e5e-130">DataGridView 控件代码目录</span><span class="sxs-lookup"><span data-stu-id="a6e5e-130">DataGridView Control Code Directory</span></span>](datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="a6e5e-131">提供有关各种任务的文档中的代码示例的链接 <xref:System.Windows.Forms.DataGridView> 。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-131">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="a6e5e-132">这些示例按任务类型进行分类。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-132">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a6e5e-133">相关章节</span><span class="sxs-lookup"><span data-stu-id="a6e5e-133">Related Sections</span></span>  
 [<span data-ttu-id="a6e5e-134">Windows 窗体 DataGridView 控件中的列类型</span><span class="sxs-lookup"><span data-stu-id="a6e5e-134">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a6e5e-135">讨论 <xref:System.Windows.Forms.DataGridView> 用于显示信息以及允许用户修改或添加信息的 Windows 窗体控件中的列类型。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-135">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="a6e5e-136">在 Windows 窗体 DataGridView 控件中显示数据</span><span class="sxs-lookup"><span data-stu-id="a6e5e-136">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a6e5e-137">提供一些主题，描述如何手动或从外部数据源向控件填充数据。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-137">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="a6e5e-138">自定义 Windows 窗体 DataGridView 控件</span><span class="sxs-lookup"><span data-stu-id="a6e5e-138">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a6e5e-139">提供一些主题，介绍自定义绘制 <xref:System.Windows.Forms.DataGridView> 单元格和行，以及创建派生的单元、列和行类型。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-139">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="a6e5e-140">Windows 窗体 DataGridView 控件中的性能优化</span><span class="sxs-lookup"><span data-stu-id="a6e5e-140">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a6e5e-141">提供一些主题，介绍如何在使用大量数据时，有效地使用控件以避免性能问题。</span><span class="sxs-lookup"><span data-stu-id="a6e5e-141">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e5e-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6e5e-142">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="a6e5e-143">DataGridView 控件</span><span class="sxs-lookup"><span data-stu-id="a6e5e-143">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="a6e5e-144">Windows 窗体 DataGridView 控件中的默认功能</span><span class="sxs-lookup"><span data-stu-id="a6e5e-144">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a6e5e-145">Windows 窗体 DataGridView 控件中的默认键盘和鼠标处理</span><span class="sxs-lookup"><span data-stu-id="a6e5e-145">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
