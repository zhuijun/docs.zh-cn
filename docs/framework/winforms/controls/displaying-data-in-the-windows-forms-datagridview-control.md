---
title: 在 DataGridView 控件中显示数据
description: 了解如何使用 Windows 窗体 DataGridView 控件显示来自各种外部数据源的数据。
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: a0f3e6627290521b8c10477c31459f1486e79162
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174570"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="5cf91-103">在 Windows 窗体 DataGridView 控件中显示数据</span><span class="sxs-lookup"><span data-stu-id="5cf91-103">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5cf91-104">`DataGridView`控件用于显示来自各种外部数据源的数据。</span><span class="sxs-lookup"><span data-stu-id="5cf91-104">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="5cf91-105">此外，也可以向控件添加行和列，并手动填充数据。</span><span class="sxs-lookup"><span data-stu-id="5cf91-105">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="5cf91-106">将控件绑定到数据源时，可以基于数据源的架构自动生成列。</span><span class="sxs-lookup"><span data-stu-id="5cf91-106">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="5cf91-107">如果这些列没有按您所需的方式显示，您可以隐藏、删除或重新排列这些列。</span><span class="sxs-lookup"><span data-stu-id="5cf91-107">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="5cf91-108">您还可以添加未绑定的列，以显示来自数据源的补充数据。</span><span class="sxs-lookup"><span data-stu-id="5cf91-108">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="5cf91-109">此外，您还可以使用标准格式（如货币格式) ）显示数据，也可以自定义显示格式以显示数据，但是您需要 (如更改负数的背景色，或将字符串值替换为) 的相应图像 (。</span><span class="sxs-lookup"><span data-stu-id="5cf91-109">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5cf91-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="5cf91-110">In This Section</span></span>  
 [<span data-ttu-id="5cf91-111">Windows 窗体 DataGridView 控件中的数据显示模式</span><span class="sxs-lookup"><span data-stu-id="5cf91-111">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5cf91-112">介绍用于用数据填充控件的选项。</span><span class="sxs-lookup"><span data-stu-id="5cf91-112">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="5cf91-113">Windows 窗体 DataGridView 控件中的数据格式设置</span><span class="sxs-lookup"><span data-stu-id="5cf91-113">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5cf91-114">描述用于设置单元格显示值格式的选项。</span><span class="sxs-lookup"><span data-stu-id="5cf91-114">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="5cf91-115">演练：创建未绑定的 Windows 窗体 DataGridView 控件</span><span class="sxs-lookup"><span data-stu-id="5cf91-115">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5cf91-116">描述如何用数据手动填充控件。</span><span class="sxs-lookup"><span data-stu-id="5cf91-116">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="5cf91-117">如何：将数据绑定到 Windows 窗体 DataGridView 控件</span><span class="sxs-lookup"><span data-stu-id="5cf91-117">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5cf91-118">介绍如何通过将数据绑定到 `BindingSource` ，其中包含从数据库中提取的信息，使用数据填充控件。</span><span class="sxs-lookup"><span data-stu-id="5cf91-118">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="5cf91-119">如何：在已绑定数据的 Windows 窗体 DataGridView 控件中自动生成列</span><span class="sxs-lookup"><span data-stu-id="5cf91-119">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="5cf91-120">描述如何基于绑定数据源自动生成列。</span><span class="sxs-lookup"><span data-stu-id="5cf91-120">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="5cf91-121">如何：从 Windows 窗体 DataGridView 控件中移除自动生成的列</span><span class="sxs-lookup"><span data-stu-id="5cf91-121">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="5cf91-122">介绍如何隐藏或删除从绑定数据源自动生成的列。</span><span class="sxs-lookup"><span data-stu-id="5cf91-122">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="5cf91-123">如何：更改 Windows 窗体 DataGridView 控件中列的顺序</span><span class="sxs-lookup"><span data-stu-id="5cf91-123">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5cf91-124">描述如何重新排列从绑定数据源自动生成的列。</span><span class="sxs-lookup"><span data-stu-id="5cf91-124">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="5cf91-125">如何：将未绑定的列添加到已绑定数据的 Windows 窗体 DataGridView 控件</span><span class="sxs-lookup"><span data-stu-id="5cf91-125">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="5cf91-126">介绍如何通过显示其他未绑定的列来补充绑定数据源中的数据。</span><span class="sxs-lookup"><span data-stu-id="5cf91-126">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="5cf91-127">如何：将对象绑定到 Windows 窗体 DataGridView 控件</span><span class="sxs-lookup"><span data-stu-id="5cf91-127">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="5cf91-128">介绍如何将控件绑定到任意对象的集合，以便每个对象显示在其自己的行中。</span><span class="sxs-lookup"><span data-stu-id="5cf91-128">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="5cf91-129">如何：访问绑定到 Windows 窗体 DataGridView 行的对象</span><span class="sxs-lookup"><span data-stu-id="5cf91-129">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="5cf91-130">介绍如何检索绑定到控件的特定行的对象。</span><span class="sxs-lookup"><span data-stu-id="5cf91-130">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="5cf91-131">演练：使用两个 Windows 窗体 DataGridView 控件创建一个主/详细信息窗体</span><span class="sxs-lookup"><span data-stu-id="5cf91-131">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="5cf91-132">介绍如何显示两个相关数据库表中的数据，以便一个控件中显示的值 `DataGridView` 依赖于其他控件中当前所选的行。</span><span class="sxs-lookup"><span data-stu-id="5cf91-132">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="5cf91-133">如何：在 Windows 窗体 DataGridView 控件中自定义数据格式设置</span><span class="sxs-lookup"><span data-stu-id="5cf91-133">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5cf91-134">描述如何处理 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> 事件以根据单元格的值更改单元格的外观。</span><span class="sxs-lookup"><span data-stu-id="5cf91-134">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5cf91-135">引用</span><span class="sxs-lookup"><span data-stu-id="5cf91-135">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="5cf91-136">提供关于 <xref:System.Windows.Forms.DataGridView> 控件的参考文档。</span><span class="sxs-lookup"><span data-stu-id="5cf91-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="5cf91-137">提供属性的参考文档 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 。</span><span class="sxs-lookup"><span data-stu-id="5cf91-137">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="5cf91-138">提供关于 <xref:System.Windows.Forms.BindingSource> 组件的参考文档。</span><span class="sxs-lookup"><span data-stu-id="5cf91-138">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5cf91-139">相关章节</span><span class="sxs-lookup"><span data-stu-id="5cf91-139">Related Sections</span></span>  
 [<span data-ttu-id="5cf91-140">Windows 窗体 DataGridView 控件中的数据输入</span><span class="sxs-lookup"><span data-stu-id="5cf91-140">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5cf91-141">提供一些主题，介绍如何改变用户添加和修改控件中数据的方式。</span><span class="sxs-lookup"><span data-stu-id="5cf91-141">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf91-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5cf91-142">See also</span></span>

- [<span data-ttu-id="5cf91-143">DataGridView 控件</span><span class="sxs-lookup"><span data-stu-id="5cf91-143">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="5cf91-144">Windows 窗体 DataGridView 控件中的列类型</span><span class="sxs-lookup"><span data-stu-id="5cf91-144">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
