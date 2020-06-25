---
title: DataGridView 控件
description: 了解如何使用 `DataGridView` 控件显示少量数据的只读视图，或缩放数据以显示非常大的数据集的可编辑视图。
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- data grids [Windows Forms
- data [Windows Forms], displaying in tabular format
- grid controls [Windows Forms]
- datasets [Windows Forms], user interface
- Windows Forms, displaying data
- data presentation
- tabular data [Windows Forms], displaying on Windows Forms
- datasets [Windows Forms], displaying in DataGridView control
- DataGridView control [Windows Forms]
ms.assetid: dbee73f2-bba6-4874-9389-cd21d44309be
ms.openlocfilehash: f9a45e8be7975697ca5c0d019c6bc4119f562aea
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325890"
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="5e5ba-103">DataGridView 控件（Windows 窗体）</span><span class="sxs-lookup"><span data-stu-id="5e5ba-103">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="5e5ba-104">`DataGridView` 控件提供一种以表格格式显示数据的功能强大且灵活的方法。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-104">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="5e5ba-105">可以使用 `DataGridView` 控件来显示少量数据的只读视图，或者可以缩放该控件以显示大型数据集的可编辑视图。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-105">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="5e5ba-106">可以使用多种方法扩展 `DataGridView` 控件，以便将自定义行为置入你的应用程序中。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-106">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="5e5ba-107">例如，可以以编程方式指定自己的排序算法，并且可以创建自己的单元格类型。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-107">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="5e5ba-108">可以通过在多个属性之间进行选择来轻松地自定义 `DataGridView` 控件的外观。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-108">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="5e5ba-109">许多数据存储类型均可用作数据源，或者，`DataGridView` 控件可以在不绑定任何数据源的情况下进行操作。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-109">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="5e5ba-110">本节中的主题介绍可用于将 `DataGridView` 功能构建到应用程序中的概念和技术。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-110">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5e5ba-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="5e5ba-111">In This Section</span></span>  
 [<span data-ttu-id="5e5ba-112">DataGridView 控件概述</span><span class="sxs-lookup"><span data-stu-id="5e5ba-112">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="5e5ba-113">提供一些主题，介绍 Windows 窗体 `DataGridView` 控件的体系结构和核心概念。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-113">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="5e5ba-114">Windows 窗体 DataGridView 控件中的默认功能</span><span class="sxs-lookup"><span data-stu-id="5e5ba-114">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5e5ba-115">描述 Windows 窗体 `DataGridView` 控件在绑定到数据源时的默认外观和行为。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-115">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="5e5ba-116">Windows 窗体 DataGridView 控件中的列类型</span><span class="sxs-lookup"><span data-stu-id="5e5ba-116">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5e5ba-117">描述 Windows 窗体 `DataGridView` 控件中用于显示数据和允许用户修改或添加数据的列类型。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-117">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="5e5ba-118">Windows 窗体 DataGridView 控件中的基本列、行和单元格功能</span><span class="sxs-lookup"><span data-stu-id="5e5ba-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="5e5ba-119">提供一些主题，描述常用的单元格、行和列属性。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-119">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="5e5ba-120">Windows 窗体 DataGridView 控件中的基本格式设置和样式设置</span><span class="sxs-lookup"><span data-stu-id="5e5ba-120">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5e5ba-121">提供一些主题，描述如何修改该控件的基本外观和单元数据的显示格式。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-121">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="5e5ba-122">在 Windows 窗体 DataGridView 控件中显示数据</span><span class="sxs-lookup"><span data-stu-id="5e5ba-122">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5e5ba-123">提供一些主题，描述如何手动或从外部数据源向控件填充数据。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-123">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="5e5ba-124">调整 Windows 窗体 DataGridView 控件中列和行的大小</span><span class="sxs-lookup"><span data-stu-id="5e5ba-124">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5e5ba-125">提供一些主题，描述可如何自动调整行和列的大小，以便适应单元格内容，或适应该控件的可用宽度。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-125">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="5e5ba-126">在 Windows 窗体 DataGridView 控件中对数据进行排序</span><span class="sxs-lookup"><span data-stu-id="5e5ba-126">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5e5ba-127">提供介绍控件中的排序功能的主题。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-127">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="5e5ba-128">Windows 窗体 DataGridView 控件中的数据输入</span><span class="sxs-lookup"><span data-stu-id="5e5ba-128">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5e5ba-129">提供一些主题，介绍如何改变用户添加和修改控件中数据的方式。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-129">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="5e5ba-130">Windows 窗体 DataGridView 控件的选项和剪贴板使用</span><span class="sxs-lookup"><span data-stu-id="5e5ba-130">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5e5ba-131">提供一些主题，介绍控件中的单元格、行和列选择功能。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-131">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="5e5ba-132">使用 Windows 窗体 DataGridView 控件中的单元格、行和列编程</span><span class="sxs-lookup"><span data-stu-id="5e5ba-132">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="5e5ba-133">提供一些主题，介绍如何使用单元格、行和列对象进行编程。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-133">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="5e5ba-134">自定义 Windows 窗体 DataGridView 控件</span><span class="sxs-lookup"><span data-stu-id="5e5ba-134">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5e5ba-135">提供一些主题，介绍自定义绘制 `DataGridView` 单元格和行，以及创建派生的单元、列和行类型。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-135">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="5e5ba-136">Windows 窗体 DataGridView 控件中的性能优化</span><span class="sxs-lookup"><span data-stu-id="5e5ba-136">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5e5ba-137">提供一些主题，介绍如何在使用大量数据时，有效地使用控件以避免性能问题。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-137">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="5e5ba-138">Windows 窗体 DataGridView 控件中的默认键盘和鼠标处理</span><span class="sxs-lookup"><span data-stu-id="5e5ba-138">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5e5ba-139">介绍用户可如何通过键盘和鼠标与 `DataGridView` 控件进行交互。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-139">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="5e5ba-140">Windows 窗体 DataGridView 控件和 DataGrid 控件之间的区别</span><span class="sxs-lookup"><span data-stu-id="5e5ba-140">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="5e5ba-141">描述 `DataGridView` 控件如何改进和替换 <xref:System.Windows.Forms.DataGrid> 控件。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-141">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="5e5ba-142">另请参阅将[设计器与 Windows 窗体 DataGridView 控件结合使用](using-the-designer-with-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-142">Also see [Using the Designer with the Windows Forms DataGridView Control](using-the-designer-with-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5e5ba-143">参考</span><span class="sxs-lookup"><span data-stu-id="5e5ba-143">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="5e5ba-144">提供关于 <xref:System.Windows.Forms.DataGridView> 控件的参考文档。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-144">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="5e5ba-145">提供关于 <xref:System.Windows.Forms.BindingSource> 组件的参考文档。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-145">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="5e5ba-146"><xref:System.Windows.Forms.DataGridView> 控件和 <xref:System.Windows.Forms.BindingSource> 组件设计为需紧密协作。</span><span class="sxs-lookup"><span data-stu-id="5e5ba-146">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e5ba-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e5ba-147">See also</span></span>

- [<span data-ttu-id="5e5ba-148">在 Windows 窗体上使用的控件</span><span class="sxs-lookup"><span data-stu-id="5e5ba-148">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
