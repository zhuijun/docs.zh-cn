---
title: 数据绑定
description: 了解如何使用 Windows 窗体中的数据绑定来显示和更改窗体上控件中的数据源中的信息。
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: 3dfce24147caf9b138916ca8dc3b7a9010439f58
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325541"
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="2688d-103">Windows 窗体数据绑定</span><span class="sxs-lookup"><span data-stu-id="2688d-103">Windows Forms Data Binding</span></span>
<span data-ttu-id="2688d-104">Windows 窗体中的数据绑定使你可以显示和更改窗体上的控件中的数据源的信息。</span><span class="sxs-lookup"><span data-stu-id="2688d-104">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="2688d-105">可以绑定到传统数据源和几乎任何包含数据的结构。</span><span class="sxs-lookup"><span data-stu-id="2688d-105">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2688d-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="2688d-106">In This Section</span></span>  
 [<span data-ttu-id="2688d-107">数据绑定和 Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="2688d-107">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)  
 <span data-ttu-id="2688d-108">提供了 Windows 窗体中的数据绑定概述。</span><span class="sxs-lookup"><span data-stu-id="2688d-108">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="2688d-109">Windows 窗体支持的数据源</span><span class="sxs-lookup"><span data-stu-id="2688d-109">Data Sources Supported by Windows Forms</span></span>](data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="2688d-110">介绍了可以与 Windows 窗体一起使用的数据源。</span><span class="sxs-lookup"><span data-stu-id="2688d-110">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="2688d-111">与数据绑定相关的接口</span><span class="sxs-lookup"><span data-stu-id="2688d-111">Interfaces Related to Data Binding</span></span>](interfaces-related-to-data-binding.md)  
 <span data-ttu-id="2688d-112">介绍了几种与 Windows 窗体数据绑定一起使用的接口。</span><span class="sxs-lookup"><span data-stu-id="2688d-112">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="2688d-113">如何：在 Windows 窗体中导航数据</span><span class="sxs-lookup"><span data-stu-id="2688d-113">How to: Navigate Data in Windows Forms</span></span>](how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="2688d-114">演示如何在数据源中的项之间进行导航。</span><span class="sxs-lookup"><span data-stu-id="2688d-114">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="2688d-115">Windows 窗体数据绑定中的更改通知</span><span class="sxs-lookup"><span data-stu-id="2688d-115">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="2688d-116">描述了 Windows 窗体数据绑定的不同类型的更改通知。</span><span class="sxs-lookup"><span data-stu-id="2688d-116">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="2688d-117">如何：实现 INotifyPropertyChanged 接口</span><span class="sxs-lookup"><span data-stu-id="2688d-117">How to: Implement the INotifyPropertyChanged Interface</span></span>](how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="2688d-118">演示如何实现 <xref:System.ComponentModel.INotifyPropertyChanged> 接口。</span><span class="sxs-lookup"><span data-stu-id="2688d-118">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="2688d-119">该接口与属性在业务对象上更改的绑定控件通信</span><span class="sxs-lookup"><span data-stu-id="2688d-119">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="2688d-120">如何：应用 PropertyNameChanged 模式</span><span class="sxs-lookup"><span data-stu-id="2688d-120">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="2688d-121">演示如何将属性*名称*更改模式应用于 Windows 窗体用户控件的属性。</span><span class="sxs-lookup"><span data-stu-id="2688d-121">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="2688d-122">如何：实现 ITypedList 接口</span><span class="sxs-lookup"><span data-stu-id="2688d-122">How to: Implement the ITypedList Interface</span></span>](how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="2688d-123">演示如何通过实现 <xref:System.ComponentModel.ITypedList> 接口，启用可绑定列表的架构发现。</span><span class="sxs-lookup"><span data-stu-id="2688d-123">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="2688d-124">如何：实现 IListSource 接口</span><span class="sxs-lookup"><span data-stu-id="2688d-124">How to: Implement the IListSource Interface</span></span>](how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="2688d-125">演示如何实现 <xref:System.ComponentModel.IListSource> 接口，以创建可绑定的类，其不实现 <xref:System.Collections.IList>，但提供其他位置的列表。</span><span class="sxs-lookup"><span data-stu-id="2688d-125">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="2688d-126">如何：确保绑定到同一数据源的多个控件保持同步</span><span class="sxs-lookup"><span data-stu-id="2688d-126">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="2688d-127">演示如何处理 <xref:System.Windows.Forms.BindingSource.BindingComplete> 事件，以确保所有绑定到数据源的控件保持同步。</span><span class="sxs-lookup"><span data-stu-id="2688d-127">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="2688d-128">如何：确保子表中的选定行保持在正确的位置</span><span class="sxs-lookup"><span data-stu-id="2688d-128">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="2688d-129">演示如何确保在更改父表的字段时，选定的子表行不会更改。</span><span class="sxs-lookup"><span data-stu-id="2688d-129">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="2688d-130">另请参阅[与数据绑定相关的接口](interfaces-related-to-data-binding.md)，[如何：在 Windows 窗体中导航数据](how-to-navigate-data-in-windows-forms.md)和[如何：在 Windows 窗体上创建简单绑定控件](how-to-create-a-simple-bound-control-on-a-windows-form.md)。</span><span class="sxs-lookup"><span data-stu-id="2688d-130">Also see [Interfaces Related to Data Binding](interfaces-related-to-data-binding.md), [How to: Navigate Data in Windows Forms](how-to-navigate-data-in-windows-forms.md), and [How to: Create a Simple-Bound Control on a Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2688d-131">参考</span><span class="sxs-lookup"><span data-stu-id="2688d-131">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="2688d-132">描述表示可绑定组件和数据源之间的绑定的类。</span><span class="sxs-lookup"><span data-stu-id="2688d-132">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="2688d-133">描述用来封装数据源以绑定到控件的类。</span><span class="sxs-lookup"><span data-stu-id="2688d-133">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2688d-134">相关章节</span><span class="sxs-lookup"><span data-stu-id="2688d-134">Related Sections</span></span>  
 [<span data-ttu-id="2688d-135">BindingSource 组件</span><span class="sxs-lookup"><span data-stu-id="2688d-135">BindingSource Component</span></span>](./controls/bindingsource-component.md)  
 <span data-ttu-id="2688d-136">包含演示如何使用 <xref:System.Windows.Forms.BindingSource> 组件的主题列表。</span><span class="sxs-lookup"><span data-stu-id="2688d-136">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="2688d-137">DataGridView 控件</span><span class="sxs-lookup"><span data-stu-id="2688d-137">DataGridView Control</span></span>](./controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="2688d-138">提供演示如何使用可绑定的 datagrid 控件的主题列表。</span><span class="sxs-lookup"><span data-stu-id="2688d-138">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="2688d-139">另请参阅[在 Visual Studio 中访问数据](/visualstudio/data-tools/accessing-data-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="2688d-139">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
