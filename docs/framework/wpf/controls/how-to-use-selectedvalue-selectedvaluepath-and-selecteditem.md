---
title: 如何：使用 SelectedValue、SelectedValuePath 和 SelectedItem
description: 了解如何使用 SelectedValue 和 SelectedValuePath 属性指定 Windows Presentation Foundation TreeView 的 SelectedItem 的值。
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
ms.openlocfilehash: ddac2455dee0bf69d25307340eddd5364e43e823
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166280"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="fe5b5-103">如何：使用 SelectedValue、SelectedValuePath 和 SelectedItem</span><span class="sxs-lookup"><span data-stu-id="fe5b5-103">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="fe5b5-104">此示例演示如何使用 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 和 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 属性来指定的的值 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> 。</span><span class="sxs-lookup"><span data-stu-id="fe5b5-104">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe5b5-105">示例</span><span class="sxs-lookup"><span data-stu-id="fe5b5-105">Example</span></span>  
 <span data-ttu-id="fe5b5-106"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>属性提供了一种 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 在中指定的的方法 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> 。</span><span class="sxs-lookup"><span data-stu-id="fe5b5-106">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="fe5b5-107"><xref:System.Windows.Controls.TreeView.SelectedItem%2A>表示集合中的一个对象 <xref:System.Windows.Controls.ItemsControl.Items%2A> ，并 <xref:System.Windows.Controls.TreeView> 显示选定项的单个属性的值。</span><span class="sxs-lookup"><span data-stu-id="fe5b5-107">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="fe5b5-108"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>属性指定属性的路径，该属性用于确定属性的值 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 。</span><span class="sxs-lookup"><span data-stu-id="fe5b5-108">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="fe5b5-109">本主题中的示例阐释了这一概念。</span><span class="sxs-lookup"><span data-stu-id="fe5b5-109">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="fe5b5-110">下面的示例演示一个 <xref:System.Windows.Data.XmlDataProvider> 包含雇员信息的。</span><span class="sxs-lookup"><span data-stu-id="fe5b5-110">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="fe5b5-111">下面的示例定义一个 <xref:System.Windows.HierarchicalDataTemplate> ，它显示的 `EmployeeName` 和 `EmployeeWorkDay` `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="fe5b5-111">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="fe5b5-112">请注意，不 <xref:System.Windows.HierarchicalDataTemplate> 会指定 `EmployeeNumber` 作为模板的一部分。</span><span class="sxs-lookup"><span data-stu-id="fe5b5-112">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="fe5b5-113">下面的示例演示一个 <xref:System.Windows.Controls.TreeView> ，它使用之前定义的， <xref:System.Windows.HierarchicalDataTemplate> 并将 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 属性设置为 `EmployeeNumber` 。</span><span class="sxs-lookup"><span data-stu-id="fe5b5-113">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="fe5b5-114">当你 `EmployeeName` 在中选择时 <xref:System.Windows.Controls.TreeView> ， <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 属性将返回 `EmployeeInfo` 对应于所选的数据项 `EmployeeName` 。</span><span class="sxs-lookup"><span data-stu-id="fe5b5-114">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="fe5b5-115">但是，由于将 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 此的 <xref:System.Windows.Controls.TreeView> 设置为，因此将 `EmployeeNumber` <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 设置为 `EmployeeNumber` 。</span><span class="sxs-lookup"><span data-stu-id="fe5b5-115">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="fe5b5-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe5b5-116">See also</span></span>

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="fe5b5-117">TreeView 概述</span><span class="sxs-lookup"><span data-stu-id="fe5b5-117">TreeView Overview</span></span>](treeview-overview.md)
- [<span data-ttu-id="fe5b5-118">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="fe5b5-118">How-to Topics</span></span>](treeview-how-to-topics.md)
